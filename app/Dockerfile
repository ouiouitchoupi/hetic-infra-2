# Utilisez une image de base
FROM node:18

# Créez un répertoire de travail dans le conteneur
WORKDIR /app

# Copiez le package.json et installez les dépendances
COPY package*.json ./
RUN npm install

# Copiez le reste du code de l'application
COPY . .

# Exposez le port que votre application utilise
EXPOSE 3000

# Commande pour démarrer l'application
CMD ["npm", "start"]
