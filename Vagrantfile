# -*- mode: ruby -*-
# vi: set ft=ruby :

machines = {
	"master" => {"memory"=>"1024", "cpus"=>"2", "ip" => "10" },
	"node01" => {"memory"=>"1024", "cpus"=>"2", "ip" => "11" },
	"node02" => {"memory"=>"1024", "cpus"=>"2", "ip" => "12" },
	"node03" => {"memory"=>"1024", "cpus"=>"2", "ip" => "13" },
}

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/xenial64"

  machines.each do |name,conf|
    config.vm.define "#{name}" do |machine|
      machine.vm.network "private_network", ip: "192.168.88.#{conf["ip"]}"
      machine.vm.hostname = "#{name}.lab.local"
      machine.vm.provider "virtualbox" do |vb|
        vb.cpus = "#{conf["cpus"]}"
				vb.memory = "#{conf["memory"]}"
	vb.name = "#{name}"
	vb.gui = false
      end
    end
  end
	config.vm.provision "shell", inline: <<-SHELL
	 sudo apt update && sudo apt install python -y
 SHELL
end
