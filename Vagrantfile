VAGRANTFILE_API_VERSION = "2"

$salt_master_install_script = <<SCRIPTA
  echo "172.16.1.10     salt" >> /etc/hosts
  echo "172.16.1.20     minion" >> /etc/hosts
  echo "salt" > /etc/hostname
  hostname salt
  wget -O - http://bootstrap.saltstack.org | sh -s -- -M -N
SCRIPTA

$salt_minion_install_script = <<SCRIPTB
  echo "172.16.1.10     salt" >> /etc/hosts
  echo "172.16.1.20     minion" >> /etc/hosts
  echo "minion" > /etc/hostname
  hostname minion
  wget -O - http://bootstrap.saltstack.org | sh
SCRIPTB

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "precise32-stackstrap"
  config.vm.box_url = "https://dl.dropboxusercontent.com/s/ftlm33esku2w8aa/ubuntu1204-i386.box"

  config.vm.provider "vmware_fusion" do |v, override|
    override.vm.box = "precise32-stackstrap-vmware"
    override.vm.box_url = "https://dl.dropboxusercontent.com/s/ev9txs7c4s0muqr/ubuntu1204-i386.box"
  end

  config.vm.define "master" do |master|
    master.vm.provision "shell", inline: $salt_master_install_script
    master.vm.network "private_network", ip: "172.16.1.10"
  end

  config.vm.define "minion" do |minion|
    minion.vm.provision "shell", inline: $salt_minion_install_script
    minion.vm.network "private_network", ip: "172.16.1.20"
  end
end
