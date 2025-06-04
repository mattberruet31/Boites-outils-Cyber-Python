# Couche 1 – Physique

## 1. Types d'attaques physiques

- **Perturbation/Interruption physique**  
  Actions visant à dégrader ou stopper le fonctionnement d’un réseau en agissant sur le matériel : débranchement de câbles, sabotage, création d’interférences (ex. : brouillage d’ondes radio).

- **Sniffing physique**  
  Connexion physique à un câble réseau (tap, répéteur…) pour intercepter le trafic.

- **Détection de topologie physique**  
  Cartographier les connexions, identifier les points faibles et les interconnexions (ex. : testeur de câble).

---

## 2. Outils et méthodes

### ⚡ Attaque : Sniffing physique

#### Outil : **Wireshark** (en mode filaire)
- **Description** : Permet de capturer tous les paquets circulant physiquement sur un segment réseau.
- **Pourquoi l’utiliser ?** :  
  - Identifier des failles physiques (ex. : hub non sécurisé)
  - Prouver qu’un réseau n’est pas isolé
- **Installation** :  
  - Debian/Ubuntu : `sudo apt install wireshark`
- **Commande** :  
  - Lancer Wireshark, choisir l’interface filaire détectée, démarrer la capture.
- **Note** : Nécessite souvent d’être root.

---

### ⚡ Attaque : Détection de topologie

#### Outil : **Mii-tool**
- **Description** : Vérifie l’état physique d’un port Ethernet, détecte si le câble est connecté/actif.
- **Installation** :  
  - Debian/Ubuntu : `sudo apt install net-tools`
- **Commande** :  
  - `sudo mii-tool eth0`

#### Outil : **Câble testeur** (matériel physique)
- **Description** : Permet de vérifier la continuité d’un câble, repérer un mauvais branchement ou une rupture.

---

### ⚡ Attaque : Perturbation

#### Outil : **Hping3**
- **Description** : Générateur de trafic (flood) pour tester la résilience d’un lien physique.
- **Installation** : `sudo apt install hping3`
- **Commande** :  
  - `sudo hping3 --icmp -i u1 [IP cible]`
- **Note** : À utiliser sur un labo/test autorisé seulement.

---

## 3. Contribution

> Pour ajouter une attaque physique ou un outil, expliquez bien le contexte et l’intérêt, et fournissez les commandes ou références nécessaires.
