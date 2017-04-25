Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"
  config.vm.synced_folder ".", "/vagrant", type:"virtualbox"
  config.ssh.forward_agent = true
  config.ssh.forward_x11 = true
  config.vm.provision "shell" do |s|
    s.inline = "yum -y update"
    s.privileged = true
  end
  config.vm.provision "shell" do |s|
    s.inline = "yum -y upgrade"
    s.privileged = true
  end
  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "/vagrant/epics.yml"
    ansible.install_mode = "pip"
  end
end
