# Projet Final Docker

Ce projet consiste à configurer et exécuter plusieurs services à l'aide de Docker, comprenant notamment un service HTML et des applications Django, avec une configuration optimisée pour un environnement léger.

## Étapes principales

### 1. Clonage des applications
ON Télécharge toutes les applications nécessaires via `git clone`.


### 2. Organisation des fichiers
- Placez un dossier `nginx` et un fichier `docker-compose.yml` dans la racine.
- Supprimez les autres dossiers inutiles.

### 3. Optimisation des Dockerfiles
- Utilisez une image légère (par exemple `python:3.10-alpine`) pour chaque application.
- Combinez les commandes dans les Dockerfiles avec `&&` pour limiter le nombre de couches.

### 4. Création du Dockerfile pour le service HTML
- Choisissez une image légère comme base pour le service HTML (par exemple, `nginx:stable-alpine-slim`).

### 5. Modification du fichier `docker-compose.yml`
- Ajoutez les services correspondants avec des images légères.

### 6. Ajustement des fichiers Gunicorn
- Modifiez le fichier `gunicorn-cfg.py` pour chaque application afin d'assurer une configuration adaptée.

### 7. Configuration de Nginx
- Modifiez le fichier `appseed-app.conf` pour inclure les services et le reverse proxy.

### 8. Build des services
Une fois toutes les configurations terminées, exécutez la commande suivante pour construire vos images et démarrer les conteneurs :

```bash
docker-compose up --build
```

## Services et URL

### Services accessibles
- **Service HTML** : [URL du service HTML]
- **Service 1 sans reverse proxy** : [URL du service]
- **Service 2** : [URL du service]
- **Service 3** : [URL du service]
- **Service 4** : [URL du service]
- **Service 5** : [URL du service]
- **Service 6** : [URL du service]

Avec le service HTML, cela fait un total de 7 services.

## Configuration GitHub

### Initialisation du dépôt
1. Initialisez un nouveau dépôt Git avec :
   ```bash
   git init
   ```
2. Ajoutez l'URL de votre dépôt GitHub :
   ```bash
   git remote add origin git@github.com:Ratebah20/projet-ahmadi.git
   ```

### Configuration SSH
1. Créez une clé SSH :
   ```bash
   ssh-keygen -t rsa -b 4096 -C "ratib132@gmail.com"
   ```
2. Ajoutez la clé à l'agent SSH :
   ```bash
   ssh-add ~/.ssh/id_rsa
   ```
3. Affichez la clé publique pour l'ajouter à GitHub :
   ```bash
   cat ~/.ssh/id_rsa.pub
   ```
4. Une fois la clé ajoutée sur GitHub, vérifiez la connexion :
   ```bash
   ssh -T git@github.com
   ```

### Push des fichiers
1. Ajoutez les fichiers au dépôt :
   ```bash
   git add .
   ```
2. Faites un commit :
   ```bash
   git commit -m "Premier commit - ajout des fichiers"
   ```
3. Poussez les fichiers vers GitHub :
   ```bash
   git push -u origin master
   ```

### Problèmes rencontrés
- **Dossiers vides après le push** : Certains répertoires comme `django-coreui` contenaient déjà leur propre dépôt Git.
- **Solution** :
  - Supprimez les répertoires imbriqués avec :
    ```bash
    rm -rf <dossier>/.git
    ```
  - Ajoutez à nouveau les fichiers et forcez la détection des modifications :
    ```bash
    git add .
    git commit -m "Réinitialisation de l'index Git"
    git push origin master
    ```

## Étapes finales
Votre projet est maintenant configuré avec succès, et les services sont opérationnels. Vous pouvez vérifier leur état en accédant aux URL correspondantes dans un navigateur.
