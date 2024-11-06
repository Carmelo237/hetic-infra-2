# Utiliser une image Node.js officielle, ici en version alpine
FROM node:14-alpine

# Définir répertoire de travail
WORKDIR /app

# Copier les fichiers du répertoire actuel vers le conteneur
COPY . /app

# Installer les dépendances définies dans package.json
RUN npm install --no-cache

# Lancer l'application (remplacez 'app.js' par votre fichier principal si différent)
CMD ["node", "app.js"]
