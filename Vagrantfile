Vagrant.configure("2") do |config|

    config.vm.box = "ubuntu/trusty64"

    config.vm.provider "virtualbox" do |v|
        v.memory = 1024
    end

    config.vm.define "wordpress" do |m|
        m.vm.network "private_network", ip: "172.17.177.40"
    end


    config.vm.define "ansible" do |ansible|
        ansible.vm.network "public_network", ip: "172.17.177.41"
        ansible.vm.provision "shell",
            inline: "apt-get update && \
                     apt-get install -y software-properties-common && \
                     apt-add-repository --yes --update ppa:ansible/ansible && \
                     apt-get install -y ansible"


                     ansible.vm.provision "shell",
                         inline: "ansible-playbook -i /vagrant/configs/ansible/hosts \
                              /vagrant/configs/ansible/playbook.yml"
    end
end
