# `src/server.js`

## Função

Estabelecer um servidor HTTP básico que utiliza middlewares e rotas para processar requisições. As rotas são definidas em um módulo separado e o servidor é configurado para tratar diferentes rotas de acordo com as definições. O middleware json também é aplicado para analisar o corpo das requisições como JSON.

## Código comentado

1. **Importação de módulos**:
   - `http`: O módulo `http` é um módulo nativo do Node.js que fornece funcionalidades para criar servidores HTTP. Ele está sendo importado usando a sintaxe `import http from 'node:http'`.
   - `json`: Este é um módulo personalizado chamado `json` que implementa um middleware para analisar o corpo das requisições como JSON. Middlewares são funções que podem ser usadas para processar as requisições antes de serem manipuladas pelas rotas. O `await json(req, res)` invoca esse middleware.
   - `routes`: Este é um módulo personalizado que contém a definição das rotas do servidor. As rotas são objetos que contêm informações sobre o método HTTP, o padrão do caminho (expressão regular) e o manipulador da rota.
   - `extractQueryParams`: Este é outro módulo personalizado que implementa uma função para extrair parâmetros de consulta da URL.

2. **Criação do servidor**:
   O servidor HTTP é criado usando o método `http.createServer()`. Ele aceita uma função de retorno de chamada que será executada sempre que uma requisição for recebida.

3. **Função de retorno de chamada do servidor**:
   - Dentro dessa função, primeiro as informações da requisição (método e URL) são extraídas usando `const { method, url } = req`.
   - Em seguida, o middleware `json` é chamado usando `await json(req, res)` para analisar o corpo da requisição como JSON, caso seja necessário.
   - O código então procura uma rota correspondente às informações da requisição dentro do array de rotas usando a função `Array.prototype.find()`. Se uma rota correspondente for encontrada, os parâmetros da rota são extraídos da URL e os parâmetros de consulta também são extraídos.
   - Os parâmetros extraídos são então adicionados ao objeto `req` para que possam ser acessados posteriormente pelo manipulador da rota. Em seguida, a função de manipulação da rota (`route.handler`) é chamada com os objetos `req` e `res`.
   - Se nenhuma rota correspondente for encontrada, o servidor responde com um status 404 (Not Found).

4. **Inicialização do servidor**:
   O servidor é configurado para escutar na porta `3333` e no host `0.0.0.0`. Quando o servidor estiver pronto para aceitar conexões, a função de retorno de chamada é executada e exibe uma mensagem no console.

> Voltar para o [`index`](../../index.md)
