Chef Test VM Bootstrap using Vagrant and Chef
---------------------------------------------

Bootstrap process for testing Chef server-client interactions and recipies, using Vagrant for setup. 

Steps:

- Setup precise64 virtualBox machines using vagrant
- use vagrant chef-solo to use the chef-server bootstrap cookbooks to install chef

- [TODO:] Automated fix for bad init scripts issue in Chef.   

    cd /usr/bin
    ln -s /usr/sbin/chef-server-webui chef-server-webui
    ln -s /usr/sbin/chef-server chef-server

    # tip from https://github.com/tdegrunt/vagrant-chef-server-bootstrap

- [TODO:] Setup chef-clients that pull from the above chef server. 
- [TODO:] Setup proper knife settings and (maybe) a dev vm. 

