# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.define :master do |master|
    master.vm.box = "jatest"
    master.vm.provision :shell, :inline => "apt-get install -y puppet"
    master.vm.provision :puppet
    #master.vm.network :forwarded_port, host: 4567, guest: 80
    master.vm.network :private_network, ip: "192.168.110.2"
    master.vm.box_url = "https://dl.dropboxusercontent.com/u/1146896/git-test/custom.box"
    master.vm.provider :vmware_fusion do |p|
      p.vmx['memsize'] = '2048'
      p.name = "fusion_vm"
    end
  end
  config.vm.define :slave do |slave|
    slave.vm.box = "slave"
    slave.vm.provision :shell, :inline => "apt-get install -y puppet"
    slave.vm.provision "puppet_server" do |puppet|
      puppet.puppet_server = "192.168.110.2"
    end
    #slave.vm.network :forwarded_port, host: 4568, guest: 80
    slave.vm.network :private_network, ip: "192.168.110.3"
    slave.vm.box_url = "https://dl.dropboxusercontent.com/u/1146896/git-test/custom.box"
  end
end
