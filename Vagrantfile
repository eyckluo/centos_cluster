# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box_check_update = false
  (1...4).each do|i|
    config.vm.define "node-#{i}" do |node|
      node.vm.box = "base/centos7"
      node.vm.hostname = "node-#{i}"
      node.vm.network "public_network"
    end
  end
end
