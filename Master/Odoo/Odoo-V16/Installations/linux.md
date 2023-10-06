# Configuration de Odoo avec Pycharm
Dans ce tutoriel, nous allons configurer Odoo avec Pycharm. Pour cela, nous allons d'abord télecharger le code source de Odoo sur github. Ensuite telecharger Pycharm et enfin configurer Odoo pour pouvoir lancer notre serveur Odoo.

Vous avez la possibilité de télécharger le code source de Odoo sur github de deux manières.

### Avec l'interface graphique
1. Rendez-vous sur [https://github.com/odoo/odoo](https://github.com/odoo/odoo) pour le télechargement.
2. Télechager le code en appuyant sur `Code` puis sur `Download Zip` comme indiqué dans l'image ci-dessous. 

**NB**: N'oubliez pas de verifier la version souhaité (La version 16 dans notre exemple).  
![odoo_github.png](./linux0.png)

### Avec le terminal    
1. Ouvrez votre terminal en cherchant dans la liste des applications ou en tapant `Ctrl + Alt + T`.    
2. Deplacer vous dans votre répertoire de travail avec la commande suivante (On considère ici que votre répertoire de travail se trouve sur votre bureau):    
```
cd ~/Bureau/Workspace
```  
### Avec le terminal  
1. Ouvrez votre terminal en cherchant dans la liste des applications ou en tapant `Ctrl + Alt + T`.  
2. Deplacer vous dans votre répertoire de travail avec la commande suivante (On considère ici que votre répertoire de travail se trouve sur votre bureau):  
```
cd ~/Bureau/Workspace
```  
3. Clonez le repository depuis git en spécifiant la branche de la version souhaitée.  
```
git clone https://github.com/odoo/odoo.git --branch 16.0
```  

## Telechargement de Pycharm community  
Ouvrez Ubuntu software puis cherchez et telechargez Pycharm community.  
Si vous ne le trouvez pas dans Ubuntu Software, allez-y sur le site officiel afin de télécharger la version commnunity. Le lien du site est:   
[https://www.jetbrains.com/products/compare/?product=pycharm&product=pycharm-ce](https://www.jetbrains.com/products/compare/?product=pycharm&product=pycharm-ce)  
# Installation de PostgreSQL  

1. Ajout du referentiel officiel  
Tout d'abord, vous devez installer les packages logiciels prérequis qui seront utilisés pour télécharger et installer des certificats logiciels pour une connexion   SSL sécurisée.  
```
sudo apt install wget ca-certificates
```  

Récupérez ensuite le certificat, ajoutez-le à l'utilitaire de gestion apt-key et créez un nouveau fichier de configuration avec une adresse de référentiel   PostgreSQL officielle à l'intérieur.  
```
wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -
```  

Enfin, faite une mise à jour des referentiels:  
```
sudo apt update
```  

2. Installation  
Il est maintenant temps de procéder à l'installation proprement dite de PostgreSQL. Cela installera la dernière version de PostgreSQL ainsi que les dernières   extensions et ajouts.  
```
sudo apt install postgresql postgresql-contrib
```  

Après l'installation, vous pouvez revérifier que le démon postgresql est actif.  
```
service postgresql status
```  

Vous deriez obtenir une sortie de ce genre:  
![capture_d’écran_du_2023-04-14_13-11-42.png](./.png)  

3. Création d'un utilisateur  
Une fois postgres installés nous allons créer un utilisateur pour la base de donnée que nous allons créer.  

Connectez-vous à postgres:  
