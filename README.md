# router-on-a-stick-lab
Inter-VLAN routing configuration using a single physical router interface and subinterfaces (CCNA 200-301).

# 🔀 Router-on-a-Stick Inter-VLAN Routing Lab (CCNA 200-301)

## 📌 Objectif du projet
Mise en œuvre d'un routage inter-VLAN sous **Cisco Packet Tracer**. Ce projet démontre la capacité à interconnecter plusieurs VLANs (VLAN 10 et VLAN 20) à l'aide d'un unique routeur physique via des **sous-interfaces dot1Q** et une architecture multi-switchs.

## 🗺️ Topologie Réseau
- **1 Routeur (Cisco 2911)** : Supporte les sous-interfaces de passerelle (`GigabitEthernet0/0.10` et `GigabitEthernet0/0.20`).
- **2 Switches (Catalyst 2960)** : Configurés avec des ports d'accès (*Access*) pour les hôtes et des liaisons agrégées (*Trunk*) pour propager les VLANs.
- **Plan d'adressage :**
  - **VLAN 10 (Admin) :** `192.168.10.0/24` (Passerelle : `192.168.10.1`)
  - **VLAN 20 (Production) :** `192.168.20.0/24` (Passerelle : `192.168.20.1`)
- Fichier Packet Tracer du lab : [Router-on-a-Stick-Lab.pkt](./Router-on-a-Stick-Lab.pkt)

## 🛠️ Technologies & Protocoles Utilisés
- **VLANs (IEEE 802.1Q) :** Segmentation logique de niveau 2.
- **Trunking :** Liaisons inter-équipements transportant plusieurs flux VLANs simultanément.
- **Sous-interfaces Routeur :** Encapsulation 802.1Q pour autoriser le routage inter-VLAN sur un port physique unique.

## 📂 Organisation du Dépôt
Le dossier `configs/` contient les fichiers de configuration brute extraits des équipements :
- [Router.cfg](./configs/Router.cfg)
- [Switch1.cfg](./configs/Switch1.cfg)
- [Switch2.cfg](./configs/Switch2.cfg)

- [Schéma de la topologie](./router-on-a-stick-lab.png) 

## 🔍 Validation & Tests
- Vérification du bon état des liaisons trunk via `show interfaces trunk` sur les switchs.
- Validation de l'encapsulation et du routage par des tests de connectivité (`ping`) réussis entre des hôtes situés sur des VLANs distincts.

## 🔒 Vérification des VLANs & Sécurité d'accès

Le résultat de la commande `show vlan brief` met en évidence la politique de segmentation du réseau :
- **VLAN 10 (ADMIN) :** Uniquement accessible via le port `Fa0/1` du Switch1 (réservé à l'administration). Le Switch2 ne possède aucun port d'accès assigné à ce VLAN pour des raisons de cloisonnement.
- **VLAN 20 (PROD) :** Étendu sur les deux switchs (`Fa0/2` sur Switch1 et `Fa0/1` sur Switch2) pour les postes de production.

---
*Projet réalisé dans le cadre de ma montée en compétences et de ma préparation à la certification Cisco CCNA 200-301 (Orientation NetDevOps).*
