# 2.1 Adicionando documentos no banco de dados

Para adicionar documentos no MongoDB é relativamente simples, podemos fazer isso utilizando os métodos `insertOne()`, `insertMany()` e `bulkWrite()`.

<br>

> Obs: Todo documento que você isnerir, terá um ID. Você pode adicionar esse ID manualmente, mas caso isso não seja feito, o próprio driver do Mongo irá adicioná-lo. Esse ID é representado por um campo chamado `_id`. É recomendável deixar o driver manusear os ID's, a não ser que você tenha um método que garanta um ID único para cada documento.

***
<br>

Antes de entrarmos em como adicionar um documento, vamos primeiro criar um contexto, para entendermos melhor o nosso código. Já vimos como utilizar nosso banco de dados em outros arquivos, partiremos dessa premissa, utilizando o código que já fizemos anteriormente. Você pode acessá-lo clicando [AQUI](../1%20-%20Conctando%20ao%20Mongo/3%20-%20utilizando-banco-de-dados-em-outros-arquivos.md).

## Inserindo um único documento

```javascript
import * as database from './database.js'
const db = database.getDb()
const doc = {name: 'teste', number: null}



db.collection('your_collection').insertOne(doc)
.then(result => {
    console.log('Documento adicionado com sucesso')
})
.catch(err => {
    console.log(err)
})

// O método insertOne() retorna uma Promise
// Podemos inserir usando o código acima
// Ou usando esse abaixo:

const result = await db.collection('your_collection').insertOne(doc)

```