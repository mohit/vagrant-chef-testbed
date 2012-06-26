Chef Test VM Bootstrap using Vagrant and Chef
---------------------------------------------

Bootstrap process for testing Chef server-client interactions and recipies, using Vagrant for setup. 

- setup precise64 virtualBox machines using vagrant
- use vagrant chef-solo to use the chef-server bootstrap cookbooks to install chef

TODO:

- automated fix for bad init scripts issue in Chef.

    ```
    cd /usr/bin
    ln -s /usr/sbin/chef-server-webui chef-server-webui
    ln -s /usr/sbin/chef-server chef-server

    # tip from https://github.com/tdegrunt/vagrant-chef-server-bootstrap
    ```
    
- setup chef-clients that pull from the above chef server. 
- setup proper knife settings and (maybe) a dev vm. 


- for chefClient:

   - after running ```knife configure -i``` on chefServer, run something like

   ``` knife bootstrap 192.168.33.2 --sudo -x vagrant -i ~/.vagrant/unsecure_private_key ```

   to bootstrap chefClient.


