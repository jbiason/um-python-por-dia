# Slots

Você sabia que Python deixa setar atributos em um objeto, mesmo que o objeto
não tenha esse atributo?

```
class Obj(object):
    pass
```

Isso gera um objeto sem nada dentro. Mesmo que `Obj` não tenha a propriedade
`value`, Python vai deixar adicionar um atributo qualquer, perdido a esmo.

```
o = Obj()
o.value = 'Hello world!'
```

Obviamente, a propria classe/objeto não vai usar esse atributo diretamente, mas
tu pode fazer o que quiser com ele.

Uma forma de "previnir" isso é usar o atributo mágico `__slots__`.

Esse atributo é uma lista de atributos que a classe vai usar. Uma vez definido, nenhum outro atributo pode ser adicionado.

```
>>> class Obj(object):
...    __slots__ = ['val']
... 
>>> o = Obj()
>>> o.value = 1
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AttributeError: 'Obj' object has no attribute 'value'
>>> o.val = 1
```

Outra vantagem de `__slots__` é que como a lista de atributos é fechada, o
tamanho do objeto em memória é menor. Eu pessoalmente nunca vi uma classe com
`__slots__`, mas pode ser útil algum dia.

E, na verdade, eu só falei de `__slots__` por causa de parte esotéria de que qualquer atributo pode ser adicionado a qualquer objeto (desde que não tenha `__slots__`, obviamente). E como funções são representadas internamente como objetos, isso significa que tu pode adicionar coisas malucas a funções. Por exemplo:

```
def fun():
    return 1
fun.value = 'Hello world!'
```

Álias, funções são tão objetos que tu pode extrair informações da função com
suas propriedades. Por exemplo, `fun.__doc__` vai retornar a docstring da
função.No Python 3, `fun.__annotations__` vai trazer um dicionário com os
type-annotations das variáveis (eu explico o que é isso quando entrar em coisas
mais específicas de Python 3).

"Mas quando se usaria slots?" Normalmente, quando tu quer realmente proteger o
objeto pra ninguém adicionar coisas que não deveria estar lá (embora, para o
mundo Python, todo mundo é adulto e sabe o que está fazendo) ou pra reduzir o
tamanho do objeto na memória (quando tu trabalha com muitos objetos ao mesmo
tempo). Então são casos bem específicos, mas eu só comentei de `__slots__` pra
dar seguimento pra ideia de que tu pode largar qualquer atributo em qualquer
objeto, mesmo que não esteja na base do objeto.
