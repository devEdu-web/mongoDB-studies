# 3.1 Exemplos de uso dos seletores de comparação para filtrar os documentos

Antes de apresentar alguns exemplos, vou criar um background para ficar mais fácil entendimento. Imagine os seguintes documentos em uma coleção chamada `inventory`:
```javascript
{ _id: 1, item: { name: "ab", code: "123" }, qty: 15, tags: [ "A", "B", "C" ] }
{ _id: 2, item: { name: "cd", code: "123" }, qty: 20, tags: [ "B" ] }
{ _id: 3, item: { name: "ij", code: "456" }, qty: 25, tags: [ "A", "B" ] }
{ _id: 4, item: { name: "xy", code: "456" }, qty: 30, tags: [ "B", "A" ] }
{ _id: 5, item: { name: "mn", code: "000" }, qty: 20, tags: [ [ "A", "B" ], "C" ] }
```

> Obs: Apesar de grande parte dos exemplos estarem utilizando métodos de busca (find), você pode usar esses operadores para atualizar ou deletar documentos do seu banco de dados.

## Seletores de comparação

### $eq
Valor especificado.
```javascript
db.collection('inventory').find( {qty: {$eq: 20}} ) 
// Retorna os documentos com a quantidade == 20

```

Campo de um objeto dentro do documento igual ao valor especificado.
```javascript
db.collection('inventory').find( {"item.name": {$eq: 'ab'}} )
// Retorna os documentos onde item.name == 'ab'
```

Elementos de um array igual ao valor especificado.
```javascript
db.collection('inventory').find({tags: {$eq: 'B'}})
// Retorna os documentos que que contém a tag 'B' dentro do array
```

***

### $gt
Buscando um documento
```javascript
db.collection('inventory').find( {qty: {$eq: 20}} )

// Retorna os documetnos em que a quantidade é maior que 20.
```

Atualizando documentos 
```javascript
db.collection('inventory').updateOne( {qty: {$gt: 20}}, {$set: {name: 'zz'}} )
// Atualiza o o nome do primeiro documento com a quantidade maior que 20
```

*** 

### $gte

Buscando documentos
```javascript
db.collection('inventory').find({ qty: {$gte: 20} })
// Retorna os documentos em que a quantida é igual ou maior a 20.
```

Atualizando documentos
```javascript
db.collection('iventory').updateOne({qty: {$gte: 15}}, {$set: {name: 'xx'}})
// Atualiza o primeiro documento com a quantidade maior ou igual a 15
```

***

### $in

Buscando documentos
```javascript
db.collection('inventory').find( { qty: { $in: [ 15, 20 ] } } )
// Retorna os documentos em que a quantidade é igual a 15 ou 20
```

***

### $lt

Buscano documentos
```javascript
db.collection('inventory').find( { qty: { $lt: 20 } } )

// Retorna os documentos em que a quantidade é menor que 20
```

*** 

### $lte

Buscando documentos
```javascript
db.collection('inventory').find( { qty: { $lte: 20 } } )

// Retorna os documentos em que a quantidade é menor ou igual a 20
```

***

### $ne

Buscando documentos
```javascript
db.collection('inventory').find( { qty: { $ne: 20 } } )

// Retorna os documentos em que a quantidade NÃO é igual 20
```

***

### $nin

Buscando documentos 
```javascript
db.collection('inventory').find( { qty: { $nin: [15, 20] } } )

// Retorna os documentos em que a quantidade NÃO é igual a 15 e nem 20
```