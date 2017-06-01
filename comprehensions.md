# Comprehensions

List comprehensions são utilizadas para gerar uma nova lista a partir de algo
iterável (onde "iterável" é qualquer coisa que possa ser percorrido, como
listas, dicionários, sets, tuplas e strings).

Em sua forma mais simples, list comprehensions é gerado com:

```
[record for record in other_list]
```

... onde:

* O primeiro `record` é o que vai ser utilizado como elemento da lista;

* O segundo `record` é o elemento que vai ser extraído da lista;

* `other_list` é o iterável que vai ser percorrido.

```
[record['item'] for record in list_of_dicts]
```

No caso acima, será percorrida uma lista de dicionários, onde cada registro
dessa lista será tradado com `record` e, deste `record`, será extraído o
elemento "item".

Também é possível filtrar elementos durante a geração da nova lista:

```
[record for record in other_list if record < 4]
```

Irá gerar uma nova lista a partir dos elementos de `other_list`, mas apenas
cujo valor for menor que 4.

Além de list comprehensions, existe ainda dictionary comprehensions:

```
[{record['key']: record['value'] for record in list_of_dicts}
``````

... vai gerar um dicionário pegando a chave 'key' de list_of_dicts que vai
servir de chave e 'value' para ser o valor do dicionário.
