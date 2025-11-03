#----------------------------------------------------------------------

#ÉTAPE 1: BUILD STAGE

#----------------------------------------------------------------------

FROM node:18-alpine AS builder
WORKDIR /app/client
COPY package.json package-lock.json ./
RUN npm install
COPY . .

#----------------------------------------------------------------------

#ÉTAPE 2: PRODUCTION STAGE (Léger et exécute 'npm run serve')

#----------------------------------------------------------------------

FROM node:18-alpine
WORKDIR /app/client
COPY --from=builder /app/client ./
EXPOSE 8061
CMD ["npm", "run", "serve"]