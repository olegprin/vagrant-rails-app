# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = '2'

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  #config.vm.box ='bento/centos-6.7'
  config.vm.box = 'geerlingguy/ubuntu1404'
  config.vm.synced_folder "scripts/", "/home/vagrant/scripts" 
  config.vm.provision :shell, path: "scripts/bootstrap.sh", privileged: false

  config.vm.boot_timeout = 600 
  config.ssh.insert_key = false
  config.ssh.private_key_path = '~/.vagrant.d/insecure_private_key'
 
  config.vm.provider :virtualbox do |v| 
    v.customize ['modifyvm', :id, '--groups', '/linux']
    v.destroy_unused_network_interfaces = true
  end 


  config.vm.define 'linux1' do |node|
    node.vm.hostname = 'linux1'
    node.vm.network 'private_network', ip: '10.10.10.10'

    config.vm.provider :virtualbox do |v| 
      v.name = 'linux1'
    end 

  end

end
