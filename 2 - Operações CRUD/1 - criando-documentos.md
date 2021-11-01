# 2.1 Adicionando documentos no banco de dados

Para adicionar documentos no MongoDB é relativamente simples, podemos fazer isso utilizando os métodos `insertOne()`, `insertMany()` e `bulkWrite()`.


<br>

> Obs: Todo documento que você isnerir, terá um ID. Você pode adicionar esse ID manualmente, mas caso isso não seja feito, o próprio driver do Mongo irá adicioná-lo. Esse ID é representado por um campo chamado `_id`. É recomendável deixar o driver manusear os ID's, a não ser que você tenha um método que garanta um ID único para cada documento.

***
<br>

Antes de entrarmos em como adicionar um documento, vamos primeiro criar um contexto, para entendermos melhor o nosso código. Já vimos como utilizar nosso banco de dados em outros arquivos, partiremos dessa premissa, utilizando o código que já fizemos anteriormente. Você pode acessá-lo clicando [AQUI](../1%20-%20Conctando%20ao%20Mongo/3%20-%20utilizando-banco-de-dados-em-outros-arquivos.md).
<br><br>
## Inserindo um único documento
Inserimos um documento com o método `insertOne()`. Esse método nos retorna um `InsertOneResult`, que representa o ID do documento inserido.

```javascript
import * as database from './database.js'
const db = database.getDb()
const doc = {name: 'documento', number: null}



db.collection('your_collection').insertOne(doc)
.then(result => {
    console.log('Documento com o id ${result.insertedId} adicionado com sucesso')
})
.catch(err => {
    console.log(err)
})

// O método insertOne() retorna uma Promise
// Podemos inserir usando o código acima
// Ou usando esse abaixo:

const result = await db.collection('your_collection').insertOne(doc)
const insertedId = result.insertedId

console.log('Documento com o id ${result.insertedId adicionado com sucesso')

```

## Inserindo múltiplos documentos
Inserimos múltiplos documentod com o método `insertMany()`.

```javascript
import * as database from './database.js'
const db = database.getDb()
const docs = [
    {name: 'documento1'},
    {name: 'documento2'},
    {name: 'documento3'},
    {name: 'documento4'}
]

db.collection('your_collection').insertMany(docs)
.then(result) => {
    console.log(`Documento com o id ${result.insertedId} adicionado com sucesso`)
}
.catch(err => console.log(err))
// O método insertMany() retorna uma Promise
// Podemos inserir usando o código acima
// Ou usando esse abaixo:

const result = await db.collection('your_collection').insertMany(docs)
const insertedId = result.insertedId
console.log(`Documento com o id ${result.insertedId adicionado com sucesso`)
```

***

## Possíveis erros

Alguns erros podem ocorrer quando estivermos tentando adicionar vários documentos. Alguns erros ocorrem quando descuidadosamente tentamos inserir documentos com o mesmo `_id`. Vamos analisar o código abaixo: 

```javascript
try {
    const docs = [
        {id: 1, name: 'documento1'},
        {id: 2, name: 'documento2'},
        {id: 1, name: 'documento3'},
        {id: 3, name: 'documento4'}
        // Vemos que temos dois id's "1".
    ]

    const result = await collection("your_collection").insertMany(docs)
    let ids = result.insertedIds

    for(let id of Object.values(ids) {
        console.log(`O documento com id ${id} foi inserido`)
    })

} catch(e) {
    console.log('Houve um erro')
    let ids = e.result.result.insertedIds
    for (let id of Object.values(ids)) {
        console.log(`Processado o documento com id ${id}`)
    }

    console.log(`Numero de documentos inseridos: ${e.result.result.insertedCount}`)

}
```

Se rodar esse código, verá a seguinte mensagem no terminal: 

```
Houve um erro
Processado o documento com id 1
Processado o documento com id 2
Processado o documento com id 1
Processado o documento com id 3
Número de documentos inseridos: 2
```

Na sua coleção, verá os seguintes documentos inseridos:

```javascript
{"_id": 1, "name": "documento1"}
{"_id": 2, "name": "documento2"}
```

A princípio pensamos que iria inserir os documentos de `id 1, 2 e 3 (documento1, documento2 e documento4) respectivamente`, descartando o documento3, que tinha o id repetido. Porém quando o Mongo chega nesse arquivo de Id repetido, ele simplesmente encerra o processo de inserção.

***
<br>

## Propriedades derivadas dos métodos de inserção

| insertOne()     | insertMany()    | Definição                                     |        
| -----------     | -----------     | -----------                                   |
| insertedId      | insertedIds     |  Mostra o Id dos documentos inseridos         |
| -               | insertedCount   | Mostra a quantidade de documentos             |
