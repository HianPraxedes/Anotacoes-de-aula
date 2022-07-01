# Intruções  de desvio

### Há duas instruções de desvio

- BEQ: branch if equal
- BNE: branch if not equal
  
-> beq/bne $s0, $s1, label (instruções do tipo I).

Se $s0 == || != $s1 (beq ou bne), desvie para a instruções rotulada por label.

### OBS: Label é so um rótulo (apelido)

# Instruções de comparação

- SLT: Seet on less than
- SLti: eet on less than immediate
  
        EX:
            SLT $t0,$s0,$s1
            -Se $s0 < $s1, $t0 = 1
            -Senão $t0 = 0.
        EX:
            SLTi $t0, $s0, 13
            -Se $s0 < 13, $t0 = 1
            -Senão, $t0 = 0.

        OBS:  SLT => tipo R.
              SLTi: => Tipo I.


# Cai na prova

E a outras comprações:
  - Sabemos ==, != e <
    - Como fazer <=, >= e >

            <= :    1) >
                    2) Se 1 não vale, verdadeiro, senão falso.

                $s0 <= $s1
                SLT $t0, $%s1, $s0 # Se $s1 < $s0 -> $t0=1, senão $t0 = 0
                beq $st0, $zero, verdadeiro

### OBS: Existem as pseudoinstruções: blt, ble, bgt e bge (resp. <, <=, > e >=).

# Desvio incondicional

- J label -> jump p/ label.
  
## Formato tipo J:

op|endereço
-----|--------
6 bits| 26 bits

## Compilando if's

            Código em C
            Ex:     if(i==j){ 
                        f=g+h;
                    else{ 
                        f=g-h;
                    }

                Em mips: (f, g, h, i, j -> $s0 a $s4)

                    beq $s3, $s4, igual
                    sub $s0, $s1 $s2
                    j exit

                igual: add $s0, $s1, $s2
                exit: 

## Compilando laços

        Código em C
        for(i=0,f=0;i<h;i++){
            f=f+i;
        }

        f -> $s0
        h -> $s1
        i -> $t0

        # inicialização

        add $s0, $zero, $zero #f = 0
        add $t0, $zero, $zero #i = 0

        # condição

        loop: slt $t1, $t0, $s1 # i < h?
        beq $t1, $zero, exit
        add $s0, $s0, $t0 #f=f+i
        addi $t0, $t0, 1 #i++
        j loop
        exit:

