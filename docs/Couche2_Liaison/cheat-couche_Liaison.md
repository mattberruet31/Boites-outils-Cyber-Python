# Couche 2 – Liaison

## 1. Types d'attaques sur la couche Liaison

- **ARP Spoofing/Poisoning**  
  Détourner le trafic local en envoyant de fausses informations ARP pour se faire passer pour une autre machine (ex. : MITM).

- **MAC Spoofing**  
  Changer l’adresse MAC de son interface pour usurper une identité réseau ou contourner des restrictions.

- **Flooding (MAC, ARP, Switch)**  
  Saturer les tables des switchs pour passer le trafic en mode hub, ou générer un déni de service local.

- **Sniffing local**  
  Intercepter le trafic sur le LAN grâce à un mode promiscuous, souvent après une attaque ARP/MAC.

---

## 2. Outils et méthodes

### ⚡ Attaque : ARP Spoofing

#### Outil : **Ettercap**
- **Description** : Un must pour les attaques Man-in-the-Middle sur réseau local (ARP, DNS, etc.)
- **Pourquoi l’utiliser ?** :  
  - Automatisation, interfaces graphique/CLI
  - Peut injecter des paquets, capturer des credentials
- **Installation** :  
  - `sudo apt install ettercap-graphical`
- **Commande** :  
  - `sudo ettercap -G` (GUI), suivre les menus pour lancer ARP spoofing

#### Outil : **arpspoof**
- **Description** : Petit outil CLI pour ARP poisoning rapide.
- **Installation** :  
  - `sudo apt install dsniff`
- **Commande** :  
  - `sudo arpspoof -i eth0 -t [IP cible] [IP passerelle]`

---

### ⚡ Attaque : MAC Spoofing

#### Outil : **Macchanger**
- **Description** : Change l’adresse MAC d’une interface à la volée.
- **Pourquoi l’utiliser ?** :  
  - Bypass filtrage MAC, anonymisation
- **Installation** :  
  - `sudo apt install macchanger`
- **Commande** :  
  - `sudo macchanger -r eth0`
- **Note** : Nécessite de down/up l’interface :  
    - `sudo ip link set eth0 down`
    - `sudo macchanger -r eth0`
    - `sudo ip link set eth0 up`

---

### ⚡ Attaque : Flooding

#### Outil : **Macof**
- **Description** : Inonde la table MAC d’un switch, pour repasser en mode hub (sniffing possible).
- **Installation** :  
  - `sudo apt install dsniff`
- **Commande** :  
  - `sudo macof -i eth0`
- **Précaution** : Peut perturber tout le réseau local ! Ne jamais utiliser sans autorisation.

---

### ⚡ Attaque : Sniffing local

#### Outil : **Wireshark** ou **tcpdump**
- **Description** : Capture et analyse de paquets.
- **Installation** :  
  - `sudo apt install wireshark tcpdump`
- **Commandes** :  
  - `sudo tcpdump -i eth0`  
  - Lancer Wireshark, choisir l’interface cible.

---

## 3. Contribution

> Pour chaque nouvelle attaque, détaillez le contexte et l’outil utilisé, donnez si possible des exemples de commandes.
