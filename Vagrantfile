# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  config.vm.box = "debian/bullseye64"
  config.vm.network "private_network", ip: "192.168.33.10"

  # Provisioning script to install and configure Squid
  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update
    sudo apt-get install -y squid
    
    # Backup the original squid.conf file
    sudo cp /etc/squid/squid.conf /etc/squid/squid.conf.bak
    
    # Create a basic Squid configuration
    echo "http_port 3128" | sudo tee /etc/squid/squid.conf
    echo "acl localnet src 192.168.33.0/24" | sudo tee -a /etc/squid/squid.conf
    echo "http_access allow localnet" | sudo tee -a /etc/squid/squid.conf
    echo "http_access deny all" | sudo tee -a /etc/squid/squid.conf

    # Restart Squid to apply the new configuration
    sudo systemctl restart squid
  SHELL
end
