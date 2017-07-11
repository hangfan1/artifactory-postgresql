# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config| 
 
  config.vm.box = "ubuntu/xenial64"

  # Add forwarded ports
  config.vm.network "forwarded_port", guest: 8081, host: 8081

  config.vm.synced_folder ".", "/vagrant", disabled: false
  
  config.vm.provider "virtualbox" do |v|
    v.memory = 4096
    v.cpus = 2
  end 
  
  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "setup.yml"
  end
  
  config.vm.provision "docker" do |d|
    d.run "hello-world"
  end

  # Install the plugin: vagrant plugin install vagrant-docker-compose
  config.vm.provision :docker_compose, yml: "/vagrant/docker-compose.yml", rebuild: true, run: "always"

end
