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
    vb.memory = "4096"
  end
  #configure general provisioners on the machines
  config.vm.provision :docker
  config.vm.provision :docker_compose
   
  #configure ci-server VM
  config.vm.define "ci-server" do |ciserver|
    ciserver.vm.network "private_network", ip: '192.168.33.61'
    ciserver.vm.hostname = "ci-server"
    ciserver.vm.provision :file, source:"./docker/docker-compose.ci.yml", destination: "/home/vagrant/docker-compose.yml"
    ciserver.vm.provision :docker_compose, yml:"/home/vagrant/docker-compose.yml", run:"always"
    ciserver.vm.provision :shell, inline: 'sudo chmod 777 /var/run/docker.sock'
  end

   #configure ci-server VM
   config.vm.define "cd-server" do |cdserver|
    cdserver.vm.network "private_network", ip: '192.168.33.62'
    cdserver.vm.hostname = "cd-server"
    cdserver.vm.provision :file, source:"./docker/docker-compose.cd.yml", destination: "/home/vagrant/docker-compose.yml"
    cdserver.vm.provision :docker_compose, yml:"/home/vagrant/docker-compose.yml", run:"always"
    cdserver.vm.provision :shell, inline: 'sudo chmod 777 /var/run/docker.sock'
  end
 
end
