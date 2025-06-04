# Couches 5-7 – Application

## 1. Types d’attaques sur la couche Application

- **Scan de vulnérabilités Web**  
  Rechercher automatiquement des failles connues sur des serveurs ou applications web.

- **Brute force/dictionnaire**  
  Tester un grand nombre d’identifiants ou d’URLs pour trouver des accès ou des fichiers cachés.

- **Fuzzing**  
  Envoyer des données aléatoires ou malicieuses pour déclencher un comportement inattendu (plantage, RCE, etc.)

- **Injection**  
  Tester l’injection de code dans des formulaires, URL ou headers (SQLi, XSS…).

---

## 2. Outils et méthodes

### ⚡ Attaque : Scan de vulnérabilités

#### Outil : **Nikto**
- **Description** : Scanner d’applications web pour vulnérabilités classiques (fichiers dangereux, headers, CGI…).
- **Pourquoi l’utiliser ?** :  
  - Rapide, facile, bon en automatisation
- **Installation** :  
  - `sudo apt install nikto`
- **Commande** :  
  - `nikto -h http://[IP ou domaine cible]`

#### Outil : **OpenVAS** (Greenbone)
- **Description** : Scanner de vulnérabilités réseau/applications très complet.
- **Installation** :  
  - Guide officiel sur [Greenbone.net](https://www.greenbone.net/)
- **Utilisation** : Interface web ou CLI.

---

### ⚡ Attaque : Brute force/dictionnaire

#### Outil : **Gobuster**
- **Description** : Fuzz de répertoires/fichiers web.
- **Installation** :  
  - `sudo apt install gobuster`
- **Commande** :  
  - `gobuster dir -u http://[IP ou domaine] -w /usr/share/wordlists/dirb/common.txt`

#### Outil : **Hydra**
- **Description** : Brute-force login sur des services (HTTP, FTP, SSH…).
- **Installation** :  
  - `sudo apt install hydra`
- **Commande** :  
  - `hydra -l admin -P /usr/share/wordlists/rockyou.txt ssh://[IP cible]`

---

### ⚡ Attaque : Fuzzing

#### Outil : **WFuzz**
- **Description** : Fuzzer d’URL, headers, données POST, etc.
- **Installation** :  
  - `sudo apt install wfuzz`
- **Commande** :  
  - `wfuzz -c -w /usr/share/wordlists/dirb/common.txt --hc 404 http://[IP]/FUZZ`

---

### ⚡ Attaque : Injection

#### Outil : **SQLmap**
- **Description** : Injection SQL automatisée.
- **Installation** :  
  - `sudo apt install sqlmap`
- **Commande** :  
  - `sqlmap -u "http://[IP]/vulnerable.php?id=1" --batch --dbs`

#### Outil : **XSStrike**
- **Description** : Teste l’injection de code (XSS) sur les applications web.
- **Installation** :  
  - `git clone https://github.com/s0md3v/XSStrike.git`
- **Commande** :  
  - `python3 XSStrike/xsstrike.py -u "http://[IP]/search.php?q=test"`

---

## 3. Contribution

> Précisez l’attaque, l’outil, expliquez l’intérêt, et ajoutez exemples et bonnes pratiques.
