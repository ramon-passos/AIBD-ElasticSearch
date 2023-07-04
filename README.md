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

## Criando um índice e populando os dados

### Criando índice:

```
PUT /alunos
{
    "mappings": {
        "properties": {
            "nome": {
                "type": "text"
            },
            "RA": {
                "type": "text"
            },
            "CR": {
                "type": "float"
            },
            "materias_matriculadas": {
                "type": "text"
            },
            "materias_feitas": {
                "type": "object"
            },
            "periodo": {
                "type": "integer"
            },
            "data_nascimento": {
                "type": "date",
                "format": "yyyy-MM-dd"
            },
            "endereco": {
                "type": "text"
            },
            "genero": {
                "type": "text"
            },
            "telefone": {
                "type": "text"
            },
            "email": {
                "type": "text"
            }
        }
    }
}
```

### Populando os dados:

```
POST _bulk
{ "index" : { "_index" : "alunos", "_id": "123456" } }
{ "nome": "João Silva", "RA": "123456", "CR": 8.5, "materias_matriculadas": ["POO", "LFA", "AIBD"], "materias_feitas": [{ "nome": "AED", "nota": 9.0, "carga_horaria": 60 }, { "nome": "TG", "nota": 8.5, "carga_horaria": 45 }, { "nome": "REDES", "nota": 7.8, "carga_horaria": 75 }, { "nome": "IA", "nota": 8.2, "carga_horaria": 60 }, { "nome": "PAA", "nota": 7.5, "carga_horaria": 45 }, { "nome": "POO", "nota": 8.0, "carga_horaria": 60 }, { "nome": "LFA", "nota": 7.5, "carga_horaria": 60 }, { "nome": "AIBD", "nota": 8.3, "carga_horaria": 45 }], "periodo": 7, "data_nascimento": "1990-01-01", "endereco": "Rua ABC, 123", "genero": "Masculino", "telefone": "123456789", "email": "joao.silva@example.com" }
{ "index" : { "_index" : "alunos", "_id": "567890" } }
{ "nome": "Carlos Ferreira", "RA": "567890", "CR": 7.6, "materias_matriculadas": ["Engenharia de Software", "Sistemas Operacionais"], "materias_feitas": [{ "nome": "Algoritmos", "nota": 8.0, "carga_horaria": 60 }, { "nome": "Banco de Dados", "nota": 7.5, "carga_horaria": 45 }, { "nome": "Engenharia de Software", "nota": 7.8, "carga_horaria": 60 }, { "nome": "Sistemas Operacionais", "nota": 7.2, "carga_horaria": 60 }], "periodo": 4, "data_nascimento": "1995-05-10", "endereco": "Rua XYZ, 456", "genero": "Masculino", "telefone": "987654321", "email": "carlos.ferreira@example.com" }
{ "index" : { "_index" : "alunos", "_id": "123789" } }
{ "nome": "Isabela Oliveira", "RA": "123789", "CR": 9.2, "materias_matriculadas": ["Inteligência Artificial", "Redes de Computadores"], "materias_feitas": [{ "nome": "Programação Orientada a Objetos", "nota": 9.5, "carga_horaria": 60 }, { "nome": "Banco de Dados", "nota": 9.2, "carga_horaria": 45 }, { "nome": "Inteligência Artificial", "nota": 9.8, "carga_horaria": 60 }, { "nome": "Redes de Computadores", "nota": 8.7, "carga_horaria": 60 }], "periodo": 6, "data_nascimento": "1993-08-15", "endereco": "Rua DEF, 789", "genero": "Feminino", "telefone": "456789123", "email": "isabela.oliveira@example.com" }
{ "index" : { "_index" : "alunos", "_id": "890123" } }
{ "nome": "Rafael Costa", "RA": "890123", "CR": 8.1, "materias_matriculadas": ["Estrutura de Dados", "Algoritmos", "Banco de Dados"], "materias_feitas": [{ "nome": "Introdução à Programação", "nota": 7.5, "carga_horaria": 60 }, { "nome": "Redes de Computadores", "nota": 8.0, "carga_horaria": 45 }, { "nome": "Estrutura de Dados", "nota": 8.5, "carga_horaria": 60 }, { "nome": "Algoritmos", "nota": 7.8, "carga_horaria": 60 }, { "nome": "Banco de Dados", "nota": 8.2, "carga_horaria": 45 }], "periodo": 5, "data_nascimento": "1992-02-20", "endereco": "Rua GHI, 123", "genero": "Masculino", "telefone": "321654987", "email": "rafael.costa@example.com" }
{ "index" : { "_index" : "alunos", "_id": "678901" } }
{ "nome": "Mariana Santos", "RA": "678901", "CR": 6.9, "materias_matriculadas": ["Programação Web", "Banco de Dados", "Sistemas Operacionais"], "materias_feitas": [{ "nome": "Algoritmos", "nota": 7.2, "carga_horaria": 60 }, { "nome": "Redes de Computadores", "nota": 7.5, "carga_horaria": 45 }, { "nome": "Programação Web", "nota": 6.8, "carga_horaria": 60 }, { "nome": "Banco de Dados", "nota": 7.0, "carga_horaria": 45 }, { "nome": "Sistemas Operacionais", "nota": 6.5, "carga_horaria": 60 }], "periodo": 4, "data_nascimento": "1994-12-05", "endereco": "Rua JKL, 456", "genero": "Feminino", "telefone": "789123456", "email": "mariana.santos@example.com" }
{ "index" : { "_index" : "alunos", "_id": "345678" } }
{ "nome": "Lucas Rodrigues", "RA": "345678", "CR": 7.8, "materias_matriculadas": ["Estrutura de Dados", "Sistemas Distribuídos"], "materias_feitas": [{ "nome": "Introdução à Programação", "nota": 7.0, "carga_horaria": 60 }, { "nome": "Estrutura de Dados", "nota": 7.8, "carga_horaria": 60 }, { "nome": "Sistemas Distribuídos", "nota": 7.5, "carga_horaria": 60 }], "periodo": 6, "data_nascimento": "1993-03-18", "endereco": "Rua MNO, 789", "genero": "Masculino", "telefone": "654789321", "email": "lucas.rodrigues@example.com" }
{ "index" : { "_index" : "alunos", "_id": "901234" } }
{ "nome": "Juliana Ferreira", "RA": "901234", "CR": 8.4, "materias_matriculadas": ["Algoritmos", "Engenharia de Software"], "materias_feitas": [{ "nome": "Introdução à Programação", "nota": 7.8, "carga_horaria": 60 }, { "nome": "Algoritmos", "nota": 8.5, "carga_horaria": 60 }, { "nome": "Engenharia de Software", "nota": 8.0, "carga_horaria": 60 }], "periodo": 5, "data_nascimento": "1993-07-10", "endereco": "Rua PQR, 123", "genero": "Feminino", "telefone": "789321654", "email": "juliana.ferreira@example.com" }
{ "index" : { "_index" : "alunos", "_id": "234567" } }
{ "nome": "Gabriel Lima", "RA": "234567", "CR": 9.7, "materias_matriculadas": ["Inteligência Artificial", "Redes de Computadores", "Banco de Dados"], "materias_feitas": [{ "nome": "Programação Orientada a Objetos", "nota": 9.5, "carga_horaria": 60 }, { "nome": "Algoritmos", "nota": 9.0, "carga_horaria": 60 }, { "nome": "Inteligência Artificial", "nota": 9.8, "carga_horaria": 60 }, { "nome": "Redes de Computadores", "nota": 8.7, "carga_horaria": 60 }, { "nome": "Banco de Dados", "nota": 9.2, "carga_horaria": 45 }], "periodo": 7, "data_nascimento": "1991-11-25", "endereco": "Rua STU, 456", "genero": "Masculino", "telefone": "987654321", "email": "gabriel.lima@example.com" }
{ "index" : { "_index" : "alunos", "_id": "456789" } }
{ "nome": "Sophia Sousa", "RA": "456789", "CR": 7.2, "materias_matriculadas": ["Estrutura de Dados", "Sistemas Operacionais"], "materias_feitas": [{ "nome": "Introdução à Programação", "nota": 6.5, "carga_horaria": 60 }, { "nome": "Estrutura de Dados", "nota": 7.0, "carga_horaria": 60 }, { "nome": "Sistemas Operacionais", "nota": 6.8, "carga_horaria": 60 }], "periodo": 4, "data_nascimento": "1994-05-12", "endereco": "Rua VWX, 789", "genero": "Feminino", "telefone": "654987321", "email": "sophia.sousa@example.com" }
{ "index" : { "_index" : "alunos", "_id": "789012" } }
{ "nome": "Matheus Castro", "RA": "789012", "CR": 8.9, "materias_matriculadas": ["Algoritmos", "Banco de Dados", "Programação Web"], "materias_feitas": [{ "nome": "Introdução à Programação", "nota": 8.2, "carga_horaria": 60 }, { "nome": "Algoritmos", "nota": 8.7, "carga_horaria": 60 }, { "nome": "Banco de Dados", "nota": 9.0, "carga_horaria": 45 }, { "nome": "Programação Web", "nota": 8.5, "carga_horaria": 60 }], "periodo": 5, "data_nascimento": "1993-09-30", "endereco": "Rua XYZ, 456", "genero": "Masculino", "telefone": "321654987", "email": "matheus.castro@example.com" }
{ "index" : { "_index" : "alunos", "_id": "567890" } }
{ "nome": "Lara Oliveira", "RA": "567890", "CR": 6.5, "materias_matriculadas": ["Engenharia de Software", "Sistemas Operacionais"], "materias_feitas": [{ "nome": "Algoritmos", "nota": 6.2, "carga_horaria": 60 }, { "nome": "Engenharia de Software", "nota": 6.8, "carga_horaria": 60 }, { "nome": "Sistemas Operacionais", "nota": 6.5, "carga_horaria": 60 }], "periodo": 4, "data_nascimento": "1994-01-05", "endereco": "Rua ABC, 123", "genero": "Feminino", "telefone": "987321654", "email": "lara.oliveira@example.com" }    
```