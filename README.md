# Create-Dockerfile-for-reactjs-node-
**dockerfile template**
>file name = dockerfile
```
FROM node:14.18.2
WORKDIR /app
# Copy app code
COPY /package*.json /app/
RUN npm install
#IT WILL COPY THE ENTIRE DIR FORECAST TO /app/src INSIDE DOCKER
COPY . .
EXPOSE 3000
CMD [ "npm","start"]
```
**docker ignore template for reactjs or node**
>file name = .dockerignore
```
README.md
.git
.gitignore
Dockerfile
node_modules
.env.staging
.env.production
.env.local
```
# *some of important docker images file name*
**#build image from dockerfile**
```
docker build -t ./dockerfile
```
**#run container**
```
docker run -d -p 3000:3000 --name APM-v1.1.0 apmlab-v1.1.0
```
**#run container with bind volume**
```
docker run -v C:\Users\LENOVO\react-apm-test\lab-inventory\frontend\src:/app/src -d -p 3000:3000 --name APM-volume-v1.1.1 apmlab-v1.1.0
```
**#run container with bind volume (for read only )not write in to local directory**
```
docker run -v C:\Users\LENOVO\react-apm-test\lab-inventory\frontend\src:/app/src:ro -d -p 3000:3000 --name APM-volume-v1.1.1 apmlab-v1.1.0
```
**#CHOKIDAR windows problem**
```
docker run -e CHOKIDAR_USEPOLLING=true -v C:\Users\LENOVO\react-apm-test\lab-inventory\frontend\src:/app/src -d -p 3000:3001 --name APM-volume-v1.1.1 apmlab-v1.1.0
```
**#run with .env**
```
docker run --env-file .\.env.production  -v C:\Users\LENOVO\react-apm-test\lab-inventory\frontend\src:/app/src -d -p 3000:3002 --name APM-volume-v1.1.1 apmlab-v1.1.0
```
**#using docker compose**
```
docker-compose up -d 
```
**#tell the composer to build new image**
```
docker-compose up -d --build
```
**#rename image**
```
docker image tag frontend_apm-frontend-compose ascend/apm-lap-v1-1-0
```
**#push image to dockerhub**
```
docker push asadzoot/ascend-private-repo:ascend/apm-lap-v1-1-0
```
