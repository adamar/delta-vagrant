# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.define "server" do |a|
    a.vm.box = "bkyoung/centos7"
    a.vm.hostname = 'server'

    a.vm.network :private_network, ip: "192.168.56.101"

    a.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--memory", 512]
      v.customize ["modifyvm", :id, "--name", "server"]
    end

    config.vm.synced_folder "~", "/home/vagrant/shared"

    config.vm.provision "shell", path: "provision-server"
    config.vm.provision "shell", path: "install-delta-server"

  end

  config.vm.define "agent" do |b|
    b.vm.box = "bkyoung/centos7"
    b.vm.hostname = 'agent'

    b.vm.network :private_network, ip: "192.168.56.102"

    b.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--memory", 512]
      v.customize ["modifyvm", :id, "--name", "agent"]
    end

    config.vm.synced_folder "~", "/home/vagrant/shared"

    config.vm.provision "shell", path: "provision-agent"
    config.vm.provision "shell", path: "install-delta-agent"


  end
end
