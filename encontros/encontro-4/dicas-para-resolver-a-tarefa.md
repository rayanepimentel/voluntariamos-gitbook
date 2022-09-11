# Dicas para resolver a tarefa

## Controller

Precisamos receber da requisição, o **`_id`** da conta + o objeto **`eventos`**, com os dados do evento.

Aqui você precisa entender a diferença entre **`$set`** e **`$push`**.

\-> **`$set`** [documentação](https://www.mongodb.com/docs/manual/reference/operator/update/set/).

\-> **`$push`** [documentação](https://www.mongodb.com/docs/manual/reference/operator/update/push/).



Precisamos do \_id para encontrar a conta/usuario e depois de encontrado, adicionamos o objeto **evento**.&#x20;

Nós já fizermos algo parecido na tarefa [tarefa-editar-usuario.md](../encontro-3/tarefa-editar-usuario.md "mention")



## Tarefa resolvida

A tarefa tá na branch **`20-criar-eventos-ray`**, antes de verificar aqui, tente resolver a tarefa, se encontrar dificuldade, coloque no grupo do discord :)&#x20;

{% embed url="https://github.com/rayanepimentel/voluntariamos-back-end/tree/20-criar-eventos-ray" %}
