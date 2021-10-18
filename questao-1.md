# Questão 01

Execute os comandos para criar os 4 bancos de dados listados com containers, e use
como se tivesse instalado eles localmente na sua máquina (Não esquece de garantir
que não vai perder os dados caso o container seja excluido).
- MongoDB
- MariaDB
- PostgreSQL
- Redis


## MongoDB

Baixar a imagem
```
docker pull mongo:4.4.10
```

Criar o volume para salvar os dados
```
docker volume create mongodb
```

Criar o container.
```
docker run -d --name mongodb -v mongodb:/data/db -p 27017:27017 mongo:4.4.10
```

Criar o banco e a collection
```javascript
use mydb
db.pessoa.insertOne({
    nome: "Leandro",
    idade: 35
})
```

Remover o container
```
docker container rm -f mongodb
```


## MariaDB

Baixar a imagem
```
docker pull mariadb:10.6.4
```

Criar o volume para salvar os dados
```
docker volume create mariadb
```

Criar o container
```
docker run -p 3306:3306 -v mariadb:/var/lib/mysql --name mariadb -e MARIADB_ROOT_PASSWORD=123mudar -d mariadb:10.6.4
```
Criar banco de dados e tabela
```sql
CREATE DATABASE teste;

USE teste;

CREATE TABLE Pessoa(
    Id INT,
    Nome VARCHAR(50),
    Idade INT
);
```
Remover container
```
docker container rm -f mariadb
```

## Postgres

Baixar a imagem
```
docker pull postgres:alpine3.14
```

Criar o volume para salvar os dados
```
docker volume create postgres
```

Criar o container
```
docker run -d --name postgres -e POSTGRES_PASSWORD=123@Mudar -v postgres_data:/var/lib/postgresql/data -p 5432:5432 postgres:alpine3.14
```

Criar banco de dados e tabela
```sql
CREATE DATABASE MyDb;

CREATE TABLE Pessoas(
   ID INT PRIMARY KEY     NOT NULL,
   Nome           TEXT    NOT NULL,
   Idade          INT     NOT NULL
);
```

Remover o container
```
docker container rm -f postgres
```

## Redis

1. Baixar a imagem
```
docker pull redis:6.2.6
```

2. Criar o volume para salvar os dados
```
docker volume create redis
```

3. Criar o container
```
docker run  -v redis:/data   --name redis -p 6379:6379 -d redis:6.2.6 redis-server --appendonly yes
```

4. Inserir alguma informação no cache por linha de comando
```
docker exec -it redis redis-cli set foo bar
```

5. Remover o container
```
docker container rm -f redis
```

6. Após destruir o container, recriá-lo com o comado do passo 3. Depois disso executar o comando abaixo para acessar o chace persistido no volume
```
docker exec -it redis redis-cli get foo
```
