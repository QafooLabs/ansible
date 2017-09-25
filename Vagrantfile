VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
    config.vm.hostname = "test.vm"
    config.vm.network :private_network, ip: "33.33.33.15"

    config.vm.box = "bento/ubuntu-16.04"
    # config.vm.box = "ubuntu/trusty64"

    config.vm.provider :virtualbox do |vb|
        vb.customize ["modifyvm", :id, "--cpus", `#{RbConfig::CONFIG['host_os'] =~ /darwin/ ? 'sysctl -n hw.ncpu' : 'nproc'}`.chomp]
        vb.customize ["modifyvm", :id, "--ioapic", "on"]

        vb.customize ["modifyvm", :id, "--memory", 1024]
        vb.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
    end

    config.vm.provision "ansible" do |ansible|
        ansible.inventory_path = "ansible/vagrant"
        ansible.playbook = "ansible/provision.yml"
        ansible.verbose = false
        ansible.limit = "all"
    end

    config.vm.network :forwarded_port, guest: 22, host: 22022, id: "ssh"
end
