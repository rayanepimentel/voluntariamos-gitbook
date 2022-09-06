# Conectando

## Conectando

{% hint style="info" %}
Faça na sua **branch**
{% endhint %}

\-> No terminal vamos instalar no mongoose e o dotenv

```bash
npm install --save mongoose dotenv
```

\-> Na raiz do projeto vamos criar um arquivo .env

Nesse aquivo, você crie uma variável e coloque a string que acabamos de colar.

```
// exemplo do arquivo .env

DATABASE_URI=mongodb+srv://elasunidas:<password>@teste.vmwj7mg.mongodb.net/?retryWrites=true&w=majority

```

Onde tem \<password> vamos substitiu pela senha que geramos no passo <mark style="background-color:purple;">04-> Escolha a opção</mark> <mark style="background-color:purple;"></mark><mark style="background-color:purple;">**"username and password"**</mark>

Digamos que a senha seja 123456 (só de exemplo, nunca deverá ser uma senha tão fácil!), o arquivo **.env** ficará assim:&#x20;

```
// exemplo do arquivo .env

DATABASE_URI="mongodb+srv://elasunidas:123456@teste.vmwj7mg.mongodb.net/?retryWrites=true&w=majority"

```

\-> Na pasta src, crie uma nova pasta e um novo arquivo .js

![](<../../../.gitbook/assets/image (33).png>)

\-> Dentro do arquivo:

```javascript

require('dotenv').config()
const mongoose = require('mongoose')

// Chamando a string(conexão do nosso banco)
const DATABASE_URI = process.env.DATABASE_URI

const connect = async() => {
   try {
     await mongoose.connect(DATABASE_URI, {
      useNewUrlParser: true,
      useUnifiedTopology: true
     })

     console.log('Banco conectado! ')
   } catch (error) {
    console.error(error)
   }
}

module.exports = { connect }
```



{% hint style="info" %}
Por que instalamos o mongoose e o dotenv? o mongoose veja [aqui](https://cibersistemas.pt/tecnologia/como-usar-mongodb-mongoose-com-node-js-praticas-recomendadas-para-desenvolvedores-de-back-end/) e  [aqui](https://www.freecodecamp.org/portuguese/news/introducao-ao-mongoose-para-mongodb/) e dotenv [aqui](https://blog.rocketseat.com.br/variaveis-ambiente-nodejs/) e [aqui](https://www.freecodecamp.org/portuguese/news/como-usar-variaveis-de-ambiente-do-node-com-um-arquivo-dotenv-para-node-js-e-npm/).
{% endhint %}
