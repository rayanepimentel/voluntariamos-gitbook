# Dicas para resolver a tarefa

## Controller

Sabemos que o usuário pode mudar o **user, email** e **psw**. E que cada conta/usuario tem o **id**, que é único, isso é ótimo porque com o id podemos identificar a conta/usuario.

Ou seja, na requisição teremos essa informação.

Aqui você precisa entender a diferença entre **req.body** e **req.params**. Veja [aqui](https://cursos.alura.com.br/forum/topico-req-params-vs-req-query-159212), [aqui](https://dev.to/gathoni/express-req-params-req-query-and-req-body-4lpc) e [aqui](https://www.digitalocean.com/community/tutorials/nodejs-req-object-in-expressjs)



#### Verificar e atualizar

Precisamos verificar pelo **id** se o usuario/conta existe e se existir podemos alterar com o que recebemos na requisição.

Existe algumas maneiras de fazermos isso. Primeiro veja como é feito no mongoDB sem o mongoose e depois com o mongoose.

MongoDB: [https://medium.com/@rapimentello/mongodb-3f5f4b6ab09e](https://medium.com/@rapimentello/mongodb-3f5f4b6ab09e)

Mongoose: [https://masteringjs.io/tutorials/mongoose/update](https://masteringjs.io/tutorials/mongoose/update)&#x20;



## Router

Aqui é simples, vamos utilizar o verbo http de atualizar, temos o verbo **PUT** ou **PATCH**, qual usar?

Veja aqui: [https://www.geeksforgeeks.org/difference-between-put-and-patch-request/](https://www.geeksforgeeks.org/difference-between-put-and-patch-request/) &#x20;

[https://www.devmedia.com.br/asp-net-web-api-atualizacoes-parciais-com-o-verbo-patch/37531](https://www.devmedia.com.br/asp-net-web-api-atualizacoes-parciais-com-o-verbo-patch/37531)&#x20;

[https://pt.stackoverflow.com/questions/217894/qual-%C3%A9-a-diferen%C3%A7a-entre-o-m%C3%A9todo-put-e-o-patch](https://pt.stackoverflow.com/questions/217894/qual-%C3%A9-a-diferen%C3%A7a-entre-o-m%C3%A9todo-put-e-o-patch) &#x20;

[https://www.devmedia.com.br/http-verbos/41224](https://www.devmedia.com.br/http-verbos/41224)

