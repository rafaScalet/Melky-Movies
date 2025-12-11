# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/jammy64"

  config.vm.provision "shell", inline: <<-SHELL
    echo 'Updating the System'
    apt update && apt upgrade -y

    echo 'Installing Docker'
    apt install docker.io docker-compose-v2 docker-buildx -y

    echo 'Activating Docker'
    systemctl enable --now docker

    echo 'Enable rootless Docker'
    usermod -aG docker vagrant
  SHELL
end
