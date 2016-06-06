# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "obihann/lamp"

  config.vm.synced_folder "www", "/var/www", create: true
      :owner=> 'vagrant', :group=>'www-data', :mount_options => ['dmode=775', 'fmode=775']
  config.vm.network "private_network", type: "dhcp" 

  config.vm.provision "puppet" do |puppet|
    puppet.manifests_path = "puppet/manifests"
    puppet.module_path = "puppet/modules"
  end

  config.push.define "atlas" do |push|
    push.app = "obihann/wordpress"
  end

  config.vm.provider "virtualbox" do |vb|
    vb.gui = true
    vb.memory = "1024"
    vb.name = "wordpress"
  end
end
