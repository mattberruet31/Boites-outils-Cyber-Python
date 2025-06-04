# Couche 2 – Liaison

## 1. Types d'attaques
- ARP Spoofing/Poisoning  : Empoisonner la table ARP pour intercepter le trafic entre deux hôtes.
- MAC Spoofing  : Usurper une adresse MAC pour se faire passer pour un autre appareil sur le réseau.
- Flooding (MAC/ARP/Switch)  : Saturer les tables d’un switch ou d’un routeur.
- Sniffing local  : Intercepter les paquets en mode promiscuous.

## 2. Outils et méthodes

### ⚡ Attaque : ARP Spoofing/Poisoning

#### Outil : Ettercap
**Description** : Outil complet pour attaques de type Man-in-the-Middle sur réseau local.
**Installation** : sudo apt install ettercap-graphical
**Commande** : sudo ettercap -G

---

### ⚡ Attaque : MAC Spoofing

#### Outil : Macchanger
**Description** : Change facilement l’adresse MAC de l’interface réseau.
**Installation** : sudo apt install macchanger
**Commande** : sudo macchanger -r [interface|eth0]

---

### ⚡ Attaque : Flooding (MAC/ARP/Switch)

#### Outil : Macof
**Description** : Inonde la table MAC d’un switch pour permettre le sniffing.
**Installation** : sudo apt install dsniff
**Commande** : sudo macof -i [interface|eth0]

---

### ⚡ Attaque : Sniffing local

#### Outil : Wireshark
**Description** : Permet la capture et l’analyse de paquets sur le LAN.
**Installation** : sudo apt install wireshark
**Commande** : wireshark
**Info** : Lancer la capture sur l’interface appropriée.

#### Outil : tcpdump
**Description** : Capture CLI en mode promiscuous.
**Installation** : sudo apt install tcpdump
**Commande** : sudo tcpdump -i [interface|eth0] -p
