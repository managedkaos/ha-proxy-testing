# -*- mode: ruby -*-
# vi: set ft=ruby :
VAGRANTFILE_API_VERSION = "2"
BOX = "ubuntu/xenial64"
servers = {
    'haproxy' => { name:'haproxy', ip:'192.168.56.200', cpus:'1', memory:'512' },
    'node1'   => { name:'node1',   ip:'192.168.56.201', cpus:'1', memory:'512' },
    'node2'   => { name:'node2',   ip:'192.168.56.202', cpus:'1', memory:'512' }
}

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
    config.vm.box = BOX
    
    servers.each do |hostname, settings|
        config.vm.define hostname do |host|
            host.vm.hostname = "#{hostname}.dev"
            host.vm.network "private_network", ip: settings[:ip]
        
            host.vm.provider "virtualbox" do |v|
                v.memory = settings[:memory]
                v.cpus   = settings[:cpus]
                v.name   = settings[:name]
            end
        end
    end
end
