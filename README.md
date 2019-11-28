# Hackathon 2019 - Desafio Técnico - DevOps
Por: Henrique Stanke Scandelari (stanke.contato@gmail.com)

--- Por favor, verificar as notas adicionais ao fim do documento ---

# Lógica e Algoritmo para Identificação, Seleção e Classificação de Anagramas baseado em um Dicionário

Este projeto se trata de um algoritmo o qual servirá de base para um programa que seja capaz de:
- Ler uma expressão (Seja ela uma palavra ou frase e que considere apenas as letras de A até Z)
- Ler uma lista de palavras válidas de um arquivo .txt (Presente no reposítorio como "dicionario.txt")
- Imprima todas as combinações possíveis de anagramas (Sem repetição de linhas ou palavras) os quais sejam válidas a partir do arquivo.
- Entregue um arquivo de saída contendo múltiplas linhas (Uma por anagrama), com as palavras ordenadas dentro de cada linha.
- O programa deve ser capaz de calcular e imprimir a lista de anagramas para uma expressão de até 16 caracteres em menos de 60 segundos.

# Conceitualização

Recorrendo à diversas fontes de informação quanto à Anagramas na Internet, buscando compreender essencialmente os requisitos para esta solução, compreendemos que:

***Um Anagrama é uma relação entre as letras de uma palavra tal qual mostra a capacidade de produzir outras palavras utilizando-se das mesmas letras e suas respectivas quantidades.***
  
  Definimos então, três tipos de Anagramas:
  
  ***Anagrama Perfeito***: Uma palavra anagrama que abrange todas as letras e suas quantidades da palavra especificada.
  Exemplo: A palavra "BARCO" contém 5 (cinco) letras, sendo elas (em ordem alfabética): {A, B, C, O, R}. As quantidades de cada uma dessas letras são: {A=1, B=1, C=1, O=1, R=1}. Dessa forma, para que se estabeleça um Anagrama Perfeito da palavra "BARCO", é necessário encontrar uma outra palavra que utilize somente as mesmas letras e suas respectivas quantidades. Neste exemplo:
  BROCA - {A=1, B=1, C=1, O=1, R=1}
  COBRA - {A=1, B=1, C=1, O=1, R=1}
  
  ***Anagrama Imperfeito***: Uma palavra anagrama que não abrange todas as letras e\ou suas quantidades perante à palavra específicada, mas que suas letras (e quantidades) cabem à palavra origem.
  Exemplo: A palavra "BARCO" abrange {A=1, B=1, C=1, O=1, R=1}. Dessa forma, é possível encontrar anagramas que não utilizem a mesma quantidade de letras ou que não contemplem todas as letras. Neste exemplo:
  ABRO - {A=1, B=1, O=1, R=1} - Sobrando de "BARCO" as letras\quantidades {C=1} 
  BROA - {A=1. B=1, O=1, R=1} - Sobrando de "BARCO" as letras\quantidades {C=1} 
  ORCA - {A=1, C=1, O=1, R=1} - Sobrando de "BARCO" as letras\quantidades {B=1}  
  RABO - {A=1. B=1, O=1, R=1} - Sobrando de "BARCO" as letras\quantidades {C=1} 
  
  ***Anagrama Complementar***: Uma união entre Anagramas Imperfeitos que juntos forma um anagrama completo (perfeito) por utilizarem todas as letras e suas quantidades da palavra especificada.
  Por exemplo: A palavra "LATARIA" - não foi possível formular um Anagrama Perfeito utilizando as letras e quantidades {A=3, I=1, L=1, R=1, T=1} - Porém, se utilizarmos os dois Anagramas Imperfeitos a seguir, formaremos um Anagrama Complementar:
  LATA - {A=2, L=1, T=1} + RIA - {A=1, I=1, R=1}
  Ao unirmos esses dois conjuntos, temos a completude de {A=3, I=1, L=1, R=1, T=1} - ou seja, temos um anagrama da palavra "LATARIA"

# Desenvolvimento

Considerando esse conceito, conseguimos então definir as formas de utilizar a programação para encontrar anagramas utilizando um dicionário pré-definido.

Utilizando-se então da leitura de diversas fontes (referenciadas no fim do documento), buscamos desenvolver formas alternativas de encontrar anagramas - ``` Infelizmente, devido à minha falta de domínio sobre uma linguagem de programação e a ausência de tembo hábil¹, eu não consegui desenvolver um programa que pudesse ser executado com sucesso e demonstrasse o uso das lógicas que eu escrevi, porém, irei tentar descrever minhas idéias da melhor maneira possível abaixo ```

