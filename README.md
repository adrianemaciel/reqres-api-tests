# API Testing - ReqRes

![Postman](https://img.shields.io/badge/Test%20Tool-Postman-orange)
![API Testing](https://img.shields.io/badge/Testing-API-blue)
![Status](https://img.shields.io/badge/Project-Completed-green)

Projeto de testes de API utilizando o Postman na API pública https://reqres.in/.

O objetivo deste projeto é demonstrar conhecimentos em **testes de API REST**, incluindo testes funcionais, testes negativos, validação de respostas JSON e análise do comportamento da API.

---

# Tecnologias Utilizadas

- Postman
- REST API
- JSON
- Git
- GitHub

---

# Tipos de Testes Realizados

- Testes Funcionais
- Testes Negativos
- Validação de Status Code
- Validação de Estrutura JSON
- Validação de Tempo de Resposta
- Testes de endpoints REST

---

# Cenários de Teste

| ID   | Cenário                           | Método | Endpoint        |
| ---- | --------------------------------- | ------ | --------------- |
| CT01 | Listar usuários                   | GET    | /api/users      |
| CT02 | Buscar usuário por ID válido      | GET    | /api/users/{id} |
| CT03 | Buscar usuário inexistente        | GET    | /api/users/{id} |
| CT04 | Criar usuário com dados válidos   | POST   | /api/users      |
| CT05 | Criar usuário com dados inválidos | POST   | /api/users      |
| CT06 | Atualizar usuário existente       | PUT    | /api/users/{id} |
| CT07 | Atualizar usuário inexistente     | PUT    | /api/users/{id} |
| CT08 | Deletar usuário existente         | DELETE | /api/users/{id} |
| CT09 | Enviar body vazio                 | POST   | /api/users      |
| CT10 | Enviar parâmetros inválidos       | POST   | /api/users      |

---

# Resultados dos Testes

| Endpoint                     | Método | Resultado Esperado | Resultado Observado  | Status |
| ---------------------------- | ------ | ------------------ | -------------------- | ------ |
| /api/users                   | GET    | 200 OK             | 200 OK               | PASS   |
| /api/users/{id}              | GET    | 200 OK             | 200 OK               | PASS   |
| /api/users/{id} inexistente  | GET    | 404                | 404                  | PASS   |
| /api/users                   | POST   | 201 Created        | 201 Created          | PASS   |
| /api/users (dados inválidos) | POST   | Erro esperado      | 201 Created          | FAIL   |
| /api/users/{id}              | PUT    | Atualizar usuário  | 200 OK sem alteração | FAIL   |
| /api/users/{id} inexistente  | PUT    | 404 Not Found      | 200 OK               | FAIL   |
| /api/users/{id}              | DELETE | 204 No Content     | 204 sem remoção      | FAIL   |

---

# Evidências dos Testes

Exemplo de execução no Postman:

<img src="docs/test-results.gif" width="600px">

---

# Análise do Comportamento da API

Durante os testes foi identificado que a API ReqRes possui comportamento de **API mockada**.

Isso significa que algumas operações retornam sucesso, porém não persistem alterações no servidor.

| Endpoint        | Método               | Resultado esperado | Resultado observado | Observação                |
| --------------- | -------------------- | ------------------ | ------------------- | ------------------------- |
| /api/users      | POST                 | Criar usuário      | 201 Created         | Usuário não é persistido  |
| /api/users/{id} | PUT                  | Atualizar usuário  | 200 OK              | Dados não são atualizados |
| /api/users/{id} | PUT (ID inexistente) | 404 Not Found      | 200 OK              | API aceita ID inexistente |
| /api/users/{id} | DELETE               | 204 No Content     | 204 No Content      | Usuário não é removido    |

A API ReqRes é utilizada para **aprendizado e testes de API**, portanto os dados não são persistidos.

---

# Como Executar os Testes

1. Instalar o Postman
2. Importar a collection do projeto
3. Importar o environment
4. Executar os testes manualmente ou utilizando o **Collection Runner**
