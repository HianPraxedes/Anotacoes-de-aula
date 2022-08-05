# Ponto flutuante

Em binário:

5,5 = 101,1

1|0|1|,|1
--|--|--|--|--
2^2|2^1|2^0|,|2^-1

Notação científica: =- F x 10^E na versão normalizada: 1 <= F <= 9 (Fração mantissa signicando)

Em binário: 1,zzz... x*2^yyy...

### Ex.: 

5,5 = 101,1 = 1,011 * 2^2

Representar um número de ponto flutuante  consiste em representar

# Padrão IEEE 754

Um número em ponto flutuante é representado por uma palavra (32 bits) da seguinte forma:

31|30|29|28|27|26|25|24|23|22|21|20|...|6|5|4|3|2|1|0
--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--
0|0|0|0|0|0|0|0|0|0|0|0|...|0|0|0|0|0|0|0

### 31: Sinal (0 = +, 1 = -)
### 30-23: Expoente
### 23-0: Fração

Chamamos essa representação de ponto flutuante de precisão simples.

Há também a representação em precisão dupla

31|30|29|...|20|19|18|...|2|1|0
--|--|--|--|--|--|--|--|--|--|--
0|0|0|...|0|0|0|...|0|0|0

### 31: Sinal
### 30-20 Exp. (11 bits)
### 19-0: Fração
### 32 bits: Fração (Total de 52 bits)

O padrão IEEE 754 estabelece os seguintes casos particulares:

Prec. Simples|Prec. Simples|Prec. Dupla|Prec. Dupla|---
--|--|--|--|--
Exp. |Fração| Exp. |Fração| Representação
0|0|0|0|Zero
0|qualquer coisa !=|0|qualquer coisa !=|Número desnormalizado
1-254|qualquer coisa|1-2046|qualquer coisa|Ponto flutuante (normalizado)
255|0|2047|0|+- Infinito
255|!= 0|2047|!= 0|NaN (Not a Number)

E por que os elementos de um ponto flutuante são representados nessa oedem no binário?

Para facilitar a ordenação

### Obs.: O exp não pode ser representado em complemento a 2.

### Ex.:

5,5 = 101,1 = 1,011 * 2^2 (normalizado)

9,25 = 1001,01 = 1,00101 * 2^3 (normalizado)

5,5 = 0 | 00000010 | 01100000 ... 0000

9,25 = 0 | 00000011 | 00101000 ... 0000

### Ex.: 

0,5 = 0 | 11111111 | 0000 ... 00

Logo, se usarmos complemento a 2 para representar expoentes negativos perdemos a propriendade de que binário ordenados implicam pontos flutuantes ordenados.

Por isso o expoente representado por excesso.

Representção por excesso: defini-se um deslocamento (bias) que somado ao número mais negativo resulte 0.

No nosso caso:

## Precisão simples: 1 a 254, deslocamento = 127
- -126 a 127

## Precisão Dupla: 
- 1 a 2046, deslocamento = 1023
- -1022 a 1023

        (-1)^5 * (1 + Fração)* 2^(E-bias)

                        /127, prec. Spimples
        Sendo, bias =  {
                        \1023, prec. Dupla

Com isso, o menor número representável é

0 | 00000001 | 000...0 = 1,000...0 * 2^-126 = 1,2*10^-38 (underflow)

0 | 11111110 | 1111...11 = 1,11...1*2^127=3,4*10^38

Em precisão dupla:

0 | 00000000001 | 0...0 = 1,00... * 2^-1022
0 | 11111111110 | 1...1 = 1,11... * 2^1023 = 1,8*10^308
