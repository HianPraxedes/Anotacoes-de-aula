# Multiplicação

        Ex.: 
                    1000 (multiplicando M)
                *   1011 (multiplicador Q)
                -------------
                    1000
                   1000           # sll Q1 * M,1 (deslocamento a esquerda)
                  0000            # sll Q2 * M,1
                 1000             # sll Q3 * M,1
                -------------
                 1011000          (Produto P)
                  

### Obs.: Não tem * em Assembly

## Para armazenar um: 
- Produto: precisa de um registrador de 64 bits.
- Multiplicando: precisa de um registrador de 64 bits.
- Multiplicador: precisa de um registrador de 32 bits.

## Algoritmo

### Passo 1: 
- Inicialize (P = 0 e contador = 1)
### Passo 2: 
- P = Q0 * M
### Passo 3: 
- Deslocar o M para à esqueda
### Passo 4: 
- Desloque Q à direita. (quando nao mencionado é sempre uma casa)
### Passo 5:
- Se contador = 32, pare. Senão, contador ++ e volte ao Passo 2