# Arredondamento

Há 4 tipos:

1) Sempre para cima: 2,11 ➝ 2,2
2) Sempre para baixo: 2,11 ➝ 2,1
3) Trucamento, despreza bits menos significativo: 1,01101 = 1,40625, 1,011 = 1,3725
4) Ao mais próximo: 2,11 ➝ 2,1, 2,19 ➝ 2,2

# instruções no MIPS

Há 32 registradores separados noutro co processador para lidar com números de ponto flutuante.

## Os registradores são:

        $f0, $f1, $f2, ... , $f30 e $f31

- Não há registrador reservado para uso especial.
- Para precisão dupla:
  - Registradores de número par. Ex.: Usa-se $f2, instrução ocupa $f2 e $f3.

Há os seguintes tipos de dados:

        (Usar em .data)
        float f1, f2, ..., fn
        double d1, d2, ..., dn

Há também as system calls associadas a ponto flutuante:

Serviço| Cod.| Arg. | Rs
--|--|--|--|
imprimir float|2| $f12|--
imprimir double|3|$f12|--
ler float|6|--|$f0
ler double| 7|--|$f0

As intruções seguem o pardrão:

        Op. prec ➝ precisão E {s,d}
        ↓
        Mnemônico da operação

1) Aritméticas
   - add.s $f2, $f4 ,$f6
     - (add.d) # $f2 = $f4 + $f6
   - sub.s
     -   sub.d
   - mul.s
     - mul.d
   - div.s
     - div.d

2) Acesso à memória
   - l.s $f0, 0 (t2) # carrega
     - l.d
   - mov.s $f0, $f2 # $f0 = $f2
     - mov.d

3) Desvios condicionais
   
   É feito em duas etapas:

a) Comparação entre registradores, salva o resultado num registrador especial.

b) Efetua o desvio baseado no valor de reg. especial.

## Comparação: .d

- c.eq.s $f2, $f4 # =
- c.ne.s          # !=
- c.le.s          # <=
- c.lt.s          # <
- c.ge.s          # >=
- c.gt.s          # >

## Desvio

- bc.1f label
- bc.1t label

### Obs.: 

Precisão simples: 4 bytes
Precisão dupla: 8 bytes

Ex.:

Suponha um vetor de ponto flutuante de precisão dupla com endereço base em $s0. Como carregar o 5º elemento em $f0?

        l.d $f0, 40( $s0 )

Ex.:

Faça um programa para converter a escala de tempoeratura Fahrenheit para Celsius.

        float f2c (floatf) {
            return (5,0/9,0)*(f-320)
        }

        ------------------------------------------------------------------

            .data
        c5: .float 5.0
        c9: .float 9.0
        c32: .float 32.0

            .text

            li $v0,6 # lê um float(retorno em $f0)
            syscall

            l.s $f1, c5
            l.s $f2, c9
            l.s $f3, c32

            sub.s $f0 ,$f0 , $f3 # F-32

            div.s $f4, $f1,$f2 # $f4 = 5/9
            mul.s $f12, $f4, $f0 # f12 ➝ Cº

            li $v0,2 # imprime $f12 na tela
            syscall
