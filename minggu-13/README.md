# Minggu 13 : Docker Swarm

## Node Server : Init / memulai docker swarm 
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
```
$ sudo docker node ls   
```
```
ID                            HOSTNAME            STATUS              AVAILABILITY        MANAGER STATUS      ENGINE VERSION
k6ikwnm7a93pcc72oytdnvz1x *   elucidator          Ready               Active              Leader              19.03.5
```

## Node Client : Bergabung ke docker swarm Node Server
```
$ sudo docker swarm join --token SWMTKN-1-4o7myza8ixtclqb2hck5z5z6stjspkpp3pwih0fcq5dxue0jro-6tgstgz3yo5e2wat2t2tzbvpy 192.168.1.20:2377
```
```
This node joined a swarm as a worker.
```

## Node Server : Mengecek node pada docker swarm 
```
$ sudo docker node ls   
```
```
ID                            HOSTNAME            STATUS              AVAILABILITY        MANAGER STATUS      ENGINE VERSION
q81mazl250oon5zepcocivkxv     docker-desktop      Ready               Active                                  19.03.5
k6ikwnm7a93pcc72oytdnvz1x *   elucidator          Ready               Active              Leader              19.03.5
```