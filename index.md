---
layout: accueil
bandeau: "420-3C3-JR · techniques de l'informatique · cégep de saint-jérôme"
titre: "Installation de serveurs."
accroche: "Services réseaux locaux et en nuages : virtualisation, Linux, Apache, pile AMP, WordPress, serveurs d'entreprise, NFS, SMB et FTP."
image: Documentation/images/serveur-entete.webp
---

## Présentation sommaire du cours

![](dessins/fiche-info.svg)

L'étudiant pourra choisir les caractéristiques de serveurs (physiques ou virtuels) et le système d'exploitation appropriés répondant à des besoins particuliers. Il sera en mesure d'assurer la gestion des différentes ressources du ou des serveurs, et de déployer une pile LAMP (Linux, Apache, MySQL et PHP) dans des contextes de virtualisation, locale et infonuagique, pour y installer des applications Web : gestionnaire de contenu, outils de performance, sécurité à l'aide d'un pare-feu et de certificats HTTPS. À la fin du cours, l'étudiant sera en mesure de rédiger la documentation permettant l'installation d'un serveur, puis de la mettre en œuvre.

- **Programme** : 420.B0 · Techniques de l'informatique
- **Famille** : Soutien aux utilisateurs et réseau
- **Pondération** : 0-3-1
- **Préalables** : 420-1C5-JR, 420-2C5-JR

## Horaire et disponibilités de l'enseignant

![](dessins/enseignant.svg)

![Alain Boudreault](Documentation/images/moi.jpg)

**Alain Boudreault**, enseignant au département de Techniques de l'informatique, Cégep de Saint-Jérôme

- **Courriel** : [Aboudrea@cstj.qc.ca](mailto:Aboudrea@cstj.qc.ca)
- **Téléphone** : poste 6516
- **Local** : D125e

## A) Plan de cours

![](dessins/porte-documents.svg) *Le plan officiel de la session*

- ![](dessins/document.svg) 01 · [Plan de cours, automne 2024 (PDF)](Documentation/fichiers/420-3C3-JR_ab_pc_A24.pdf)

## B) Virtualisation et serveurs Web

![](dessins/fureteur.svg) *Linux, Apache, pile AMP, WordPress*

- ![](dessins/conteneur-vm.svg) 02 · [Concepts de virtualisation : N1/N2](Documentation/Virtualisation-des-technologies-web.md)
- ![](dessins/telechargement.svg) + · [Installation d'Ubuntu Serveur](Documentation/Virtualisation-d-Ubuntu.md)
- ![](dessins/terminal.svg) 03 · [Retour sur les commandes de base de Linux](Documentation/Commandes-Linux.md)
- ![](dessins/fureteur.svg) 04 · [Apache2](Documentation/Apache2-Mise-en-route.md)
- ![](dessins/fiole.svg) 05 · [Laboratoire S3 – Apache](Documentation/Laboratoire-S3-Apache.md) · facultatif
- ![](dessins/couches.svg) 06 · [Installation et configuration d'une pile AMP](Documentation/Ajout-d-une-pile-AMP.md)
- ![](dessins/bouclier.svg) 07 · [Mise en place et configuration de ufw (Uncomplicated FireWall)](https://doc.ubuntu-fr.org/ufw) · lien externe
- ![](dessins/plume.svg) 08 · [Installation et configuration de WordPress](Documentation/Installer-WordPress.md)
- ![](dessins/reseau.svg) 09 · [Apache 2 – Hôtes virtuels](Documentation/Apache2-Hotes-virtuels-et-htaccess.md)
- ![](dessins/badge.svg) 11 · [Installation d'un certificat signé sur un hôte virtuel (certbot)](http://ve2cuy.com/420-21e/index.php/installation-dun-certificat-signe-sur-un-hote-virtuel-apache2/) · lien externe
- ![](dessins/badge.svg) 12 · Installation d'un certificat auto-signé (pour une application Web locale) · facultatif
- ![](dessins/bouclier.svg) 13 · Stratégies de sécurité des serveurs Web (fail2ban, Lynis, Kali Linux, Kasm via Docker) · facultatif
- ![](dessins/disque.svg) 14 · [Sauvegarde et restauration d'un site WordPress](Documentation/WordPress-Sauvegarde-et-restauration.md)
  - Staging

## C) Serveurs d'entreprise et services réseau

![](dessins/ordinateur-central.svg) *ESXi, Vagrant, ssh, NFS, SMB, FTP*

- ![](dessins/serveur.svg) 15 · [ESXi – Installation](Documentation/VMware-ESXi-et-vCenter.md)
- ![](dessins/ordinateur-central.svg) 16 · [Serveurs d'entreprises](Documentation/Serveurs-d-entreprises.md)
- ![](dessins/cluster.svg) 17 · [Vagrant – Automatisation de la création de VMs](Documentation/Vagrant-Automatisation-creation-VM.md)
- ![](dessins/cle.svg) 18 · [ssh, clés (private/public) et fichier « config »](Documentation/Configuration-et-utilisation-de-ssh.md)
- ![](dessins/dossier-lien.svg) 19 · [NFS – Installation et utilisation](Documentation/NFS-Installation-et-utilisation.md)
- ![](dessins/reseau.svg) 20 · [Mise en place du protocole SMB](Documentation/Mise-en-place-d-un-serveur-SMB.md) · facultatif
- ![](dessins/telechargement.svg) 21 · [Installation d'un serveur FTP](Documentation/Installation-d-un-serveur-FTP.md)
  - vsftpd, pare-feu, FileZilla
- ![](dessins/engrenage.svg) 23 · [Ansible – Introduction](Documentation/Ansible-Introduction.md) · facultatif
- ![](dessins/conteneur.svg) 24 · [Démonstration d'une application en micro-services (introduction à Docker)](https://4204d4.ve2cuy.com/docker-introduction/) · lien externe

## D) Projets

![](dessins/drapeau.svg) *Projet 1 et épreuve synthèse*

- ![](dessins/fureteur.svg) 10 · [Projet numéro 1](Documentation/Projet-01-A2024.md) · 30 %
- ![](dessins/coupe.svg) 22 · [Projet numéro 2 – Épreuve synthèse 2024](Documentation/Epreuve-synthese-2024.md)
