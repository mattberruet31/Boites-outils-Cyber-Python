# Couche 1 – Physique

## 1. Types d'attaques

- Perturbation/Interruption physique  : Provoquer une coupure ou perturber physiquement le réseau (débranchement de câble, sabotage, brouillage...).
- Sniffing physique  : Capturer le trafic en se connectant physiquement à un câble réseau.
- Détection de topologie physique  : Analyser le câblage et l’état des connexions du réseau.

## 2. Outils et méthodes

### ⚡ Attaque : Perturbation/Interruption physique

#### Outil : Hping3
- **Description**: Génère du trafic pour tester la résistance physique d’un lien réseau.
- **Installation**: `sudo apt install hping3`
- **Commande**: `sudo hping3 --icmp -i u1 [IP cible]`

### ⚡ Attaque : Sniffing physique

#### Outil : Wireshark
- **Description**: Capture tous les paquets qui passent physiquement sur un câble.
- **Installation**: `sudo apt install wireshark`
- **Commande**: Lancer Wireshark et démarrer la capture sur l’interface filaire.

### ⚡ Attaque : Détection de topologie physique

#### Outil : Mii-tool
- **Description**: Vérifie l’état physique des ports Ethernet.
- **Installation**: `sudo apt install net-tools`
- **Commande**: `sudo mii-tool eth0`
