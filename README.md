# Documentação da API de Filmes

## Introdução
Esta API permite que você gerencie uma coleção de filmes, incluindo operações para listar filmes, obter detalhes de um filme, autenticação de usuários e upload de imagens.

## Autenticação
A API utiliza autenticação baseada em JSON Web Tokens (JWT). Para obter um token, faça uma solicitação POST para o endpoint `/token/` com as credenciais do usuário.

### Obter Token
- **Endpoint**: `/token/`
- **Método**: `POST`
- **Corpo da Requisição**:
  ```json
  {
      "username": "seu_usuario",
      "password": "sua_senha"
  }

# Resposta:

    200 OK:

    json

{

    "refresh": "refresh_token",

    "access": "access_token"

        }

        401 Unauthorized: Credenciais inválidas.

Atualizar Token

    Endpoint: /token/refresh/
    Método: POST
    Corpo da Requisição:

    json

{

    "refresh": "refresh_token"

}

Resposta:

    200 OK:

    json

{

    "access": "novo_access_token"

        }

        401 Unauthorized: Token de atualização inválido.

Endpoints
Listar Filmes

    Endpoint: /filmes
    Método: GET
    Descrição: Retorna uma lista de todos os filmes.
    Resposta:
        200 OK:

        json

[

    {

        "id": 1,

        "titulo": "Filme Exemplo",

        "genero": "Ação",

        "ano": 2021

    },

    {

        "id": 2,

        "titulo": "Outro Filme",

        "genero": "Comédia",

        "ano": 2020

    }

        ]

Detalhes do Filme

    Endpoint: /filme/<int:pk>
    Método: GET
    Descrição: Retorna os detalhes de um filme específico.
    Parâmetros:
        pk: ID do filme.
    Resposta:
        200 OK:

        json

{

    "id": 1,

    "titulo": "Filme Exemplo",

    "genero": "Ação",

    "ano": 2021,

    "sinopse": "Uma breve descrição do filme.",

    "imagem": "url_da_imagem"

        }

        404 Not Found: Filme não encontrado.

Criar Filme

    Endpoint: /filmes
    Método: POST
    Descrição: Adiciona um novo filme à coleção.
    Corpo da Requisição:

    json

{

    "titulo": "Novo Filme",

    "genero": "Drama",

    "ano": 2022,

    "sinopse": "Descrição do novo filme.",

    "imagem": "url_da_imagem"

}

Resposta:

    201 Created:

    json

{

    "id": 3,

    "titulo": "Novo Filme",

    "genero": "Drama",

    "ano": 2022

        }

        400 Bad Request: Dados inválidos.

Atualizar Filme

    Endpoint: /filme/<int:pk>
    Método: PUT
    Descrição: Atualiza os detalhes de um filme existente.
    Parâmetros:
        pk: ID do filme.
