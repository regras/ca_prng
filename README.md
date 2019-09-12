# ca_prng

Autômato Celular

Autômatos Celulares (AC) são sistemas dinâmicos, com tempo e espaço discretos que, a partir de simples iterações e computações, podem exibir comportamentos complexo. Um AC consiste de um conjunto de células que podem ser organizadas em um espaço n-dimensional, com um número finito de estados, os quais variam com a aplicação de regras determinísticas.
Mais detalhes sobre esse assunto, podem ser encontrados na dissertação de mestrado “AVALIAÇÃO DE GERADORES DE NÚMEROS PSEUDOALEATÓRIOS BASEADOS EM AUTÔMATOS CELULARES NÃO ELEMENTARES”  de Sílvia R. L. Magossi, disponível no repositório digital da Unicamp em http://repositorio.unicamp.br/

Objetivo

Foram utilizados programas desenvolvidos em Python (versão 2.7.12 SO Ubuntu 16.04.3 LTS VM) durante o trabalho de mestrado, a fim de produzir sequências binárias aleatórias a partir de ACs. Os ACs e a produção das sequências binárias, podem ser empregadas como um Gerador de Números Aleatórios.

Uso

Os programas devem ser copiados/salvos em pastas do seu sistema operacional. Eles produzem dados que são armazenados em arquivos binários (cujo nome do arquivo se encontra no próprio código), são necessários 12.500.000 bytes de espaço em disco, para cada programa executado, no final ele armazena 10^8 bits, e todas as informações e parâmetros necessários para executar, estão embutidas no código dos programas, uma explanação é feita nas linhas a seguir.
Para executar os programas, é necessário digitar na linha de comando (Linux): python nome_do_programa.py. Após, o programa é executado até produzir 10^8 bits, armazena em arquivo esses bits, e termina o processamento.

Abaixo temos os nomes dos programas com uma breve descrição de cada um, a coleta dos programas a seguir é feita por linha, plano e coluna central.

Programa    |	Descrição do AC e Tipo de Coleta
------------|-------------------------------------------------------------------
AC_R30      |  AC Raio 1 - unidimensional regra 30 - coleta por linha
AC_R4405    |  AC Raio 2 - unidimensional regra 1436194405, coleta por linha
AC_R8345    |  AC Raio 1 - bidimensional regra 1453938345, coleta por plano
AC_R30col   |  AC Raio 1 - unidimensional regra 30, coleta coluna central
AC_R4405col |  AC Raio 2 - unidimensional regra 1436194405, coleta coluna central
AC_R8345col |  AC Raio 1 - bidimensional regra 1453938345, ccoleta coluna central
AC90_150H   |  AC 90/150 Híbrido coleta por linha
AC90_150Hcol|  AC 90/150 Híbrido coleta por coluna central


Programas para coleta de 50% (1/2) dos bits

AC_R8345_50	AC Raio 1 – bidimensional regra 1453938345, coleta 50%. 

Foram criadas 4 versões para coleta de ½ dos bits de um plano, considerando que é possível acessar esses bits de várias formas, alteramos os laços de psição e a variação de um dos laço, essa alteração acontece saltando duas linhas ou duas colunas.

Programa       |   Descrição do AC e Tipo de Coleta
---------------|--------------------------------------------------------------------
AC_R8345_50v1	 | AC Raio 1 – bidimensional regra 1453938345, variação coluna1linha2
AC_R8345_50v2  | AC Raio 1 – bidimensional regra 1453938345, variação linha2coluna1
AC_R8345_50v3  | AC Raio 1 – bidimensional regra 1453938345, variação linha1coluna2
AC_R8345_50v4	 | AC Raio 1 – bidimensional regra 1453938345, variaçao coluna2linha1


Além das versões acima, existem mais 4 versões para a coleta na diagonal. Essas coletas se preocupam com o eixo, x e y , ou seja, a coleta pode ser no sentido horizontal, começando na posição [0,0] ou posição [0,1], ou no sentido vertical, começando na posição [0,0] ou na posição [0,1]. As versões abaixo contemplam cada uma das formas:

Programa       |   Descrição do AC e Tipo de Coleta
---------------|--------------------------------------------
AC_R8345_50v1D | AC Raio 1 – bidimensional regra 1453938345
AC_R8345_50v2D | AC Raio 1 – bidimensional regra 1453938345
AC_R8345_50v3D | AC Raio 1 – bidimensional regra 1453938345
AC_R8345_50v4D | AC Raio 1 – bidimensional regra 1453938345


Deve-se observar alguns parâmetros (variáveis) que precisam estar com seus valores adequados para cada tipo de AC. Abaixo segue informações necessárias:

Para execução dos programas unidimensionais é preciso setar as variáveis rule = 30 programa R_30, rule = 14436194405 para o programa R_4405, e rule = 90 e 150 para o programa AC90_150H, esses números de regras foram definidos por apresentarem comportamentos complexos. As variáveis a seguir, devem ficar com os seguintes valores, conforme Tabela 1.

Tabela 1
----------------
width |  height
------|---------
32    |  31.250
64    |  15.624
126   |   7.813

A variável random = 1, para que o programa construa um vetor com bits aleatórios (primeira linha do AC), a partir da função randint( ).
Para os programas bidimensionais as variáveis rows, columns e layersnum devem ser atribuídos valores como na Tabela 2.

Tabela 2
--------
rows  |  columns | layersnum
-------------------------------
4     |     8    |  31.250
8     |    16    |  15.525
8     |     8    |  15.625
4     |    32    |   7.813
8     |    16    |   7.813

