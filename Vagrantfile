Vagrant.configure("2") do |config|
#
# Quando uma configuração é colocada nessa seção do Vagrant.configure
# essa configuração será "global", ou seja, será aplicada para todas
# as VMs... para configurações especificas de VMs, a configuração
# deve ser aplicada na seção "config.vm.define"
#
  config.vm.provision "shell", path: "script.sh"

  config.vm.define "controle" do |controle|
    controle.vm.box = "shekeriev/debian-11"
    controle.vm.hostname = "controle"
    controle.vm.network "private_network", ip: "172.17.177.100"
    controle.vm.provider "virtualbox" do |vb|
        vb.memory = "2048"
        vb.cpus = 2
        vb.name = "controle"
    end
    controle.vm.provision "ansible_local" do |al|
        al.playbook = "playbook.yml"
        al.install_mode = "pip"
    end
    controle.vm.provision "ansible_local" do |al|
        al.playbook = "installdocker.yml"
        al.install_mode = "pip"
    end
  end
end
