# Dicas para resolver a tarefa

### Mudanças nos arquivos

\-> No **`server.js`** deve ficar apenas o servidor. As nossas rotas serão chamadas no arquivo `app.js`

\-> No **`app.js`** precisamos importar o express e chamar o nosso arquivo que estará dentro da pasta router. Aqui, diferente do usarmos o **app.get**, vamos usa o **app.use** e chamar o nosso arquivo de rota.&#x20;

Agora pare e pesquise pq utilizamos o **app.use** ao invés de **app.get?**

<mark style="background-color:purple;">**Descobriu?**</mark>

→ Na **`models`**, vamos simular um banco de dados utilzando arquivo **.json**, você pode fazer algo assim:

```json
[{
"id": 1,
"chave": "valor"
}] 
```

Onde chave e valor, você coloca o seu contexto. A chave sempre será igual o que foi definido no diagrama e por sua vez, estará igual no banco de dados(por enquanto não temos a integração com BD, será a tarefa da próxima semana).

→ Na pasta **`controller`**, você precisa criar um arquivo **.js** e sempre importar a **models**, afinal as mudanças serão refletidas no nosso banco, que nesse caso é o nosso arquivo**.json**(ele estará dentro da pasta models)

<mark style="background-color:purple;">“Na controller você vai receber(requisição) e enviar uma respostas(response).”</mark>&#x20;

**Pense**:&#x20;

O que eu preciso **receber** para criar um usuario? o meu usuario ele precisa de quer para ser criado? Olhando o nosso diagrama, podemos ter uma ideia.

![](<../../.gitbook/assets/image (21).png>)\


Como eu **recebo** essas informações e como eu **envio ?**

[Aqui](http://gabsferreira.com/o-que-e-o-http-como-funciona-request-respose/) você terá uma ideia de como funciona o request e o response.

Sabendo como funciona, agora você pode continuar.

Agora você cria uma variavel para agrupar essas informações que você recebeu.&#x20;

```
// exemplo

const novoUsuario = {
 chave: valor,
 chave2: valor2
}

// a chave será igual a chave do BD, do diagrama, ex: user
//e o valor é o que você irá receber do request
```

E você precisa enviar esse novo usuário(simular) para o nosso arquivo **.json** (model).&#x20;

**Dica**: aqui você pode usar o **push**, tem um exemplo de como o [push](https://bobbyhadz.com/blog/javascript-push-object-to-array) funciona.

E no final não podemos esquecer de enviar(response) o [status code](https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Status) e o nosso **novousuario.**

****

→ Na **`router`** vamos usar os verbos do http (lembra do get, post, put, delete?)

Precisamos também importar e chamar o arquivo da controller do usuario.

Aqui é importante entender o básico de um roteamento do **express**, você pode verificar [aqui](https://expressjs.com/pt-br/starter/basic-routing.html).

```

app.METHOD(PATH, HANDLER)

Onde:

    app é uma instância do express.
    METHOD é um método de solicitação HTTP.
    PATH é um caminho no servidor.
    HANDLER é a função executada quando a rota é correspondida.

Exemplo:

app.get('/home', controller.funcaoListarUsuarios)

```

**Importante:** Sempre lembre de exportar os seus arquivos, ou você não irá conseguir chama-los em outros lugares do projeto.

[Aqui](https://medium.com/@jonathanjuliani/nodejs-require-exports-module-exports-entenda-de-vez-9297dcd5654f) e [aqui](https://www.alura.com.br/artigos/utilizando-export-modules-no-node-js) tem uma explicação sobre require(), exports & module.exports.

### Olhando a estrutura&#x20;

Agora a estrutura do projeto deve parecer com isso aqui:

![](<../../.gitbook/assets/image (30).png>)

## Como testar:

* Baixe o postman ou insomia
* Rode o projeto: node server

Abra o insomia > new document

Escolha o verbo HTTP post, na url passe o caminho, nesse exemplo o **/criar**, em json passe os **paremêtros** que a controller precisa receber e clique em **send**. Se tuder der certo, você receberar o status 200



![](<../../.gitbook/assets/image (12).png>)
