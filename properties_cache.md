# Atributos cache

No capítulo anterior vimos como é possível definir atributos calculados usando
`@property`. Uma utilização comum dessa funcionalidade é criar atributos
cacheados, da seguinte forma:

```
class Foo:
	def __init__(self):
		self._val = None

	@property
	def val(self):
		if self._val is None:
			self._val = long_process()
		return self._val
```

Dessa forma, quando o atributo for utilizado pela primeira vez, a função
`long_process()` será chamada; a partir desse ponto, será utilizado o valor
encontrado na primeira execução.
