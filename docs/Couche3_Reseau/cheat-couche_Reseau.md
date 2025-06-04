# Couche 3 – Réseau

## 1. Types d'attaques
- Scan de ports  : Découvrir les ports ouverts sur une cible pour repérer les services actifs.
- Fingerprinting d’OS  : Détecter le système d’exploitation d’une cible via l’analyse réseau.
- Scan d’hôtes  : Identifier toutes les machines d’un réseau.
- Flood (SYN/UDP/ICMP)  : Saturer la pile réseau d’une cible pour provoquer un déni de service.

## 2. Outils et méthodes

### ⚡ Attaque : Scan de ports

#### Outil : Nmap
**Description** : Scanner de ports et services très puissant.
**Installation** : sudo apt install nmap
**Commande** : nmap -sS [IP cible|192.168.1.1]

---

### ⚡ Attaque : Fingerprinting d’OS

#### Outil : Nmap
**Description** : Détection d’OS via analyse des réponses réseau.
**Installation** : sudo apt install nmap
**Commande** : nmap -O [IP cible|192.168.1.1]

---

### ⚡ Attaque : Scan d’hôtes

#### Outil : Netdiscover
**Description** : Découverte rapide des hôtes via ARP sur un sous-réseau.
**Installation** : sudo apt install netdiscover
**Commande** : sudo netdiscover -r [plage|192.168.1.0/24]

---

### ⚡ Attaque : Flood (SYN/UDP/ICMP)

#### Outil : Hping3
**Description** : Générateur de paquets pour flood TCP/UDP/ICMP.
**Installation** : sudo apt install hping3
**Commande** : sudo hping3 -S --flood -V [IP cible|192.168.1.1] -p [port|80]
