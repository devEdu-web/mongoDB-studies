# 3.1 Exemplos de uso dos seletores para filtrar documentos

Antes de apresentar alguns exemplos, vou criar um background para ficar mais fácil entendimento. Imagine os seguintes documentos em uma coleção chamada `inventory`:
```javascript
{ _id: 1, item: { name: "ab", code: "123" }, qty: 15, tags: [ "A", "B", "C" ] }
{ _id: 2, item: { name: "cd", code: "123" }, qty: 20, tags: [ "B" ] }
{ _id: 3, item: { name: "ij", code: "456" }, qty: 25, tags: [ "A", "B" ] }
{ _id: 4, item: { name: "xy", code: "456" }, qty: 30, tags: [ "B", "A" ] }
{ _id: 5, item: { name: "mn", code: "000" }, qty: 20, tags: [ [ "A", "B" ], "C" ] }
```

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