# Questão 05

Chegou um cliente pra você que possui todas as suas aplicações em data centers e a
gestão dessas aplicações está cada vez mais complexa então pra iniciar um plano de
gestão unificada e migração pra um ambiente cloud, as aplicações serão migradas pra
containers. E hoje você precisa iniciar esse processo com um projeto piloto, o portal de
conteúdos da empresa construido em Wordpress. Então hoje sua missão é criar esse
ambiente wordpress pronto para a equipe de publicidade começar a popular.

# Ambiente Wordpress

Executar o comando abaixo para criar a imagem, em seguida os containers e iniciar a aplicação
```
docker-compose --env-file .env up
```

Executar o comando abaixo para interromper a aplicação e remover os containers
```
docker-compose down --remove-orphans
```