No caso da variável rulenum consideramos o número 1453938345 definido como número da regra bidimensional, para dorandom atribuímos o número um, que conduz o programa a iniciar o primeiro plano com os bits posicionados de forma aleatória, utilizando para isso a função randint( ) e cycles = 100, que define o número de iterações para produzir 108 bits.

Os números apresentados nas Tabelas 1 e 2, deve-se ao fato que a escolha dos tamanhos dos ACs (width, rows e columns), serem compatíveis com as arquiteturas de processadores mais comuns, e (height e layersnum) são para gerar 106 bits, esses bits são armazenados em arquivo (nome que pode ser encontrado dentro do próprio código), ao final de 100 iterações, 108 milhões de bits produzidos estarão gravados.

Para os programas onde a coleta é feita somente a partir da (célula) coluna central, as variáveis devem ficar como nas Tabelas 3, caso dos programas unidimensionais e Tabela 4 para os programas bidimensionais.

Notamos que apenas a variável height é que se alterou para 1.000.000, valor necessário para coletar 10^6 bits, apenas a célula central é que se fará uso, isto a partir de cada atualização do AC.

Tabela 3

width   32           64            128

height  1.000.000    1.000.000     1.000.000


Ao observarmos a Tabela 4, notamos que também houve alterações na variável layersnum, nos diversos tamanhos,  com o mesmo propósito para realizarmos a coleta de 106 bits, da posição central a partir de cada plano.  

Tabela 4

rows          4              4            8          4          8

columns       8             16            8         32         16

layersnum   1.000.000   1.000.000   1.000.000   1.000.000   1.000.000


Para realizarmos a coleta de 25% ou 50%, optamos pelo bidimensional pelo fato que, ao efetuarmos a coleta a partir de diversas colunas do AC unidimensional, entregamos muitas informações a um observador, e assim, destruímos todas as possibilidades de segurança.  
Para a execução da coleta de ½ e ¼ dos bits, consideramos a mesma semente, para as 100 iterações,  e 4 tamanhos foram analisados: 4x16, 8x8, 4x32 e 8x16.

AC_R8345_50v1	AC Raio 1 – bidimensional regra 1453938345, variação coluna1linha2

AC_R8345_50v2	AC Raio 1 – bidimensional regra 1453938345, variação linha2coluna1

AC_R8345_50v3	AC Raio 1 – bidimensional regra 1453938345, variação linha1coluna2

AC_R8345_50v4	AC Raio 1 – bidimensional regra 1453938345, variação coluna2linha1

Os programas devem inicializar as variáveis, rulenum = 1453938345 número da regra bidimensional, prop = 2 valor que define ½ dos bits a serem coletados, qteCol = (rows * columns)/ prop que indica quantos valores serão coletados em cada plano, e a variável layersnum = 1000000/qteCol que define o número de iterações necessárias para alcançarmos 106 bits. Os valores para as variáveis rows e columns segue na Tabela 5:

Tabela 5

Uma outra mudança se dá nas linhas do código do programa referente a coleta de 50% dos bits, abaixo um exemplo parcial do código:
       for coluna in range(0,columns,1):
       	for linha in range(0,rows,2):        	
           	vetor[kl] = data[linha][coluna]       	
           	kl = kl + 1
Observar a variação da linha e da coluna , e a posição dos laços, em cada uma das 4 versões dos programas, essas mudanças são necessárias e deverão ser efetuadas para o acesso das células por diferentes formas.
Programas para coleta de 25% dos bits
AC_R8345_25	AC Raio 1 – bidimensional regra 1453938345, coleta 25%.
Na coleta de ¼ dos bits do plano, deve-se alterar a variável prop para 4, e as linhas de código onde ocorrem as alterações são apresentadas abaixo, nesse caso a variação da linha passa a ser de 4 em 4. 
Todas as alterações de linha e coluna e as posições dos laços deverão ser feitas para a coleta de 25%. Os código para a coleta de ¼ dos bits são os mesmos de ½ , e destacamos que não foram realizadas coletas na diagonal para ¼ dos bits.
  
  for coluna in range(0,columns,1):            
     for linha in range(0,rows,4):
   	          vetor[kl] = data[linha][coluna]             	          
              kl = kl + 1
 
Programas para coleta 50% dos bits na Diagonal

AC_R8345_50v1D		AC Raio 1 – bidimensional regra 1453938345

AC_R8345_50v2D		AC Raio 1 – bidimensional regra 1453938345

AC_R8345_50v3D		AC Raio 1 – bidimensional regra 1453938345

AC_R8345_50v4D	AC Raio 1 – bidimensional regra 1453938345


Para a coleta na diagonal, os programas devem inicializar as variáveis, rulenum = 1453938345, prop = 2 valor que define ½ dos bits a serem coletados, qteCol = (rows * columns)/ prop  que indica quantos valores serão coletados em cada plano, e a variavél layersnum = 1000000/qteCol que define o número de iterações necessárias para alcançarmos 106 bits. Os valores para as variáveis rows e columns segue a Tabela 6:

Tabela 6


Deve-se notar nas linhas de códigos a seguir como é realizada a coleta na diagonal, as quais fazem o processamento de atribuir a um vetor os bits, observa-se que as alterações devem ser efetuadas na inicialização dos valores de linha e coluna e durante a evolução dos dois laços while. 
linha = 0
        	coluna = 0          	
        	while coluna < columns: 
           	while linha < rows:         	
              		vetor[kl] = data[linha][coluna]  	
              		linha += 2
              	kl = kl + 1
           	coluna += 1
           	if (coluna % 2):
              		linha = 0              	
           	else:
              		linha = 1              
