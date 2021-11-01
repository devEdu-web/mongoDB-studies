# 2.2 Apagando documentos no banco de dados

Para deletar documentos de uma coleção podemos utilizar dois métodos: `deleteOne()` para um único documento e `deleteMany()` para múltiplos documentos. Você pode especificar o(s) documento(s) a serem deletados por esses métodos. Vejamos o exemplo:

<br>

## Apagando um documento com deleteOne()

```javascript
import * as database from './database.js'
const db = database.getDb()

const doc = {
    pageViews: {
        $gt: 10,
        $lt: 10000
    }
}

db.collection("your_collection").deleteOne(doc)
.then(result => {
    console.log(result)
})
.catch(err => console.log(err))

// Podemos utilizar o await

const result = await db.collection("your_collection").deleteOne()
console.log(result)
```
> Obs: Se você não entendeu as especificações passadas para o objeto `doc`, entraremos em mais detalhes no final desse arquivo.

## Apagando múltiplos documentos com deleteMany()

```javascript
import * as database from './database.js'
const db = database.getDb()

const query = {
    title: {$regex: "Documento"}
    // Todos os documentos que possui a string "Documento"
}

db.collection("your_collection").deleteMany(query)
.then(result => {
    console.log(result)
})
.catch(err => console.log(err))


// Utilizando o await
const result = await db.collection("your_collecion").deleteMany(query)
console.log(result)
```

## Apagando todos os documentos de uma collection

Para realizar essa operação, podemos utilizar o `deleteMany()`, mas por razões de performance é aconselhável que se utilize o `drop()`.

```javascript
import * as database from './database.js'
const db = database.getDb()

db.collection("your_collection").drop()
.then(result => {
    console.log(result)
})
.catch(err => console.log(err))
```

Dessa forma você irá dropar a collection, ***removendo-a permanentemente do seu banco de dados***.

***

[Clique aqui para ver os seletores queries para filtrar suas buscas ao deletar, atualizar ou buscar um documento](3%20-%20seletores-querie.md)