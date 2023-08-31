# `src/utils/build-route-path.js`

## Função

Construir uma expressão regular personalizada que corresponde a um caminho de rota com parâmetros de rota e uma possível parte de consulta.

## Código comentado

- `export function buildRoutePath(path)`: define uma função chamada `buildRoutePath` que aceita um argumento `path`.
- `const routeParametersRegex = /:([a-zA-Z]+)/g;`: cria uma expressão regular (`routeParametersRegex`) que irá coincidir com padrões de parâmetros de rota no formato `:parametro`. Os parâmetros de rota são identificados por uma palavra após `:`.
- `const paramsWithParams = path.replaceAll(routeParametersRegex, '(?<$1>[a-z0-9-_]+)');`: `replaceAll` é usado para substituir todos os padrões de parâmetros de rota na string de entrada `path` pelo padrão de grupo de captura nomeado. O grupo de captura nomeado é criado usando `(?<$1>[a-z0-9-_]+)`, onde `$1` é substituído pelo nome do parâmetro da rota correspondente.
`const pathRegex = new RegExp(^${paramsWithParams}(?<query>\\?(.*))?$);`: Isso cria uma expressão regular completa para corresponder ao caminho da rota. Ele começa com os parâmetros de rota substituídos (`paramsWithParams`) e inclui um grupo de captura nomeado chamado `query` para lidar com consultas opcionais. O `\\?` corresponde a um ponto de interrogação literal (pois o ponto de interrogação tem significado especial em expressões regulares) e `.*` corresponde a zero ou mais caracteres que podem seguir a consulta.
- `return pathRegex;`: A função retorna a expressão regular completa criada.

> Voltar para o [`index`](../../../index.md)
