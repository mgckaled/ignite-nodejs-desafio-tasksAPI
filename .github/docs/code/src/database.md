# `src/database.js`

## Função

Implementar uma classe `Database` que simula a funcionalidade de um banco de dados simples usando um arquivo JSON como armazenamento persistente. Ela permite selecionar, inserir, atualizar e excluir registros de diferentes tabelas do banco de dados.

## Código comentado

- o módulo `fs/promises` é importado para lidar com operações de leitura e escrita de arquivos de forma assíncrona usando Promises.
- `const databasePath = new URL('../db.json', import.meta.url)` - cria-se uma nova instância da classe `URL` do JavaScript. A classe `URL` é usada para trabalhar com URLs (Uniform Resource Locators), que podem ser endereços da web ou caminhos locais. `import.meta.url` é uma propriedade especial disponível em módulos ECMAScript (ESM) e fornece a URL de onde o código está sendo executado.
- A classe `Database` é exportada e possui um campo privado `#database` que armazena os dados do banco de dados em memória. No construtor da classe, o arquivo JSON é lido de forma assíncrona usando `fs.readFile`. Se a leitura for bem-sucedida, os dados são analisados como um objeto JavaScript e armazenados no campo `#database`. Se a leitura falhar (por exemplo, se o arquivo ainda não existir), o método privado `#persist` é chamado para criar o arquivo JSON vazio.
- O método privado `#persist` escreve os dados do banco de dados de volta no arquivo JSON usando `fs.writeFile`.
- O método `select` é usado para recuperar dados da tabela especificada. Ele aceita um parâmetro `table` que indica a tabela alvo e um parâmetro opcional `search` que contém critérios de busca. Se nenhum critério for fornecido, todos os dados da tabela são retornados. Se critérios de busca forem fornecidos, os dados são filtrados com base nas condições especificadas.
- O método `insert` insere um novo conjunto de dados na tabela especificada. Se a tabela já tiver dados, o novo conjunto é adicionado ao final do array existente. Se a tabela ainda não tiver dados, um novo array com o conjunto de dados é criado.
- O método `update` é usado para atualizar um conjunto de dados existente na tabela. Ele aceita um parâmetro `table` que indica a tabela alvo, um parâmetro `id` que identifica o registro a ser atualizado e um parâmetro data contendo os novos valores a serem aplicados. O método encontra o índice do registro pelo `id`, atualiza os valores relevantes e chama o método `#persist` para salvar as alterações no arquivo JSON.
- O método `delete` é usado para excluir um conjunto de dados da tabela. Ele aceita um parâmetro `table` que indica a tabela alvo e um parâmetro `id` que identifica o registro a ser excluído. O método encontra o índice do registro pelo `id`, remove-o do array e chama o método `#persist` para refletir a alteração no arquivo JSON.

> Voltar para o [`index`](../../index.md)
