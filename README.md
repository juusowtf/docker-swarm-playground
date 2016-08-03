# docker-swarm-playground

A Vagrant environment for testing Docker Swarm mode in Docker 1.12.

## Requirements

- Vagrant
- Virtualbox
- Ansible

## Setup

```shell
ansible-galaxy install -r roles.yml
vagrant up
ansible-playbook provision.yml
```

## Checking if everything is setup

```shell
ansible managers -m shell -a "docker node ls"
```

It should show you all the nodes in the swarm.
