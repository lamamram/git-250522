## Toute commande doit-ere exécution dans le répertoire contenant le Vagrantfile
## UP / DOWN
# vagrant up : lance TOUT
# vagrant up <hostname>: lance hostname
# vagrant halt [<hostname>]: arête tout ou seulement hostname
# vagrant destroy [-f] [<hostname>] : détruit [-f sans confirmation] //
# vagrant reload [<hostname>]: halt && up
## CNX
# vagrant ssh [<hostname>]: connexion SSH sur le compte "vagrant" 
#                           via l'interface NAT (127.0.0.1 + redirection 2222 <=> 22)
# vagrant ssh-config: configuration du vagrant ssh
# vagrant global-config
# vagrant plugin (un)install <plg>
##------------------------------------------------------------------

Vagrant.configure(2) do |config|

  image = "ml-registry/debian12-plus"
  subject = "git"
  hostname = "#{subject}.lan"
  memory = 512
  cpus = 1

  
  config.vm.define node[:hostname] do |machine|

    machine.vm.provider "virtualbox" do |v|
      v.memory = "#{memory}"
      v.cpus = "#{cpus}"
      v.name = "#{hostname}"
      v.customize ["modifyvm", :id, "--ioapic", "on"]
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    end
    machine.vm.box = "#{image}"
    machine.vm.hostname = "#{hostname}"
    machine.ssh.insert_key = false
    # lancer la création d'un dépôt git nu
    # machine.vm.provision "shell", 
      # path: "install_repo.sh",
  end
end
