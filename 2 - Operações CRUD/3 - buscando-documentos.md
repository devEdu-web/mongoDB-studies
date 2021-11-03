# 2.3 Buscando documentos no banco de dados

Os principais métodos usados para buscar dados de seu banco, são: `find()` e `findOne()`. Você também pode especificar informações que você está buscando incluindo parâmetros adicionais ou encadeando métodos como:

 - Sort results 
 - Skip returned results
 - Limit the number of returned results
 - Specify which fields to return

Essas formas de busca de dados serão abordados mais adiante.

***

## Find

O método `find()` é chamado no método `collection`. Este método aceita uma descrição (query) que lhe permite especificar os documentos que está buscando. **Para ver mais sobre os seletores para especificar os documentos que deseja buscar, clique [aqui](4%20-%20seletores-querie.md)**.

O método `find()` retorna uma Promise, que se vocẽ resolver, terá acesso a referência ao `Cursor`, com esse Cursor você poderá navegar nos documentos buscados.


> O `find()` busca múltiplos documentos, sendo possível especificá-los através de queries.


```javascript
import * as database from './database.js'
const db = database.getDb()

const findResult = db.collection('your_collection').find({
    name: 'nome',
    age: {
        $gt: 10,
        $lt: 30
    }
})

// Utilizando o await

await result.forEach(e => console.log(e))


// Tentei executar esse código usando Promises, mas o método find() retorna um Cursor e não uma Promise
```

<br>

## FinOne

Você pode fazer uma busca por um único documento em uma colleção com método `findOne()`. Este método usa uma query para poder retornar apenas os documentos na coleção que atendem a query passada. Se você não passar uma query, será retornado todos os documentos na coleção. 

É importante ressaltar que ele vai retornar apenas o primeiro documento que atende a query especificada, por exemplo, se você está buscando por uma pessoa com o nome "Carlos" e no seu banco de dados tem duas pessoas com esse nome, irá retornar somente a primeira.

> Obs: Esse método retorna uma Promise, diferentemente do `find()` que retorna um Cursor.

```javascript
import * as database from './database.js'
const db = database.getDb()

const query = {title: 'documento'}

db.collection('your_collection').findOne(query)
.then(documento => {
    console.log(documento)
})
.catch(err => console.log(err))

// Utilizando await

const result = await db.collection('your_collection').findOne(query)

console.log(result)
```