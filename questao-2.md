 <!-- fabricio@kubedev.io -->

# Questão 02

> O exemplos abaixo assumem que os containers já foram devidamente criados na questão 01.

## Mongo Express

Baixar a imagem 
```
docker pull mongo-express:1.0.0-alpha.4
```

Criar uma rede e conectá-la ao container mongodb existente
```
docker network create mongodb && \
docker network connect mongodb mongodb

```

Criar o container
```
docker run -d \
    --network mongodb \
    --name mongo-express \
    -p 8081:8081 \
    -e ME_CONFIG_MONGODB_SERVER="mongodb" \
    mongo-express:1.0.0-alpha.4
```

## phpmyadmin

Baixar a imagem
```
docker pull phpmyadmin:latest
```

Criar uma rede e conectá-la ao container mariadb existente
```
docker network create mariadb && \
docker network connect mariadb mariadb
```

Criar o container
```
docker run -d --name phpmyadmin -p 8081:80 --network mariadb -e PMA_HOST=mariadb -e PMA_USER=root -e PMA_PASSWORD=123mudar phpmyadmin:latest
```

## PgAdmin

Baixar a imagem 
```
docker pull dpage/pgadmin4:latest
```

Criar um volume para salvar os servers do PgAdmin
```
docker volume create pgadmin4
```

Criar uma rede e conectá-la ao container postgres existente
```
docker network create postgres && \
docker network connect postgres postgres
```

Criar o container
```
docker run --name pgadmin4 --network=postgres -v pgadmin4:/var/lib/pgadmin -p 8081:80 -e "PGADMIN_DEFAULT_EMAIL=teste@email.com" -e "PGADMIN_DEFAULT_PASSWORD=123mudar" -d dpage/pgadmin4:latest
```

## Redis Commander

Baixar a imagem
```
docker pull rediscommander/redis-commander:latest
```

Criar uma rede e conectá-la ao container redis existente
```
docker network create redis && \
docker network connect redis redis
```

Criar o container
```
 docker run  -d --name redis-commander --env REDIS_HOSTS=local:redis:6379 -p 8081:8081 --network redis rediscommander/redis-commander:latest
```