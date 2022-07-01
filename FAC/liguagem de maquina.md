# Linguagem de maquina

* Binario
* Cada instruçcao é representada por PALAVRAS (32 bts - 4 bytes)

Ha tres padroes de representaçao.

* Tipo R
* Tipo I
* Tipo J

OBS: Pseudointruçoes nao entram nesses padroes.

## Fomato tipo R


 op      | rs          |rt           |shamt             |fund          
---------|-------------|-------------|----------------- |----------------
6 bits   |5 bits    | 5 bits|5 bits| 6 bits

* op: codigo da operaçcao (tabela);
* RS e RT: registradores de origem;
* RD: registrador de destino;
* SHAMt: tamanho do deslocamento (shift  amonut);
* FUNCT: funçao (complementa op);

É o formato padrao das insttruçoes aritmetica e lógica.

EX: add $t0, $s1, $s2

        ↓

 ------      | $s1         |    $s2       |$t0           |------          |------
---------|-------------|-------------|----------------- |----------------|---------
0   |17    | 18|8| 0| 32

                  ↓

00000   |10001    | 10010|01000| 00000| 10000
---------|-------------|-------------|----------------- |----------------|---------
6 bits|5 bits|5 bits|5 bits|5 bits|6 bits

OBS: Por que os campos RS, RT, RD e SHAM possuem 5 bits?

* 32 registradores;
* cada registrdor possui 32 bits (shamt)

## Formato tipo I

 op      | rs          |rt           |constante/endereço                   
---------|-------------|-------------|-----------------
6 bits   |5 bits    | 5 bits|16 bits

* op: cód. operaçao
* rs: registro de origem
* rt: origem/destino
* Intruções imediatas e de acesso á memória

EX: addi $t0, $t0, $s0,3

                 ↓

 --------      | $s0        |    $to       |--------          
---------|-------------|-------------|----------------- 
1   |16    | 8|3 
6 bits|5 bits|5 bits|16 bits

                       ↓


000001 |10000    | 01000|0000000000000001
---------|-------------|-------------|----------------- 

Obs: Ultimo campo possui capacidade de -2^15 a 2^-1.

## E se precisarmos de mais?

* CONSTANTE: O assembler divide a intruçcao em mais de uma.
* e quando foi acesso a memoria?
* w $s0,0( $s3)

Em 8GB da RAM, quantas posiçoes possui a memoria

8 GiB = 2^3 GiB

------ = 2^3*2^30 B

------ = 2^33 B

1) Offset representa palavras, e nao bytes.

2) Deslocamento relativo -> base + offset

##  Operações lógicas

### Deslocamento

* à esquerda: sll (shift left logical);
* à direita: srl (shift right logical);

EX: sll $t0, $t0,2 (shamt=2)

$t0 = 000...01001 (sll2)-> 000...100100

0101 (sll 1) -> 01010 portanto Cada shift a esquerda corresponde a multiçlicar por 2.

0101 (srl 1) -> 0010 portanto Cada deslocamento a direita corresponde a dividir por 2 (inteiro)

OBS: Sll r Srl são as unicas instruções do tiponn R que operam sobre dois registradores  e uma constante (usa o campo shamt para contanttes).

### E,ou,não

* and/andi
* or/ori
* nor (ou, não)

Ex: nor $t0, $s0, $s1

$t0 = Não ( $s0 ou $s1)

### Para negar um reg.

* nor $t0, $s0, $s0
* nor $t0, $s0, $zero

Instruções lógicas são úteis para implementar MÁSCARAS.

Ex: Extrair o segundo bit  do $t0.

    0  |  0  | 0  | ... | 0 | 1 | 1   $t0 (and)
    0  |  0  | 0  | ... | 0 | 1 | 0
    -----------------------------
    0 | 0 | 0 | ... | 0 | 1 | 0

Ex: Incluir bits na quarta posição

    $t0 = 0000...100101 (or)
          0000...001000
          -------------
          0000...101101