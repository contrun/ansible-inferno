# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.synced_folder ".", "/vagrant", type: "nfs"

  config.vm.box = "debian/jessie64"
  config.vm.box_version = "8.5.0"
  config.vm.box_check_update = false
  config.ssh.forward_agent = true
  config.ssh.forward_x11 = true

  config.vm.hostname = "inferno"
  config.vm.network "private_network", ip: "192.168.33.10"

  config.vm.define "inferno"

  config.vm.provider "virtualbox" do |vb|
    vb.name = "inferno"
    vb.customize ["modifyvm", :id, "--memory", "512"]
  end

  config.vm.provision "ansible" do |ansible|
    ansible.verbose = "vvv"
    ansible.playbook = "site.yml"
    ansible.inventory_path = "inventory"
  end
end
