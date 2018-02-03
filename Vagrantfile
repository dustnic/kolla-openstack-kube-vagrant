BOX_IMAGE = "ubuntu/xenial64"
NODE_COUNT = 4

Vagrant.configure("2") do |config|
  (1..NODE_COUNT).each do |i|
    config.vm.define "worker-#{i}" do |subconfig|
      subconfig.vm.box = BOX_IMAGE
      subconfig.vm.hostname = "worker-#{i}"
      subconfig.vbguest.auto_update = false
      subconfig.vm.network "private_network", ip: "172.40.100.10#{i}"
      subconfig.vm.provision "shell", inline: "sudo apt-get -y install python"
      subconfig.vm.provision "ansible" do |ansible|
        ansible.playbook = "install-docker.yml"
       end
    end
  end
end
