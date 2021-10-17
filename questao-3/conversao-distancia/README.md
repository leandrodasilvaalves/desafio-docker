# Conversor de Distância

## Construir a imagem

Abra um terminal no diretorio da aplicação e execute os comandos abaixo para criar a imagem.

```
docker build -t {{your-namespace}}/conversao-distancia:{{tag}} .
```

Execute o comando abaixo para criar um container.
```
docker run --name conversao-distancia -d -p 8080:5000 {{your-namespace}}/conversao-distancia:{{tag}}
```

Abrar um browser no endereço abaixo para ver a aplicação.
```
http://localhost:8080
```