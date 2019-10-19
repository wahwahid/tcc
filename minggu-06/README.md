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

![NGINX](./img/b01.png)

## Membuild docker image
```
docker build -t webserver-image:v1 .
```
Membuild dockerimage dengan nama "webserver-image" serta versi "v1"

![NGINX](./img/b02.png)

## Mengecek docker image
```
docker images
```
Menampilkan daftar docker image yang tersedia di komputer host

![NGINX](./img/b03.png)

## Menjalankan docker container
```
docker run -d -p 80:80 webserver-image:v1
```
Menjalankan docker container di background serta mengekspose secara static port 80 ke port 80 dari docker image yang baru dibuat (webserver-image:v1)

![NGINX](./img/b04.png)

## Mengecek NGINX
```
curl docker
```
Mengecek webserver nginx yang ada didalam docker telah berjalan dengan melakukan HTTP request menggunakan curl ke host "docker"

![NGINX](./img/b05.png)

# Building Container Images

## Step 1 - Base Images
Menentukan basis dari docker image yang akan digunakan. Disini kita akan menggunakan basis docker image dari "nginx:1.11-alpine"
```
FROM nginx:1.11-alpine
``` 

![Build](./img/c01.png)

## Step 2 - Running Commands
Menuliskan perintah-perintah yang akan dieksekusi ketika docker images dijalankan menjadi docker container. Disini kita akan menjalankan perintah untuk menyalin file "index.html" yang ada pada direktori aktif ke suatu direktori di dalam docker image yaitu "/usr/share/nginx/html"

Sebelumnya kita siapkan terlebih dahulu file "index.html", contoh sebagai berikut :
```html
<h1>Kulanuwun Donya !!!</h1>
```

![Build](./img/c03.png)

Kemudian kita tambahkan perinyah ke dalam dockerfile

```
COPY index.html /usr/share/nginx/html/index.html
```

![Build](./img/c02.png)

## Step 3 - Exposing Ports
Menentukan port yang perlu di ekspose oleh docker. Disini kita akan mengekspose port 80.
```
EXPOSE 80
```

![Build](./img/c04.png)

## Step 4 - Default Commands
Menentukan perintah baku yang akan dijalankan docker untuk meluncurkan aplikasi. Disini perintah yang akan kita atur adalah :
```
nginx -g daemon off;
```

Penulisannya akan menjadi seperti dibawah ini pada dockerfile
```
CMD ["nginx", "-g", "daemon off;"]
```

![Build](./img/c05.png)

## Step 5 - Building Containers
Membuild suatu docker image container. Disini kita akan membuild docker image dari dockerfile yang sudah kita siapkan sebelumnya, nama image yang akan dibuat adalah "sleman-nginx"
```
docker build -t sleman-nginx:latest .
```

![Build](./img/c06.png)

Cek docker image yang telah di build menggunakan perintah
```
docker images
```

![Build](./img/c07.png)

## Step 6 - Launching New Image
Menjalankan docker image yangtelah di build menjadi suatu docker container.
```
docker run -d -p 80:80 sleman-nginx:latest
```

![Build](./img/c08.png)

Daftar docker container yang berjalan dapat dilihat dengan menggunakan perintah 
```
docker ps
```

![Build](./img/c09.png)

Untuk megecek docker container yang kita buat, kita dapat mengakses protokol HTTP / port 80 menggunakan curl 
```
curl docker
```

![Build](./img/c10.png)

Bisa juga dengan mengaksesnya melalui browser

![Build](./img/c11.png)