Vagrant.configure(2) do |config|
    config.vm.box = "bento/centos-8"
   
    #Habilitar el reenvio de puerto SSH
    config.vm.network "forwarded_port", guest: 22, host:2222, id: "ssh", auto_correct: true
   
    #Habilitar el reenvio de puerto Apache
    config.vm.network "forwarded_port", guest: 80, host:8080, id: "http", auto_correct: true
   
    #Creacion de la VM en Virtualbox
    config.vm.define "vm_cos8" do |vm_cos8|
      vm_cos8.vm.provision "ansible" do |ansible|
        ansible.inventory_path = "staging"
        ansible.verbose = 'vvv'
        ansible.playbook = "site.yml"
      end
    
    #Ampliacion de la memoria de la VM
      config.vm.provider "virtualbox" do |v|
        v.memory = 2048
        v.name = "vm_cos8"
        v.cpus = 1
      end
    end
  end