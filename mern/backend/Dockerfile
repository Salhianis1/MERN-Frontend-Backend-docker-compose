# ----------- Stage 1: Build the application -----------
FROM node:18.9.1 AS builder

WORKDIR /app

COPY package*.json ./
RUN npm ci --omit=dev

COPY . .

# Uncomment if you have a build step (e.g., React/TS)
# RUN npm run build

# ----------- Stage 2: Run the application -----------
FROM node:18.9.1-slim

WORKDIR /app

COPY --from=builder /app /app

EXPOSE 5050

CMD ["npm", "start"]
