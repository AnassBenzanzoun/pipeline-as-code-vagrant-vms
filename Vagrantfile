# -*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant.configure("2") do |config|
    config.vm.define "nexus" do |nexus|
      nexus.vm.box = "geerlingguy/centos7"
      nexus.vm.network "public_network"
      nexus.vm.provider "virtualbox" do |vb|
        vb.memory = "2048"
        vb.cpus = "2"
      end
      nexus.vm.provision "shell", path: "nexus.sh"
    end
  
    config.vm.define "sonar_qube" do |sonar_qube|
      sonar_qube.vm.box = "bento/ubuntu-22.04"
      sonar_qube.vm.network "public_network"
      sonar_qube.vm.provider "virtualbox" do |vb|
        vb.memory = "2048"
        vb.cpus = "2"
      end
      sonar_qube.vm.provision "shell", path: "sonar_qube.sh"
    end
  
    config.vm.define "jenkins" do |jenkins|
      jenkins.vm.box = "bento/ubuntu-22.04"
      jenkins.vm.network "public_network"
      jenkins.vm.provider "virtualbox" do |vb|
        vb.memory = "1600"
        vb.cpus = "2"
      end
      jenkins.vm.provision "shell", path: "jenkins.sh"
    end
  end