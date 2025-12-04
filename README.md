pipeline {
    agent any
    tools{
        maven 'MAVEN_HOME'
    }
    stages {
        stage('git repo & clean') {
            steps {
                //bat "rmdir  /s /q mavenjava"
                bat "git clone https://github.com/NagulapallyHarshitha/MavenJava.git"
                bat "mvn clean -f mavenjava"
            }
        }
        stage('install') {
            steps {
                bat "mvn install -f mavenjava" //project name#
            }
        }
        stage('test') {
            steps {
                bat "mvn test -f mavenjava"
            }
        }
        stage('package') {
            steps {
                bat "mvn package -f mavenjava"
            }
        }
    }
}






docker pull redis
docker run --name my-redis -d redis
docker ps
docker exec -it my-redis redis-cli
SET name "Alice"
GET name
exit
docker stop my-redis
docker start my-redis
docker rm my-redis
docker rmi redis

docker build -t redisnew .
docker run --name myredisnew -d redisnew
docker ps -a
docker stop myredisnew
docker rm myredisnew

docker login
docker images
docker ps -a

docker commit <container_id> yourdockerhub/redis1
docker push yourdockerhub/redis1
docker pull yourdockerhub/redis1

docker run --name myredis -d yourdockerhub/redis1
docker exec -it myredis redis-cli
SET name "Abcdef"
GET name
exit

docker logs myredis
docker stats
docker stop myredis
docker rm myredis
docker rmi yourdockerhub/redis1

docker logout



FROM redis:latest
CMD ["redis-server"]

docker-compose.yml
version: "3.9"
services:
  redisdb:
    image: redis
    container_name: myredis
    ports:
      - "8088:6379"


version: "3.9"
services:
  redisdb:
    image: redis
    container_name: myredis
    ports:
      - "8088:6379"
    networks:
      - mynet
    volumes:
      - mydata:/data

networks:
  mynet:

volumes:
  mydata:


docker pull redis
docker run --name my-redis -d redis
docker ps
docker exec -it my-redis redis-cli
SET name "Alice"
GET name
exit
docker stop my-redis
docker start my-redis
docker rm my-redis
docker rmi redis

docker build -t redisnew .
docker run --name myredisnew -d redisnew
docker ps -a
docker stop myredisnew
docker rm myredisnew

docker login
docker images
docker ps -a

docker commit <container_id> yourdockerhub/redis1
docker push yourdockerhub/redis1
docker pull yourdockerhub/redis1

docker run --name myredis -d yourdockerhub/redis1
docker exec -it myredis redis-cli
SET name "Abcdef"
GET name
exit

docker logs myredis
docker stats
docker stop myredis
docker rm myredis
docker rmi yourdockerhub/redis1
docker logout

# Docker-Compose Commands
docker compose up -d
docker compose ps
docker compose logs
docker compose stop
docker compose down
docker compose up --build -d

