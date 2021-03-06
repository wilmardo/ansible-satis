# -*- mode: ruby -*-
# vi: set ft=ruby :
# vi: set tabstop=2 :
# vi: set shiftwidth=2 :

Vagrant.configure("2") do |config|

  vms = [
    { :name => "debian-jessie", :box => "debian/jessie64" },
    { :name => "debian-stretch", :box => "debian/stretch64" }
  ]

  conts = [
    { :name => "docker-debian-jessie", :docker => "hanxhx/vagrant-ansible:debian8" },
    { :name => "docker-debian-stretch", :docker => "hanxhx/vagrant-ansible:debian9" }
  ]

  config.vm.network "private_network", type: "dhcp"

  conts.each do |opts|
    config.vm.define opts[:name] do |m|
      m.vm.provider "docker" do |d|
        d.image = opts[:docker]
        d.remains_running = true
        d.has_ssh = true
      end
      m.vm.provision "ansible" do |ansible|
        ansible.playbook = "tests/test.yml"
        ansible.verbose = 'vv'
        ansible.sudo = true
      end
    end
  end

  vms.each do |opts|
    config.vm.define opts[:name] do |m|
      m.vm.box = opts[:box]
      m.vm.provider "virtualbox" do |v|
        v.cpus = 1
        v.memory = 256
      end
       m.vm.provision "ansible" do |ansible|
         ansible.playbook = "tests/test.yml"
         ansible.verbose = 'vv'
         ansible.sudo = true
       end
    end
  end
end
