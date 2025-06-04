# Couches 5-7 – Application

## 1. Types d'attaques
- Scan de vulnérabilités Web  : Rechercher des failles courantes sur un site/app.
- Brute force/dictionnaire  : Tester un grand nombre d’identifiants ou URLs.
- Fuzzing  : Envoyer des données inattendues pour déclencher un comportement anormal.
- Injection  : Exploiter les failles d’injection (SQL, XSS…) sur une appli.

## 2. Outils et méthodes

### ⚡ Attaque : Scan de vulnérabilités Web

#### Outil : Nikto
**Description** : Scanner automatisé de failles web classiques.
**Installation** : sudo apt install nikto
**Commande** : nikto -h http://[cible|192.168.1.1]

---

### ⚡ Attaque : Brute force/dictionnaire

#### Outil : Gobuster
**Description** : Fuzz de répertoires et fichiers sur un serveur web.
**Installation** : sudo apt install gobuster
**Commande** : gobuster dir -u http://[cible|192.168.1.1] -w /usr/share/wordlists/dirb/common.txt

---

### ⚡ Attaque : Fuzzing

#### Outil : WFuzz
**Description** : Fuzzer d’URL, headers, POST, etc.
**Installation** : sudo apt install wfuzz
**Commande** : wfuzz -c -w /usr/share/wordlists/dirb/common.txt --hc 404 http://[cible|192.168.1.1]/FUZZ

---

### ⚡ Attaque : Injection

#### Outil : SQLmap
**Description** : Automatiser l’exploitation d’injections SQL.
**Installation** : sudo apt install sqlmap
**Commande** : sqlmap -u "http://[cible|192.168.1.1]/vulnerable.php?id=1" --batch --dbs
