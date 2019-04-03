# encoding: utf-8
# -*- mode: ruby -*-
# vi: set ft=ruby :
# Box / OS
VAGRANT_BOX = 'debian/jessie64'
# Memorable name for your
VM_NAME = 'srv-web-1'
# Host folder to sync
HOST_PATH = '/home/franck/code/perso/cesi/code'
# Where to sync to on Guest — 'vagrant' is the default user name
GUEST_PATH = '/home/vagrant'
# # VM Port — uncomment this to use NAT instead of DHCP
# VM_PORT = 8080
Vagrant.configure(2) do |config|
  # Vagrant box from Hashicorp
  config.vm.box = VAGRANT_BOX
  
  # Actual machine name
  config.vm.hostname = VM_NAME
  # Set VM name in Virtualbox
  config.vm.provider "virtualbox" do |v|
    v.name = VM_NAME
    v.memory = 512
  end
  config.vm.network "private_network", type: "dhcp"
  # Sync folder
  #config.vm.synced_folder HOST_PATH, GUEST_PATH
  # Disable default Vagrant folder, use a unique path per project
  #config.vm.synced_folder '.', '/home/'+VM_USER+'', disabled: true
  # Install
  config.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt-get install -y git
    apt-get upgrade -y
    apt-get autoremove -y
  SHELL
end
