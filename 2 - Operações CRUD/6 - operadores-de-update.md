# 2.6 Operadores utilizados na atualização de documentos

| Name           | Description |
| -------------- | ----------- |
| `$currentDate` | Define a data atual no campo especificado.                     |
| `$inc`         | Incrementa o valor do campo com a quantidade especificada      |
| `$min`         | Apenas atualiza o campo se o valor especificado é menor que o valor que está no campo.        |
| `$max`         | Apenas atualiza o campo se o valor especificado for maior que o valor que está no campo.        |
| `$mul`         | Multiplica o valor do campo pela quantidade especificada        |
| `$rename`      | Renomeia um campo.        |
| `$set`         | Define o valor de um campo em um documento.        |
| `$setOnInsert` | Define o valor de um campo se uma atualização resultar na inserção de um documento. Não possui efeito em operações que modifica documentos existentes.        |
| `$unset`         | Remove o campo especificado de um documento.       |
