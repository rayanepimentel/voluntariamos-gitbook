# Tarefa: Criar evento

### Atividade para serem desenvolvidas:

No diagrama será a parte `"criar evento"`

Vai ser necessário atualizar o arquivo de rotas, o arquivo da controller e da models.

\-> Na **rotas**, será necessário criar uma nova rota.

\-> Na **controller** é necessário pesquisar pelo id do usuario/conta, para saber se o usuario existe e se existir, incluir o evento.

\-> Na **models** o evento precisa desses campos:

```
// models
eventos[{
 nomeEvento
  tipo
  local: {
    cidade
    estado
  }
  data
  turnoHoras
  recorrente
  linkInscricao
  label
}]
```



<figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

### Referências

{% embed url="https://stackoverflow.com/questions/33049707/push-items-into-mongo-array-via-mongoose" %}

{% embed url="https://www.mongodb.com/docs/manual/reference/operator/update/push/#up._S_push" %}
