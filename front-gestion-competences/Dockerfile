# Utiliser une image de base Node.js pour construire l'application Angular
FROM node:20 AS build

# Définir le répertoire de travail
WORKDIR /app

# Copier le fichier package.json et package-lock.json
COPY package*.json ./

# Installer les dépendances
RUN npm install

# Copier tout le code source dans le répertoire de travail
COPY . .

# Construire l'application Angular pour la production
RUN npm run build -- --prod

# Utiliser une image de base Nginx pour servir l'application Angular
FROM nginx:alpine

# Copier les fichiers de build Angular vers le répertoire de Nginx
COPY --from=build /app/dist/gestion-competences /usr/share/nginx/html

# Exposer le port 80
EXPOSE 80

# Démarrer Nginx
CMD ["nginx", "-g", "daemon off;"]md

