# Ordenação

- Inserção * O(n^2)
- Bolha * O(n^2)
- Shell O(n)
- Contagem O(n)
- Seleção * O(n^2)
- Quicksort O(nlgn)
- Mergesort O(nlgn)
- Heapsort O(nlgn)
- Distribuição O(n)<br>

## Ordenação por inserção

Dado um vetor V[0...n-1] com n elementos.

### Ideia: 
Para cada i de 0 ... n-1 insere v[i] na posição correta do subvetor v[0..i].

### Pior caso:
O elemento retirado é comparado com todos à esquerda. (vetor ordenado em ordem crescente)

            1+2+3+4+...+(n-1) = n/2 * (An+A1) = (n-1)/2 * n

### Melhor caso
O elemento retirado é maior que o antecessor. (vetor ordenado em ordem crescente)

→ O(n)

### Caso médio
→ O(n^2)

            void insercao(int *v, int n){
                for(i = 1; i < n; i++){
                    elem = v[i];
                    for(j = i-1; j >= 0 && v[j] > elem; j--){
                        v[j+1] = v[j];
                        v[j+1] = elem;
                    }
                }
            }

## Ordenação por seleção

### Ideia

Para cada i, de 0 ... n-, selecione o menor elemento do subvetor v[i...n-1]  e insira-o em v[i].

## Estabilidade

Dizemos que um algoritmo de ordenação é estável se ele conserva a ordem relativa de elementos iguais. 

O algoritmo de ordenação por inserção é estável. O de seleção é instável.

