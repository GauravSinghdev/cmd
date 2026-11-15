## __PUll docker image from Hub__

    docker run mongo
    docker run -d mongo  
    docker run -p 2701:2701 -d mongo


## __basic cmd__
    
    docker ps
    docker images
    docker kill container_id


## __Dockerfile__

    FROM node:20-alpine

    WORKDIR /app

    COPY . .

    RUN npm install
    RUN npm run build
    Run npx prisma generate

    EXPOSE 3000

    CMD ["node", "dist/nodejs"]


## __.dockerignore__

    node_modules
    dist


## __Build the image__

    docker built -t karavaan-be folder_path


## __Get inside the container__

    docker exec -it container_id /bin/bash


## __Inject the env__

    docker run -p 2701:2701  -e DATABASE_URL="" -d nodejs-app


## __Push your image to docker hub__

    docker login
    docker push karadevs/react-app


## __Docker Multiple Container__
1.using Network and Volume

    docker network create kara_network  //create a network
    docker volume create volume_database //create a volume
    docker run -d -v volume_database:/data/db --name mongo --network kara_network mongo
    docker run --network kara_network -p 3000:3000 react_app_image

    docker network ls
    docker volume ls


2.Docker Compose file 
(docker-compose.yaml)