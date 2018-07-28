    # -*- mode: ruby -*-
    # vi: set ft=ruby :
     
    Vagrant.configure("2") do |config|
        config.vm.box = "hashicorp/precise32"
		
		config.vm.provider "virtualbox" do |v|
 		v.memory = 1024
  		v.cpus = 1
	end
     
        # Configs for web1
        config.vm.define :web1 do |web1_config|
            web1_config.vm.provider :virtualbox do |vb_config|
                vb_config.name = "web1"
            end
            web1_config.vm.hostname = "web1"
            web1_config.vm.network "private_network", ip: "192.168.50.10"
            web1_config.vm.provision :shell, path: "bootstrap-apache.sh"
        end
     
        # Configs for web2
        config.vm.define :web2 do |web2_config|
            web2_config.vm.provider :virtualbox do |vb_config|
                vb_config.name = "web2"
            end
           web2_config.vm.hostname = "web2"
            web2_config.vm.network "private_network", ip: "192.168.50.20"
            web2_config.vm.provision :shell, path: "bootstrap-apache.sh"
        end
     
        # Configs for lb
        config.vm.define :lb do |lb_config|
            lb_config.vm.provider :virtualbox do |vb_config|
                vb_config.name = "lb"
            end
            lb_config.vm.hostname = "lb"
            lb_config.vm.network :forwarded_port, guest: 80, host: 8080
            lb_config.vm.network "private_network", ip: "192.168.50.30"
            lb_config.vm.provision :shell, path: "bootstrap-haproxy.sh"
        end
    end
