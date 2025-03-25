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

### Deletar Filme
- **Endpoint**: `/filme/<int:pk>`
- **Método**: `DELETE`
- **Descrição**: Remove um filme da coleção.
- **Parâmetros**:
  - `pk`: ID do filme.
- **Resposta**:
  - **204 No Content**: O filme foi removido com sucesso.
  - **404 Not Found**: Filme não encontrado.

## Erros Comuns
A API pode retornar os seguintes códigos de erro:

- **400 Bad Request**: A requisição não pôde ser entendida devido à sintaxe inválida.
- **401 Unauthorized**: As credenciais fornecidas são inválidas ou o token de acesso expirou.
- **403 Forbidden**: O acesso ao recurso solicitado é proibido.
- **404 Not Found**: O recurso solicitado não foi encontrado.
- **500 Internal Server Error**: Ocorreu um erro no servidor ao processar a requisição.

## Considerações Finais
- **CORS**: Certifique-se de que as configurações de CORS estão adequadas para permitir chamadas da sua aplicação frontend.
- **Documentação**: Mantenha a documentação atualizada com quaisquer alterações na API ou nos endpoints.
- **Feedback**: Se você encontrar problemas ou tiver sugestões, sinta-se à vontade para entrar em contato com os desenvolvedores da API.

## Conclusão
Esta documentação fornece uma visão geral completa da API de Filmes, incluindo autenticação, operações CRUD e tratamento de erros. Sinta-se à vontade para explorar e integrar a API em suas aplicações!


