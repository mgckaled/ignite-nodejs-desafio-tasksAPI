# `src/middleware/json.js`

## Função

Fornecer uma função que lida com solicitações HTTP. Ela recebe os pedaços de dados da solicitação, tenta interpretá-los como JSON e, se for bem-sucedida, armazena o resultado na propriedade `body` do objeto de solicitação.

## Código comentado

- `export async function json (req, res) {`: Esta linha declara uma função assíncrona chamada `json` que aceita dois parâmetros: `req` e `res`, são objetos de solicitação (request) e resposta (response) HTTP, respectivamente.
- `const buffers = []`: array vazio chamado `buffers` para armazenar os pedaços (chunks) de dados da solicitação enquanto eles são recebidos.
- `for await (const chunk of req) {`: loop que utiliza a sintaxe `for await...of` para iterar através dos pedaços (chunks) de dados da solicitação `req`. A palavra-chave `await` sugere que `req` é um objeto assíncrono que fornece os dados da solicitação em partes, e o loop percorre cada pedaço de forma assíncrona.
- `buffers.push(chunk)`: A cada iteração do loop, o pedaço de dados atual (`chunk`) é adicionado ao array `buffers`. Isso ajuda a coletar todos os pedaços da solicitação em um só lugar.
- `req.body = JSON.parse(Buffer.concat(buffers).toString())`: Aqui, todos os pedaços de dados coletados são concatenados em um único buffer usando `Buffer.concat(buffers)`. Em seguida, o buffer resultante é convertido em uma string usando `.toString()`. Essa string é interpretada como um objeto JSON usando `JSON.parse()`. O resultado é atribuído a `req.body`, o que geralmente significa que os dados JSON agora estão disponíveis na propriedade `body` do objeto de solicitação.
- `} catch { req.body = null }`: Se houver um erro ao analisar os dados JSON (por exemplo, se os dados não forem um JSON válido), o bloco `catch` será executado. Nesse caso, a propriedade `body` do objeto de solicitação `req` será definida como `null`, indicando que a análise do JSON falhou.
- `res.setHeader('Content-type', 'application/json')`: cabeçalho da resposta `res`. O cabeçalho `'Content-type'` é configurado para `'application/json'`, o que significa que a resposta contém dados JSON.

> Voltar para o [`index`](../../../index.md)
