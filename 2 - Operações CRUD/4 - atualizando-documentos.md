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

<br>

## updateMany

Esse método irá atualizar todos os documentos que atender as especificações que você passar.

```javascript
import * as database from './database.js'
const db = database.getDb()

db.collection('your_collection').updateMany(
    {nome: 'documento'},

    {
        $set: {nome: 'mudado'}
    }
)
.then(result => console.log(result))
.catch(err => console.log(err))

// Utilizando await

const result = await db.collection('your_collection').updateMany(
    {nome: 'documento'},

    {
        $set: {nome: 'mudado'}
    }
)

console.log(result)
```

<br>

## replaceOne()

Esse método é utilizado para substituir um documento de uma coleção, por outro documento.

```javascript
import * as database from './database.js'
const db = database.getDb()

db.collection('your_collection').replaceOne(
    {nome: 'documento'}, // substitui o primeiro documento com o nome = 'documento'

    {
        nome: 'documento-mudade',
        type: 'string',
        isDocument: true
    }
)
.then(result => console.log(result))
.catch(console.log(result))

// Utilizando await

const result = await db.collection('your_collection').replaceOne(
    {nome: 'documento'}, // substitui o primeiro documento com o nome = 'documento'

    {
        nome: 'documento-mudade',
        type: 'string',
        isDocument: true
    }
)

console.log(result)

```