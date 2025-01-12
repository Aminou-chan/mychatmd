---
title: "Manuel d’utilisateur ChatbotMD pour la plateforme Middleware COT"
version: "1.0"
author: Amina Benzina
date: "2025-01-10"
---

# Manuel d’utilisateur : ChatbotMD sur les environnements de TEST

Bienvenue dans le manuel d’utilisateur dédié à **ChatbotMD** intégré pour notre **plateforme Middleware CATS ON TREES**.  

1. [Menu principal](Menu principal)


## Menu principal

1. [Introduction](1. Introduction)  
2. [Avertissements et conventions utilisées](2. Avertissements et conventions utilisées)  
3. [Présentation de ChatbotMD](3. Présentation de ChatbotMD)  
4. [Installation et configuration](4. Installation et configuration) 
5. [Guide d’utilisation](5. Guide d’utilisation)
6. [Maintenance et mises à jour](6. Maintenance et mises à jour)
7. [Résolution des problèmes](7. Résolution des problèmes)
8. [FAQ](8. FAQ)
9. [Annexes](9. Annexes)
10. [Au revoir!](10. Au revoir!)






## 1. Introduction

Ce manuel décrit l’utilisation de **ChatbotMD**, un agent conversationnel (chatbot) conçu pour s’intégrer à la **plateforme COT** . Il vous guidera pas à pas dans :

- La compréhension du fonctionnement de ChatbotMD  
- L’installation et la configuration  
- L’utilisation au quotidien (commandes, automatisations, etc.)  
- La résolution de problèmes et la maintenance

1. [Retour au menu principal](Menu principal)  
2. [Section suivante : Avertissements et conventions](2. Avertissements et conventions utilisées)



## 2. Avertissements et conventions utilisées

- **Avertissements de sécurité** : veillez à ne pas divulguer de données sensibles (identifiants, mots de passe, etc.) dans le chatbot.  
- **Conventions d’écriture** :  
  - Les commandes à taper sont présentées dans un bloc de code, par exemple :  
    ```bash
    npm install chatbotmd
    ```
  - Les éléments d’interface (boutons, champs) sont en **gras** ou *italique*.
  - Les chemins de fichiers sont au format `/chemin/vers/fichier`.


1. [Retour au menu principal](Menu principal)  
2. [Section suivante : Présentation de ChatbotMD](3. Présentation de ChatbotMD)  


## 3. Présentation de ChatbotMD

### 3.1 Objectifs

1. **Fournir** un outil de conversation et d’assistance pour la plateforme COT.  
3. **Guider** les utilisateurs (internes/developpeurs de COT ou externes à notre équipe) dans l’utilisation de la plateforme et la recherche d'informations dans notre documentation (enduser et internal).

### 3.2 Fonctionnalités clés

- **Réponses rapides et contextuelles** aux questions liées à la plateforme.  
- **Intégration** avec les API internes de COT.  
- **Traçabilité** : possibilité de stocker et d’exporter l’historique des conversations.

### 3.3 Environnement requis

- **Système d’exploitation** : RHEL8+  
- **Dépendances (!sera installées avec ansible)** : Node.js (version 16 ou +).  
- **Réseau** : Port ouvert (HTTP).  
- **Accès** : Crédentials/API Key pour la plateforme COT si nécessaire (partie à developper plus tard).

1. [Retour au menu principal](Menu principal)  
2. [Section suivante : Installation et configuration](4. Installation et configuration)  

## 4. Installation et configuration

### 4.1 initiliser ansible

- Procéder comme suit à partir de votre user sur l'ansible de DEV `<user>@<machine_dev_ansible>`

```sh
cd /env/ambz/cot_ansible/playbook-init

git pull

# puis basculer sur la branche feature/chatbotMD

git checkout feature/chatbotMD

# mettre à jour les roles via ansible-galaxy
ansible-galaxy install -f -g -r requirements.txt
```

### 4.2 installation

Mise à jour du composant GUI de l'EXEC

```sh
cd ~/cot_ansible/playbook-init

ansible-playbook inst_CM.yml -i inventory/test --tags="install_GUI_CM"
```

1. [Retour au menu principal](Menu principal)  
2. [Section suivante :  Guide d’utilisation](5. Guide d’utilisation)  


