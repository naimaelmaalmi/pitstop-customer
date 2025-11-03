# ==========================================================
# ÉTAPE 1: ÉTAPE DE BUILD (Construction de l'application)
# Utilise une image de développement plus complète pour npm install
# ==========================================================
FROM node:18-alpine AS builder

# Définir le répertoire de travail
WORKDIR /app

# Copier les fichiers de dépendances uniquement
COPY package.json package-lock.json ./

# Installer les dépendances
# Le flag --production permet de n'installer que les dépendances nécessaires à l'exécution
RUN npm install --production

# Copier le reste du code source
COPY . .

# ==========================================================
# ÉTAPE 2: ÉTAPE DE PRODUCTION (Image finale, légère et sécurisée)
# Utilise une image d'exécution Node.js beaucoup plus petite (alpine)
# ==========================================================
FROM node:18-alpine

# Définir le répertoire de travail final
WORKDIR /app

# Copier les fichiers construits et les dépendances du stage 'builder'
COPY --from=builder /app ./

# Définir le port d'exécution (doit correspondre au port de l'application)
# (Par défaut, 3001 pour le customer service d'après votre TP)
EXPOSE 3001

# Commande de démarrage de l'application
CMD ["npm", "start"]