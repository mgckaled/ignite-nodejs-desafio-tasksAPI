# `streams/import-csv.js`

## Função

Leitura de um aquivo CSV: faz o parsing das linhas do CSV e envia os dados para um servidor local através de requisições HTTP POST, adicionando um atraso entre as requisições para evitar sobrecarga do servidor.

## Código comentado

1. **Importação de Módulos:**
   - `import { parse } from 'csv-parse'`: Importa a função `parse` do módulo `csv-parse`, que é usada para fazer o parsing do CSV.
   - `import fs from 'node:fs'`: Importa o módulo `fs` para manipulação de arquivos.

2. **Obtenção do Caminho do CSV:**
   - `const csvPath = new URL('./tasks.csv', import.meta.url)`: Cria um objeto `URL` que representa o caminho do arquivo CSV relativo ao módulo atual.

3. **Criação do Stream de Leitura:**
   - `const stream = fs.createReadStream(csvPath)`: Cria um stream de leitura para o arquivo CSV especificado.

4. **Configuração do Parsing CSV:**
   - `const csvParse = parse({ ... })`: Cria um objeto de configuração para o parser CSV.
     - `delimiter: ','`: Define a vírgula como delimitador das colunas no CSV.
     - `skipEmptyLines: true`: Pula linhas vazias no CSV.
     - `fromLine: 2`: Começa a fazer o parsing a partir da segunda linha para ignorar o cabeçalho.

5. **Função Principal Assíncrona:**
   - `async function run () { ... }`: Define a função principal assíncrona que faz o parsing das linhas do CSV e envia os dados para o servidor.

6. **Parsing e Envio de Dados:**
   - `const linesParse = stream.pipe(csvParse)`: Cria um pipeline que lê o stream de leitura e faz o parsing das linhas do CSV.
   - `for await (const line of linesParse) { ... }`: Itera de forma assíncrona sobre cada linha parseada do CSV.
     - `const [title, description] = line`: Destrutura a linha em um array, onde a primeira coluna é atribuída a `title` e a segunda a `description`.
     - `await fetch('http://localhost:3333/tasks', { ... })`: Faz uma requisição HTTP POST para um servidor local, enviando os dados `title` e `description` como um JSON no corpo da requisição.
     - `await wait(1000)`: Aguarda 1 segundo (1000 milissegundos) antes de continuar para a próxima linha.

7. **Execução da Função Principal:**
   - `run()`: Chama a função `run()` para iniciar o processamento.

8. **Função de Espera:**
   - `function wait (ms) { ... }`: Define uma função que retorna uma promessa que é resolvida após um certo número de milissegundos. Essa função é usada para criar um atraso entre as requisições.

> Voltar para o [`index`](../../index.md)
