### Prérequis
#### 1 VM Windows Server 2022 
=> Carte Reseau interne
=> IP fixe : 10.10.5.10/24
=> Role AD DS installé 
=> Nom AD : corp.entreprise
=> Ajouter role **Services de fichiers et de stockage" > "Serveur de fichiers"**

#### 1 Client Windows 10
=> Carte Reseau interne 
=> IP fixe : 10.10.5.15/24
=> Fait partie de l'AD corp.entreprise

### Configuration Serveur AD 
=> Ouvrir **Active Directory User ans Computeur**
=> Créer 3 OU : Direction, Comptabilité et RH
=> Créer 3 groupe : Direction, Comptabilité et RH
=> Créer 3 utilisateur : Client1, Client2, Client3
=> Dans OU Direction mettre :
- Groupe Direction
- Client1
=> Dans OU Comptabilité mettre :
- Groupe Comptabilité
- Client2
=> Dans OU RH mettre :
- Groupe RH
- Client3

### Configuratuin Serveur partage fichier 
=> Créer Dossier **"Documents_Entreprise"** à la racine du disque C:
=> Créer 3 sous dossier dans Documents_Entreprise : 
- Direction
- Comptabilité
- RH
=> Cliquer Sur **File and storage service** (dans le **Dashboard** de **Server Manager**)
=> clique gauche sur **Share**
=> Clique droit et sélectionne **New Share**
=> **Select Profile** -> **SMB Share - Quick**
=> **Share location** -> clique sur **Type a custom path** et renseigne le chemin absolu de ton dossier que tu veux partager (ici **C:\Documents_Entreprise**)
=> **Share name** -> ici nous allons mettre **Docs**
=> **Other setting** -> **Next**
=> **Permission** -> **Customize permissions...** -> **Share** -> **add** -> **everyone** -> **ok**
=> **Next**
=> **Create**

Maintenant nous avons un dossier visible par les utilisateur de l'AD.
Nous allons configurer les droits d'acces :

=> Ouvrir l'explorateur de fichier -> C:\Documents_Entreprise
=> Clique droit sur le dossier **Comptabilité** -> **Propertie** -> **Sharing** -> **Share** -> Dans la barre de recherche tape "Comptabilité" et "Direction" -> Modifier les droits en "Read/Write" -> **Share**
=> Clique droit sur le dossier **RH** -> **Propertie** -> **Sharing** -> **Share** -> Dans la barre de recherche tape "RH" et "Direction" -> Modifier les droits en "Read/Write" -> **Share**
=> Clique droit sur le dossier **Direction** -> **Propertie** -> **Sharing** -> **Share** -> Dans la barre de recherche tape "Direction" -> Modifier les droits en "Read/Write" -> **Share**

### Test avec les Clients
=> Sur une VM client connectez vous avec Client3 (pour rappel, cet utilisateur fait partie du groupe RH)
=> Dans explorateur de fichier clique sur **Réseau**
=> Renseigne le chemin du dossier partagé, ici **\\WinServ\Docs** (WinServ est ici le nom du serveur Windows)
=> Double clique 






