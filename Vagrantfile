IMAGE_NAME = "ubuntu/bionic64"

Vagrant.configure("2") do |config|
    config.ssh.insert_key = false

    config.vm.provider "virtualbox" do |v|
        v.memory = 2048
        v.cpus = 2
    end

    config.vm.provision "ansible_local" do |ansible|
        ansible.playbook = "provision/common-playbook.yml"
        ansible.compatibility_mode = "2.0"
        ansible.extra_vars = {
            ansible_python_interpreter:"/usr/bin/python3",
        }
    end
      
    config.vm.define "k8s-master" do |master|
        master.vm.box = IMAGE_NAME
        master.vm.network "private_network", ip: "192.168.50.10"
        master.vm.hostname = "k8s-master"
        master.vm.provision "ansible_local" do |ansible|
            ansible.playbook = "provision/master-playbook.yml"
            ansible.compatibility_mode = "2.0"
            ansible.extra_vars = {
                ansible_python_interpreter:"/usr/bin/python3",
                node_ip: "192.168.50.10",
            }
        end
    end

    config.vm.define "node-1" do |node|
        node.vm.box = IMAGE_NAME
        node.vm.network "private_network", ip: "192.168.50.11"
        node.vm.hostname = "node-1"
        node.vm.provision "ansible_local" do |ansible|
            ansible.playbook = "provision/worker-playbook.yml"
            ansible.compatibility_mode = "2.0"
            ansible.extra_vars = {
                ansible_python_interpreter:"/usr/bin/python3",
                node_ip: "192.168.50.11",
            }
        end
    end

end
