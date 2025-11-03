#----------------------------------------------------------------------

#ÉTAPE 1: BUILD STAGE

#----------------------------------------------------------------------

FROM node:18-alpine AS builder
WORKDIR /app/workshop-planning
COPY package.json package-lock.json ./
RUN npm install --production
COPY . .

#----------------------------------------------------------------------

#ÉTAPE 2: PRODUCTION STAGE

#----------------------------------------------------------------------

FROM node:18-alpine
WORKDIR /app/workshop-planning
COPY --from=builder /app/workshop-planning ./
EXPOSE 3003
CMD ["npm", "start"]