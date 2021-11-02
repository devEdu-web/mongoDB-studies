# 2.4 Seletores Queries para buscas no banco de dados

## Comparação

| Name     | Description                                                           |
| -------- | --------------------------------------------------------------------  |
| `$eq`    | Retorna valores iguais a o valor especificado.                      |
| `$gt`    | Retorna valores maiores que o valor especcficado.                   |
| `$gte`   | Retorna valores que são maiores ou iguais ao valor específico       |
| `$in`    | Retorna dentro de um array, qualquer valor especificado.            |
| `$lt`    | Retorna valores que são menores que o valor especificado.           |
| `$ne`    | Retorna valores que não são iguais ao valor especificado.           |
| `$nin`   | Retorna dentro de um array, valores não iguais ao especificado.     |
| `$lte`   | Retorna valores menores ou iguais ao especificado.                  |

***

## Lógicos

| Name     | Description                                                                            |
| -------- | -------------------------------------------------------------------------------------- |
| `$and`   | Junta duas clausulas (queries) e retorna os documentos que atendem ambas.              |
| `$not`   | Inverte o efeito da query e retorna os documentos que não a atende.                    |
| `$nor`   | Junta duas clausulas (queries) e retorna os documentos que não atende ambas.           |
| `$or`    | Junta duas clausulas (queries) e retorna os documentos que atende ao menos uma delas.  |

***

## Elementos

| Name      | Description                                                                            |
| --------  | -------------------------------------------------------------------------------------- |
| `$exists` | Retorna documentos que tem um campo (propriedade) especificado.                        |
| `$type`   | Retorna documentos em que o campo (propriedade) tem o tipo especificado.               |

***

## Avaliação

| Name     | Description                                                                            |
| -------- | -------------------------------------------------------------------------------------- |
| `$regex` | Retorna os documentos onde os valores atendem uma expressão especificada.              |
| `$text`  | Realiza uma busca de texto.                                                            |
| `$where` | Retorna os documentos que atendem uma expressão em Javascript.                         |

***

## Array

| Name          | Description                                                                            |
| ------------- | -------------------------------------------------------------------------------------- |
| `$all`        | Retorna os documentos que contém todos os elementos especificados.              |
| `$elemMatch`  | Retorna os documentos em que um elemento do array atende as condições especificadas.                                                  |
| `$size`       | Retorna os documentos em que o array é do tamanho especificado.                        |
| `$`           | Retorna o primeiro elemento de um arrai que atende a condição passada.                         |

*** 