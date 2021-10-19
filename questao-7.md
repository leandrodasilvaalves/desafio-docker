# Docker


![Docker](https://upload.wikimedia.org/wikipedia/commons/thumb/4/4e/Docker_%28container_engine%29_logo.svg/1200px-Docker_%28container_engine%29_logo.svg.png)
O docker é uma plataforma Open Source (por enquanto 😉) para empacotar uma aplicação em container. O seu uso traz muitas vantagens desde o desenvolvimento até a entrega em produção.

## Algumas de suas principais características:

- **Portabilidade e facilidade de deploy**: o fato da aplicação estar empacotada, torna fácil implantá-la de maneira extremamente rápida em qualquer servidor que execute containers, ou melhor ainda, em qualquer Cloud Provider.
- **Facilidade de rollback**: a cada nova versão do software, uma nova versão da imagem docker também dever gerada. Logo, se a versão mais recente apresentou algum problema, basta reimplantar a versão anterior (supostamente mais estável) novamente.
- **Economia de recursos**: possibilita limitar o uso de CPU e memória. Além disso, sua imagem é divida em camadas as quais podem ser compartilhadas com imagens derivadas ou semelhantes. Portanto, se eu tenho uma imagem A com 40mb de tamanho e eu crio uma imagem B a partir de A com algumas novas funcionalidades, teoricamente terei duas imagens de 40mb cada, porém, na prática para a imagem B será criada apenas a camada que difere da A, otimizando assim o uso do disco rígido.
- **Ambientes Similares**: o fato do container poder ser altamente configurável (principalmente por variáveis de ambiente) faz com que uma mesma  imagem possa ser utilizada em diferentes ambientes sem comprometer o funcionamento da aplicação.
- **Isolamento do servidor**: é possível executar vários containers da mesma imagem rodando em um único servidor facilitando assim o processo de escalonamento.


# Docker Compose
![Docker Compose](https://www.kindpng.com/picc/m/27-272537_docker-compose-docker-compose-svg-hd-png-download.png)

Embora o docker traga muitas vantagens, seu uso pode se tornar complexo quando temos que lidar com várias aplicações. Criar imagens, volumes, containers, redes adequadas para cada tipo de serviço, variáveis de ambientes adequadas, etc. Tudo isso pode ser muito complicado de fazer apenas por linha de comando. 

É aí que entra o **Docker Compose**. Ele é um orquestrador de containers, os quais podemos definir de forma declarativa em um arquivo `yaml`.


Abaixo segue um exemplo de um arquivo `docker-compose.yalm`. Aqui temos um ambiente WordPress onde os dados de conexão com o banco de dados são passados por variáveis de ambiente. Além deste recurso, temos também o mapeamento de portas do host para o container e também o mapeamento de volumes. Tudo isso torna muito fácil o levantamento  desta aplicação em qualquer ambiente com as configurações corretas e fáceis de ajustar.

![Exemplo Docker Compose](https://miro.medium.com/max/524/1*TeBgetHlGCePc9Nq0__AtQ.png)

Desta forma consigo subir todo um conjunto de aplicações com uma única linha de comando. Como no exemplo abaixo, porém é preciso abrir o terminal dentrodo diretório em que se encontra o arquivo `docker-compose.yaml`.
```
docker-compose up
```

Para parar as aplicações basta executar o comando abaixo também com o terminal dentro do diretório em que se encontra o arquivo `docker-compose.yalm`.
```
docker-compose down
```

Apesar de todas estas facilidades do Docker Compose não é indicado para ambiente de produção, pois não provê resiliência e auto escalonamento. No entanto, seu uso é muito indicado para ambientes de desenvolvimento e homologação onde os requisitos acima não são obrigatórios. Para ambiente de produção é indicado Kubernetes como serviço, mas isso é assunto para outro post.

Docker e Docker Compose formam um ferramental muito poderoso para auxiliar o dia a dia do desenvolvedor. Até aqui citamos apenas algumas de suas caraterísticas básicas. Com certeza ainda há muito conteúdo para mergulhar e se tornar cada vez mais um profissional de elite.
