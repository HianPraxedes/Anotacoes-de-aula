# Aritmétca Computacional

## Regitradores

- Armazena 32 bits
  
### Operações sobre interios de 32 bits

- Números com sinal
  - Complemento a dois
    - x é um inteiro positivo
      - (2^n)-x, onde n é o tamanho da nossa representação.
  
### Ex.: Num sintema de 4 bits

                                0101 = 5
                         nega   ↓
                                1010
                             +  0001
                              --------------
                                1011 = -5
                                ↓
                                (2^3)+(2^1)+(2^0)=(2^4)-5

## Adição e subtração de binários

                                0111 = 7
                             +  0110 = 6
                             ---------------
                                1101 = 13

## Overflow

### Ex.: Num sistema de 4 bits:

                                    1011 = 11
                                  + 0110 = 6
                                ---------------------
                                    0001 = overflow

## Lidando com o overflow na adição

Operação| Sinal A| Sinal B| Sinal A+B
-----|-----|-----|-----
A+B| >=|>=|<
A+B|<|<|>=
A-B|>=|<|<
A-B|<|>=|>=

Casos em que ocorrem overflow.

### Obs.: Nunca ocorre overflow na soma de inteiros de sinais diferentes (equiv. na subtração de inteiros de sinais iguais).

As instruções add, addi e sub lançam exceção no caso de overflow, enquanto que addu, addiu e subu não lançam exceção.

### Obs.: Exceção é a interrução de um programa.

Para fazer o tratamento (sem insterrupção) de um overflow em assembly MIPS:

1) Calcula a soma usando addu.
2) Se os sinais dos operandos forem iguais: se o sinal do resultado for igual ao sinal do primeiro operando, não há overflow; senão, há overflow.

### EX.: Tratar overflow na soma de $t0 e $t1
        addu $t2, $t0, $t1
        xor $t3, $t0, $t1               # $t3 < 0 se os sinais forem distitos
        slt $t3, $t3, $zero             # Se os sinais são diferentes
        bne $t3, $zero,semOverFlow      # Não há overflow

        xor $t3, $t0, $t2
        slt $t3, $t3, $zero
        bne $t3, $zero, overFlow

### Obs.: Para verificar se o sinal de dois operandos sao diferentes:

        $t0 = 1...\
                    }xor = 1... <0
        $t1 = 0.../

