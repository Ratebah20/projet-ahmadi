# Utiliser l'image Nginx officielle comme base
FROM nginx:stable-alpine-slim

# Copier les fichiers HTML, CSS, JS depuis le répertoire html-tp vers le répertoire par défaut d'Nginx
COPY ../html /usr/share/nginx/html

# Copier le fichier de configuration Nginx pour ce service
COPY ./nginx/appseed-app.conf /etc/nginx/conf.d/default.conf

# Exposer le port 8080
EXPOSE 8080
