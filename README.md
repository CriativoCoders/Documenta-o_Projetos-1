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

