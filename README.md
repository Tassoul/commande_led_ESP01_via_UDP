Système de Contrôle IoT via UDP Asynchrone (ESP-01S)
Auteur : KIANPI TASSOULA MAXIME OSIAS

Institution : École Nationale Supérieure Polytechnique de Douala (5ème Année)

Version : 1.0 (Release Finale)

Ce projet est une introduction pratique aux concepts de l'Internet des Objets (IoT). Il permet de transformer un module ESP-01S en un nœud réactif capable de piloter une LED à distance via le protocole UDP.

1. Présentation du Projet
Ce système permet d'établir une communication sans fil entre un smartphone et un microcontrôleur. Contrairement aux méthodes classiques, nous utilisons ici l'asynchronisme, ce qui signifie que le module reste toujours disponible pour recevoir des ordres sans jamais bloquer son programme principal.

Points clés techniques :
Communication bidirectionnelle : L'ESP reçoit des ordres et renvoie une confirmation (Feedback) au smartphone.

Routage Explicite : Utilisation de writeTo() pour garantir que la réponse arrive sur le bon port du terminal mobile.

Signal de vie (Beacon) : Le module signale sa présence sur le réseau toutes les 10 secondes.

2. Matériel Requis
Module ESP-01 ou ESP-01S.

Adaptateur USB-Série (FTDI/CH340) avec switch UART/Prog.

PC avec VS Code et l'extension PlatformIO.

Smartphone avec une application de terminal UDP (ex: UDP TCP Server).

3. Guide de Déploiement (Étape par étape)
Étape A : Préparation du code
Ouvrez le projet sous PlatformIO.

Dans src/main.cpp, configurez vos identifiants Wi-Fi :

C++
const char * ssid = "votre_nom_wifi";
const char * password = "votre_mot_de_passe";
Étape B : Téléversement (Upload)
Placez votre adaptateur USB sur le mode Flash/Prog.

Branchez-le et cliquez sur le bouton Upload de PlatformIO.

Étape C : Mise en service
Débranchez l'adaptateur, basculez le switch sur UART (mode exécution) et rebranchez-le.

Ouvrez le Serial Monitor de PlatformIO à 115200 bauds.

Relevez l'adresse IP qui s'affiche après la connexion (ex: 10.53.242.234).

4. Utilisation du Terminal UDP
Connectez votre téléphone au même réseau Wi-Fi que l'ESP-01.

Ouvrez votre application UDP et configurez :

IP Cible : L'adresse IP relevée au point précédent.

Port : 1234.

Envoyez les commandes :

Tapez ON : La LED intégrée s'allume et vous recevez ACTION ALLUMAGE VALIDEE.

Tapez OFF : La LED s'éteint et vous recevez ACTION EXTINCTION VALIDEE.

5. Licence & Sécurité
Ce projet est distribué sous la Licence MIT. Note de sécurité : Ce système est une preuve de concept éducative. Pour une utilisation industrielle ou domotique réelle, l'ajout d'un cryptage et d'un mot de passe de commande est fortement recommandé pour protéger l'accès à votre réseau.
