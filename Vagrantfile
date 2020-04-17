# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"
  config.vm.box_version = "20191030.0.0"
  config.vm.box_check_update = false

  config.vm.provider "virtualbox" do |vb|
    vb.cpus = 4
    vb.memory = "16384"
  end

  config.vm.synced_folder "./data", "/from-host", create: true, owner: "root", group: "root"

  config.vm.provision "file", source: "hust.list", destination: "/home/vagrant/hust.list"
  config.vm.provision "shell", inline: <<-SHELL
    mv /home/vagrant/hust.list /etc/apt/sources.list.d/hust.list
    apt-get update
    apt-get install -y build-essential
  SHELL
end
