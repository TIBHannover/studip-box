require 'yaml'
settings = YAML.load_file 'ansible/group_vars/all.yml'

Vagrant.configure("2") do |config|

  config.vm.define "studip-vm" do |srv|
    srv.vm.box = "debian/stretch64"
    srv.ssh.insert_key = false
    srv.vm.hostname = "studip.box"
    srv.vm.network :private_network, ip: settings['studip_host']

    srv.vm.provider :virtualbox do |vb|
      vb.name = "studip"
      vb.memory = 4096
      vb.cpus = 4
    end
  end

  config.vm.provision "ansible_local" do |ansible|
    ansible.install = true
    ansible.install_mode = "pip"
    # fix pip installation
    ansible.pip_install_cmd = "curl https://bootstrap.pypa.io/get-pip.py | sudo python"
    ansible.version = "latest"
#  config.vm.provision "ansible" do |ansible|
    ansible.compatibility_mode = "2.0"
    ansible.playbook = "ansible/system.yml"
    ansible.groups = {
      "studip" => ["studip-vm"],
      "all:vars" => {
        "timezone" => "Europe/Berlin"
      }
    }
    #ansible.skip_tags = [ "demo-data" ]
  end
end
