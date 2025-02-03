***Configurer un environnement réseau virtuel à l'aide de deux machines virtuelles Debian, en mettant en place un serveur DHCP et DNS sur la première machine, ainsi qu'un serveur-client FTP avec SSH sur la seconde machine.***

***
# INSTALLATION & CONFIGURATION DU SERVEUR DHCP
*Ce projet consiste en l'installation d'un serveur DHCP sur une première machine Linux (Debian sans interface graphique), de sorte qu'il puisse attribuer des adresses de catégorie B aux machines connectées au réseau.*

## Services configurés
- Serveur DHCP



##  Tests de connexion
Les tests de connexion ont été effectués avec FileZilla et la ligne de commande. Toutes les erreurs rencontrées ont été documentées et résolues.

## Mesures de sécurité
- Restriction de l'accès
- Modification du port SSH par défaut
- Blocage des connexions non authentifiées

Pour plus de détails, consultez les fichiers dans le dossier `ConfigurationFiles` et le document `SecurityMeasures.md`.

***
# INSTALLATION & CONFIGURATION DU SERVEUR FTP et SSH
*Ce projet consiste à configurer un serveur FTP (proFTPd) et SSH sur une machine Linux. Les services ont été configurés pour garantir un transfert de fichiers sécurisé et une gestion des accès restreinte.*

## Services configurés
- Serveur DNS

##  Tests de connexion
Les tests de connexion ont été effectués avec FileZilla et la ligne de commande. Toutes les erreurs rencontrées ont été documentées et résolues.

## Mesures de sécurité
- Restriction de l'accès
- Modification du port SSH par défaut
- Blocage des connexions non authentifiées

## Points clés FTP

- Installer proFTPD : `sudo apt install proftpd -y`

- Démarrer le service proftpd : `sudo systemctl start proftpd`

- Afficher les informations sur l'état du service (service en cours d'exécution, erreurs...) :  `sudo systemctl status proftpd` 

- Installer UFW :  `sudo apt-get install ufw`
- S'assurer que le client peut se connecter sur le port 21 : `sudo ufw allow 21/tcp`

- Créer le profil "laplateforme" : `sudo adduser laplateforme`

- Vérifier l'existence du profil crée : `su - laplateforme`


**Modification du fichier /etc/proftpd**

Rentrer nombre de clients max :
	-> MaxInstances 1
	-> MaxClientsPerHost 1

- Vérifier la bonne configuration du fichier (ex. Vérifier la présence de fautes de frappe) : `sudo proftpd -t` 

## Points clés SSH
- Installation d'OpenSSH : `sudo apt install openssh-server`
- Configuration dans /etc/ssh/sshd_config :

![Pasted image 20250130180127](https://github.com/user-attachments/assets/5290ba4e-f00a-494b-a24e-196c12ea9baa)

- Redémarrage du service : `sudo systemctl restart ssh`
***

# INSTALLATION & CONFIGURATION DU SERVEUR DNS
## Configuration du service DNS
Ce projet consiste à configurer un serveur FTP (proFTPd) et SSH sur une machine Linux. Les services ont été configurés pour garantir un transfert de fichiers sécurisé et une gestion des accès restreinte.
Ce projet consiste à installer un serveur DNS sur la première machine virtuelle (Debian sans interface graphique) et configurer le DNS de telle sorte que le lien soit "dns.ftp.com", pointant vers l'adresse IP de la deuxième machine où le serveur FTP est installé.


Points clés :
- Installation de BIND9 : sudo apt install bind9 -y

- Configuration des zones DNS dans : /etc/bind/zones/db.ftp.com

- Configuration des options DNS dans : /etc/bind/named.conf.options

- Redémarrage du service : sudo systemctl restart bind9

## Services configurés
- Serveur FTP (proFTPd)
- Serveur SSH (avec SFTP)

##  Tests de connexion
Les tests de connexion ont été effectués avec FileZilla et la ligne de commande. Toutes les erreurs rencontrées ont été documentées et résolues.

## Mesures de sécurité
- Restriction de l'accès
- Modification du port SSH par défaut
- Blocage des connexions non authentifiées

Pour plus de détails, consultez les fichiers dans le dossier `ConfigurationFiles` et le document `SecurityMeasures.md`.
installation d'OpenSSH :sudo apt install openssh-server

- Configuration dans /etc/ssh/sshd_config:

- Restrictions des utilisateurs : AllowUsers laplateforme

- Changement du port SSH : Port 6500

- Interdiction des connexions racine : PermitRootLogin no

- Redémarrage du service : sudo systemctl restart ssh


***

# TEST DE CONNEXION AU SERVEUR SFTP
## Configuration des services FTP et SSH
Ce projet consiste à configurer un serveur FTP (proFTPd) et SSH sur une machine Linux. Les services ont été configurés pour garantir un transfert de fichiers sécurisé et une gestion des accès restreinte.

## Services configurés
- Serveur FTP (proFTPd)
- Serveur SSH (avec SFTP)

##  Tests de connexion
Les tests de connexion ont été effectués avec FileZilla et la ligne de commande. Toutes les erreurs rencontrées ont été documentées et résolues.

## Mesures de sécurité
- Restriction de l'accès
- Modification du port SSH par défaut
- Blocage des connexions non authentifiées

Pour plus de détails, consultez les fichiers dans le dossier `ConfigurationFiles` et le document `SecurityMeasures.md`.
***

# PARAMETRES DE SECURITE ADDITIONNELS
## Configuration des services FTP et SSH
Ce projet consiste à configurer un serveur FTP (proFTPd) et SSH sur une machine Linux. Les services ont été configurés pour garantir un transfert de fichiers sécurisé et une gestion des accès restreinte.

## Services configurés
- Serveur FTP (proFTPd)
- Serveur SSH (avec SFTP)

##  Tests de connexion
Les tests de connexion ont été effectués avec FileZilla et la ligne de commande. Toutes les erreurs rencontrées ont été documentées et résolues.

## Mesures de sécurité
- Restriction de l'accès
- Modification du port SSH par défaut
- Blocage des connexions non authentifiées

Pour plus de détails, consultez les fichiers dans le dossier `ConfigurationFiles` et le document `SecurityMeasures.md`.
