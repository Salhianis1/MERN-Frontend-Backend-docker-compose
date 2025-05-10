FROM node:latest

WORKDIR /app

COPY package.json .

# Optional: change registry or extend timeout
RUN npm config set registry https://registry.npmmirror.com
RUN npm config set fetch-retry-maxtimeout 60000

RUN npm install --no-cache

COPY . .

EXPOSE 5050

CMD ["npm", "start"]

