<!-- markdownlint-disable MD033 -->

# Ignite Node.js - Desafio `CRUD Tasks - API`

<div align="center">
   <img alt="Node.js" src=".github/assets/nodejs-logo.jpg" width="25%"/>
</div>
<br>

<div align="center">
   <a href="https://github.com/mgckaled">
      <img alt="Made by mgckaled" src="https://img.shields.io/badge/made%20by-mgckaled-yellow">
   </a>
   <img alt="GitHub Repo Size" src="https://img.shields.io/github/repo-size/mgckaled/ignite-nodejs-desafio-tasksAPI">
   <img alt="GitHub Language Count" src="https://img.shields.io/github/languages/count/mgckaled/ignite-nodejs-desafio-tasksAPI">
</div>
<br>

<div align="center">

[**Desafio**](#desafio) &nbsp;&nbsp;**•**&nbsp;&nbsp;
[**Tecnologias**](#tecnologias) &nbsp;&nbsp;**•**&nbsp;&nbsp;
[**Licença**](#licença)

</div>

## Desafio

Nesse desafio você desenvolverá uma API para realizar o CRUD de suas *tasks* (tarefas).

A API deve conter as seguintes funcionalidades:

- Criação de uma *task*
- Listagem de todas as *tasks*
- Atualização de uma *task* pelo `id`
- Remover uma *task* pelo `id`
- Marcar pelo `id` uma *task* como completa
- E o verdadeiro desafio: Importação de *tasks* em massa por um arquivo CSV

### Regras de negócio

Antes das rotas, vamos entender qual a estrutura (propriedades) que uma task deve ter:

- `id` - Identificador único de cada *task*
- `title` - Título da *task*
- `description` - Descrição detalhada da *task*
- `completed_at` - Data de quando a *task* foi concluída. O valor inicial deve ser `null`
- `created_at` - Data de quando a *task* foi criada.
- `updated_at` - Deve ser sempre alterado para a data de quando a *task* foi atualizada.

### Rotas:

#### `POST - /tasks`

- Deve ser possível criar uma *task* no banco de dados, enviando os campos `title` e `description` por meio do `body` da requisição.
- Ao criar uma *task*, os campos: `id`, `created_at`, `updated_at` e `completed_at` devem ser preenchidos automaticamente, conforme a orientação das propriedades acima.

#### `GET - /tasks`

- Deve ser possível listar todas as tasks salvas no banco de dados.
- Também deve ser possível realizar uma busca, filtrando as tasks pelo `title` e `description`

#### `PUT - /tasks/:id`

- Deve ser possível atualizar uma *task* pelo `id`.
- No `body` da requisição, deve receber somente o `title` e/ou `description` para serem atualizados.
- Se for enviado somente o `title`, significa que o `description` não pode ser atualizado e vice-versa.
- Antes de realizar a atualização, deve ser feito uma validação se o `id` pertence a uma *task* salva no banco de dados.

#### `DELETE - /tasks/:id`

- Deve ser possível remover uma *task* pelo `id`.
- Antes de realizar a remoção, deve ser feito uma validação se o `id` pertence a uma *task* salva no banco de dados.

##### `PATCH - /tasks/:id/complete`

- Deve ser possível marcar a *task* como completa ou não. Isso significa que se a *task* estiver concluída, deve voltar ao seu estado “normal”.
- Antes da alteração, deve ser feito uma validação se o `id` pertence a uma *task* salva no banco de dados.

## Tecnologias

- [`Node.js`](https://nodejs.org/n/)
- [`Javascript`](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript)
- [`csv-parse`](https://www.npmjs.com/package/csv-parse)

## Licença

Distribuído sob a licença _MIT_. Veja [LICENSE](LICENSE) para mais informações.  <img alt="License" src="https://img.shields.io/static/v1?label=license&message=MIT&color=49AA26&labelColor=000000">

---

<h5 align="center">
 2023 - <a href="https://github.com/mgckaled/">Marcel Kaled</a>
</h5>
