# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"
Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "ubuntu/bionic64"

  config.vm.provider "virtualbox" do |vb|
    vb.gui = true
    vb.memory = 4096
    vb.customize ["modifyvm", :id, "--accelerate3d", "on"]
    vb.customize ["modifyvm", :id, "--vram", "128"]
  end

  config.vm.synced_folder "/Users/brousch/Documents", "/home/vagrant/Documents", create: true, owner: "vagrant", group: "vagrant" 

  config.vm.provision "file", source: "./fonts", destination: "/home/vagrant/.fonts"

  config.vm.provision "shell", inline: <<-SHELL
    cd /home/vagrant
    sudo apt-get update && sudo apt-get upgrade
    sudo apt-get install -y vim unzip fonts-cabin fonts-lato fonts-linuxlibertine fonts-lobster inkscape lubuntu-core lubuntu-default-session lubuntu-default-settings lubuntu-desktop 
    sudo shutdown -r now
  SHELL

end
