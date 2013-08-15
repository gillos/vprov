# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "jatest"
  config.vm.provision :shell, :path => "bootstrap.sh"
  config.vm.network :forwarded_port, host: 4567, guest: 80
  config.vm.box_url = "https://dl.dropboxusercontent.com/u/1146896/git-test/custom.box"
  config.vm.provider :vmware_fusion do |p|
    p.vmx['memsize'] = '2048'
    p.name = "fusion_vm"
  end
end
