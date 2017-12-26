# -*- mode: ruby -*-
# vi: set ft=ruby :

$script = <<SHELL
  yum install -y git
  systemctl start docker
  docker pull gitlab/gitlab-ce
  docker pull jenkins
SHELL

Vagrant.configure("2") do |config|
  config.vm.box_check_update = false
  config.vm.define "master" do |node|
  	node.vm.box = "base/centos7"
    node.vm.hostname = "master"
    node.vm.network "public_network"
    node.vm.provision "shell", inline: $script
    node.vm.provider "virtualbox" do |v|
      v.memory = 4096
    end
  end
  (1...3).each do|i|
    config.vm.define "slave-#{i}" do |node|
      node.vm.box = "base/centos7"
      node.vm.hostname = "slave-#{i}"
      node.vm.network "public_network"
      node.vm.provider "virtualbox" do |v|
        v.memory = 1024
      end
    end
  end
end
