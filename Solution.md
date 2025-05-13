### Prérequis
#### 1 VM Windows Server 2022 
=> Carte Reseau interne
=> IP fixe : 10.10.5.10/24
=> Role AD DS installé 
=> Nom AD : corp.entreprise

#### 1 Client Windows 10
=> Carte Reseau interne 
=> IP fixe : 10.10.5.15/24
=> Fait partie de l'AD corp.entreprise

### Configuration Serveur
=> Ajouter role **Services de fichiers et de stockage" > "Serveur de fichiers"**
=> Créer Dossier **"Documents_Entreprise"** à la racine du disque C:
=> Créer 3 sous dossier dans Documents_Entreprise : 
- Direction
- Comptabilité
- RH
=> Ouvrir **Active Directory User ans Computeur**
