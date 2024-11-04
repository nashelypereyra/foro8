 # -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
    # Usa una caja de Ubuntu como base
    config.vm.box = "ubuntu/bionic64"
  
    # Configuración de la memoria RAM y CPU de la máquina virtual
    config.vm.provider "virtualbox" do |vb|
      vb.memory = "512"
      vb.cpus = 1
    end
  
    # Configura la sincronización de carpetas
    config.vm.synced_folder "./web", "/var/www/html"
  
    # Configura la red para acceder al servidor web
    config.vm.network "private_network", ip: "192.168.33.10"
  
    # Provisiona el servidor web Apache
    config.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update
      sudo apt-get install -y apache2
      echo "<h1>¡Hola Mundo!</h1>" | sudo tee /var/www/html/index.html
      sudo systemctl restart apache2
    SHELL
  end
  