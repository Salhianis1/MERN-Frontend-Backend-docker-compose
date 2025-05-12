# ----------- Stage 1: Build the application -----------
FROM node:18.9.1 AS builder

WORKDIR /app

COPY package*.json ./
RUN npm ci  # <-- include dev dependencies here

COPY . .
RUN npm run build

# ----------- Stage 2: Serve the built app -----------
FROM node:18.9.1-slim

WORKDIR /app

COPY --from=builder /app/dist ./dist

EXPOSE 5173
CMD ["npx", "serve", "-s", "dist", "-l", "5173"]
