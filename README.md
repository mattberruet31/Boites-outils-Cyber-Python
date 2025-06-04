# 🛡️ Pentest Toolkit – Kit Interactif d’Audit Sécurité Réseau

![Python](https://img.shields.io/badge/python-3.8%2B-blue?logo=python)
![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)

---

## 🚀 Objectif du projet

**Pentest Toolkit** vise à faciliter et professionnaliser la conduite de tests d’intrusion (pentesting) réseau pour :
- Les étudiants en cybersécurité,
- Les consultants sécurité,
- Les administrateurs systèmes,
- Toute personne souhaitant auditer, automatiser et documenter ses tests réseau, sur toutes les couches du modèle OSI.

Le projet apporte :
- **Un guide interactif** étape par étape pour lancer des attaques contrôlées,
- **Des cheatsheets centralisées** pour chaque couche réseau, **modifiables** facilement,
- **La génération automatique d’un rapport d’audit structuré**,
- **L’intégration et l’installation automatique des outils** nécessaires,
- **Un cadre communautaire** : chacun peut enrichir, adapter et maintenir l’outil.

---

## 🧭 Structure détaillée du projet

```

racine/
│
├── docs/                               # Documentation et bases d’attaques/outils (par couche réseau)
│   ├── Couche1\_Physique/
│   │   └── cheat-couche\_Physique.md
│   ├── Couche2\_Liaison/
│   │   └── cheat-couche\_Liaison.md
│   ├── Couche3\_Reseau/
│   │   └── cheat-couche\_Reseau.md
│   ├── Couche4\_Transport/
│   │   └── cheat-couche\_Transport.md
│   ├── Couche5-7\_Application/
│   │   └── cheat-couche\_Application.md
│   ├── Couche8\_Social-Engineering/
│   │   └── cheat-couche\_Social-Engineering.md
│
├── logs/                               # Tous les rapports générés automatiquement (Markdown)
│
├── pentest.py                          # Script principal interactif (à lancer)
│
├── README.md                           # Documentation du projet (ce fichier)
│
└── requirements.txt (optionnel)        # Liste des dépendances (Python ≥ 3.8 conseillé)

````

---

## 🖥️ Fonctionnement général

1. **Lance le script principal** :
    ```bash
    python3 pentest.py
    ```

2. **Renseigne les informations du test** :
    - Ton nom/prénom ou pseudo (testeur)
    - Client ou contexte
    - Bien essentiel testé (serveur, application, segment réseau…)
    - Risque associé (ce que tu veux tester, ex : attaque DoS, fuite de données…)

3. **Navigue dans l’outil grâce aux menus interactifs** :
    - Choisis la **couche réseau** (physique, liaison, réseau, etc.)
    - Choisis le **type d’attaque** (spoofing, scan, flood…)
    - Choisis l’**outil** à utiliser (nmap, ettercap, tcpdump…)
    - Renseigne les **paramètres interactifs** (IP, port, interface…)
    - **Automatisation** de l’installation des outils si besoin (confirmation proposée)
    - **Choisis le mode d’exécution** :
        - *Attendre la fin et obtenir un résultat* (pour scans, brute force, etc.)
        - *Ouvrir dans un terminal séparé* (recommandé pour outils interactifs : Wireshark, shell, hping3…)
        - *Lancer en arrière-plan* (utile pour floods/tests prolongés)
    - **Enchaîne autant d’attaques/tests que souhaité** dans la même session.

4. **Toutes les actions sont automatiquement loguées** (commande, outil, résultat, paramètres utilisés…).

5. **En fin de session**, rédige un commentaire et une conclusion :  
   Le rapport final est généré en Markdown dans `logs/`, prêt à être envoyé, archivé ou converti en PDF.

---

## 📋 Exemple de rapport généré

```markdown
# Rapport de Test de Sécurité
## Informations Générales
- **Date du test** : 04/06/2025
- **Testeur** : alice
- **Client** : ACME Corp
---
## Bien Essentiel Testé
- **Bien essentiel** : Serveur Web
- **Risque associé** : Exposition aux attaques réseau
---
## Attaque réalisée 1 : Scan de ports
- **Outil utilisé** : nmap
- **Commande exécutée** : `nmap -sS 192.168.1.1`
### Résultats du Test
````

Starting Nmap 7.94...
PORT   STATE SERVICE
80/tcp open  http

```
---
## Commentaires
Tout s’est bien passé.
---
## Conclusion
Le test a permis de détecter des ports ouverts.
```

---

## 📝 Structure d’un fichier Markdown de couche (`cheat-couche_X.md`)

Chaque fichier décrit toutes les attaques et outils connus de la couche concernée, sous un format **Markdown strict**.
Le script extrait et interprète ces fichiers.

### **Exemple de structure dans `docs/Couche2_Liaison/cheat-couche_Liaison.md`** :

```markdown
## 1. Types d'attaques
- ARP Spoofing/Poisoning  : Empoisonner la table ARP pour intercepter le trafic entre deux hôtes.
- MAC Spoofing  : Usurper une adresse MAC pour se faire passer pour un autre appareil sur le réseau.

## 2. Outils et méthodes

### ⚡ Attaque : ARP Spoofing/Poisoning

#### Outil : Ettercap
**Description** : Outil complet pour attaques de type Man-in-the-Middle sur réseau local.
**Installation** : sudo apt install ettercap-graphical
**Commande** : sudo ettercap -G

### ⚡ Attaque : MAC Spoofing

#### Outil : macchanger
**Description** : Change facilement l’adresse MAC d’une interface.
**Installation** : sudo apt install macchanger
**Commande** : sudo macchanger -r [interface|eth0]
```

**Explication des sections :**

* Chaque attaque commence par `### ⚡ Attaque : ...`
* Chaque outil par `#### Outil : ...`
* La commande shell réelle doit être indiquée dans `**Commande** : ...`
* Les paramètres dynamiques sont entre crochets `[parametre|valeur_par_defaut]`, ex : `[IP cible|192.168.1.1]`
* **Ajoute `**Info** : ...` si besoin pour donner un conseil utilisateur (jamais de commande dans ce champ)**

---

## ➕ Ajouter ou modifier des attaques / outils

**Pour contribuer** :

1. **Ajoute une attaque** dans la section “Outils et méthodes” :

   ```markdown
   ### ⚡ Attaque : NomAttaque

   #### Outil : NomOutil
   **Description** : Ce que fait cet outil.
   **Installation** : sudo apt install nomoutil
   **Commande** : nomoutil [param1|defaut1] [param2|defaut2]
   **Info** : Tips ou précisions à lire avant/pendant l’exécution
   ```

2. **Ajoute autant d’outils que tu veux pour la même attaque.**

3. **Exemples :**

   * **Nouvelle attaque**

     ```markdown
     ### ⚡ Attaque : DNS Spoofing

     #### Outil : dsniff
     **Description** : Collection de scripts pour le spoofing DNS.
     **Installation** : sudo apt install dsniff
     **Commande** : dnsspoof -i [interface|eth0]
     ```
   * **Nouveau paramètre**

     ```markdown
     **Commande** : nmap -p [port|80] [IP cible|192.168.1.1]
     ```
   * **Info pour l’utilisateur**

     ```markdown
     **Info** : Attention, nécessite des droits root.
     ```

4. **Enregistre et lance le script** : Les modifications sont prises en compte immédiatement.

---

## 📚 Comprendre le rapport généré

* **Toutes les informations du test sont structurées** (date, testeur, client, cible, risque, attaques effectuées…)
* **Chaque attaque testée est détaillée** (attaque, outil, commande, résultat)
* **Les résultats “stdout/stderr” sont inclus**
* **Le rapport est au format Markdown**, tu peux le convertir en PDF (avec Pandoc, Typora…), le versionner ou le transmettre au client.

---

## 🙌 Bonnes pratiques et conseils

* **Testez dans un environnement sécurisé/légal** (laboratoire, machine de test, VM…)
* **Adaptez les cheatsheets** à vos besoins (outils, types d’attaques, OS…)
* **Contribuez** en pull request : chaque ajout profite à la communauté
* **Gardez les résultats confidentiels** : le rapport peut contenir des infos sensibles (IPs, identifiants, bannières…)

---

## 🛡️ Sécurité et disclaimer

* **Ce projet est éducatif et destiné à l’audit éthique**.
  **Utilisez-le uniquement sur des systèmes dont vous avez l’autorisation.**
* L’auteur et la communauté ne sauraient être tenus responsables de son utilisation hors cadre légal.

---

## 🖊️ FAQ rapide

**Q : Peut-on ajouter de nouveaux outils ?**
R : Oui, modifie simplement les `.md` de la couche correspondante !

**Q : Les outils sont-ils installés automatiquement ?**
R : Oui, tu peux choisir de lancer l’installation depuis le script.

**Q : Peut-on exporter le rapport en PDF ?**
R : Oui, avec [Pandoc](https://pandoc.org/) ou tout éditeur Markdown moderne.

**Q : Puis-je adapter la structure ?**
R : Oui, tout est modulaire (Python et Markdown).

---

## 🤝 Contribution

* Forkez le repo, créez une branche et proposez vos ajouts/améliorations !
* Toute PR sérieuse et testée est la bienvenue.
* Adoptez une rédaction claire (voir exemples).
* Utilisez le système d’issues pour vos questions ou suggestions.

---

## 📫 Contact & Support

* [Issues GitHub](https://github.com/tonrepo/tonprojet/issues)
* [Pull Requests](https://github.com/tonrepo/tonprojet/pulls)

---

## 📝 Licence

Ce projet est sous licence MIT : open-source, vous pouvez l’utiliser, l’adapter et le diffuser (merci de citer l’outil en cas d’utilisation pro).

---

*Happy Pentest !* 🕵️‍♂️✨

```

---

**C’est structuré, explicite, pédagogique et prêt pour le partage sur Github.**  
Personnalise le nom du repo, l’auteur, les liens, la licence si besoin !  
Si tu veux une version anglaise, un “quick start”, un modèle PDF de rapport : demande 😉
```
