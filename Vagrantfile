Vagrant.configure("2") do |config|
  config.vm.provider "virtualbox" do |v|
    v.name = "desafio03"
  end
  config.vm.box = "hashicorp/bionic64"
  config.vm.network "public_network"
  config.vm.network "forwarded_port", guest: 80, host: 8050
  config.vm.synced_folder "./site", "/tmp/site"
  
  config.vm.provision "shell", inline: <<-SHELL
     sudo apt update 
     sudo apt install docker.io -y 
     sudo service docker start
     sudo docker run --name nginx -v /tmp/site/:/usr/share/nginx/html -d -p 8050:80 nginx
  SHELL
  
end
