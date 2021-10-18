# Questão 04
Agora que você já afiou o seu conhecimento sobre criação de imagens Docker, tá na
hora de fazer o deploy de uma aplicação 100% em containers Docker. A aplicação está
no GitHub do KubeDev e um detalhe MUITO importante, a aplicação precisa ser toda
criada com apenas uma linha de comando

# Rotten Potatoes

Executar o comando abaixo para criar a imagem, em seguida os containers e iniciar a aplicação
```
docker-compose --env-file .env up
```

Executar o comando abaixo para interromper a aplicação e remover os containers
```
docker-compose down --remove-orphans
```
