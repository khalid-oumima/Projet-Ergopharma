Projet Ergopharma : Infrastructure Réseau Multisite & Haute Disponibilité
📝 Présentation du Projet

Ce projet, réalisé dans le cadre du cursus ingénieur à l'ESEO (2024-2025), consiste en la conception intégrale d'une infrastructure réseau pour l'entreprise pharmaceutique Ergopharma.

L'objectif était de répondre à un déménagement global en créant une architecture segmentée, sécurisée et hautement disponible répartie sur quatre bâtiments distincts:

    Bâtiment A : Administration et Salle Serveur (Cœur de réseau).

    Bâtiment B : Recherche & Développement (400+ collaborateurs).

    Bâtiment C : Commercial, SAV et WiFi.

    Bâtiment D : Production et Automates industriels.

🛠️ Architecture Technique

L'infrastructure repose sur le modèle hiérarchique à trois couches de Cisco (Cœur, Distribution, Accès).
Points clés de la configuration :

    Haute Disponibilité : Doublement des commutateurs de cœur (3560 Layer 3) pour éliminer tout point unique de défaillance (SPOF).

    Redondance & Performance :

        Mise en œuvre de l'EtherChannel (LACP/PAgP) entre les switchs de cœur pour doubler la bande passante.

        Activation du protocole STP (802.1D) pour la gestion des boucles et la tolérance aux pannes.

    Segmentation (VLANs) : Isolation stricte des services (Secrétariat, R&D, Automates, WiFi) via plus de 10 VLANs dédiés.

    Services Centralisés : Configuration d'un serveur unique pour le DHCP Relay, le DNS et l'application ERP.

🔢 Plan d'Adressage (VLSM)

L'adressage a été optimisé à partir du réseau source 121.53.0.0/16 pour minimiser le gaspillage d'adresses.
Bâtiment	Service	VLAN	Plage d'adresses utiles	Passerelle
A	Serveurs	13	121.53.2.65−121.53.2.126	

121.53.2.126 
B	R&D	20	121.53.0.1−121.53.1.254	

121.53.1.254 
C	WiFi	50	121.53.5.1−121.53.5.30	

121.53.5.30 
D	Automates	42	121.53.4.49−121.53.4.62	

121.53.4.62 
🚀 Tests et Validation

La solution a été validée sous Cisco Packet Tracer via :

    Tests de connectivité : Succès des commandes ping et tracert entre tous les VLANs via le routage inter-VLAN.

    Attribution Dynamique : Vérification de la réception correcte des baux DHCP pour les postes clients et le WiFi.

    Simulation de panne : Coupure de liens physiques pour confirmer la bascule automatique du trafic via STP.

📂 Contenu du dépôt

    Projet_Ergopharma.pkt : Fichier source Cisco Packet Tracer.

    /Configurations : Exports texte des configurations running-config des équipements clés.

    /Screenshots : Captures de la topologie logique et des tests de connectivité.
