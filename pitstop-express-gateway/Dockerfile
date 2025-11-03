FROM node:18-alpine AS builder

#Définir le répertoire de travail

WORKDIR /app/gateway

#Copier les fichiers de dépendances uniquement

COPY package.json package-lock.json ./

#Installer les dépendances

RUN npm install --production

#Copier le reste du code source

COPY . .

#==========================================================

#ÉTAPE 2: ÉTAPE DE PRODUCTION (Image finale, légère et sécurisée)

#==========================================================

FROM node:18-alpine

#Définir le répertoire de travail final

WORKDIR /app/gateway

#Copier les fichiers construits et les dépendances du stage 'builder'

COPY --from=builder /app/gateway ./

#Définir le port d'exécution (Port 8080 pour l'API Gateway)

EXPOSE 8080

#Commande de démarrage de l'application

CMD ["npm", "start"]