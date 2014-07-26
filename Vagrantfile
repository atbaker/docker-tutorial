# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.box_url = "https://vagrantcloud.com/ubuntu/trusty64/version/1/provider/virtualbox.box"

  config.vm.network :forwarded_port, guest: 80, host: 8080

  config.vm.provision "ansible" do |ansible|
      ansible.playbook = "ansible/playbook.yml"
      ansible.sudo = true
      ansible.host_key_checking = false
      ansible.extra_vars = { vagrant_box: true }
#      ansible.verbose = "v"
  end

  (49000..49900).each do |port|
    config.vm.network :forwarded_port, :host => port, :guest => port
  end
end
