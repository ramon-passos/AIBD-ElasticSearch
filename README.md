# AIBD-ElasticSearch

Este projeto é referente ao trabalho final da disciplina de Aspectos e Implementação de Banco de Dados do ICT-UNIFESP
A ideia é implementar um banco de dados não relacional, para esse projeto escolhemos utilizar ElasticSearch, um banco não relacional orientado a documentos.

Para rodar o projeto é necessário ter instalado docker e docker-compose.

## Rodando o projeto

Primeiramente é necessário rodar na raiz do projeto o seguinte comando:

`docker-compose up -d kibana`

Ou então para as novas versões do docker compose como engine do docker:

`docker compose up -d kibana`

Após aguardar alguns segundos para inicialização do container basta acessar no navegador: `localhost:5601`
Clique em `explore on my own` e em seguida abra o menu no canto superior esquerdo e nas últimas opções tem a opção `Dev Tools`. Lá está o console de desenvolvimento onde é possivel criar índices e altera-los
