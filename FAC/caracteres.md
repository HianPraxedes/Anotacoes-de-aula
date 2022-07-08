## Última questão da lista

            li $t0, 1
            loop and $t1, $t0, $a0
                 beq $t0, $t1, soma
                 slt $t0, $t0, 1
                 j loop
            soma: addi $t3, $t3, 1
                 j loop
    ==================================================================
        Para acabar o código
             li $v0, 10
             syscall

## Caracteres

- Conjunto especial tabelado
  - ASCII (1 caracter -> 1 número (8 bits))
  - Unicode

## Instruções

- lb offset (base)

- sb reg, offset (base)

          EX.: Código C

               void strcpy(char *x, char *y){
                    int i = 0;
                    do{
                         x[i] = y[i];
                         i++;
                    }while(y[i] != '\0');
                    
               }

## End. de x e y em $a0 e $a1

          strcpy:
               add $t0, $zero, $zero # $t0: end de x[0]
               add $t1, $a1, $zero # $t1: end de y[0]
          loop: 
               lbu $t2, 0($t1) # $t2 = y[i]
               sb $t2, 0($t0) #x[i] = y[i]
               addi $t0, $t0, 1
               addi $t1, $t1, 1
               bne $t2, $zero, loop
               jr $ra
       
     
## Constantes de 32 bits

### Forato do tipo I

op    | rs    |rt    |const
------|-------|------|-----
6 bits| 5 bits|5 bits| 16 bits

### Como armazenar uma constante com mais de 16 bits?

### Ex.: Queremos armazenar 4.000.000

31|30|29|28|27|26|25|24|23|22|21|20|19|18|17|16|15|14|13|12|11|10|9|8|7|6|5|4|3|2|1|0
-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|-----|
0|0|0|0|0|0|0|0|0|0|1|1|1|1|0|1|0|0|0|0|1|0|0|1|0|0|0|0|0|0|0|0

- Do 0 até o 15 = 2304
- Do 16 até o 31 = 61

          1) addi $s0, $zer0, 61
             sll $s0, $s0, 16
             addi $s0, $s0, 2304
          
          2) lui $s0, 61
             addi $s0, $s0, 2304

- lui: Pseudinstrução
