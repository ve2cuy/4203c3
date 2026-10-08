# Laboratoire S3 – Apache

*Document converti depuis [ve2cuy.com/420-3c3](https://ve2cuy.com/420-3c3/?page_id=1633) — dernière modification : 2024-03-18*

---

1. Au besoin, installer virtualbox
2. Dans virtuelBox, installer deux VM Ubuntu server:
   1. 21.04 – **srv01**, avec un réseau de type bridge (pont) et un disque de 20go.
   2. 20.04 – **srv02**, avec un réseau de type bridge (pont) et un disque de 18go.
      - Au besoin, Télécharger le fichier ISO du site d’Ubuntu.
3. Renseigner le DNS dans Windows: ip-vm1. **srv01.j**, ip-vm2 **srv02.j**.
4. Tester les noms de domaine de l’étape 3 avec la commande ***ping*** à partir d’un terminal Git Bash.
5. Effectuer la Mise à jour des packages sur les deux serveurs.
6. Installer **apache2** sur **srv01**.
7. Installer **nginx** sur **srv02**.
8. Installer **mc** sur **srv02**
9. Créer un compte ´**gestion** ´ sur **srv02**,
10. Ajouter le compte ‘**gestion**‘ au groupe des **sudoers**
11. Lancer **mc** automatiquement au login du compte ‘**gestion**‘.
12. Installer le cheatsheet de bootstrap sur **srv01**
13. Ajuster les droits d’accès pour interdire tout accès à **other** dans le rep home des deux serveurs web.
14. Remplacer la page d’accueil web de **srv02** par une page qui souhaite la bienvenue sur le site de la cie ABC avec votre nom sur la ligne numéro deux.
15. Tester les deux serveurs web en utilisant leur nom de domaine.
16. Tester le site web de **srv02** de votre voisin.

---

[⬅️ Retour à la liste des documents](../README.md)
