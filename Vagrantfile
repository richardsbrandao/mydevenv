# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  
  config.vm.define "node" do |node|
  	node.vm.box = "bento/ubuntu-18.04"
    node.ssh.forward_agent = true
    node.vm.hostname = 'node.vm'
    
    # Apps
    node.vm.network "forwarded_port", guest: 9000, host: 9000
    node.vm.network "private_network", ip: "192.168.33.20"

    node.vm.synced_folder "#{ENV['HOME']}/vagrant_sync/node", "/home/vagrant/projects"

    node.vm.provider "virtualbox" do |vb|
      vb.memory = "1024" # 1 GB
    end

  	node.vm.provision :ansible do |ansible|
  	  ansible.playbook       = './main.yml'
  	end
  end

  config.vm.define "ruby" do |ruby|
    ruby.vm.box = "bento/ubuntu-18.04"
    ruby.ssh.forward_agent = true
    ruby.vm.hostname = 'ruby.vm'
    
    # Apps
    ruby.vm.network "forwarded_port", guest: 3000, host: 3000
    ruby.vm.network "private_network", ip: "192.168.33.23"

    ruby.vm.synced_folder "#{ENV['HOME']}/vagrant_sync/ruby", "/home/vagrant/projects"

    ruby.vm.provider "virtualbox" do |vb|
      vb.customize [ "guestproperty", "set", :id, "/VirtualBox/GuestAdd/VBoxService/--timesync-set-threshold", 5000 ]
      vb.memory = "1024" # 1 GB
    end

    ruby.vm.provision :ansible do |ansible|
      ansible.playbook       = './main.yml'
    end
  end

  config.vm.define "java" do |java|
    java.vm.box = "bento/ubuntu-18.04"
    java.ssh.forward_agent = true
    java.vm.hostname = 'java.vm'

    # Apps
    java.vm.network "forwarded_port", guest: 8080, host: 8080

    java.vm.network "private_network", ip: "192.168.33.22"

    java.vm.synced_folder "#{ENV['HOME']}/vagrant_sync/java", "/home/vagrant/projects"

    java.vm.provider "virtualbox" do |vb|
      vb.gui = true
      vb.memory = "3072" # 3 GB
    end  

    java.vm.provision :ansible do |ansible|
      ansible.playbook       = './main.yml'
    end
  end

  config.vm.define "elixir" do |elixir|
    elixir.vm.box = "bento/ubuntu-18.04"
    elixir.ssh.forward_agent = true
    elixir.vm.hostname = 'elixir.vm'

    # Apps
    elixir.vm.network "forwarded_port", guest: 4000, host: 4000
    elixir.vm.network "private_network", ip: "192.168.33.25"

    elixir.vm.synced_folder "#{ENV['HOME']}/vagrant_sync/elixir", "/home/vagrant/projects"

    elixir.vm.provider "virtualbox" do |vb|
      vb.memory = "1024" # 1 GB
    end  

    elixir.vm.provision :ansible do |ansible|
      ansible.playbook       = './main.yml'
    end
  end

  config.vm.define "crystal" do |elixir|
    elixir.vm.box = "bento/ubuntu-18.04"
    elixir.ssh.forward_agent = true
    elixir.vm.hostname = 'crystal.vm'

    # Apps
    elixir.vm.network "forwarded_port", guest: 3001, host: 3001
    elixir.vm.network "private_network", ip: "192.168.33.26"

    elixir.vm.synced_folder "#{ENV['HOME']}/vagrant_sync/crystal", "/home/vagrant/projects"

    elixir.vm.provider "virtualbox" do |vb|
      vb.memory = "1024" # 1 GB
    end  

    elixir.vm.provision :ansible do |ansible|
      ansible.playbook       = './main.yml'
    end
  end
  
  config.vm.define "services" do |services|
    services.vm.box = "bento/ubuntu-18.04"
    services.vm.hostname = 'services.vm'
    services.ssh.forward_agent = true
    
    services.vm.network "forwarded_port", guest: 15672, host: 15672 # Access http://localhost:15672 to access UI admin
    services.vm.network "forwarded_port", guest: 3306, host: 3306 # Use MysqlWorkbench or similar to use a UI admin
    services.vm.network "forwarded_port", guest: 7070, host: 7070 # Nginx
    services.vm.network "private_network", ip: "192.168.33.21"

    services.vm.synced_folder "#{ENV['HOME']}/vagrant_sync/services", "/home/vagrant/projects"

    services.vm.provider "virtualbox" do |vb|
      vb.memory = "5072" # 3 GB
    end  

  	services.vm.provision :ansible do |ansible|
  	  ansible.playbook       = './main.yml'
  	end
  end
end
