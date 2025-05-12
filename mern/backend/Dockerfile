# ----------- Stage 1: Build the application -----------
FROM node:21 AS backend-builder

WORKDIR /app

COPY package*.json ./

COPY . .

# Uncomment if you have a build step (e.g., React/TS)
# RUN npm run build

# ----------- Stage 2: Run the application -----------
FROM node:21-slim
WORKDIR /app

COPY --from=backend-builder /app /app

EXPOSE 5050

CMD ["npm", "start"]
