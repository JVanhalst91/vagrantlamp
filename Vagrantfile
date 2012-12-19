Vagrant::Config.run do |config|

  # Box
  config.vm.box = "centos"
  config.vm.box_url = "https://dl.dropbox.com/u/7225008/Vagrant/CentOS-6.3-x86_64-minimal.box"

  # Boot with a GUI so you can see the screen. (Default is headless)
  # config.vm.boot_mode = :gui

  # Netwerk
  config.vm.host_name = "lampsrv"
  config.vm.network :hostonly, "192.168.56.20"
  config.vm.forward_port 80, 8080
  config.vm.share_folder "www", "/var/www/html", "www"

  config.vm.provision :chef_solo do |chef|
    chef.cookbooks_path = "cookbooks"
    chef.add_recipe "yum"
    chef.add_recipe "openssl"
    chef.add_recipe "apache2"
    chef.add_recipe "mysql"
    chef.add_recipe "mysql::server"
    chef.add_recipe "php"
    chef.add_recipe "php::module_apc"
    chef.add_recipe "php::module_curl"
    chef.add_recipe "php::module_mysql"
    chef.add_recipe "apache2::mod_php5"
    chef.add_recipe "apache2::mod_rewrite"
    chef.json = {
        :mysql => {
            :server_root_password => 'root',
	    :server_repl_password => 'root',
	    :server_debian_password => 'root',
            :bind_address => '127.0.0.1'
        }
    }    
   end

end
