Vagrant.configure("2") do |config|

  config.vm.box = "ubuntu/bionic64"

  config.vm.hostname = "docker-node"

  config.vm.network "private_network", ip: "192.168.33.10"
  config.vm.network "forwarded_port", guest: 3000, host:3000

  config.vm.provider "virtualbox" do |vb|
     vb.gui = false
     vb.name = "docker-node"
     vb.cpus = 2
     vb.memory = "1024"
     vb.customize ["modifyvm", :id, "--natdnsproxy1", "off"]
     vb.customize ["modifyvm", :id, "--natdnshostresolver1", "off"]
     vb.customize ["modifyvm", :id, "--uartmode1", "file", File.join(Dir.pwd, "log/ubuntu-bionic-18.04-cloudimg-console.log")]
  end

  config.disksize.size = "10GB"

  config.vm.synced_folder "./", "/home/vagrant/app", type: "rsync", rsync_auto: true, rsync__exclude: "log/"
  config.vm.provision :docker, run: "always"
  config.vm.provision :docker_compose
end
