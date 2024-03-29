# Listas encadeadas

São utilizadas para armazenar uma coleção de elementos. É uma alternativa a vetores.


Lista | Vetores
--|--
Não contíguo|Contíguo na memória
Acesso O(n)|Acesso O(1)
Inserir um novo elemento O(1)|Inserir um novo elemento O(n)


Dizer que um algoritmo consome tempo O(f(n)), onde f é uma função e n é algo que caracteriza a entrada, significa dizer que o algoriitmo consome no máximo C*f(n) operações, para qualquer n >= n0 onde c>=0 e n>=0

## Funções classicas consideradas

f(n) = 1 <br>
f(n) = lg(n)<br>
f(n) = n<br>
f(n) = n*lg(n)<br>
f(n) = n^k, k>=2<br>
f(n) = k^n, k>=2<br>
f(n) = n^n,n!<br>

### Ex.: Complexidade O(n)

        int maior(int v[], int n){
            int m = v=[0];              //1
            for(int i = 1;i < n; i++){  // 2n-1
                if(v[i]>m){             // n-1
                    m=v[i];             // n-1
                }
            }
            return m;                   // 1
        } 

## Implementação da lista encadeada

        typedef struct no{
            int dado;
            struct no *prox;
        }no;

Lista encadeada| duplamente encadeada
--|--
Simplesmente|anterior e próximo

### Ex:

<div align="center">
	<img src=".././fotos/quadro.jpeg" alt="quadro">
</div>

## Inserção

            void insere(no *p, int x){
                no *novo = malloc(sizeof(no));
                
            }