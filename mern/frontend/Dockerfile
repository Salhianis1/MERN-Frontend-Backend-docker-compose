FROM node:18.9.1-slim AS builder


RUN apt-get update && apt-get install -y \
     python3 make g++ \
  && rm -rf /var/lib/apt/lists/*


WORKDIR /app


COPY package*.json ./

RUN npm ci --force


COPY . .
RUN npm run build


FROM nginx:alpine


RUN rm -rf /usr/share/nginx/html/*


COPY --from=builder /app/dist /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
