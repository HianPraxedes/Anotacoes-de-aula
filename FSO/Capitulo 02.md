# Capítulo 02

## Estruturas do sistema operacional

- Serviços do sistema operacional 
- Interface 
do sistema operacional do usuário
- Chamadas do 
sistema
- Inicialização do sistema
- Tipos de Chamadas do Sistema
- Programas do sistema 
- Projeto 
e implementação do sistema operacional
- Estrutura do sistema operacional 
- Depuração do sistema operacional 
- Geração do sistema operacional
- Inicialização do sistema

### Objetivos

- Descrever os serviços que um sistema operacional oferece aos usuários, processos e outros sistemas
- Discutir as várias formas de estruturar um sistema
- Explicar como os sistemas operacionais são instalados e personalizados e como inicializam

## Serviços do sistema operacional

- Manipulação do sistema de arquivos
- Comunicações
  - Os processos podem trocar 
informações, no mesmo computador ou entre computadores em uma rede
- Detecção de erros
  - O sistema operacional precisa estar constantemente ciente de possíveis erros
  ### Existe outro conjunto de funções do sistema operacional para garantir a operação eficiente do próprio 

- Alocação de recursos
  - Quando vários usuários ou vários trabalhos são executados 
simultaneamente, os recursos devem ser alocados para cada um deles
- Contabilidade
  - Para acompanhar quais usuários usam quanto e quais tipos de recursos 
do computador
- Proteção e 
segurança
  - Os proprietários das informações armazenadas em um sistema de computador multiusuário ou em rede pode querer controlar o uso dessa informação, processos simultâneos não devem interferir uns com os outros
    -  A proteção envolve garantir que todo o acesso aos recursos do sistema seja controlada
    -  A segurança do sistema contra estranhos requer autenticação do usuário, estende-se à 
defesa de dispositivos externos de I/O contra tentativas de acesso inválidas

## Interface do sistema operacional do usuário - CLI

- CLI significa interface de linha de comando.
- O CLI permite a entrada direta de comandos.
- Pode ser implementado no kernel ou por sistemas de programa.
- Existem vários sabores de CLI, chamados de shells.
- O objetivo principal do CLI é buscar e executar comandos.
- Pode ter comandos integrados ou apenas nomes de programas.
- Adicionar novos recursos não requer modificação do shell em caso de apenas nomes de programas.

## Interface do sistema operacional do usuário - GUI

- GUI significa interface gráfica do usuário.
- É uma interface de metáfora de área de trabalho amigável.
- Geralmente é usado com mouse, teclado e monitor.
- Ícones representam arquivos, programas, ações, etc.
- Vários botões do mouse sobre objetos na interface causam várias ações.
- Foi inventado na Xerox PARC.
- Muitos sistemas agora incluem interfaces CLI e GUI.
- O Microsoft Windows é uma GUI com shell de “comando” CLI.
- O Apple Mac OS X é uma interface GUI “Aqua” com kernel UNIX embaixo e conchas disponíveis.
- Unix e Linux têm CLI com interfaces GUI opcionais (CDE, KDE, GNOME).

## Interfaces de tela sensível ao toque

-  Dispositivos touchscreen requerem 
novas interfaces
   -  Mouse não é possível ou não é desejado
   -  Ações e seleção com base em gestos
   -  Ações e seleção com base em
- Comandos de voz.

## A GUI do Mac OS X
### Chamadas do sistema

- A interface de programação é usada para acessar serviços fornecidos pelo sistema operacional.
- Geralmente é escrita em uma linguagem de alto nível, como C ou C++.
- É acessada principalmente por programas por meio de uma linguagem de alto nível, a API (Application Programming Interface).
- As três APIs mais comuns são a Win32 API para Windows, a POSIX API para sistemas baseados em POSIX (incluindo praticamente todas as versões de UNIX, Linux e Mac OS X) e a API Java para a máquina virtual Java (JVM).
- Os nomes de chamada do sistema usados ao longo do texto são genéricos.

## Exemplo de Chamadas do Sistema

Sequência de chamada do sistema para copiar o conteúdo de um arquivo para outro arquivo