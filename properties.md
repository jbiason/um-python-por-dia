# Properties

Quando é criada uma classe, ela aceita que as propriedades sejam sempre
públicas.

```
class Foo:
	def __init__(self, val):
		self.val = val
```

... cria uma classe com um atributo pública `val` que qualquer um pode
alterar. Isso pode parecer estranho se você estiver vindo de linguagens que
utilizem "setters" e "getters". Nesses casos, seria criada uma classe da
seguinte forma:

```
class Foo:
	def __init__(self, val):
		self._val = val

	def get_val(self):
		return self._val

	def set_val(self, value):
		self._val = value
```

Entretanto, `_val` ainda não é um atributo privado, apenas oculto. Qualquer um
poderia acessar `_val` e não seria barrado.

Entretanto, se acontecer de ser necessário um processamento do atributo (como é
feito em setters e/ou getters), é possível utilizar o decorator `@property`
para definir um atributo calculado.

```
class Foo:
	def __init__(self, val):
		self._val = val

	@property
	def val(self):
		return self._val * 2
```

Aqui, o atributo `val` agora é calculado, mas seu acesso continua como se fosse
um atributo normal.

```
foo = Foo(4)
foo.val		# retorna 8
```

A questão agora é que, como é um atributo calculado, ele não pode ser definido.

```
foo.val = 5

AttributeError: can't set attribute
```

Entretanto, é possível também definir o setter do atributo. Para isso, usa-se
também um decorator, mas dessa vez usando o nome do atributo seguido de `.setter`:

```
class Foo:
	def __init__(self, val):
		self._val = val

	@property
	def val(self):
		return self._val * 2

	@val.setter
	def val(self, val):
		self._val = val / 2
```

PS: Ao contrário de outras linguagens que partem imeditamente do uso de getters
e setters para o caso de, no futuro, ser necessário adicionar algum
processamento nos atributos ou evitar que atributos sejam atributos, Python
parte do princípio que tudo é aberto inicialmente e, quando necessário,
atributos sejam bloqueados/alterados. Por isso, não comece colocando tudo como
`@property`; coloque atributos calculados apenas quando for necessário.
