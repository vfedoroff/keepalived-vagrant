VERSIONS = {
  'precise' => {
    'box' => "canonical-ubuntu-12.04",
    'box_url' => "https://cloud-images.ubuntu.com/vagrant/precise/current/precise-server-cloudimg-amd64-vagrant-disk1.box",
    'ami' => "ami-1ebb2077",
  },
}

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  version = VERSIONS["precise"]
  config.vm.provider "virtualbox" do |v, override|
    v.customize ["modifyvm", :id, "--memory", 1024]
    v.customize ["modifyvm", :id, "--cpus", 2]
    override.vm.network :private_network, ip: "192.168.33.10"
    override.vm.box = version['box']
    override.vm.box_url = version['box_url']
  end

  config.vm.hostname="keepalived.example.com"

  config.vm.provision "shell" do |sh|
        sh.path = "ansible.sh"
        sh.args = "ansible/playbook.yml ansible/inventory"
  end
end
