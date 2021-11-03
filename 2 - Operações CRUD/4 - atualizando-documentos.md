# 2.4 Atualizando documentos no banco de dados

Antes de atualizar um documento, devemos saber que o Mongo disponibiliza alguns **operadores de atualização** para modificar os valores dos campos, como por exemplo o operador `$set`. Alguns métodos irão criar o campo que está sendo alterado caso ele não exista.

> Você irá encontrar o link para esses operadores no final desse arquivo.

Forma do documento atualizado:

```javascript
{
  <update operator>: { <field1>: <value1>, ... },
  <update operator>: { <field2>: <value2>, ... },
  ...
}
```

***

## updateOne

Esse método irá atualizar o primeiro documento que atende a especificação que você passar, por exemplo, se você quer atualizar um documento onde o `nome` equivale a `exemplo` e tiver mais de um documento com esse nome, ele irá atualizar o primeiro.

```javascript
import * as database from './database.js'
const db = database.getDb()

db.collection('your_collection').updateOne(
    {id: 0}, // atualizar o primeiro documento que atende essa condição

    {
        $set: {id: 1, nome: 'mudado'}
        // muda o id para "1" e o nome para "mudado"
    }
)
.then(result => console.log(result))
.catch(err => console.log(err))

// utilizando o await

const result = await db.collection('your_collection').updateOne(
    {id: 0}, // atualizar o primeiro documento que atende essa condição

    {
        $set: {id: 1, nome: 'mudado'}
        // muda o id para "1" e o nome para "mudado"
    }
)

console.log(result)

```