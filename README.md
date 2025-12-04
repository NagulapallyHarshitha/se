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








  



sudo apt update
sudo apt-get install docker.io
sudo apt install git
sudo apt install nano
need to keep github url of aws
git clone url
ls
cd aws
nano Dockerfile
FROM nginx:alpine
COPY . /usr/share/nginx/html
sudo docker build -t mywebapp .
sudo docker run -d -p 80:80 mywebapp

