# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.box = "xoan/Leap-15.4"

  # evitamos actualizacions automaticas
  config.vm.box_check_update = false
  config.vbguest.auto_update = false

  # Activamos a opcion de linked clones para optimizar o espazo usado polos discos
  # As 3 VMs comparten o disco dunha imaxe base e en cada unha so se almacenan os cambios
  config.vm.provider :virtualbox do |vb|
    vb.linked_clone = true
    vb.cpus = 2
  end

  # Definicion dos nos do cluster

  ###################### IMPORTANTE #############################
  # Cambia os nomes das VM para usar a nomenclatura das practicas 
  ###############################################################

  # VM master
  config.vm.define "igc2223-master" do |master|
    master.vm.network "private_network", ip: "192.168.56.2"
    # aprovisionar o master
    master.vm.provision "shell" do |s|
      s.path = "bootstrap.sh"
      s.args = ["igc2223-master"]
    end
  end

  # VM slave
  config.vm.define "igc2223-slave" do |slave|
    slave.vm.network "private_network", ip: "192.168.56.3"
    # aprovisionar o slave
    slave.vm.provision "shell" do |s|
      s.path = "bootstrap.sh"
      s.args = ["igc2223-slave"]
    end
  end

  # VM spare
  config.vm.define "igc2223-spare" do |spare|
    spare.vm.network "private_network", ip: "192.168.56.4"
    # aprovisionar o spare
    spare.vm.provision "shell" do |s|
      s.path = "bootstrap.sh"
      s.args = ["igc2223-spare"]
    end
  end

end