## 5. Guide d’utilisation
### 5.1 Premier démarrage

Accédez à l’URL (***) (entreprise)
`https://chatmd.forge.apps.education.fr/#https://github.com/Aminou-chan/RA9/blob/main/README.md`(ecole_RA9)

Connectez-vous à l’aide de vos identifiants (si la plateforme le requiert/plus tard).

### 5.2 Interactions de base

1. Saisir votre question ou commande dans le champ de texte.
2. Envoyer la demande (bouton *Envoyer* ou touche *Entrée*).
3. Lire la réponse produite par ChatbotMD.

### 5.3 Fonctionnalités avancées

Commandes spécifiques : exemple `!restart moduleX` pour redémarrer un module.
Scripts personnalisés : ex. `!script backupDB`.


1. [Retour au menu principal](Menu principal)  
2. [Section suivante : Maintenance et mises à jour](6. Maintenance et mises à jour)  


## 6. Maintenance et mises à jour
### 6.1 Consignes de maintenance

Vous pouvez surveiller les logs (`logs/chatbotmd.log`) pour détecter des erreurs.
Il faudra sauvegarder régulièrement la configuration (`config.yaml`).

### 6.2 Procédure de mise à jour

1. Mettre à jour le Repo chatMD sur COT (Repo Mirror du repository original)
2. Mettre à jour la bonne version dans `~/playbook-init/inventory/test/groups_vars/vm_cm`
et `~/playbook-init/inventory/test/groups_vars/oak_cm`

variable: `src_gui_ext`

3. reinstaller le GUI CM

```sh
cd ~/cot_ansible/playbook-init

ansible-playbook inst_CM.yml -i inventory/test --tags="install_GUI_CM"
```

4. Tester le lien (***) pour verifier le bon fonctionnement


5. (optionnel) Vérifier le fonctionnement dans les logs.

1. [Retour au menu principal](Menu principal)  
2. [Section suivante : Résolution des problèmes](7. Résolution des problèmes) 


## 7. Résolution des problèmes
### 7.1 Problèmes courants

- **Réponses incohérentes :** 
    - relancer votre navigateur/vider le cache de votre navigateur
    - vérifier l’API ou la base de connaissances.

- **Temps de réponse élevé :** regarder la charge serveur et la connectivité.

### 7.2 Dépannage avancé

- **Le chatbot ne se lance pas :** vérifier la config et les ports (logs).
- **Support :** contacter l’équipe de COT et au pire l'equipe de chatbotMD si rien ne fonctionne.


1. [Retour au menu principal](Menu principal)  
2. [Section suivante : FAQ](8. FAQ) 

## 8. FAQ

**ChatbotMD gère-t-il plusieurs langues ?**
Oui, si les modules linguistiques sont installés et configurés.
**Comment personnaliser l’interface ?**
Modifier les fichiers .css et .js dans public/.
**Existe-t-il des limites ?**
Les performances dépendent du serveur et de la configuration réseau.

1. [Retour au menu principal](Menu principal)  
2. [Section suivante : Annexes](9. Annexes) 


## 9. Annexes
### 9.1 Glossaire

- **API :** Interface de programmation, permet à plusieurs apps de communiquer.
- **Middleware :** Logiciel d’interfaçage entre différents systèmes ou services.
- **Chatbot :** Agent conversationnel automatisé.
- **COT**: Cats On Trees, plateforme middleware de AG2R La Mondiale pour hébérger des applications tomcat

### 9.2 Références

<ul>
<li><a href="https://fr.wikibooks.org/wiki/La_documentation/R%C3%A9daction_technique/R%C3%A9daction_d&#39;un_manuel_d&#39;utilisation">Wikibooks – Rédaction d’un manuel d’utilisation</a></li>
<li>Documentation interne de la plateforme COT</li>
</ul>

1. [Retour au menu principal](Menu principal)  
2. [Section suivante : Au revoir!](10. Au revoir!) 


## 10. Au revoir!
:star2: Merci d’avoir consulté ce manuel d’utilisation

ChatbotMD est conçu pour améliorer l’expérience utilisateur et simplifier la gestion de notre plateforme Middleware.
Pour tout complément d’information ou problème spécifique, consultez la section de résolution des problèmes ou contactez le support interne.
