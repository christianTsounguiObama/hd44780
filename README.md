# Affichage de texte sur un écran LCD HD44780 1602 via protocole parallèle en C bas-niveau sur ATmega2560

Ce projet implémente, en langage C bare-metal, une interface directe entre un microcontrôleur ATmega2560 (Arduino Mega) et un capteur de température et d’humidité DHT11, sans utiliser de bibliothèques externes. Les données mesurées sont ensuite transmises via le protocole UART à un terminal série ou un autre périphérique. L’objectif est de comprendre le protocole de communication 1-Wire spécifique au DHT11, de le mettre en œuvre via des manipulations de registres, et de configurer l’UART pour envoyer les données en ASCII.

## Structure du projet
dht11_ws/ ├── include/ # Fichiers d'en-tête (headers)</br>
		  │ ├── hd44780.h </br>
		  │ └── gpio.h </br>
          ├── drivers/ # Fichiers source pour les pilotes bas-niveau </br>
          │ ├── hd44780/hd44780.c </br>
		  │ └── gpio/gpio.c</br>
		  ├── main/ # Logique principale de l’application </br>
          │ └── main.c </br>
		  ├── build/ # Fichiers compilés </br>
		  └── Makefile # Système de compilation </br>
    		  ├── Schemas/ # Schemas de connections </br>
		  │ └── HD44780_Schematics

## Fonctionnalités

- Initialisation manuelle de l’écran selon le protocole HD44780.
- Affichage de messages texte sur deux lignes.
- Implémentation de l’envoi de données/commandes via un bus parallèle 4 bits.
- Gestion de l'affichage ligne par ligne (avec saut automatique à la ligne 2 après 16 caractères).
- Codé entièrement sans bibliothèques Arduino.

## Prérequis

- **Matériel** : Arduino Mega 2560, Ecran LCD HD44780 16x2
- **Outils** :
  - `avr-gcc`
  - `avrdude`
- **Système** : Linux (testé sous Ubuntu 20.04+)

## Schema
![Schema](https://github.com/user-attachments/assets/6e28fa02-f21e-44d2-bc99-86c8fb1de44c)


## Démarrage rapide

### 1. Cloner le dépôt

```bash
git clone https://github.com/christianTsounguiObama/hd44780.git
cd hd44780/hd44780_ws
```
### 2. Flasher le fichier binaire
Assurez-vous que votre carte Arduino Mega2560 est connectée via USB et ajustez PORT dans le Makefile si nécessaire.
```bash
make
```

### 3. Lire les données sur le port série
Utilisez un outil comme screen :
```bash
screen /dev/ttyUSB0 9600
```

## Licence
Ce projet est open source et disponible sous la Licence Apache 2.0.

### Contribuer
Les contributions sont les bienvenues. Si vous trouvez des problèmes, n’hésitez pas à ouvrir une issue ou à proposer des améliorations.

### Remerciements
Ce projet fait partie de mon initiative pour te montrer comment construire des systèmes embarqués à partir de zéro au travers de projets 
dont le niveau de difficulté augmente progressivement.





