BOX_IMAGE = "ubuntu/trusty64"
NODE_COUNT = 4

Vagrant.configure("2") do |config|
  config.vm.define "master" do |subconfig|
    subconfig.vm.box = BOX_IMAGE
    subconfig.vbguest.auto_update = true
    subconfig.vm.network "private_network", ip: "172.40.100.2", :name => 'vboxnet3'
    # subconfig.vm.provision "ansible" do |ansible|
      # ansible.playbook = "install-docker_kube.yml"
      # ansible.verbose = "vvv"
    # end
  end
  config.vm.define "etcd" do |subconfig|
    subconfig.vm.box = BOX_IMAGE
    subconfig.vbguest.auto_update = true
    subconfig.vm.network "private_network", ip: "172.40.100.3", :name => 'vboxnet3'
    # subconfig.vm.provision "ansible" do |ansible|
      # ansible.playbook = "install-docker_kube.yml"
      # ansible.verbose = "vvv"
    # end
  end

  (1..NODE_COUNT).each do |i|
    config.vm.define "worker-#{i}" do |subconfig|
      subconfig.vm.box = BOX_IMAGE
      subconfig.vbguest.auto_update = false
      subconfig.vm.network "private_network", ip: "172.40.100.10#{i}", :name => 'vboxnet3'
      # subconfig.vm.provision "ansible" do |ansible|
        # ansible.playbook = "install-docker_kube.yml"
      #  end
    end
  end
end
