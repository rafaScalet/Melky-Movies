# -*- mode: ruby -*-p
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/jammy64"

  config.vm.network "forwarded_port", guest: 80, host: 8080

  config.vm.provision "shell", inline: <<-SHELL
    echo 'Updating the System'
    apt update && apt upgrade -y

    echo 'Installing Docker'
    apt install docker.io docker-compose-v2 docker-buildx -y

    echo 'Installing Git'
    apt install git -y

    echo 'Activating Docker'
    systemctl enable --now docker

    echo 'Enable rootless Docker'
    usermod -aG docker vagrant

    echo 'Cloning the project'
    git clone https://github.com/rafaScalet/Melky-Movies

    echo 'Configuring project'
    chown -R vagrant: Melky-Movies
    git -C Melky-Movies submodule update --init
  SHELL
end
