# -*- mode: ruby -*-
# vi: set ft=ruby :

num_instances = 6
box_image = "debian/jessie64"

Vagrant.configure(2) do |config|

  (1..num_instances).each do |i|
    box_name = "swarm-node-#{i}"
    config.vm.define box_name do |env|
      env.vm.box = box_image
      env.vm.hostname = box_name

      env.vm.provider :virtualbox do |vb|
        vb.name = box_name
        vb.cpus = 1
        vb.memory = 1024
      end

      env.ssh.insert_key = false
      env.vm.network :private_network, ip: "192.168.37.10#{i}"
    end
  end

end
