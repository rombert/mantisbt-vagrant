# -*- mode: ruby -*-
# vim: set ft=ruby tabstop=2 expandtab:

Vagrant::Config.run do |config|
  config.vm.box = "precise32"
  config.vm.box_url = "http://files.vagrantup.com/precise32.box"
  
  # TODO:
  #  - apt-get update before installing stuff; mysql installation fails otherwise

  config.vm.provision :chef_solo do |chef|
    chef.add_recipe "apache2"
    chef.add_recipe "mysql"
    chef.add_recipe "mysql::server"
    chef.add_recipe "git"
    chef.add_recipe "mantisbt"
    chef.add_recipe "php"
    chef.add_recipe "php::module_mysql"
    chef.add_recipe "apache2::mod_php5"

    chef.json = { 
      :apache => { 
        :default_site_enabled => true 
      },
      :mysql => {
        :server_root_password => 'toor',
        :server_repl_password => 'toor',
        :server_debian_password => 'toor',
        :bind_address => '127.0.0.1'
      },
      :git => {
        :repository => "https://github.com/mantisbt/mantisbt.git",
        :reference => "master",
        :action => "checkout",
        :destination => "/home/vagrant/mantisbt"
      }
    }
    
  end

  config.vm.forward_port 80, 8888
  
end
