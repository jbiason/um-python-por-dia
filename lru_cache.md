# Cache de funções

Quando você tem uma função que é muito chamada com muita frequência, é possível
fazer cache da mesma, considerando os parâmetros da mesma, usando
`functools.lru_cache`.

```
from functools import lru_cache

@lru_cache()
def get_page(url):
	try:
		with urllib.request.urlopen(url) as content:
			return content.read()
		except urllib.error.HTTPError:
			return 'Not found'
```

Isso irá fazer com que, se você chamar
`get_page('http://python.org/dev/peps/pep-0008/')` de forma seguida, somente a
primeira irá fazer a requisição pela rede; as demais irão vir do cache do
`lru_cache`; uma chamada para
`get_page('http://python.org/dev/peps/pep-0257/')` irá fazer uma nova
requisição, mas apenas uma vez.

Por padrão, `lru_cache` guarda os 128 últimos chamadas com os mesmos
parâmetros; para alterar esse valor, utilize 

```
@lru_cache(max_size=32)
```

Ainda é possível ver qual a taxa de acertos no cache e quantos itens estão no
cache com `.cache_info()`:

```
get_page.cache_info()
```
