# Deploying First Container (Redis)

## Mencari docker image dengan nama "redis"
```
docker search redis
```
![DeployingFirstContainer](./img/A01.png)

## Menjalankan docker image menjadi docker container secara background
```
docker run -d redis
```
![DeployingFirstContainer](./img/A02.png)

## Melihat seluruh container yang sedang berjalan
```
docker ps
```
![DeployingFirstContainer](./img/A03.png)

## Melihat detail dari suatu container yang sedang berjalan
```
docker inspect a72
```
![DeployingFirstContainer](./img/A04.png)

## Melihat log dari suatu container yang sedang berjalan
```
docker logs a72
```
![DeployingFirstContainer](./img/A05.png)

## Menjalankan container dan mengekspose suatu port secara statis
```
docker run -d --name redisHostPort -p 6379:6379 redis:latest
```
![DeployingFirstContainer](./img/A06.png)

## Menjalankan container dan mengekspose suatu port secara dinamis
```
docker run -d --name redisDynamic -p 6379 redis:latest
```
![DeployingFirstContainer](./img/A07.png)

## Mencari suatu port dari suatu container yang diekspose secara dinamis
```
docker port redisDynamic 6379
```
![DeployingFirstContainer](./img/A08.png)

## Menjalankan docker yang menyimpan data di komputer host
```
docker run -d --name redisMapped -v /opt/docker/data/redis:/data redis
```
![DeployingFirstContainer](./img/A09.png)

## Menjalankan docker image menjadi docker container secara foreground
```
docker run ubuntu ps
```
![DeployingFirstContainer](./img/A10.png)

## Mengakses bash shell di dalam container
```
docker run -it ubuntu bash
```
![DeployingFirstContainer](./img/A11.png)

# NGINX
## Membuat dockerfile
```
FROM nginx:alpine
COPY . /usr/share/nginx/html
```
Mendefinisikan basis docker image serta menyalin seluruh file yang ada di direktori kerja ke suatu tempat didalam container (/usr/share/nginx/html).

## Membuild dockerimage
```
docker build -t webserver-image:v1 .
```
Membuild dockerimage dengan nama "webserver-image" serta versi "v1"