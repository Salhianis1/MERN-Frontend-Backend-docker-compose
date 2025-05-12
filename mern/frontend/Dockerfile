# ----------- Stage 1: Build the application -----------
FROM node:18.9.1 AS builder

WORKDIR /app

# Copy package files and install dependencies (including devDependencies)
COPY package*.json ./
RUN npm install  

# Copy the rest of the application code
COPY . .

# Build the application using Vite
RUN npm run build

# ----------- Stage 2: Serve the built app -----------
FROM node:18.9.1-slim

WORKDIR /app

# Copy the build output from the builder stage
COPY --from=builder /app/dist ./dist

# Expose the port the app runs on
EXPOSE 5173

# Use serve to serve the built app
CMD ["npx", "serve", "-s", "dist", "-l", "5173"]
