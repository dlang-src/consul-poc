# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.define :pnode1 do |pnode1|
    pnode1.vm.box = "chef/centos-6.6"

    pnode1.vm.provider :vmware_fusion do |v|
      v.vmx["memsize"]  = "2048"
      v.vmx["numvcpus"] = "2"
    end

    pnode1.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--memory", "2048"]
      v.customize ["modifyvm", :id, "--cpus", 2]
    end

    pnode1.vm.network :private_network, ip: "192.168.100.10"
    pnode1.vm.hostname = "pnode1"
  end

  config.vm.define :pnode2 do |pnode2|
    pnode2.vm.box = "chef/centos-6.6"

    pnode2.vm.provider :vmware_fusion do |v|
      v.vmx["memsize"]  = "2048"
      v.vmx["numvcpus"] = "2"
    end

    pnode2.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--memory", "2048"]
      v.customize ["modifyvm", :id, "--cpus", 2]
    end

    pnode2.vm.network :private_network, ip: "192.168.100.11"
    pnode2.vm.hostname = "pnode2"
  end

  config.vm.define :pnode3 do |pnode3|

    pnode3.vm.box = "chef/centos-6.6"

    pnode3.vm.provider :vmware_fusion do |v|
      v.vmx["memsize"]  = "2048"
      v.vmx["numvcpus"] = "2"
    end

    pnode3.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--memory", "2048"]
      v.customize ["modifyvm", :id, "--cpus", 2]
    end

    pnode3.vm.network :private_network, ip: "192.168.100.12"
    pnode3.vm.hostname = "pnode3"

  end

  config.vm.define :pnode4 do |pnode4|

    pnode4.vm.box = "chef/centos-6.6"

    pnode4.vm.provider :vmware_fusion do |v|
      v.vmx["memsize"]  = "2048"
      v.vmx["numvcpus"] = "2"
    end

    pnode4.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--memory", "2048"]
      v.customize ["modifyvm", :id, "--cpus", 2]
    end

    pnode4.vm.network :private_network, ip: "192.168.100.13"
    pnode4.vm.hostname = "pnode4"

  end

  config.vm.define :pnode5 do |pnode5|
    pnode5.vm.box = "chef/centos-6.6"

    pnode5.vm.provider :vmware_fusion do |v|
      v.vmx["memsize"]  = "2048"
      v.vmx["numvcpus"] = "2"
    end

    pnode5.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--memory", "2048"]
      v.customize ["modifyvm", :id, "--cpus", 2]
    end

    pnode5.vm.network :private_network, ip: "192.168.100.14"
    pnode5.vm.hostname = "pnode5"
  end

  config.vm.provision "ansible" do |ansible|
      ansible.playbook = "provisioning/site.yml"
      ansible.host_key_checking = false
      ansible.sudo = true
      ansible.groups = {
	"consul-server" => ["pnode1","pnode3","pnode5"],
	"consul-agent" => ["pnode2","pnode4"],
	"consul:children" => ["consul-server","consul-agent"]
      }
    end

end
