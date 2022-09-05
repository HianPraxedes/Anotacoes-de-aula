# Hierarquia de memória

Memória: unidade persistente para armazenamento de dados de usuário e software.

- acesso aos dados consome o maior tempo
- +rapida => + cara (preço monetário)

A memória trabalha de acordo com dois principios de localidade:

- temporal: um dado acessado tende a ser acessado novamente em breve.
- Espacial: se um dado foi acessado, dados proximos dever ser acessados em breve.

Esses pricipios sugem uma organização hierárquica da memória

                            Processador

                            ^         ^
                           /1\        |
                          / 2 \       |
                         /  3  \      | + rapida
                        /  ...  \     |
                       /    n    \    |
                     <-------------->
                         tamanho

cache <- ram <- disco

Os níveis hierárquicos são divididos de tal forma que:

- o custo beneficio seja o mesmo nos níveis
- a memoria mais rápida fique mais próxima ao processador

# Conceito

- Os dados são mantidos no nível mais baixo, e as cópias são feitas apenas entre níveis adjacentes.
-  o processador acessa dados apenas do nível mais alto.
-  se um dado requisitado estiver no nível mais alto, dizemos que houve um acerto. Caso contrário, houve uma falha.
-   Taxa de acerto (taxa de falha) é a fração de acessos que resultaram em acerto (falha).
-   Tempo de acerto (penalidade de falha) é o tempo para acessar um dado quando houve acerto (falha).
-   
