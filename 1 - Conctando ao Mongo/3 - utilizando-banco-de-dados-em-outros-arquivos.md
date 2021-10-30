# 1.3 Como utilizar seu banco de dados em outro arquivo

Para podermos utilizar o banco de dados o qual nos conectamos, utilizaremos um código parecido com o que usamos para criar a conexão, fazendo algumas modificações.

```javascript

import {MongoClient} from 'mongodb'
const URI = 'mongodb+srv://admin:admin123@cluster0.uco4x.mongodb.net/myFirstDatabase?retryWrites=true&w=majority'

// criando cariável que irá armazenar nosso banco de dados
const db;

const client = new MongoClient(URI)


// Vamos criar uma função que nos conecte ao Mongo
async function criandoConexao() {

    try {
        // Estabilizando uma conexão
        await client.connect() 

        // atribuindo nosso banco a variável
        db = client.db("database_name")
        console.log("Conectado com sucesso")

    } catch (e) {
        
        throw e

    } 
    // finally {
    //     await client.close().
    // }

// Comentaremos o client.close() pois não queremos que a conexão feche após estabelecermos.

}

```

Ao atribuirmos nosso banco de dados a nossa constante, poderíamos simplesmente exportar essa constante. Eu prefiro utilizar uma função para fazer isso, assim podemos executá-lá em outro arquivo. Para isso, adicionaremos ela no final de nosso código:

```javascript

export const getDb = () => {

    if(db) {
        return db
    } else {
        return []
    }

}

```

***

Para utilizar a função em outro arquivo é bastante simples:

```javascript
import * as database from './database.js'


const myDatabase = database.getDb()

console.log(myDatabase)

// Agora você poderá fazer operações no seu banco de dados, utilizando myDatabase.
```