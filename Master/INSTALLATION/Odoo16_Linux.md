# Configuration de Odoo avec Pycharm
Dans ce tutoriel, nous allons configurer Odoo avec Pycharm. Pour cela, nous allons d'abord télecharger le code source de Odoo sur github. Ensuite telecharger Pycharm et enfin configurer Odoo pour pouvoir lancer notre serveur Odoo.

Vous avez la possibilité de télécharger le code source de Odoo sur github de deux manières.

### Avec l'interface graphique
1. Rendez-vous sur [le github d'odoo](https://github.com/odoo/odoo) pour le télechargement.
2. Télechager le code en appuyant sur `Code` puis sur `Download Zip` comme indiqué dans l'image ci-dessous. 

**NB**: N'oubliez pas de verifier la version souhaité (La version 16 dans notre exemple).  
![odoo_github.png](.Master/Odoo/Odoo-V16/Installations/Ressources/linux0.png)

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
[www.jetbrains.com](https://www.jetbrains.com/products/compare/?product=pycharm&product=pycharm-ce)  
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
![capture_d’écran_du_2023-04-14_13-11-42.png](.Master/Odoo/Odoo-V16/Installations/Ressources/linux1.png)  

3. Création d'un utilisateur  
Une fois postgres installés nous allons créer un utilisateur pour la base de donnée que nous allons créer.  

Connectez-vous à postgres:  
```
psql -U postgres
```  
Ensuite créez l'utilisateur odoo16 puis accordez lui les droits de créer des bases de données:  
```
CREATE ROLE odoo16;
ALTER ROLE odoo16 WITH LOGIN;
ALTER ROLE odoo16 WITH SUPERUSER;
ALTER ROLE odoo16 WITH CREATEDB;
```  

## Configuration de Odoo avec Pycharm  
Une fois Odoo et Pycharm téléchargés, nous pouvons passer à la configuration.  

### Créer un environnement virtuel  
1. Déplacez vous dans le repertoire Odoo télechargé ou cloné.  
```
cd ~/Bureau/Workspace/odoo
```  
2. Créer l'environnement virtuel.
```
python3 -m venv venv
```  
3. Activation de l'environnement  
```
source venv/bien/activate
```  

### Installer les dépendances  
Après avoir créé l'environnement virtuel puis activé celui-ci, nous allons installer les dépendances nécessaire au bon fonctionnement de notre programme.  
```
pip install -r requirements.txt
```  

### Passer à la configuration  
1. Ouvez Pycharm et chargez le code Odoo `File` -> `Open`.  
2. Créez un fichier `odoo.conf` à la racine du projet puis collez-y le contenu ci-dessous:  
```
[options]
; This is the password that allows database operations:
; admin_passwd = admin
addons_path = addons, odoo/addons
db_host = False
db_port = 5432
db_user = odoo16
db_password = False
http_port = 8069
```  
2. Ensuite cliquez sur `Edit configurations...` comme dans l'image suivante:  

![configop.png](.Master/Odoo/Odoo-V16/Installations/Ressources/linux2.png)  

3. Cliquez sur `Add new configuration` puis selectionnez `Python`.  
![Add new configuration](.Master/Odoo/Odoo-V16/Installations/Ressources/linux3.png)  

4. Dans le formulaire selectionnez le script en cliquant sur l'icone de dossier qui est dans le champ `Script path` et en selectionnant le fichier odoo-bin dans   notre répertoire odoo.  

![Script path](.Master/Odoo/Odoo-V16/Installations/Ressources/linux4.png)  

5. Assurez-vous d'avoir une configuration comme ceci et appuyez sur `OK`:  

![cliquer sur OK](.Master/Odoo/Odoo-V16/Installations/Ressources/linux5.png)  

6. Cliquez sur `Run`	 pour lancer odoo.  

![Run](.Master/Odoo/Odoo-V16/Installations/Ressources/linux6.png)  
# Fin du tutoriel  
Une fois notre serveur lancé, vous pouvez accéder à page de création de donnée via le lien suivant: http://localhost:8069 .  
Vous aurez ainsi la page suivante:  

![acceder à la page de création de donnée](.Master/Odoo/Odoo-V16/Installations/Ressources/linux7.png)  

Copiez le `master password` et sauvegardez le dans votre fichier odoo.conf comme ceci:  
`admin_passwd = 9scx-e5wa-ah8m`  
Assurez que la ligne ne soit pas en commentaire en verifiant que le `;` n'est pas au debut de la ligne.  
Remplissez le formulaire en reseignant les différents champs et cliquez sur `Create database`.  
Une fois la base de donnée créée connectez-vous en renseignants les champs `Email` et `Password` que vous avez indiqués lors de la création de la base de donnée   puis cliquez sur `Se connecter`.  

![Connectez-vous](.Master/Odoo/Odoo-V16/Installations/Ressources/linux8.png)  

Vous obtenez ainsi une interface semblable à celle de l'image ci-dessous.  

![Congratulation! vous êtes sur l'interface d'odoo](.Master/Odoo/Odoo-V16/Installations/Ressources/linux9.png)  
