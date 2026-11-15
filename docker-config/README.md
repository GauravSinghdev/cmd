## 1) PUll docker image from Hub

docker run mongo

docker run -d mongo
(detached mode run in background)

*__IDEALLY RUN:__*
docker run -p 2701:2701 -d mongo


## 2) basic cmd

*__list of containers:__*
docker ps

docker images
docker kill container_id


## 3) Dockerfile

FROM node:20

WORKDIR /app

COPY . .

RUN npm install
RUN npm run build
Run npx prisma generate

EXPOSE 3000

CMD ["node", "dist/nodejs"]


## 4) .dockerignore

node_modules
dist


## 5) Build the image

docker built -t karavaan-be (path or . for current)


## 6) Get inside the container 

docker exec -it container_id /bin/bash


## 7) Inject the env 

docker run -p 2701:2701  -e DATABASE_URL="" -d nodejs-app


## 8) Push your image to docker hub

docker login
docker push karadevs/react-app


## 9) Docker Multiple Container

### using Network and Volume
docker network create kara_network  //create a network
docker volume create volume_database //create a volume
docker run -d -v volume_database:/data/db --name mongo --network kara_network mongo
docker run --network kara_network -p 3000:3000 react_app_image

docker network ls
docker volume ls


## 10) Docker Compose file 
(docker-compose.yaml)