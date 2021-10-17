# Conversor de Peso

## Construir a imagem

Abra um terminal no diretorio da aplicação e execute os comandos abaixo para criar a imagem.

```
cd ConversaoPeso.Web/
docker build -t {{your-namespace}}/conversao-peso:{{tag}} .
```

Execute o comando abaixo para criar um container.
```
docker run --name conversao-peso -d -p 8080:80 {{your-namespace}}/conversao-peso:{{tag}}
```

Abrar um browser no endereço abaixo para ver a aplicação.
```
http://localhost:8080
```