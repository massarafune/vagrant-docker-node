Vagrant.configure("2") do |config|

  config.vm.box = "ubuntu/bionic64"

  config.vm.hostname = "docker-node"

  config.vm.network "private_network", ip: "192.168.33.10"

  config.vm.provider "virtualbox" do |vb|
     vb.gui = false
     vb.name = "docker-node"
     vb.cpus = 2
     vb.memory = "1024"
     vb.customize ["modifyvm", :id, "--natdnsproxy1", "off"]
     vb.customize ["modifyvm", :id, "--natdnshostresolver1", "off"]
  end
end
