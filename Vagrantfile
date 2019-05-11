Vagrant.require_version ">= 2.2.0"

require 'getoptlong'

Vagrant.configure(2) do |config|
  config.vm.provider 'virtualbox' do |vb|
    vb.memory = 2048
    vb.cpus = 2
  end

  config.vm.box = "centos/7"
  config.ssh.insert_key = false
  config.vm.provision "ansible" do |ansible|
    ansible.verbose = "vv"
    ansible.playbook = "provision_vagrant_jenkins_slave.yml"
  end
end
