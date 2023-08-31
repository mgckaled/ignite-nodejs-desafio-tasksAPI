# `src/routes.js`

## Função

Criar um conjunto de rotas para uma aplicação web que gerencia tarefas (tasks). A aplicação utiliza um objeto `Database` para armazenar, recuperar, atualizar e excluir tarefas. Cada rota é definida com um método HTTP (como POST, GET, PUT, DELETE, PATCH), um caminho de rota, e a função manipuladora [`buildRoutePath`](../src/utils/build-route-path.md) que é executada quando a rota é acessada.

## Código comentado

1. **Importações**:
   - `randomUUID` é uma função importada do módulo `node:crypto` que é usada para gerar um identificador único universal (UUID) para as tarefas.
   - `Database` é uma classe importada de um arquivo chamado `database.js`. Esta classe lida com operações de banco de dados, como inserção, seleção, atualização e exclusão.
   - `buildRoutePath` é uma função importada de um arquivo chamado `build-route-path.js`, que é usada para construir e validar o caminho completo das rotas.

2. **Instância do Banco de Dados**:
   - Uma instância da classe `Database` criada para interagir com a fonte de dados (banco de dados) para as tarefas.

3. **Definição de Rotas**:
   - Um array chamado `routes` é definido. Cada elemento deste array representa uma rota da aplicação.
   - Cada objeto de rota contém os seguintes campos:
     - `method`: O método HTTP associado à rota (por exemplo, 'POST', 'GET', 'PUT', 'DELETE', 'PATCH').
     - `path`: O caminho da URL associado à rota.
     - `handler`: Uma função manipuladora que é executada quando a rota é acessada.

4. **Manipuladores de Rota**:
   - Cada manipulador de rota (`handler`) é uma função que recebe os objetos `req` (requisição) e `res` (resposta) como argumentos. Estes objetos são padrões do Node.js para lidar com requisições e respostas HTTP.
   - Cada manipulador de rota executa diferentes operações dependendo do método HTTP:
     - **POST**: Cria uma nova tarefa e a insere no banco de dados.
     - **GET**: Retorna uma lista de tarefas, possivelmente filtrada pelo título ou descrição, do banco de dados.
     - **PUT**: Atualiza uma tarefa existente com novos dados.
     - **DELETE**: Remove uma tarefa do banco de dados.
     - **PATCH**: Marca uma tarefa como completa ou incompleta.

5. **Respostas HTTP**:
   - A função `res.writeHead(statusCode)` é usada para definir o código de status da resposta HTTP.
   - A função `res.end(data)` é usada para enviar a resposta, juntamente com os dados fornecidos.

> Voltar para o [`index`](../../index.md)
