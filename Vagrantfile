# -*- mode: ruby -*-
# vi: set ft=ruby :

$script = <<-EOF
sudo apt-get update
sudo apt --fix-missing update
sudo apt upgrade -y
sudo apt install -y mc nginx
sudo apt install -y nodejs npm
git clone https://github.com/nathannmvr/MouraTech
cd ./MouraTech
npm install
npm run build
sudo mkdir /var/www/html/MouraTech
sudo cp -r build/. /var/www/html/MouraTech
EOF

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/jammy64"
  config.vm.network "private_network", ip: "192.168.56.123"
  config.vm.network "public_network"
  # config.vm.provision "shell", inline: "sudo apt update && sudo apt install nginx -y"
  config.vm.provision "shell", inline: $script
  # config.vm.provision "shell", path: /home/aluno/monta_ambiente.sh
  # config.vm.provision "ansible" do |ansible|
  #  ansible.playbook = "ambiente_playbook.yml"
  # end"""
  config.vm.provider "virtualbox" do |vbox_config|
    vbox_config.name = "servidorWebUbuntu"
    vbox_config.memory = 1024
    vbox_config.cpus    = 2
  end
end