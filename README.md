# Projet Final Docker

Ce projet consiste à configurer et exécuter plusieurs services à l'aide de Docker, comprenant notamment un service HTML et des applications Django, avec une configuration optimisée pour un environnement léger.

## Étapes principales

### 1. Clonage des applications
ON Télécharge toutes les applications nécessaires via `git clone`.

![image](https://github.com/user-attachments/assets/7440c7d7-e8ba-473d-92f5-315de9412f98)

## Une fois les tous les application cloner
![image](https://github.com/user-attachments/assets/ee2e2dc0-8983-403b-8e4a-b99f78824e4f)


### 2. Organisation des fichiers
- ON Place un dossier `nginx` et un fichier `docker-compose.yml` dans la racine.
- On Supprime les autres dossiers inutiles.


  ![image](https://github.com/user-attachments/assets/49d36cc1-fd40-4806-a6af-43bae0a0be6b)


### 3. Optimisation des Dockerfiles
- On Utilise une image légère (par exemple `python:3.10-alpine`) pour chaque application.
- On Combine les commandes dans les Dockerfiles avec `&&` pour limiter le nombre de couches.


  ![image](https://github.com/user-attachments/assets/3af90c59-c5f3-45f9-8413-b69b296a84c5)


### 4. Création du Dockerfile pour le service HTML
- On choisisse une image légère comme base pour le service HTML (par exemple, `nginx:stable-alpine-slim`).


![image](https://github.com/user-attachments/assets/062c9098-26e3-49f8-aa1b-0e72c3184166)


### 5. Modification du fichier `docker-compose.yml`
- On ajoute les services correspondants avec l'images légères.

![image](https://github.com/user-attachments/assets/4f302083-9adf-4c67-8896-e4fe77b5c888)

![image](https://github.com/user-attachments/assets/2479b87c-0187-4afc-a673-f6f1c174943b)


  

### 6. Ajustement des fichiers Gunicorn
- On modifie le fichier `gunicorn-cfg.py` pour chaque application afin d'assurer une configuration adaptée.


![image](https://github.com/user-attachments/assets/d095f7c1-978c-4e07-bc65-59535f59f209)

  

### 7. Configuration de Nginx
- On Modifie le fichier `appseed-app.conf` pour inclure les services et le reverse proxy.


  ![image](https://github.com/user-attachments/assets/98be22d3-dba9-4767-9ae7-be630b778d13)


### 8. Build des services
Une fois toutes les configurations terminées, On exécute la commande suivante pour construire  l'images et démarrer les conteneurs :

```bash
docker-compose up --build
```

![image](https://github.com/user-attachments/assets/b778d335-7517-4c6e-ae2e-8b622116ff1e)

## Mes services marche correctement
![image](https://github.com/user-attachments/assets/8768cad3-a259-4e1d-977e-26ce1c0c8ceb)


## Services et URL

### Services accessibles
- **Service HTML** : ![image](https://github.com/user-attachments/assets/98a6a954-82ac-416c-9bef-a105d6794a87)

- **Service 1 sans reverse proxy** : ![image](https://github.com/user-attachments/assets/b76211fa-53ff-4fea-8e95-f472b28ae1fe)

- **Service 2** : ![image](https://github.com/user-attachments/assets/001fff44-27f3-4e30-b9df-822cb801afd9)

- **Service 3** : ![image](https://github.com/user-attachments/assets/ca8cf7d6-1b41-4dba-a7fd-d1723aaae4cd)

- **Service 4** : ![image](https://github.com/user-attachments/assets/8c0bd7de-c745-4de2-9b91-1e4f0c6283fd)

- **Service 5** : ![image](https://github.com/user-attachments/assets/2ea36972-c6cd-4e09-b4e9-181465f2cc46)

- **Service 6** : ![image](https://github.com/user-attachments/assets/960ef831-3588-44fa-b3e6-54729f9c5afd)

Avec le service HTML, cela fait un total de 7 services.

## Configuration GitHub

![image](https://github.com/user-attachments/assets/40fd18ae-13d6-4a81-bdf2-c60d1d45e606)


### Initialisation du dépôt
1. Initialise un nouveau dépôt Git avec :
   ```bash
   git init
   ```
2. Ajoute l'URL de votre dépôt GitHub :
   ```bash
   git remote add origin git@github.com:Ratebah20/projet-ahmadi.git
   ```

### Configuration SSH
1. Crée une clé SSH :
   ```bash
   ssh-keygen -t rsa -b 4096 -C "ratib132@gmail.com"
   ```
on peut voir que la clé a été créer : 

![image](https://github.com/user-attachments/assets/a3dc7937-ef4d-43c2-891f-351cf9a31307)

   
2. Ajoute de la clé à l'agent SSH :
   ```bash
   ssh-add ~/.ssh/id_rsa
   ```
   

   
3. Affichez la clé publique pour l'ajouter à GitHub :
   ```bash
   cat ~/.ssh/id_rsa.pub
   ```

   ![image](https://github.com/user-attachments/assets/aebe8e11-472b-4eb7-8826-d168b0c80ee1)

4. Une fois la clé ajoutée sur GitHub, on vérifie la connexion :
   ```bash
   ssh -T git@github.com
   ```

![image](https://github.com/user-attachments/assets/a5b7d8e1-63d2-46bd-acf1-c5d96af4b4a5)

![image](https://github.com/user-attachments/assets/651e7e43-ebc1-4ed0-b6c5-6f665d8c83ef)


### Push des fichiers
1. ON ajoute les fichiers au dépôt :
   ```bash
   git add .
   ```
2. on Faite un commit :
   ```bash
   git commit -m "Premier commit - ajout des fichiers"
   ```
3. On pousse les fichiers vers GitHub :
   ```bash
   git push -u origin master
   ```

### Problèmes rencontrés
- **Dossiers vides après le push** : Certains répertoires comme `django-coreui` contenaient déjà leur propre dépôt Git.
- **Solution** :
  - Supprimez les répertoires imbriqués avec :
    ```bash
    rm -rf django-coreuil/.git
    ```

    ![image](https://github.com/user-attachments/assets/b91e4701-2a02-41d6-b5b1-0f330c8c98af)

  - Ajoute des nouveaux fichiers et on force la détection des modifications :
    ```bash
    git add .
    git commit -m "Réinitialisation de l'index Git"
    git push origin master
    ```


    ![image](https://github.com/user-attachments/assets/d2014d84-8c03-4d2a-b312-8813d3d655f5)


## Étapes finales
Mon projet est maintenant configuré avec succès, et les services sont opérationnels.


![image](https://github.com/user-attachments/assets/045cc9a1-5775-427b-a0b0-3c3f7739f9f6)

