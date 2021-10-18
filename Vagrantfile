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
  #configure provisioners on tha machine
  config.vm.provision :docker
  
  config.vm.define "server1" do |server1|
   server1.vm.network "private_network", ip: '192.168.33.60'
   server1.vm.hostname = "server1"
  end
  
end
