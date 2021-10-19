# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"
  config.vm.boot_timeout = 1200
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "1024"
  end
  #configure general provisioners on the machines
  config.vm.provision :docker
  config.vm.provision :docker_compose

  #configure server-1 VM
  config.vm.define "server-1" do |server1|
    server1.vm.network "private_network", ip: '192.168.33.61'
    server1.vm.hostname = "server-1"
    server1.vm.provision "shell", path: "provision.sh" 
  end

  #configure server-2 VM
  config.vm.define "server-2" do |server2|
    server2.vm.network "private_network", ip: '192.168.33.62'
    server2.vm.hostname = "server-2"
  end
  
end
