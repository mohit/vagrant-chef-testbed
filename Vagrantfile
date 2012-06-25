# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant::Config.run do |config|
   # All Vagrant configuration is done here. The most common configuration
   # options are documented and commented below. For a complete reference,
   # please see the online documentation at vagrantup.com.
   

   config.vm.define :chefServer do |chef_server|

     # Every Vagrant virtual environment requires a box to build off of.
     chef_server.vm.box = "precise64"

     # The url from where the 'config.vm.box' box will be fetched if it # doesn't already exist on the user's system.  # config.vm.box_url = "http://domain.com/path/to/above.box"
     chef_server.vm.box_url = "http://files.vagrantup.com/precise64.box"

     # Boot with a GUI so you can see the screen. (Default is headless)
     # config.vm.boot_mode = :gui

     # Assign this VM to a host-only network IP, allowing you to access it
     # via the IP. Host-only networks can talk to the host machine as well as
     # any other machines on the same network, but cannot be accessed (through this
     # network interface) by any external networks.
     chef_server.vm.network :hostonly, "192.168.33.10"
     chef_server.vm.host_name = "chefServer"

     # Assign this VM to a bridged network, allowing you to connect directly to a
     # network using the host's network device. This makes the VM appear as another
     # physical device on your network.
     # config.vm.network :bridged

     # Forward a port from the guest to the host, which allows for outside
     # computers to access the VM, whereas host only networking does not.
     chef_server.vm.forward_port 80, 9080
     chef_server.vm.forward_port 4000, 4000
     chef_server.vm.forward_port 4040, 4040

     # Share an additional folder to the guest VM. The first argument is
     # an identifier, the second is the path on the guest to mount the
     # folder, and the third is the path on the host to the actual folder.
     # config.vm.share_folder "v-data", "/vagrant_data", "../data"

     # Enable provisioning with chef solo, specifying a cookbooks path, roles
     # path, and data_bags path (all relative to this Vagrantfile), and adding 
     # some recipes and/or roles.
     #
     
     chef_server.vm.provision :chef_solo do |chef|
       #chef.recipe_url = "http://s3.amazonaws.com/chef-solo/bootstrap-latest.tar.gz"
       chef.cookbooks_path = "cookbooks"
       #chef.roles_path = "../locationlabs/roles"
       #chef.data_bags_path = "../locationlabs/data_bags"

       chef.run_list.clear
     
       # You may also specify custom JSON attributes:
       chef.json = {
            :chef_server => {
               :server_url => "http://localhost:4000",
               :webui_enabled => true
            }
       }

       chef.add_recipe "apt"
       chef.add_recipe "build-essential"
       chef.add_recipe "chef-server::rubygems-install"

     end
   end

   config.vm.define :chefClient do |chef_client|

      chef_client.vm.box = "precise64"

      chef_client.vm.forward_port 80, 9081
      chef_client.vm.network :hostonly, "192.168.33.2"
      chef_server.vm.host_name = "chefClient"

     # Enable provisioning with chef server, specifying the chef server URL,
     # and the path to the validation key (relative to this Vagrantfile).
     #
     # The Opscode Platform uses HTTPS. Substitute your organization for
     # ORGNAME in the URL and validation key.
     #
     # If you have your own Chef Server, use the appropriate URL, which may be
     # HTTP instead of HTTPS depending on your configuration. Also change the
     # validation key to validation.pem.
     
      #chef_client.vm.provision :chef_client do |chef|
         #chef.chef_server_url = "https://192.168.33.10/"
         #chef.validation_key_path = "chef-validator.pem"
      #end
     
     # If you're using the Opscode platform, your validator client is
     # ORGNAME-validator, replacing ORGNAME with your organization name.
     #
     # IF you have your own Chef Server, the default validation client name is
     # chef-validator, unless you changed the configuration.
     #
     #   chef.validation_client_name = "ORGNAME-validator"
   end

end
