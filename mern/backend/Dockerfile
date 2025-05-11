# ----------- Stage 1: Build the application -----------
FROM node AS builder

WORKDIR /app

# Copy package.json and install dependencies
COPY package.json .
RUN npm install

# Copy the rest of the application code
COPY . .

# Optional: run build step if your app has one (e.g., for TypeScript, React SSR, etc.)
# Uncomment the following line if applicable
# RUN npm run build

# ----------- Stage 2: Run the application -----------
FROM node

WORKDIR /app

# Copy only necessary files from the builder
COPY --from=builder /app /app

# Expose the port
EXPOSE 5050

# Start the application
CMD ["npm", "start"]
