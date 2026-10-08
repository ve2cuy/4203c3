# Vagrant – Automatisation de la création des VM

*Document converti depuis [ve2cuy.com/420-3c3](https://ve2cuy.com/420-3c3/?page_id=1707) — dernière modification : 2024-10-23*

---

## 1 – Installation de vagrant

[Downloads | Vagrant by HashiCorp (vagrantup.com)](https://www.vagrantup.com/downloads)

Vagrant crée les machines virtuelles à partir de ‘Boxe’.

La liste des ‘Boxes’ est disponible [ici](https://portal.cloud.hashicorp.com/vagrant/discover?providers=virtualbox&query=).

**NOTE IMPORTANTE**: À la date du 2024.10.23 – Vagrant n’est pas compatible avec VirtualBox 7.1. Voici un lien vers la version [7.0.22 de virtualbox](https://download.virtualbox.org/virtualbox/7.0.22/VirtualBox-7.0.22-165102-Win.exe)

## 2 – Création d’un playbook Vagrant – Fichier Vagrantfile

```
# Dans un terminal, taper la commande suivante:

$ vagrant init

ou bien

$ vagrant init ubuntu/focal64

A `Vagrantfile` has been placed in this directory. You are now
ready to `vagrant up` your first virtual environment! Please read
the comments in the Vagrantfile as well as documentation on
`vagrantup.com` for more information on using Vagrant. 
```

Ceci devrait produire le fichier Vagrantfile suivant:

```
# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://vagrantcloud.com/search.

  config.vm.box = "base"

NOTE: Remplacer la ligne précédente par
  config.vm.box = "ubuntu/focal64"

  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # NOTE: This will enable public access to the opened port
  # config.vm.network "forwarded_port", guest: 80, host: 8080

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine and only allow access
  # via 127.0.0.1 to disable public access
  # config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  # config.vm.network "private_network", ip: "192.168.33.10"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "../data", "/vagrant_data"

  # Disable the default share of the current code directory. Doing this
  # provides improved isolation between the vagrant box and your host
  # by making sure your Vagrantfile isn't accessible to the vagrant box.
  # If you use this you may want to enable additional shared subfolders as
  # shown above.
  # config.vm.synced_folder ".", "/vagrant", disabled: true

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  # config.vm.provider "virtualbox" do |vb|
  #   # Display the VirtualBox GUI when booting the machine
  #   vb.gui = true
  #
  #   # Customize the amount of memory on the VM:
  #   vb.memory = "1024"
  # end
  #
  # View the documentation for the provider you are using for more
  # information on available options.

  # Enable provisioning with a shell script. Additional provisioners such as
  # Ansible, Chef, Docker, Puppet and Salt are also available. Please see the
  # documentation for more information about their specific syntax and use.
  # config.vm.provision "shell", inline: <<-SHELL
  #   apt-get update
  #   apt-get install -y apache2
  # SHELL
end
```

Dans un répertoire vide, créer un fichier nommé ‘Vagrantfile’ avec le contenu suivant:

```
# Ficher: Vagrantfile
# Auteur: Alain Boudreault
# Date:   2024.10.23
# ---------------------------------------------------------------
# Description: Mise en place de trois (3) VM Ubuntu,
#              dans le but de tester des clés privées/publiques
# ---------------------------------------------------------------
# NOTE: La syntaxe utilisée dans un fichier Vagrant est Ruby
# ---------------------------------------------------------------
Vagrant.configure("2") do |config|
    numberSrv=3
    # Serveurs de tests pour les clés RSA
    (1..numberSrv).each do |i|
      config.vm.define "CFG-serveur-0#{i}" do |knode|
        # Désactiver le stockage lié avec l'hôte.
        knode.vm.synced_folder '.', '/vagrant', disabled: true
        # Renseigner la 'box' à utiliser
        knode.vm.box = "ubuntu/focal64"        
        knode.vm.hostname = "mon-serveur-0#{i}"

        # Définition du type d'accès réseau
        # Référence: https://www.vagrantup.com/docs/networking
        knode.vm.network "private_network", ip: "192.168.56.10#{i}"
        # config.vm.network "public_network"
        # config.vm.network "public_network", ip: "192.168.0.17"
        # config.vm.network "public_network", bridge: "en1: Wi-Fi (AirPort)"

        # Utiliser un hyperviseur pour créer/démarrer les VM
        knode.vm.provider "virtualbox" do |v|
         v.name = "VM-Serveur-0#{i}"
          v.memory = 1024
          v.cpus = 1
        end
        # Activation du ssh hors vagrant.
        # Note: Par défaut, l'accès ssh est désactivé dans les BOX Vagrant.
        config.vm.provision "shell", inline: <<-SHELL
          # Activer les connexions ssh dans le fichier /etc/ssh/sshd_config
          sed -i 's/ChallengeResponseAuthentication no/ChallengeResponseAuthentication yes/g' /etc/ssh/sshd_config    
          service ssh restart
        SHELL
      end
    end
  end
```

**NOTE**: Les fichiers Vagrantfile sont programmés en utilisant le langage [Ruby](https://www.ruby-lang.org/en/).

## 3 – Démarrage des VM

```
# Dans le répertoire qui contient le fichier "Vagrantfile"

$ vagrant up
```

## 4 – Connexion à une VM

```
$ vagrant ssh nom-du-fichier-conf-de-la-vm
$ vagrant ssh CFG-serveur-01

# NOTE: Pour obtenir la liste des fichiers conf, utiliser la commande
  vagrant status

# Ou bien
$ ssh vagrant@192.168.56.101
# Le mot de passe est vagrant
```

## 5 – Shutdown des VM

```
$ vagrant halt
```

6 – Suppression des VM

```
# Note: -f = effacer sans confirmation
$ vagrant destroy -f
```

---

[Référence Vagrant](https://www.vagrantup.com/docs)

Document d’introduction externe ([en anglais](https://opensource.com/article/19/12/beginner-vagrant))

---

[⬅️ Retour à la liste des documents](../README.md)
