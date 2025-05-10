# A simple MERN stack application 

### Create a network for the docker containers

`sudo docker network create demo`

### Build the client 

```sh
cd mern/frontend
sudo docker build -t mern-frontend .
```

### Run the client

`sudo docker run --name=frontend --network=demo -d -p 5173:5173 mern-frontend`

### Verify the client is running

Open your browser and type `http://localhost:5173`

### Run the mongodb container

`sudo docker run --network=demo --name mongodb -d -p 27017:27017 -v ~/opt/data:/data/db mongo:latest`

### Build the server

```sh
cd mern/backend
sudo docker build -t mern-backend .
```

### Run the server

`sudo docker run --name=backend --network=demo -d -p 5050:5050 mern-backend`

## Using Docker Compose

`sudo docker compose up -d`

