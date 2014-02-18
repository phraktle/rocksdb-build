VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.box = "trusty64"
  config.vm.box_url = "http://cloud-images.ubuntu.com/vagrant/trusty/current/trusty-server-cloudimg-amd64-vagrant-disk1.box"

  config.vm.host_name = "rocksdb-build"
  # config.vm.network :private_network, ip: "10.0.0.123"

  config.vm.provision :ansible do |ansible|
    ansible.playbook = "provisioning/playbook.yml"
    ansible.groups = { "rocksdb" => ["default"] }
    ansible.verbose = ''
    ansible.host_key_checking = false
    ansible.sudo = false
  end

  config.vm.provider :virtualbox do |vb|
    # vb.customize ["modifyvm", :id, "--memory", "1024"]
    vb.customize ["modifyvm", :id, "--cpus", "2"]
  end

end
