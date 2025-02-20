FROM node:18 AS builder
WORKDIR /app
COPY package.json package-lock.json ./
RUN npm ci --only=production  # Remplace `npm install` pour éviter les conflits
COPY . .
RUN npx prisma generate

FROM node:18 AS production
WORKDIR /app
COPY --from=builder /app /app
EXPOSE 3000
CMD ["npm", "start"]
