# Ansible – Introduction

*Document converti depuis [ve2cuy.com/420-3c3](https://ve2cuy.com/420-3c3/?page_id=1651) — dernière modification : 2024-03-18*

---

Ansible est un outils d’orchestration pour la configuration, la modification, la gestion et la mise à jour de serveurs distants.

## Document en cours de rédaction

```
# Note: srv02 est défini dans ~/.ssh/config avec une clé privée
# "srv02," all = tous les noeuds de la liste, -m = module à exécuter 
ansible -i "srv02," all -m ping

# Exécuter une commande sur le noeud
ansible -i "srv02," all -m command -a ps
# ou bien
ansible -i "srv02," all -m shell -a ¨ ps | grep chaine | …¨

# Installer python avec le module raw
ansible -i ¨node,¨ all -u username -b -K -m raw -a ¨apt install -y python3¨

# ansible -i "srv02," all -m apt -a ¨name=nginx state=latest¨
```

---

[⬅️ Retour à la liste des documents](../README.md)
