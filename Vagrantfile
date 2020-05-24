Vagrant.configure("2") do |config|
  config.vm.box = "generic/ubuntu1804"
  
  # Set VM resources
  config.vm.provider :libvirt do |lv|
    lv.cpus = 1
    lv.memory = 2048
  end

  # Disable sync folder
  config.vm.synced_folder ".", "/vagrant", disabled: true

  # Set VM settings
  config.vm.define vm_name = "ubuntu"
  config.vm.hostname = "ubuntu.lab.local"
  ip = "192.168.240.10"
  config.vm.network :private_network, ip: ip

  # Launch Ansible playbook
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "site.yml"
  end
end
