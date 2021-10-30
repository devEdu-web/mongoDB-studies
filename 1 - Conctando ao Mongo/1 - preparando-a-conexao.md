# 1.1 Preparando a conexão no Mongo

Existem duas formas de se conectar no MongoDB, utilizando o servidor local que você pode instalar na sua máquina, ou podemos nos conectar através de uma **URI**, utilizando o servidor em nuvem do Mongo. Irei utilizar a segunda abordagem de conexão, por ser um pouco mais prático.

Ao criar uma conta no MongoGB, precisamos criar um **CLUSTER**, é atavés dele que vamos manusear nosso banco de dados. Após criar nosso Cluster, devemos adicionar um usuário e configurar as máquinas que queremos permitir acesso aquele banco de dados, cadastrando o endereço de IP de cada uma. 

> No linux você pode verificar seu IP utilizando `hostname -I` no terminal. No windows, o comando `ipconfig` no CDM deve funcionar.

<br>

![database-user](https://cdn.discordapp.com/attachments/611633543420051458/903998583144079410/unknown.png)
![database-network](https://cdn.discordapp.com/attachments/611633543420051458/903996811700744252/unknown.png)

<br>

Após ter criado nosso usuário e cadastrado nossas máquinas, podemos dar início a nossa conexão. Entrando no seu ***Cluster > Connect > Connect your aplication*** Você irá se deparar com a seguinte tela:
![connection-uri](https://cdn.discordapp.com/attachments/611633543420051458/903998640811544676/unknown.png)

Aqui você irá selecionar a versão do Node que está utilizando e irá copiar a URI. O lugar que está borrado, é o nome do usuário que você cadastrou (censurado por questões de segurança), em seguida temos a senho do mesmo usuário. Para fins didáticos, vamos colocar um usuário e senha representativos:

User: admin <br>
Password: admin123

***

Pronto, agora temos nosso usuário, cadastramos nossa máquina e temos a nossa URI. Agora vamos ver [como fazer a connexão no código](./2%20-%20connectando.md).