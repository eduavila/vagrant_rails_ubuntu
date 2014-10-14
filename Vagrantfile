# -*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant.configure('2') do |config|
  config.vm.box      = 'hellobits-trusty64'
  config.vm.box_url  = 'http://files.hellobits.com/vagrant/hellobits-trusty64-virtualbox.box'
  config.vm.hostname = 'rails-dev-box'

  config.vm.network :forwarded_port, guest: 3000, host: 3005
  config.vm.network :forwarded_port, guest: 8080, host: 8085
  config.vm.network :forwarded_port, guest: 80, host: 8095
  config.vm.network :forwarded_port, guest: 5432 , host: 5433

  config.vm.synced_folder  "./", "/var/www/production", id: "vagrant-root",owner: "vagrant", group:  "www-data", mount_options: [ "dmode=775,fmode=664" ]



  config.vm.provision :puppet do |puppet|
    puppet.manifests_path = 'puppet/manifests'
    puppet.manifest_file = 'default.pp'
    puppet.module_path    = 'puppet/modules'
  end
end
