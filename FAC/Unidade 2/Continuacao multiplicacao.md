# Continuação de multiplicação

                            1000
                         X  1011 
                        _____________
                            1000
                           10000
                          000000
                         1000000
                        _____________
                         1011000


### Método para fazer multiplicação

1) Faz a a primeira multiplicação
2) Guarda o resultado e da um shift para a direita
3) Faz a soma com a próxima multiplicação e da um shift para a direita
   

                        0110
                     X  1101
                     __________

-----|-----|-----|-----|-----|-----|-----|-----
-----|-----|-----|-----|-----|-----|-----|-----
0|1|1|0|0|0|0|0
0|0|1|1|0|0|0|0
0|1|1|1|1|0|0|0
1|0|0|1|1|1|0|0
0|1|0|0|1|1|1|0

# Algoritmo de multiplicação (Otimizado)

Dados: M e Q. Saída: P[63...0]

                    M (multiplicando)
                 X  Q (multiplicador)
                 _____________________
                    P (produto)

1) Inicialize P[63...32] = 0 (Zerar tudo) e P[31..0] = Q
2) Se P[0] = 1, P[63...32] += M
3) Desloque P à direita
4) Se não for a 32ª repetição, volte ao passo 2

## Cai na prova similação de interações no algoritimo de multiplicação

            M = 0110, Q = 1101, P = 01001110

Interação | Descrição |  P
----|----|----
0|Inicialização|00001101
1|P[7...4(63...32)] += M |01101101
---|srl P # move para a direita|00110110
2|manter P|00110110
---|srl P|00011011
3|P[7...4(63...32)] += M|01111011
---|srl P|00111101
4|P[7...4(63..32)] += M|10011101
---|srl P|01001110

### Obs.: Como o exemplo é de multiplicação de númros de 4 bits, são usados os registradores extra de 7 ate 4, o nomrla é de 63 ate 32.

### Obs.: Esse algoritmo so serve para numeros positivos

## Para o caso com sinal

1) Armazene os sinais dos operandos e transforme-os em positivos
2) rode  o algoritmo
3) Se os sinais dos operandos eram diferentes, negue o produto. (complemento de 2)
   
## Instruções MIPS

mult reg1, reg2
- calcula reg1 x reg2
  - Salva o produto num par de registradores especiais chamados lo e hi.
- mflo reg: copia o conteúdo do lo para reg
- mfhi reg: copia o conteúdo do hi para reg
- mtlo reg: Escreve o conteúdo de reg em lo
- mthi reg: Escreve o conteúdo de reg em hi
