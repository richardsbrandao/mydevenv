# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  
  config.vm.define "node" do |node|
  	node.vm.box = "ubuntu/trusty64"
    node.ssh.forward_agent = true
    node.vm.hostname = 'node.vm'
    
    # Apps
    node.vm.network "forwarded_port", guest: 9000, host: 9000
    node.vm.network "private_network", ip: "192.168.33.20"

    node.vm.synced_folder "/home/richard/vagrant_sync/node", "/home/vagrant/projects"

  	node.vm.provision :ansible do |ansible|
  	  ansible.playbook       = './main.yml'
  	end
  end

  config.vm.define "ruby" do |ruby|
    ruby.vm.box = "ubuntu/trusty64"
    ruby.ssh.forward_agent = true
    ruby.vm.hostname = 'ruby.vm'
    
    # Apps
    ruby.vm.network "forwarded_port", guest: 3000, host: 3000
    ruby.vm.network "private_network", ip: "192.168.33.23"

    ruby.vm.synced_folder "/home/richard/vagrant_sync/ruby", "/home/vagrant/projects"

    ruby.vm.provision :ansible do |ansible|
      ansible.playbook       = './main.yml'
    end
  end

  config.vm.define "java" do |java|
    java.vm.box = "ubuntu/trusty64"
    java.ssh.forward_agent = true
    java.vm.hostname = 'java.vm'

    # Apps
    java.vm.network "forwarded_port", guest: 8080, host: 8080
    java.vm.network "private_network", ip: "192.168.33.22"

    java.vm.synced_folder "/home/richard/vagrant_sync/java", "/home/vagrant/projects"

    java.vm.provider "virtualbox" do |vb|
      vb.gui = true
      vb.memory = "3072" # 3 GB
    end  

    java.vm.provision :ansible do |ansible|
      ansible.playbook       = './main.yml'
    end
  end

  config.vm.define "elixir" do |elixir|
    elixir.vm.box = "ubuntu/trusty64"
    elixir.ssh.forward_agent = true
    elixir.vm.hostname = 'elixir.vm'

    # Apps
    elixir.vm.network "forwarded_port", guest: 4000, host: 4000
    elixir.vm.network "private_network", ip: "192.168.33.25"

    elixir.vm.synced_folder "/home/richard/vagrant_sync/elixir", "/home/vagrant/projects"

    elixir.vm.provision :ansible do |ansible|
      ansible.playbook       = './main.yml'
    end
  end
  
  config.vm.define "services" do |services|
  	services.vm.box = "ubuntu/trusty64"
    services.vm.hostname = 'services.vm'
    services.ssh.forward_agent = true
    
    # Mongo
    services.vm.network "forwarded_port", guest: 27017, host: 27017
    services.vm.network "private_network", ip: "192.168.33.21"

    services.vm.synced_folder "/home/richard/vagrant_sync/services", "/home/vagrant/services"

  	services.vm.provision :ansible do |ansible|
  	  ansible.playbook       = './main.yml'
  	end
  end
end
