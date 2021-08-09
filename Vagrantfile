Vagrant.configure("2") do |config|

  if Vagrant.has_plugin?("vagrant-vbguest") then
    config.vbguest.auto_update = false
  end
  
  config.vm.box = "generic/centos8"
# config.ssh.username = 'ansible'
  
  VAGRANT_COMMAND = ARGV[0]
  if VAGRANT_COMMAND == "ssh"
    config.ssh.username = 'ansible'
  end 

  config.vm.define "master" do |master|
    master.vm.hostname = "master"
    master.vm.network "private_network", ip: "192.168.10.20"
    master.vm.provider "virtualbox" do |v|
      v.name = "master"
      v.linked_clone = true
      v.memory = 2048
      v.cpus = 1
    end
    master.vm.provision "ansible" do |ansible|
      ansible.playbook = "provisioning/master.yml"
      ansible.config_file = "provisioning/ansible.cfg"
      ansible.host_key_checking = false
#     ansible.verbose = true
    end
  end

N = 5
  (1..N).each do |machine_id|
    config.vm.define "host-#{machine_id}" do |host|
      host.vm.hostname = "host-#{machine_id}"
      host.vm.network "private_network", ip: "192.168.10.2#{machine_id}"
      host.vm.provider "virtualbox" do |v|
        v.name = "host-#{machine_id}"
        v.linked_clone = true
        v.memory = 1024
        v.cpus = 1
      end
      host.vm.provision "ansible" do |ansible|
        ansible.playbook = "provisioning/hosts.yml"
        ansible.config_file = "provisioning/ansible.cfg"
        ansible.host_key_checking = false
      end
    end
  end

end
