# Stage 1: Builder
FROM mcr.microsoft.com/mirror/docker/library/node:18-alpine AS builder
WORKDIR /app
COPY package*.json ./
RUN npm ci --only=production
COPY . .

# Stage 2: Production
FROM mcr.microsoft.com/mirror/docker/library/node:18-alpine
WORKDIR /app
COPY --from=builder /app .
EXPOSE 5000
CMD ["node", "index.js"]