# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
#
#Vagrant::DEFAULT_SERVER_URL.replace('https://vagrantcloud.com')
Vagrant.configure("2") do |config|
    config.vm.boot_timeout = 500
  config.vm.define "dockertest" do |dockertest|
    dockertest.vm.box = "bento/ubuntu-16.04"
    dockertest.vm.network "private_network", ip: "192.167.10.75"
	dockertest.vm.hostname = "dockertest"
	dockertest.vm.provider "virtualbox" do |vb|
      vb.memory = "2048"
	  vb.name = "dockertest"
      vb.cpus = 2
      vb.customize ["modifyvm", :id, "--cableconnected1", "on"]
    end
	dockertest.vm.provision "shell", run: "always", inline: <<-SHELL
      sudo swapoff -a
      sudo sed -i '/ swap / s/^\(.*\)$/#\1/g' /etc/fstab
      sudo echo "192.167.10.75 dockertest" >> /etc/hosts
    SHELL
  end
#  config.vm.define "k8snode1" do |k8snode1|
#    k8snode1.vm.box = "bento/ubuntu-16.04"
#    k8snode1.vm.network "private_network", ip: "192.167.10.71"
#	k8snode1.vm.hostname = "k8snode1"
#	k8snode1.vm.provider "virtualbox" do |vb|
#      vb.memory = "2048"
#	  vb.name = "k8snode1"
#      vb.cpus = 2
#      vb.customize ["modifyvm", :id, "--cableconnected1", "on"]
#    end
#	k8snode1.vm.provision "shell", run: "always",inline: <<-SHELL
#      sudo swapoff -a
#      sudo sed -i '/ swap / s/^\(.*\)$/#\1/g' /etc/fstab
#      sudo echo "192.167.10.70 k8smaster" >> /etc/hosts
#	  sudo echo "192.167.10.71 k8snode1" >> /etc/hosts
#    SHELL
#  end
  
end