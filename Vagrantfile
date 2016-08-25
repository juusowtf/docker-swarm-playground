# -*- mode: ruby -*-
# vi: set ft=ruby :

num_managers = 3
num_workers = 3
vm_cpus = 1
vm_memory = 1024

box_image = "debian/jessie64"

Vagrant.configure(2) do |config|
  config.ssh.insert_key = false
  config.vm.box = box_image

  (1..num_managers).each do |i|
    box_name = "manager-#{i}"
    config.vm.define box_name do |env|
      env.vm.hostname = box_name

      env.vm.provider :virtualbox do |vb|
        vb.name = box_name
        vb.cpus = vm_cpus
        vb.memory = vm_memory
      end

      env.vm.network :private_network, ip: "192.168.37.1#{i}"
    end
  end

  (1..num_workers).each do |i|
    box_name = "worker-#{i}"
    config.vm.define box_name do |env|
      env.vm.hostname = box_name

      env.vm.provider :virtualbox do |vb|
        vb.name = box_name
        vb.cpus = vm_cpus
        vb.memory = vm_memory
      end

      env.vm.network :private_network, ip: "192.168.37.1#{num_managers + i}"
    end
  end

end