-- As informações abaixo são especulativas e são o caminho realizado até a chegada da escolha de um algoritmo final--

**Pontos em Comum:**
Existirá no diretório de recursos um documento chamado "dicionario.txt" o qual contém uma lista de palavras que servirá de referência para o computador.
As expressões\palavras inseridas deverão apenas conter letras de "A" até "Z" - caso isso não seja validado, o programa cancela as ações.

# Algoritmo 1:
** (Encontra apenas Anagramas Perfeitos e Imperfeitos) **

``` 
1) Recebe-se uma palavra do INPUT do Usuário (Ex: Batata)
2) Converter todas as letras para caixa alta (Ex: Batata -> BATATA)
3) Identifica-se a palavra
  3.1) Identifica todas as letras presentes (Ex: "A", "B" e "T")
  3.2) Identifica quantas letras estão presentes (Ex: 6)
4) Lê-se o documento auxiliar ("dicionario.txt")
  4.1) Identifica todas as palavras as quais tem a quantidade de letras referidas (Ex: 6 - TABELA, TABATA, SELECT, SAFIRA, etc...)
  4.2) Identifica-se destas palavras, quais são palavras formadas pelas mesmas letras (Ex: 6 - TABATA, etc...)
5) Demonstra-se o resultado
```

# Algoritmo 2:
** (Encontra apenas Anagramas Perfeitos) **

``` 
Neste Algoritmo, o arquivo "dicionario.txt" será processado uma vez antes de se executar o programa que realiza a solução;
Parte 1:
1) Lê-se o documento auxiliar ("dicionario.txt")
2) Cria-se um identificador para todas as palavras por linha baseado em suas letras em ordem alfabética
•	Por exemplo: BATATA = AAATTB, TABATA = AAATTB, STOP = OPST, TOPS = OPST, POTS = OPST, ACORDEM = ACDEMOR, COMADRE = ACDEMOR, CREMADO = ACDEMOR, DECORAM = ACDEMOR, etc..
3) Salva-se na memória

Parte 2:
1) Recebe-se uma palavra do INPUT do Usuário (Ex: Mercado)
  1.1) Converte-se todas as letras para caixa alta (Ex: Mercado -> MERCADO)
2) Cria-se um identificador em ordem alfabética a partir das letras da palavra recebida para a mesma (Ex: MERCADO -> ACDEMOR)
3) Lê-se o documento auxiliar processado salvo na memória
4) Busca-se no documento todas as palavras as quais compartilham do mesmo identificador que a palavra inserida (Ex: "ACDEMOR" - ACORDEM, COMADRE, CREMADO, DECORAM, DEMARCO)
5) Demonstra-se o resultado
```

# Algoritmo 3:
** (Encontra vários anagramas possíveis, podendo ser limitado de diversas formas como: quantidade de linhas de respsota, tipos de respostas (se pode se sobrar letras ou não), etc...) **

```
1) Recebe-se uma expressão do INPUT do Usuário (Ex: American Dream)
  1.1) Converte-se para caixa alta (Ex: American Dream -> AMERICAN DREAM)
  1.2) Remove-se os espaços (Ex: AMERICAN DREAM -> AMERICANDREAM)
  1.3) Organiza em ordem alfabética (Ex: AMERICANDREAM -> AAACDEEIMMNRR)
2) Utiliza o resultado da última operação (Ex: AAACDEEIMMNRR) para definir as letras que serão utilizadas na busca
3) Busca-se no documento auxiliar ("dicionario.txt") a palavra mais compátivel em letras e suas quantidades (Ex: "AAACDEEIMMNRR" - Encontra-se "AIRMAN" - Que consome as letras "AAIMNR" - Retornando as restantes "ACDEEMR")
4) Se possível, repete-se o processo com o restante das letras até que que não seja mais possível encontrar anagramas (Ex: "ACDEEMR" - Encontra-se "DREAM" - Que consome as letras "ADEMR" - Retornando as restantes "CE")
5) Se não for mais possível encontrar anagramas, demonstra-se o resultado e as letras restantes
```

# Algoritmo 4:
** (Encontra todos os anagramas possíveis baseado em todas as palavras existentes no documento) **

