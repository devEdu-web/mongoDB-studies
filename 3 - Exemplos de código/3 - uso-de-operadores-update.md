# 3.3 Usando operadores para atualizar documentos 

## $currentDate
```javascript
db.collection('your_collection').updateOne(

    { _id: 1 },
    {
        $currentDate: {
            lastModified: true,
        }
    }

)

// Atualiza o campo "lastModified" para a data atual, caso não exista, o mongo irá criar um.
```

***

## $inc
```javascript
db.collection('your_collection').updateOne(
    { _id: 1 },
    { $inc: { qty: 2 } }
)

// Incrementa o campo "quantidade" por 2. Você também pode decrementar, colocando valores negativos.
```

***

## $min

Documento a ser atualizado: `{ _id: 1, score: 200 }`.

```javascript
db.collection('your_collection').updateOne(
    { _id: 1 },
    { $min: { score: 150 } }
)

// O valor inicial de "score" é de 200, o valor passado no update é 150 (menor que 200), portanto o valor será atualizado para 150. Se o valor passado fosse maior que 200, ele não seria atualizado
```

***

## $max

Documento a ser atualizado: `{ _id: 1, score: 200 }`

```javascript
db.collection('your_collection').updateOne(
    { _id: 1 },
    { $max: { score: 950 } }
)

// O valor inicial de "score" é 200, o valor passado no update é 950 (maior que 200), portanto o valor será atualizado para 950. Se o valor passado fosse menor que 200, ele não seria atualizado.
```

***

## $mul

```javascript
db.collection('your_collection').updateOne(
    { _id: 1 },
    { $mul: { price: NumberDecimal("1.5"), qty: 2 } }
)

// Multiplica o "price" por 1,25 e a "qty" por 2
```

***

## $rename

```javascript
db.collection('your_collection').updateMany( {}, $rename: { "nmae": "name" } )

// Renomeia todos os campos "nmae" para "name" para todos os documentos na coleção.
```

***

## $set

```javascript
db.collection('your_collection').updateOne(
    { _id: 1 },
    { $set: {
        qty: 100,
        name: 'document'
    } }
)

// Substitui "qty" para 100 e "name" para document no documento de id 1. Caso esses campos não existam, o mongo os cria.
```

***

## $setOnInsert
Se um update com a operação `upsert:true` resulta na inserção de um documento, então `$setOnInsert` atribui os valores especificados para os campos no documento. Se o update não resultar em uma inserção, `$setOnInstert` não faz nada.
```javascript
db.collection('your_collection').updateOne(
    { _id: 1 },
    {
        $set: { item: 'newItem' },
        $setOnInsert: { qty: 100 }
    },
    { upsert: true }
)

// Cria um novo documento com id 1 com os campos especificados

```

***

## $unset

```javascript
db.collection('your_collection').updateOne(
    { _id: 1 },
    { $unset: { quantity: "", instock: "" } }
)

// Remove os campos "quantity" e "instock" no documento de id 1.
```