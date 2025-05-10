# Use the official image as a parent image
# Description: Dockerfile for the client side of the MERN stack application

# Use the official image as a parent image
FROM node:latest

# Set the working directory
WORKDIR /app

# Copy the file from your host to your current location
COPY package.json .

# Run the command inside your image filesystem
# Optional: change registry or extend timeout
RUN npm config set registry https://registry.npmmirror.com
RUN npm config set fetch-retry-maxtimeout 60000

RUN npm install --no-cache

# Inform Docker that the container is listening on the specified port at runtime
EXPOSE 5173

# Copy the rest of your app's source code from your host to your image filesystem
COPY . .

# Run the specified command within the container
CMD ["npm", "run", "dev"]
