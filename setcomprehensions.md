# Set Comprehensions

Quando falei de comprehensions, eu falei de list comprehensions e dict
comprehensions. Tem mais um ainda: set comprehensions. Sets são como listas que
não aceitam itens duplicados. E set comprehensions consegue gerar sets baseados
em processamento de algum iterável.

Um set comprehension funciona exatamente como um list comprehension, mas
utiliza `{` e `}` como delimitadores. E sim, assim como dict comprehensions,
mas sem o `:` no elemento. Por exemplo

```
{record['value'] for record in list_of_dict if len(record['name']) > 10}
```

E como dica final: para converter uma lista para um set, removendo os elementos
duplicados no processo, não é preciso usar um set comprehension; basta usar
`set(list_of_values)`.
