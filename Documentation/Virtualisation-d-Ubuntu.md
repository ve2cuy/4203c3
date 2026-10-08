# Virtualisation d’Ubuntu

*Document converti depuis [ve2cuy.com/420-3c3](https://ve2cuy.com/420-3c3/?page_id=2027) — dernière modification : 2024-08-21*

---

##### Document en cours de rédaction …

<img src="images/Virtualisation-d-Ubuntu/ubuntu.logo_-1024x1024.png" alt="" width="512" />

Au courant de la session, nous verrons comment mettre en place et assurer la configuration des services couramment utilisés par les applications modernes. Règles générales, ces services sont déployés en infonuagique sur des serveurs de type Linux.

Pour débuter, nous commencerons par une virtualisation locale d’un serveur Linux de type Ubuntu.

---

## Partie 01 – Téléchargement et installation de VirtualBox

**Étape 01** : [Télécharger Oracle VM VirtualBox via ce lien](https://www.virtualbox.org/wiki/Downloads)

<img src="images/Virtualisation-d-Ubuntu/Capture-decran-2024-08-09-171446.png" alt="" width="490" />

**QUESTION** : Pourquoi utiliser VirtualBox?

---

## Téléchargement d’Ubuntu, version Serveur LTS

**Étape 02** : [Télécharger Ubuntu serveur via ce lien](https://ubuntu.com/download/server)

<img src="images/Virtualisation-d-Ubuntu/Capture-decran-2024-08-09-171917-1024x656.png" alt="" width="512" />

**QUESTION**: Que veux dire LTS au bout du numéro de version?

---

## Partie 02 – Création d’une machine virtuelle

### Utilisation de VirtualBox

**Étape 03** : Démarrer l’application VirtualBox

<img src="images/Virtualisation-d-Ubuntu/Capture-decran-2024-08-09-172323-1024x492.png" alt="" width="512" />

**PRÉ-REQUIS**: S’assurer que le dossier par défaut des machines virtuelles de VirtualBox est sur un disque contenant suffisamment d’espace. Le disque C: des postes de travail du local D139 est souvent saturé.

<img src="images/Virtualisation-d-Ubuntu/Capture-decran-2024-08-20-160143-1024x245.png" alt="" width="512" />

---

**Étape 04** : Sélectionner Outils->Support->Disques Optiques: **Ajouter**

Ajouter l’image du CDROM d’installation à la bibliothèque de VirtualBox:

<img src="images/Virtualisation-d-Ubuntu/Capture-decran-2024-08-09-173029-1024x703.png" alt="" width="512" />

**Étape 05** : Ajouter la référence au fichier d’installation d’Ubuntu serveur.

<img src="images/Virtualisation-d-Ubuntu/Capture-decran-2024-08-09-173322-1024x267.png" alt="" width="512" />

---

## Création d’une machine virtuelle

**Étape 06** : Option – Outils->Bienvenue-> **Nouvelle**

6.1 – Compléter les champs selon les écrans suivants:

- Nom, localisation des fichiers de la VM, disque d’installation et ‘**skip Unattended Installation**‘;

<img src="images/Virtualisation-d-Ubuntu/Capture-decran-2024-08-09-173922-1024x649.png" alt="" width="512" />

**ATTENTION** – Ne pas passer à l’étape suivante avant d’avoir sélectionné ‘**skip Unattended Installation**‘.

---

- 6.2 – Mémoire vive et nombre de CPUs

<img src="images/Virtualisation-d-Ubuntu/Capture-decran-2024-08-09-174153-1024x650.png" alt="" width="512" />

---

- 6.3 – Taille du disque virtuel

<img src="images/Virtualisation-d-Ubuntu/Capture-decran-2024-08-09-174238-1024x646.png" alt="" width="512" />

---

- 6.4 – Récapitulatif et confirmation

<img src="images/Virtualisation-d-Ubuntu/Capture-decran-2024-08-09-174306-1024x647.png" alt="" width="512" />

---

Retour à l’écran de bienvenue de virtualBox

<img src="images/Virtualisation-d-Ubuntu/Capture-decran-2024-08-09-174337-1024x445.png" alt="" width="512" />

La machine virtuelle qui servira à installer et à exploiter Ubuntu serveur est maintenant créée.

---

Il reste quelques paramètres supplémentaire à renseigner.

**Étape 07** : Sélectionner l’option ‘Configuration’

<img src="images/Virtualisation-d-Ubuntu/Capture-decran-2024-08-09-175227-1024x740.png" alt="" width="512" />

7.1 – Suivi de l’option ‘**Réseau**‘ et renseigner la première interface réseau à ‘**Accès par pont**‘ (bridge):

<img src="images/Virtualisation-d-Ubuntu/Capture-decran-2024-08-09-175309-1024x737.png" alt="" width="512" />

**Cette option assure que la machine virtuelle aura une adresse IP dans la même plage que le réseau de la station hôte.**

Voilà, les préparatif de départ sont terminés, il ne reste plus qu’à démarrer la VM. Le CdRom d’installation devrait être insérer dans le lecteur de la VM et le programme d’installation d’Ubuntu Serveur devrait se lancer automatiquement.

---

**Étape 08** : Appuyer sur l’option ‘**Démarrer**‘

<img src="images/Virtualisation-d-Ubuntu/Capture-decran-2024-08-09-180429.png" alt="" width="364" />

---

## Partie 03 – Installation d’Ubuntu serveur

**Étape 09** : Sélection de la langage d’installation:

<img src="images/Virtualisation-d-Ubuntu/Capture-decran-2024-08-09-180726-1024x815.png" alt="" width="512" />

**Étape 10** : Sélection du clavier – disposition des touches du clavier.

<img src="images/Virtualisation-d-Ubuntu/Capture-decran-2024-08-09-180832-1024x755.png" alt="" width="512" />

**Étape 11** : Sélection du type de serveur:

- Serveur
- Serveur minimal avec peu de logins

<img src="images/Virtualisation-d-Ubuntu/Capture-decran-2024-08-09-180849-1024x755.png" alt="" width="512" />

---

**Étape 12**: Configuration des paramètres des interfaces réseaux.

Par défaut, une configuration DHCP est proposée. La carte réseau de la machine virtuelle, renseignée en mode Pont, devrait recevoir une adresse IP – du serveur DHCP.

<img src="images/Virtualisation-d-Ubuntu/Capture-decran-2024-08-09-181203-1024x252.png" alt="" width="512" />

**NOTE**: La machine virtuelle devrait avoir une adresse IP dans la même classe IP que votre poste de travail. Si ce n’est pas le cas, il faut corriger la situation avant de continuer l’installation.

<img src="images/Virtualisation-d-Ubuntu/Capture-decran-2024-08-09-181615-1024x652.png" alt="" width="512" />

---

**Étape 13** : Recherche des serveurs miroirs Ubuntu externes – requis pour les mises à jour pendant l’installation.

<img src="images/Virtualisation-d-Ubuntu/Capture-decran-2024-08-09-181639-1024x650.png" alt="" width="512" />

**Étape 14** : Renseignement des paramètres du/des disque/s de la VM.

<img src="images/Virtualisation-d-Ubuntu/Capture-decran-2024-08-09-181700-1024x652.png" alt="" width="512" />

---

## 14.1 – Définition d’une partition LVM

Une **partition LVM** (Logical Volume Manager) est une méthode de gestion des disques sous Linux qui permet de créer et de gérer des volumes logiques. Contrairement au partitionnement traditionnel, LVM offre une plus grande flexibilité et facilite la gestion de l’espace de stockage. Voici quelques points clés :

- [**Flexibilité** : LVM permet de redimensionner les volumes logiques sans reformater les disques](https://doc.ubuntu-fr.org/lvm)[1](https://doc.ubuntu-fr.org/lvm).
- [**Gestion simplifiée** : Vous pouvez ajouter ou supprimer des disques à la volée, sans interruption de service](https://doc.ubuntu-fr.org/lvm)[1](https://doc.ubuntu-fr.org/lvm).
- [**Snapshots** : Il est possible de créer des snapshots (copies instantanées) des volumes pour des sauvegardes ou des tests](https://doc.ubuntu-fr.org/lvm)[1](https://doc.ubuntu-fr.org/lvm).

---

<img src="images/Virtualisation-d-Ubuntu/Capture-decran-2024-08-09-181724-1024x652.png" alt="" width="512" />

<img src="images/Virtualisation-d-Ubuntu/Capture-decran-2024-08-09-181751-1024x523.png" alt="" width="512" />

---

**Étape 15** : **Renseignement du premier compte utilisateur**. Ce compte sera utiliser pour la gestion du serveur.

**NOTE**: Un autre compte sera disponible, au besoin, pour la gestion du serveur. Il se nomme ‘root’. Il n’est pas recommandé de l’utiliser et il possède un mot de passe inconnu à cette étape.

<img src="images/Virtualisation-d-Ubuntu/Capture-decran-2024-08-09-191058-1024x344.png" alt="" width="512" />

- Votre nom = **etudiant**
- Your servers name = **serveur01**
- Choisir un nom d’utilisateur = **etudiant**
- Choisir un mot de passe = **password**

<img src="images/Virtualisation-d-Ubuntu/Capture-decran-2024-08-09-191125-1024x248.png" alt="" width="512" />

---

**Étape 16** : Installation du service openssh-server. **Ce service est absolument requis pour la connexion à distance au serveur**.

<img src="images/Virtualisation-d-Ubuntu/Capture-decran-2024-08-09-191154-1024x403.png" alt="" width="512" />

**NOTE**: Clé SSH couvert dans ce [laboratoire](Configuration-et-utilisation-de-ssh.md)

---

**Étape 17** : Sélection des applications supplémentaires à installer.

**NOTE**: Nous installerons des applications manuellement plus tard…

<img src="images/Virtualisation-d-Ubuntu/Capture-decran-2024-08-09-191224-1024x784.png" alt="" width="512" />

---

**Étape 18** : Installation du système

**NOTE**: Il ne reste plus qu’à attendre le fin de l’installation 😉

<img src="images/Virtualisation-d-Ubuntu/Capture-decran-2024-08-09-191242-1024x789.png" alt="" width="512" />

<img src="images/Virtualisation-d-Ubuntu/Capture-decran-2024-08-09-191837-1024x785.png" alt="" width="512" />

**Étape 18** : L’installation d’Ubuntu Serveur est terminée. Il ne reste qu’à ‘**Redémarrer maintenant**‘

<img src="images/Virtualisation-d-Ubuntu/Capture-decran-2024-08-09-193627-1024x782.png" alt="" width="512" />

---

## Partie 04 – Login au serveur Ubuntu

<img src="images/Virtualisation-d-Ubuntu/Capture-decran-2024-08-09-194459.png" alt="" width="354" />

**Étape 19** : Ouverture d’une session directement via la VM

**NOTE**: login: ***etudiant***, password: ***password***

---

<img src="images/Virtualisation-d-Ubuntu/Capture-decran-2024-08-09-194540-1024x1013.png" alt="" width="512" />

---

## Connexion ssh

Une session SSH permet de se connecter à un serveur à partir d’un lieu distant. Par exemple, gérer le serveur de l’entreprise à partir de la maison.

Pour ce faire, il faut connaitre l’adresse IP du serveur.

<img src="images/Virtualisation-d-Ubuntu/Capture-decran-2024-08-09-200718-1024x287.png" alt="" width="512" />

**Étape 20** : Obtenir l’adresse IP de notre serveur Ubuntu, avec la commade ‘***ip a***‘

Pour cette VM, l’adresse IP est 192.168.2.221

**Étape 21** : Ouvrir une session ssh à partir de windows:

21.1 – Ouvrir un terminal et taper la commande:

```
ssh etudiant@adresseIPduServeur
```

<img src="images/Virtualisation-d-Ubuntu/Capture-decran-2024-08-09-201240-1024x929.png" alt="" width="512" />

En cas de problème, s’assurer que le service ssh roule:

```
etudiant@serveur01:~$ sudo systemctl | grep ssh
[sudo] password for etudiant:
  ssh.service           loaded active running   OpenBSD Secure Shell server
  ssh.socket            loaded active running   OpenBSD Secure Shell server socket
---
etudiant@serveur01:~$ sudo apt list openssh-server
En train de lister... Fait
openssh-server/noble-updates,noble-security,now 1:9.6p1-3ubuntu13.4 amd64 [installé]

# Au besoin, installer avec:
$ sudo apt install openssh-server -y
```

---

## Ajout d’une référence au DNS local de Windows

**Étape 22**

1. Ouvrir un terminal ***Powershell*** en mode administrateur
2. Naviguer dans le dossier ***\windows\system32\drivers\etc***
3. Éditer le fichier ‘***hosts***‘

<img src="images/Virtualisation-d-Ubuntu/Capture-decran-2024-08-20-151001.png" alt="" width="402" />

**Étape 23** : Ajouter une référence à l’adresse IP du serveur Ubuntu:

<img src="images/Virtualisation-d-Ubuntu/Capture-decran-2024-08-20-151549-1024x361.png" alt="" width="512" />

23.1 – Enregistrer les changements

---

**Étape 24** : Tester la connexion ssh avec l’entrée DNS au serveur Ubuntu:

```
PS C:\Windows\system32\drivers\etc> ssh etudiant@srv01

The authenticity of host 'srv01 (192.168.2.211)' can't be established.
ED25519 key fingerprint is SHA256:dAITMd6Nmcyr/l08jSUm7/OhoukppSVrtZIabbgPA5Q.
This host key is known by the following other names/addresses:
    C:\Users\alin_/.ssh/known_hosts:18: 192.168.2.211

Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added 'srv01' (ED25519) to the list of known hosts.
etudiant@srv01's password:

Welcome to Ubuntu 24.04 LTS (GNU/Linux 6.8.0-40-generic x86_64)
```

---

FIN DU DOCUMENT

---

[⬅️ Retour à la liste des documents](../README.md)
