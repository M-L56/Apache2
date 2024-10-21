# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "debian/bookworm64"
  config.vm.hostname = "www.192.168.57.10.nip.io"
  config.vm.network "private_network", bridge: "enp3s0", ip: "192.168.57.10"
  config.vm.synced_folder "htdocs", "/var/www/192.168.57.10.nip.io/html"
  config.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt-get install -y apache2
    cp -v /vagrant/apache2.conf /etc/apache2
    cp -v /vagrant/www.192.168.57.10.nip.io.conf /etc/apache2/sites-available
    a2ensite www.192.168.57.10.nip.io.conf
    systemctl reload apache2
  SHELL

end
