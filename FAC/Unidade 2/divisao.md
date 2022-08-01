# Algoritmo de Divisão

            Dividendo
            100101000 / 1000 → Divisor
            1000        100101 → Quociente
               1010
                 1000
                    0
                     → Resto
---------------------------------------------------------------

            
            100101000 / 1000 
            1001        000100101
               1010   
                 1000
                    0 


- Divisor (D): 64
- Resto (R): 64
- Quociente (Q): 32

## Passo 1

R = D, contador = 1

## Passo 2

R = R - D

## Passo 3

Desloque Q à esqueda

1) Se R >= 0, Q[0] = 1
2) Se R < 0, restaure o valor original de R

## Passo 4

Desloqeu D à direita

Passo 5 Se contador < 33, contador ++ e volte ao Passo 2

            0111 / 0010
       0010 0000   0001
       0001 0000
       0000 1000
       0000 0100
       0000 0011

        Divisor: 0010 0000
        (8 bits)
        Resto: 0000 0111
        (8 bits)

It.|Descrição|Quoc.| Divisor|Resto
---|---|---|---|---
0|Inicializ.|0000|0010 0000|0000 0111
1| R = R - D| 0000| 0010 0000| < 0
--|srl D|0000|0001 0000|0000 0111
2| R = R-D|0000| 0000 1000| < 0
--| srl D|0000| 0000 0100| 0000 0111
3| R = R - D| 0000| 0000 1000| < 0
--|srl D|0000|0000 0100| 0000 0111
4|R = R - D|0000| 0000 0100| 0000 0011
--| Q[0] = 1, srl D|0001|0000 0010|0000 0011
5|sll Q, R = R - D| 0010|0000 0010|0000 0001
--|Q[0] = 1, srl D|0011|0000 0001| 0000 0001