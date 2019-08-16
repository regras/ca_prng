# ca_prng

Cellular Automata based pseudorandom number generators

Sobre

Autômatos Celulares (AC) são sistemas dinâmicos, com tempo e espaço discretos que, a partir de simples iterações e computações, podem exibir comportamentos complexo.

Um AC consiste de um conjunto de células que podem ser organizadas em um espaço n-dimensional, com um número finito de estados, os quais variam com a aplicação de regras determinísticas.

Mais detalhes sobre esse assunto, podem ser encontrados na dissertação de mestrado “AVALIAÇÃO DE GERADORES DE NÚMEROS PSEUDOALEATÓRIOS BASEADOS EM AUTÔMATOS CELULARES NÃO ELEMENTARES”  de Sílvia R. L. Magossi, disponível no repositório digital da Unicamp em http://repositorio.unicamp.br/

Objetivo

Foram utilizados programas desenvolvidos em Python durante o trabalho de mestrado, a fim de produzir sequências binárias aleatórias a partir de ACs. Os ACs e a produção das sequências binárias, podem ser empregados como um Gerador de Números Aleatórios.

Programa      Descrição do AC e Tipo de Coleta

AC_R30        AC Raio 1 - unidimensional regra 30, coleta por linha

AC_R4405      AC Raio 2 - unidimensional regra 1436194405, coleta por linha

AC_R8345      AC Raio 1 - bidimensional regra 1453938345

AC_R30col     AC Raio 1 - unidimensional regra 30, coleta coluna central

AC_R4405col   AC Raio 2 - unidimensional regra 1436194405, coleta coluna central

AC_R8345col   AC Raio 1 - bidimensional regra 1453938345, coleta coluna central

AC90_150H     AC 90/150 Híbrido coleta por linha

AC90_150Hcol  AC 90/150 Híbrido coleta por coluna central
