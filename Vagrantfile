# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"
BOX_NAME = 'corefile/router'
node_ex_ip = "192.168.111.254"
Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|


  config.vm.define "router-node", primary: true, autostart: true do |node|
    node.vm.box = BOX_NAME
    node.vm.define "router" 
    node.vm.hostname = "router"
    node.vm.network "private_network", ip: "#{node_ex_ip}", virtualbox__intnet: "mylocalnet", auto_config: true
    node.vm.provider :virtualbox do |vb|
      # vb.gui = true
      vb.customize ["modifyvm", :id, "--memory", "128"]
      vb.customize ["modifyvm", :id, "--cpus", "1"]
      vb.customize ["modifyvm", :id, "--hwvirtex", "on"]
      vb.customize ["modifyvm", :id, "--audio", "none"]
      vb.customize ["modifyvm", :id, "--nictype1", "virtio"]
      vb.customize ["modifyvm", :id, "--nictype2", "virtio"]
      # vb.customize ["modifyvm", :id, "--nicpromisc2", "allow-all"]
      # vb.customize ["modifyvm", :id, "--macaddress2", "0000000000FE"]
    end
    node.vm.provider "vmware_fusion" do |vf|
      vf.vmx["memsize"] = "128"
    end
  end
end
