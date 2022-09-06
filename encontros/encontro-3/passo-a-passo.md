# Passo a passo

## Model

Até agora a model era apenas um arquivo .json:

```json
//exemplo
[
  {
    "id": 1,
    "user": "Mia",
    "email": "mia@mia.com",
    "pwd": "miasuperfacil123"
  }
] 
```

### Schema/Model

Schema ou model é o nosso modelo de dados, assim podemos mapear o nossa model, exemplo: uma Pessoa, ela possui um nome, sobrenome, uma data de nascimento...

#### Criando o Schema/Model

Quando criamos a nossa Schema, precisamos definir a tipagem da propriedade bem como as regras, existe cenarios que o campo é requirido, que o campo é unico e sucessivamente.

| Tipo       | Definição                           | Exemplo de uso                                                          |
| ---------- | ----------------------------------- | ----------------------------------------------------------------------- |
| **String** | texto                               | para nomes, email, senhas...                                            |
| **Number** | numero                              | para idades, likes, contadores...                                       |
| **Date**   | data                                | data de criação, data de modificação...                                 |
| **Array**  | array que seria equivalente a lista | lista de objetos, como por exemplo: Filmes, Profissão, Comentários, etc |

... e outros tipos do Javascript

Como sabemos, precisamos de user, email e pwd, ficaria assim:

```javascript
// Some code
const mongoose = require('mongoose')

const usuarioSchema = new mongoose.Schema({

  _id: {
    type: mongoose.Types.ObjectId,
    default: mongoose.Types.ObjectId //cria automático e unico como um CPF
  },

  user: {
    type: String, //tipo
    required: true //obrigatório
  },

  email: {
    type: String,
    required: true,
    unique: true //unico
  },

  pwd: {
    type: String,
    required: true
  }
}, { timestamps: true }) //add automaticamente createdAte updatedAt

//exportando nosso Schema ou seja nossa model e criando a collection
module.exports = mongoose.model('usuario', usuarioSchemaav
```

## Controller

A controller estava criando e salvando(simulando) na model.json, agora precisamos salvar na nossa collection do banco de dados, o novoUsuario, documento.

### Importante:

#### uso da palavra reservada `new`

Quando possuímos uma classe, podemos utilizar a palavra reservada `new` para instanciar um objeto, ou seja, construir um novo documento a partir da classe( nossa `Schema` ).

```javascript
// exemplo
new modelUsuario({
      user: user,
      email: email,
      pwd: pwd
})
```

**Métodos relação com a nossa API**

| OPERAÇÃO   | MONGODB            | MOOGOSE                      | DESCRIÇÃO             | HttpCode   |
| ---------- | ------------------ | ---------------------------- | --------------------- | ---------- |
| **C**REATE | **db**.insertOne() | new **ModelUsuario**()       | cria um documento     | 201        |
| Create     | **db**.insertOne() | **novoUsuario**.save         | salva um documento    |            |
| **R**EAD   | **db**.find()      | **ModelUsuario**.find()      | ler um documento      | 200        |
| **U**PDATE | **db**.updateOne() | **ModelUsuario**.updateOne() | atualiza um documento | 200        |
| **D**ELETE | **db**.deleteOne() | **ModelUsuario**.deleteOne() | deleta um documento   | 200 ou 204 |



| OPERAÇÃO   | MONGODB            | MONGOOSE                |
| ---------- | ------------------ | ----------------------- |
| **C**REATE | **db**.insertOne() | **novoUsario**.save()   |
| **R**EAD   | **db**.find()      | **novoUsario**.find()   |
| **U**PDATE | **db**.updateOne() | **novoUsario**.save()   |
| **D**ELETE | **db**.deleteOne() | **novoUsario**.delete() |

### Antes

Antes a nossa controller de usuario estava assim:

```javascript
// Some code
const modelUsuario = require('../models/userModel')

const criarUsuario = (req, res) => {
  const { user, email, pwd } = req.body
  
  //verifica se tem algum campo vazio
  if (!user || !email || !pwd) {
    return res
      .status(400)
      .json({ message: 'Dados inválidos' })
  }

  const novoUsario = {
    user: user,
    email: email,
    pwd: pwd,
  }


  modelUsuario.push(novoUsario)

  res.status(200).send(novoUsario)
};

module.exports = {
  criarUsuario
}avas
```

Além de usarmos async, await e try, catch (veja aqui em [conceitos-importantes.md](../encontro-2/conceitos-importantes.md "mention")), teremos outra mudanças:

\-> Em `const novoUsuario`, vamos usar a palavra reservada `new`, afinal estamos criando um novo `documento`.

```javascript
// Some code
const novoUsario = new ModelUsuario({
      user: user,
      email: email,
      pwd: pwd
})
```

\-> E ao salvar não usaremos o `.push`, já que nossa model não é mais um arquivo.js e sim o **`novoUsuario`**`.save`

```javascript
// Some code
const novoUsarioSave = await novoUsario.save()
```

### Depois

```javascript
// Some code
const ModelUsuario = require('../models/userModel')


const criarUsuario = async (req, res) => {
  const { user, email, pwd } = req.body

  if (!user || !email || !pwd) {
    return res
      .status(400)
      .json({ message: 'Dados inválidos' })
  }

  try {
    const novoUsario = new ModelUsuario({
      user: user,
      email: email,
      pwd: pwd
    })

    const novoUsarioSave = await novoUsario.save()
    res.status(201).json(novoUsarioSave)

  } catch (error) {
    res.status(500).json({ message: error.message })
  }


};

module.exports = {
  criarUsuario,
};
```

### app.js

É preciso incluir o arquivo database

```javascript
// Some code
const db = require('./database/mongooseConnect')
db.connect()jav
```

## Branch

Aqui você encontra a branch dessa tarefa:

{% embed url="https://github.com/rayanepimentel/voluntariamos-back-end/tree/14-conectar-com-banco-de-dados-ray" %}

### Criando um novo usuario

<figure><img src="../../.gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

## Referências:



{% embed url="https://github.com/reprograma/On14-TodasEmTech-s12-BD-Integracao" %}

{% embed url="https://github.com/reprograma/On12-s12-BD" %}

