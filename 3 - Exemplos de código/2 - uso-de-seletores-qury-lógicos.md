# 3.2 Exemplos de uso dos seletores lógicos para filtrar documentos

Antes de apresentar alguns exemplos, vou criar um background para ficar mais fácil entendimento. Imagine os seguintes documentos em uma coleção chamada `inventory`:
```javascript
{ _id: 1, item: { name: "ab", code: "123" }, qty: 15, tags: [ "A", "B", "C" ] }
{ _id: 2, item: { name: "cd", code: "123" }, qty: 20, tags: [ "B" ] }
{ _id: 3, item: { name: "ij", code: "456" }, qty: 25, tags: [ "A", "B" ] }
{ _id: 4, item: { name: "xy", code: "456" }, qty: 30, tags: [ "B", "A" ] }
{ _id: 5, item: { name: "mn", code: "000" }, qty: 20, tags: [ [ "A", "B" ], "C" ] }
```

> Obs: Apesar de grande parte dos exemplos estarem utilizando métodos de busca (find), você pode usar esses operadores para atualizar ou deletar documentos do seu banco de dados.

## Seletores lógicos

### $and

Buscando documentos
```javascript
db.collection('inventory').find( { $and: [ { code: 123 }, { qty: 15 } ] } )

// Retorna os documentos em que o código é igual a 1234 e a quantidade igual a 15
```

***

### $not

Buscando documentos
```javascript
db.collection('inventory').find( {qty: {$not: {$eq: 20}}} )

// Retorna os documentos em que a quantidade não é igual a 20
```

***

### $nor

Buscando documentos
```javascript
db.collection('inventory').find( { $nor: [ { code: 123 }, { qty: 15 } ] } )

// Retorna os documentos em que o código não é 123 e a quantidade não é 15
```

***

### $or

Buscando documentos
```javascript
db.collection('inventory').find( { $or: [ { qty: { $gt: 20 } }, { id: 1 } ] } )

// Retorna os documentos em que ou a quantidade é maior que 20, ou o id é igual a 1
```