```
1) Rcebe-se uma expressão do INPUT do Usuário (Ex: Rude Boy)
  1.1) Converte-se para caixa alta (Ex: Rude Boy -> RUDE BOY)
  1.2) Remove-se os espaços (Ex: RUDE BOY -> RUDEBOY)
  1.3) Organiza em ordem alfabética (Ex: RUDEBOY -> BDEORUY)
  1.4) Define quantas letras tem o resultado (Ex: BDEORUY = 7)
2) Utiliza o resultado da última operação (Ex: BDEORUY) para definir as letras e a quantidade inicial (Ex: 7) que serão utilizadas na busca
3) Busca-se no documento auxiliar ("dicionario.txt") todos os anagramas possíveis com as letras e quantidade inicial (Ex: Qtd: 7 - CREAMED) e então repete o processo subtraindo "1" da quantidade inicial até o mínimo de "2") (Ex: CAMERA, REMADE / 5 – DRAMA, DREAM, MADRE, CARED, CEDAR, RACED, CREAM, EDEMA / 4 – CARE, CAME, CARD, CRAM, DAME, DEER, DEAR, DEEM, MARE, MEAD, RACE, READ, REED / 3 ERE, RAD, RAM, RED, REC / 2 – AD, AM)
4) Demonstra o resultado na tela
```
Utilizando-se dessas formas, é possível desenvolver um algoritmo o qual atenda às regras emplacadas no desafio.
``` Imaginei, por exemplo, estes algoritmos na Linguagem C ou C++ com o uso de Vetores, Vetores de Vetores, livrarias de string e funções para leitura de dados em documento externo - mas acredito fortemente que é virtualmente possível que esses algoritmos possam ser implementados em outras linguagens como Python, Ruby, Java e JavaScript ou linguagens mais simples como Go (https://golang.org/) e Potigol (http://potigol.github.io/) conforme os exemplos demonstrados nos links de referência ao fim deste documento.

Outra forma que imaginei em realizar essa permutação de anagramas seria utilizando bancos de dados, como o uso do SQL - aonde poderiamos dividir a palavra inserida em caracteres individuais usando SUBSTRING() em um loop e gerar todas as permutações se baseando no banco de dados de palavras - no caso, o arquivo .txt.

Devo ressaltar que minha falta de domínio quanto à essas linguagens me limitou e eu não fui capaz de demonstrar uma execução - porém, eu assumo que pode ser completamente possível dado esta documentação e as documentações de referência no fim do documento.
```

``` 
¹ A razão pela qual eu não tive tempo para estudar o suficiente e desenvolver um programa funcional foi por conta de um problema que eu tive com minha inscrição que, graças à incrível ajuda de prontidão de Ana (da Panic Lobster), fomos capazes de consertar o problema nas últimas horas de Domingo (24/11) - assim tendo analisado e desenvolvido este documento e todas essas informações somente no último dia previsto, Segunda-feira (25/11)

Portanto, gostaria de deixar aqui meus sinceros pedidos de desculpas por não ter completado o desafio - mas me disponho a realizar outro desafio, tentar novamente ou até memso realizar alguma espécie de atividade em prol de poder ter a chance de apresentar minhas ideias, capacidades e competências perante aos jurados e envolvidos.
```

# Referências

https://osprogramadores.com/desafios/d06/ - Os Programadores - Blog de incentivo à programação - Desafio 06 retrata o mesmo desafio proposto pelo evento.

https://github.com/OsProgramadores/op-desafios/tree/master/desafio-06 - Arvore de respostas de usuários do desafio 06 proposto pelo blog, com algumas respostas em diversas linguagens (Go, Rust, Scala e Potigol);

Jogo “Scrabble” que consiste em encontrar palavras formando uma espécie de palavra-cruzada em base de um dicionário incluso – foi um dos jogos que me deu a ideia de indexar as palavras por um identificador comum, já que no jogo existe a possibilidade de jogar utilizando somente uma mesma palavra, e uma das técnicas é tentar formar palavras após organizar a palavra base de forma alfabética - https://en.wikipedia.org/wiki/Scrabble 

A documentação abaixo se origina de um Assignment da Stanford University tal qual deu base para o desafio proposto - nessa documentação é demonstrado a resolução completa sobre o desafio, incluindo descrição, implementação, detalhes de estilo e um FAQ (Perguntas frequentes): 
https://web.stanford.edu/class/archive/cs/cs106b/cs106b.1176/assn/anagrams.html#implementation
https://web.stanford.edu/class/archive/cs/cs106b/cs106b.1176/assn/anagrams.html#
