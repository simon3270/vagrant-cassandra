require 'rbconfig'
require 'yaml'
inventory = YAML.load_file("inventory.yml")


Vagrant.configure("2") do |config|

  config.vm.box = "centos/7"
  
  config.vm.synced_folder ".", "/vagrant"

  config.vm.define "node1" do |machine|
    machine.vm.network "private_network", ip: inventory["all"]["hosts"]["node1"]["ansible_ssh_host"]
	machine.vm.provider "libvirt" do |vbox|
		vbox.memory = "768"
		vbox.cpus = "1"
	end
  end

  config.vm.define "node2" do |machine|
    machine.vm.network "private_network", ip: inventory["all"]["hosts"]["node2"]["ansible_ssh_host"]
	machine.vm.provider "libvirt" do |vbox|
		vbox.memory = "768"
		vbox.cpus = "1"
	end
  end
  
  config.vm.define "node3" do |machine|
    machine.vm.network "private_network", ip: inventory["all"]["hosts"]["node3"]["ansible_ssh_host"]
	machine.vm.provider "libvirt" do |vbox|
		vbox.memory = "768"
		vbox.cpus = "1"
	end
  end

  config.vm.define 'controller' do |machine|
    machine.vm.network "private_network", ip: inventory["all"]["hosts"]["controller"]["ansible_ssh_host"]
	machine.vm.provider "libvirt" do |vbox|
		vbox.memory = "768"
		vbox.cpus = "1"
	end

    machine.vm.provision :ansible_local do |ansible|
      ansible.playbook       = "CassandraCluster.yml"
      ansible.verbose        = true
      ansible.install        = true
      ansible.limit          = "all" # or only "nodes" group, etc.
      ansible.inventory_path = "inventory.yml"
    end
  end

end
