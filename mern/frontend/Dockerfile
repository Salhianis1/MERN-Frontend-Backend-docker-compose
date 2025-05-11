# ----------- Stage 1: Build the application -----------
FROM node AS builder

# Set the working directory
WORKDIR /app

# Copy only the package.json to install dependencies
COPY package.json .

# Install dependencies
RUN npm install

# Copy the rest of the application code
COPY . .

# Build the application (assuming it's a Vite/React app or similar)
RUN npm run build

# ----------- Stage 2: Serve the built app -----------
FROM node

# Set the working directory
WORKDIR /app

# Copy only the production build from the builder stage
COPY --from=builder /app/dist ./dist

# Optionally install a lightweight server (e.g., serve)
RUN npm install -g serve

# Expose the port your app will run on
EXPOSE 5173

# Command to serve the built app
CMD ["serve", "-s", "dist", "-l", "5173"]
