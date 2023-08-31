# `src/utils/extract-query-params.js`

## Função

Extrair parâmetros de consulta de uma string de consulta (query string) e organizá-los em um objeto JavaScript.

Função `extractQueryParams` - recebe uma *string* de consulta, remove o ponto de interrogação inicial, divide os pares chave-valor e os organiza em um objeto JavaScript, que é então retornado. Isso é útil para analisar as informações de consulta de URLs, onde os parâmetros são passados no formato `chave=valor` e separados por `&`.

## Código comentado

- `export function extractQueryParams(query)`: Esta linha define uma função chamada `extractQueryParams`, que aceita um único parâmetro chamado `query`. O `export` indica que essa função será exportada para que possa ser utilizada em outros arquivos ou módulos.
- `return query.substr(1)`: Aqui, a função começa manipulando a *string* `query`. Ela usa o método `substr(1)` para remover o primeiro caractere (normalmente o ponto de interrogação `?`) da *string* de consulta. Isso é feito porque as strings de consulta geralmente começam com um ponto de interrogação, e este não é necessário para a análise posterior dos parâmetros.
- `.split('&')`: O resultado da operação anterior é uma *string* sem o ponto de interrogação inicial. Esta linha usa o método `split('&')` para dividir a *string* em uma matriz de substrings, usando o caractere `&` como delimitador. Isso é feito para separar os diferentes parâmetros da consulta, já que eles são geralmente separados por `&`.
- `.reduce((queryParams, param) => { ... }, {})`: O método `reduce` é usado para percorrer cada elemento na matriz resultante do passo anterior e acumulá-los em um único objeto. O segundo argumento `{}` é o valor inicial do objeto acumulador (`queryParams`).
- `const [key, value] = param.split('=')`: Aqui, cada elemento da matriz de substrings é uma sequência no formato `"chave=valor"`. Esta linha divide a sequência usando o caractere `=` como delimitador e armazena a chave na variável `key` e o valor na variável `value`.
- `queryParams[key] = value`: A chave e o valor extraídos do passo anterior são usados para adicionar uma propriedade ao objeto `queryParams`. O nome da propriedade será a chave extraída e o valor será o valor extraído.
-`return queryParams`: No final de cada iteração, o objeto `queryParams` é retornado para ser usado na próxima iteração

> Voltar para o [`index`](../../../index.md)
