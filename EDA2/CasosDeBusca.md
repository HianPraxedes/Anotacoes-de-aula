Quando compensa ordenar para fazer buscas?

Ordenar + buscar = O(nlgn + lgn)

O(nlgn) + O(lgn) = O((n+1)lgn)

Busca sequencial = O(n)

Portanto, para uma única busca, não compensa ordenar.

Por outro lado, se a quantidade de buscar for grande (into é, muito mais que n busca) compesa, pois:

Ordenar + n buscas = O(nlgn)

O(nlgn) + n*O(lgn)

Por outro lado

n buscas sequenciais

n*O(n) = O(n²)

Consideremos o problema dos números proibidos

- Temos uma lista com n números proibidos (n <= 140000) dada na entrada
- Cada número varia entre 1 e 2³¹
- Para cada consulta, deseja classificar o número se proibido ou não.

Solução 1: Salvo os números proibidos num vetor de tamanho n e para cada consulta, faça um busca sequencial **Custo: O(m*n)**

- Custo elevado se forem muitas buscas
  
Solução 2: Ordenar e buscar **O(nlgn) + O(nlgn) = O((n+m)lgn)**

- Bom se tiver muitas buscas

Solução 3: **O(m+n-)**

- Declara um vetor v comm 2³¹ elementos e zero o vetor
- Para cada número proibido i, define v[i] = 1 * O(n)
- Para cada busca com número k, se v[j] = 0, então o número não é proibido, se v[j] = 1, o número j é proibido. O(m)

**Custo total = O(1)+O(n)+O(n+m)**

<div align="center">
	<img src="./fotos/quadro4.jpeg" alt="quadro">
</div>