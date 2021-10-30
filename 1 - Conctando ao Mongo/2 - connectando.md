# 1.2 Conectando usando o Node

Para nos conectar com o MondoDb, utilizamos o `MogoClient`, que é uma classe que nos permite fazer essa conexão. Para termos acesso a essa classe, precisamos ter o pacote **mongodb** instalado. Para fazer isso, basta executar `npm install mongodb` em seu terminal.

<br>


```javascript

import {MongoClient} from 'mongodb'
const URI = 'mongodb+srv://admin:admin123@cluster0.uco4x.mongodb.net/myFirstDatabase?retryWrites=true&w=majority'

// Criando uma instância chamada client, passando a URI como parâmetro para dizermos qual banco de dados queremos nos conectar.
const client = new MongoClient(URI)


// Vamos criar uma função que nos conecte ao Mongo
async function criandoConexao() {

    try {
        // Estabilizando uma conexão
        await client.connect() // conecta com o mongo
        client.db("database_name") // 
        console.log("Conectado com sucesso")

    } catch (e) {
        // Pegando um possível erro
        throw e

    } finally {
        // Fechando a conexão
        await client.close()


// Obs: Esse trecho de código irá fechar sua conexão assim que ela for feita e a mensagem for logada no console. Seguindo essa abordagem, só é possível fazer operações no banco de dados dentro dessa mesma função. Caso você esteja utilizando uma estrutrua MVC, por exemplo, você não será capaz de fazer operações em seu model, pois a conexão estará fechada.
    }

}

```

Certo, com isso nos conectamos ao MongoDB. Como dito anteriormente, essa abordagem, utilizando o `finally {await client close}` conseguimos apenas fazer operações dentro da própria função que criamos, caso contrário a conexão estará fechada, impossibilitando operações após isso. ***Para resolver isso, podemos simplesmente retirar esse bloco, deixando apenas o `try and catch`.***

Outro problema, que não está aparente, é que não temos acesso ao nosso banco de dados fora da função, o que pode ser problemático, já que geralmente iremos utilizar nosso banco em outros arquivos.
<br>

[Veja como podemos utilizar nosso banco de dados em outros arquivos](3%20-%20utilizando-banco-de-dados-em-outros-arquivos.md)

***