Vagrant.configure("2") do |config|
  
  config.vm.provider "virtualbox" do |v|
    v.gui = true
  end
  
  config.ssh.username = "cyberlab"
  config.ssh.password = "cyberlab"
  config.ssh.insert_key = true

  config.vm.define "cyberlab_attacker" do |attacker|
    attacker.vm.box = "ezeutno/cyberlab_attacker"
    attacker.vm.provider "virtualbox" do |v|
      v.customize ["modifyvm", :id, "--natnet1", "192.168.0.0/24"]
      v.customize ["modifyvm", :id, "--nic2", "natnetwork", "--nat-network2", "NatNetwork", "--nictype2", "virtio"]
      v.name = "cyberlab_attacker"
    end
    attacker.vm.provision "shell",
      inline: "sudo ifconfig enp0s8 10.0.2.7 netmask 255.255.255.0"
  end

  config.vm.define "cyberlab_client" do |client|
    client.vm.box = "ezeutno/cyberlab_clientbox"
    client.vm.provider "virtualbox" do |v|
      v.customize ["modifyvm", :id, "--natnet1", "192.168.0.0/24"]
      v.customize ["modifyvm", :id, "--nic2", "natnetwork", "--nat-network2", "NatNetwork", "--nictype2", "virtio"]
      v.name = "cyberlab_client"
    end
    client.vm.provision "shell",
      inline: "sudo ifconfig enp0s8 10.0.2.8 netmask 255.255.255.0"
  end

  config.vm.define "cyberlab_server" do |server|
    server.vm.box = "ezeutno/cyberlab_serverbox"
    server.vm.provider "virtualbox" do |v|
      v.customize ["modifyvm", :id, "--natnet1", "192.168.0.0/24"]
      v.customize ["modifyvm", :id, "--nic2", "natnetwork", "--nat-network2", "NatNetwork", "--nictype2", "virtio"]
      v.name = "cyberlab_server"
    end
    server.vm.provision "shell",
      inline: "sudo ifconfig enp0s8 10.0.2.6 netmask 255.255.255.0"
  end

end
