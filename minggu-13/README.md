# Minggu 13 : Docker Swarm

## Legenda
- Node Server : Docker pada komputer/node yang akan digunakan sebagai manager docker swarm
- Node Client : Docker pada komputer/node yang akan digunakan sebagai member docker swarm

## Node Server : Init / memulai docker swarm 
Perintah ini akan membuat docker pada komputer/node menjadi docker swarm manager
```
$ sudo docker  swarm init --advertise-addr 192.168.1.20
```
```
Swarm initialized: current node (k6ikwnm7a93pcc72oytdnvz1x) is now a manager.

To add a worker to this swarm, run the following command:

    docker swarm join --token SWMTKN-1-4o7myza8ixtclqb2hck5z5z6stjspkpp3pwih0fcq5dxue0jro-6tgstgz3yo5e2wat2t2tzbvpy 192.168.1.20:2377

To add a manager to this swarm, run 'docker swarm join-token manager' and follow the instructions.
```

## Node Server : Mengecek node pada docker swarm 
Perintah ini melihat node-node yang terdapat pada docker swarm. Setelah init hanya ada satu node, yaitu si Node Server sendiri.
```
$ sudo docker node ls   
```
```
ID                            HOSTNAME            STATUS              AVAILABILITY        MANAGER STATUS      ENGINE VERSION
k6ikwnm7a93pcc72oytdnvz1x *   elucidator          Ready               Active              Leader              19.03.5
```

## Node Client : Bergabung ke docker swarm Node Server
Perintah ini menggabungkan suatu komputer/node lain menjadi anggota dari suatu docker swarm. Hal yang perlu diperhatikan adalah token unik yang digunakan untuk bergabung serta alamat IP dari Node Server.
```
$ sudo docker swarm join --token SWMTKN-1-4o7myza8ixtclqb2hck5z5z6stjspkpp3pwih0fcq5dxue0jro-6tgstgz3yo5e2wat2t2tzbvpy 192.168.1.20:2377
```
```
This node joined a swarm as a worker.
```

## Node Server : Mengecek node pada docker swarm 
Perintah ini melihat node-node yang terdapat pada docker swarm. Setelah ada node yang bergabung maka akan muncul pada list, dan node tersebut tidak berstatus sebagai docker swarm manager.
```
$ sudo docker node ls   
```
```
ID                            HOSTNAME            STATUS              AVAILABILITY        MANAGER STATUS      ENGINE VERSION
q81mazl250oon5zepcocivkxv     docker-desktop      Ready               Active                                  19.03.5
k6ikwnm7a93pcc72oytdnvz1x *   elucidator          Ready               Active              Leader              19.03.5
```