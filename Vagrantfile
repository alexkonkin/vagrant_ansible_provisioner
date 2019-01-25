VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.define "ca" do |ca|
    ca.vm.box = "bento/centos-7.1"
    ca.vm.hostname = "centos7"
    ca.vm.network :private_network, ip: "192.168.1.4"
    ca.vm.network "forwarded_port", guest: 8080, host: 8193, auto_correct: true
    ca.vm.network "forwarded_port", guest: 80, host: 8192, auto_correct: true
  end

  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--memory", "1024"]
  end

  config.vm.provision "ansible" do |ansible|
    ansible.compatibility_mode = "2.0"
    ansible.playbook = "provisioning/playbook.yml"
    ansible.verbose = "v"
#    ansible.inventory_path = "provisioning/inventory"
    ansible.become = true
  end
    
end
