# Étape 1 : Build de l'application Nuxt avec Node.js
FROM node:20-alpine3.18 as builder

WORKDIR /app/frontend

# Copier les fichiers package.json et installer les dépendances
COPY package*.json ./
RUN npm install

# Copier le reste du code de l'application
COPY . .

ENV ENVIRONMENT=production

# Construire les fichiers statiques pour la production
RUN npm run build

# Exposer le port 3000
EXPOSE 3000

# Commande pour démarrer l'application
CMD ["node", ".output/server/index.mjs"]
