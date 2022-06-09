
IMAGE_NAME = "bento/ubuntu-16.04"
N = 2

Vagrant.configure("2") do |config|
      config.vm.provision "shell", inline: <<-SHELL
          apt-get update -y
          echo "192.168.56.20  master-node" >> /etc/hosts
          echo "192.168.56.191  worker-node01" >> /etc/hosts
          echo "192.168.56.192 worker-node02" >> /etc/hosts
      SHELL
      
      config.vm.define "k8s-master" do |master|
        master.vm.box = "bento/ubuntu-16.04"
        master.vm.hostname = "k8s-master-node"
        master.vm.network "private_network", ip: "192.168.56.20"
        master.vm.provider "virtualbox" do |vb|
            vb.memory = 4048
            vb.cpus = 2
        end
        master.vm.provision "shell", path: "scripts/common.sh"
        master.vm.provision "shell", path: "scripts/master.sh"
      end
  
      (1..N).each do |i|
    
      config.vm.define "node0#{i}" do |node|
        node.vm.box = "bento/ubuntu-16.04"
        node.vm.hostname = "k8s-worker-node0#{i}"
        node.vm.network "private_network", ip: "192.168.56.19#{i}"
        node.vm.provider "virtualbox" do |vb|
            vb.memory = 2048
            vb.cpus = 1
        end
        node.vm.provision "shell", path: "scripts/common.sh"
        node.vm.provision "shell", path: "scripts/node.sh"
      end
      
      end
    end
#Vagrantfile for kubernetes cluster.txt
#Affichage de Vagrantfile for kubernetes cluster.txt