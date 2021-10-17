# Conversor de Temperatura

## Construir a imagem

Abra um terminal no diretorio da aplicação e execute os comandos abaixo para criar a imagem.

```
cd src/
docker build -t {{your-namespace}}/conversao-temperatura:{{tag}} .
```

Execute o comando abaixo para criar um container.
```
docker run --name conversao-temperatura -d -p 8080:8080 {{your-namespace}}/conversao-temperatura:{{tag}}
```

Abrar um browser no endereço abaixo para ver a aplicação.
```
http://localhost:8080
```