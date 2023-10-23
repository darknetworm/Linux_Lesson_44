# -*- mode: ruby -*-
# vim: set ft=ruby :
MACHINES = {
  :node1 => {
    :box_name => "ubuntu/focal64",
    :vm_name => "node1",
    :cpus => 2,
    :memory => 1024,
    :ip => "192.168.57.11",
  },
  :node2 => {
    :box_name => "ubuntu/focal64",
    :vm_name => "node2",
    :cpus => 2,
    :memory => 1024,
    :ip => "192.168.57.12",
  },
  :barman => {
    :box_name => "ubuntu/focal64",
    :vm_name => "barman",
    :cpus => 1,
    :memory => 1024,
    :ip => "192.168.57.13",
  },
}
Vagrant.configure("2") do |config|
  MACHINES.each do |boxname, boxconfig|
    config.vm.define boxname do |box|
      box.vm.box = boxconfig[:box_name]
      box.vm.host_name = boxconfig[:vm_name]
      box.vm.network "private_network", ip: boxconfig[:ip]
      box.vm.provider "virtualbox" do |v|
        v.memory = boxconfig[:memory]
        v.cpus = boxconfig[:cpus]
      end
      if boxconfig[:vm_name] == "barman"
        box.vm.provision "ansible" do |ansible|
          ansible.playbook = "provision.yml"
          ansible.inventory_path = "hosts"
          ansible.host_key_checking = "false"
          ansible.limit = "all"
        end
      end
    end
  end
end
