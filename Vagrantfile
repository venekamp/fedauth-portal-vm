# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|
#  config.vm.box = "centos/7"
#  config.ssh.insert_key=false
#  config.vm.synced_folder ".", "/vagrant", disabled: true

  config.vm.box = "centos72-vbox-ga"
  config.vm.hostname = "portal"

  config.vm.provider "virtualbox" do |vbox|
    vbox.name = "portal"
    vbox.memory = "2048"
  end

  config.vm.network "forwarded_port", guest:443, host:4443

  config.vm.provision "shell", inline: <<-SHELL
    sudo yum update -y
  SHELL

  config.vm.provision "portal", type: "ansible" do |ansible|
    #ansible.verbose = "vvv"
    ansible.playbook = "ansible/portal.yml"
  end

  # The below provisioning is for personal use only. It can be
  # safely removed without affecting the portal provisioning.
  config.vm.provision "private", type: "ansible" do |ansible|
    ansible.playbook = "ansible/private.yml"
  end
end
