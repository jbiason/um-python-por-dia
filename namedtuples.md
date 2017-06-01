# NamedTuples

NamedTuples são tuplas (que são aquelas listas com `(valor, valor)` que não
deixa mexer nos dados) com nomes pros campos.

Elas se aproximam um bocado de objetos (mais sobre isso amanhã) no
funcionamento, só mudando a criação.

O primeiro elemento é o nome do namedtuple, e depois vem uma lista de campos
que a tupla vai ter.  Para criar um namedtuple, é preciso fazer:

```
from collections import namedtuple

Obj = namedtuple('Obj', ['field1', 'field2', 'field3']
```

Depois, pra usar: 

```
tupla = Obj(field1='val1', field2='val2', field3='val3')
```

Como o `namedtuple` não injeta as coisas diretamente no escopo atual, é preciso
associar a um nome, e normalmente se usa o próprio nome da tupla.

"Mas qual a vantagem disso?" você deve estar se perguntando. A vantagem é que,
na hora de imprimir o namedtuple, ele vai imprimir exatamente os campos da
tupla, ao invés de simplesmente `('val1', 'val2', 'val3')`. E para acessar os
elementos, ao invés de usar `tupla[0]`, pode ser usado `tupla.field1`.
