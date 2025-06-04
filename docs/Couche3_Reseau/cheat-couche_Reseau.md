# Couche 3 – Réseau

## 1. Types d'attaques réseau (avec explications)

- **Scan de ports**  
  Permet d’identifier les ports ouverts sur une cible, afin de repérer les services exposés et d’évaluer la surface d’attaque.  
  → Très utile en phase de reconnaissance lors d’un pentest.

- **Fingerprinting d’OS**  
  Technique permettant de déduire le système d’exploitation d’un hôte distant grâce à l’analyse des réponses réseau.  
  → Peut orienter le choix des exploits à utiliser plus tard.

- **Scan d’hôtes (host discovery)**  
  Recherche de toutes les machines présentes sur un segment réseau.  
  → Essentiel pour la cartographie du réseau.

- **Flood (SYN/UDP/ICMP Flood)**  
  Saturation de la pile réseau d’une cible en envoyant un grand nombre de paquets (DoS/DDoS).  
  → Utilisé pour tester la résistance d’un service ou réaliser une attaque de déni de service.

---

## 2. Outils et méthodes d’attaque

---

### ⚡ Attaque : Scan de ports

#### Outil principal : **Nmap**
- **Description** : Le scanner de ports de référence, très complet (TCP/UDP, scripts NSE…).
- **Pourquoi l’utiliser** :  
    - Rapide, modulable, résultats très détaillés.
    - Permet aussi de détecter les services et versions associés à chaque port.
- **Installation** :  
    - Debian/Ubuntu : `sudo apt install nmap`
    - Arch : `sudo pacman -S nmap`
- **Exemples de commandes** :
    - **Scan TCP basique** :  
      `nmap -sS [IP cible]`
    - **Scan UDP** :  
      `nmap -sU [IP cible]`
    - **Scan de tous les ports** :  
      `nmap -p- [IP cible]`
- **Bonus** : Pour scanner un range IP :  
  `nmap -sP 192.168.1.0/24`
- **Alternatives/outils complémentaires** :
    - **Masscan** : Ultra rapide pour les gros réseaux (`sudo apt install masscan`)
    - **Rustscan** : Pour aller encore plus vite

---

### ⚡ Attaque : Fingerprinting d’OS

#### Outil principal : **Nmap**
- **Pourquoi l’utiliser** : Il utilise différentes signatures TCP/IP pour deviner l’OS cible.
- **Commande** :  
  `nmap -O [IP cible]`
- **Explication** : Les bannières, les réponses à des paquets “exotiques” permettent de déduire Windows/Linux/Unix, et parfois la version.

---

### ⚡ Attaque : Scan d’hôtes (Host Discovery)

#### Outil principal : **Nmap**
- **Commande** :  
  `nmap -sn 192.168.1.0/24`
- **Explication** : Permet d’identifier tous les hôtes actifs sur un sous-réseau.

#### Outil secondaire : **Netdiscover**
- **Description** : Idéal pour une découverte ARP rapide en local.
- **Installation** : `sudo apt install netdiscover`
- **Commande** :  
  `sudo netdiscover -r 192.168.1.0/24`

---

### ⚡ Attaque : Flood réseau (SYN Flood / UDP Flood)

#### Outil principal : **Hping3**
- **Description** : Générateur de paquets personnalisés (TCP, UDP, ICMP…).
- **Pourquoi l’utiliser** : Permet de simuler de vraies attaques DoS pour des tests de résistance.
- **Installation** : `sudo apt install hping3`
- **Commandes** :  
    - **SYN Flood** :  
      `sudo hping3 -S --flood -V [IP cible] -p 80`
    - **UDP Flood** :  
      `sudo hping3 --udp --flood -p 53 [IP cible]`
- **Notes** : À utiliser dans un cadre légal (tests de charge sur une infra autorisée uniquement).

#### Outil secondaire : **Scapy**
- **Description** : Framework Python pour manipuler et générer des paquets réseau.
- **Utilisation** : Pour des floods custom, des scans “stealth”, ou des exploits plus fins.

---

## 3. Contribution

> Pour ajouter une attaque :  
> - Ajoutez une nouvelle section sous “Types d’attaques disponibles”  
> - Expliquez le but, la technique, et les risques  
> - Présentez les outils (description, installation, exemples de commandes)
