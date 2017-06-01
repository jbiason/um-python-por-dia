# Generators

Um generator é uma função especial que, cada vez que é chamada, retorna um
valor de uma sequência, ao invés de retornar a sequência inteira.

Por exemplo, quando falou-se de List Comprehensions, toda vez era gerada uma
lista nova.  Com generators, ficaria algo do tipo:

```
(record for record in list_of_values)
```

(Percebam que a sintaxe é bem parecida com list comprehensions, só que se usa
`(` ao invés de `]`).

Para percorrer um generator, é preciso usar uma estrutura que percorra
elementos (como `for`) ou usar `next`. 

Ainda, é possível fazer uma função generator usando `yield`:

```
def func():
	while True:
		value = random.randint(0, 255)
		if value < 127:
			yield value
		else:
			break
```

Essa função vai ficar gerando valores randômicos enquanto o valor randômico for
menor de 127 e depois disso irá encerrar o processamento. Funções generator não
tem return.

(PS: E se não ficou claro: a vantagem de generators é que eles não gera uma
lista inteira de uma vez; à medida que valores são necessários, ele retorna o
valor. Isso normalmente é chamado de "lazy evaluation" porque o valor somente é
processado/recuperado quando necessário, ao invés de retornar tudo de uma vez
só.)
