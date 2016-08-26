# docker-swarm-playground

A Vagrant environment for testing Docker Swarm mode in Docker 1.12.

**NOTE:** This project is mainly meant for (me) testing how to set up a cluster in swarm mode with Ansible. If you want to only test the new features of v1.12, it's almost always better to just use Docker Machine via [Docker Toolbox](https://www.docker.com/products/docker-toolbox).

## Requirements

- Vagrant
- Virtualbox
- Ansible

## Setup

```shell
ansible-galaxy install -r roles.yml
vagrant up
ansible-playbook install-docker.yml
# Because of a bug in the jzmch.ansible-docker role, you have to reload the servers so Ansible can find the docker daemon.
# I will fix this soonish.
vagrant reload
ansible-playbook initialize-cluster.yml
```

## Checking if everything is setup

```shell
ansible managers -m shell -a "docker node ls"
```

## Adding new worker nodes

### Add them to inventory

```yaml
[workers]
new_worker ansible_host=<ip>
```

### Run add-worker-nodes.yml playbook

```shell
ansible-playbook add-worker-nodes.yml
```
