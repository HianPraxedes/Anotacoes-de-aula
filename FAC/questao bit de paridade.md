# Bit de paridade

        # $a0 = 127 = (1)11111111 } 155 na base 10

        bitparidade:
              move $v0, $zero
              
              # $t0: mascara
              # $t1: contador
              # $t9: contador debits 1

              li $st0, 1
              li $t1, 7
              move $t9, $zero
        loop1:  
                beq $t1, $zero, exit1
                and $t2, $t0, $a0               # verifica se ha 1 no i-esiomo bit
                move $t4, $t0                   # Salva a mascara da interaçao
                sll $t0, $t0, 1                 # atualiza a mascara
                addi $t1, $t1, -1               # Atualiza o contador de interaçoes
                bne $t4, $t2, loop1             # Se o resultado do and for diferente, entao nao ha 1 na i-esinma posiçao
                addi $t9, $t9, 1                # Soma 1 no contador de bits 1
                j loop1
        exit1:
                andi $t8, $t9, 1                # verifica se $t9 e par $t8 = 1 se $t9 for impar, O $t9 e par
                beq $t8, $zero, return

                li $v0, 1ori $v1, $a0, 128      #100000000

        return:
                jr $ra