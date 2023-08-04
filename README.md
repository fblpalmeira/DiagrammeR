# DiagrammeR

Até pouco tempo atrás, gastava horas e, às vezes, dias para construir os meus fluxogramas no PowerPoint ou no Canva. Depois que comecei a utilizar o pacote ['DiagrammeR'](https://rich-iannone.github.io/DiagrammeR/), consegui otimizar bastante o tempo que eu gastava nisso. O pacote utiliza a biblioteca `mermaid.js` do JavaScript e possue uma infraestrutura fornecida pelo `htmlwidgets`. Pode ser publicado em `html` e incorporado em documentos R Markdown e Shiny. Também pode ser convertido para outros formatos ou exportados como arquivos de imagem. O pacote também possibilita a construção de outras visualizações gráficas como a rede de interações. 

Adaptei o fluxograma abaixo (Figura 1), misturando as informações contidas nos blogs [SocialMente da Unicamp](https://www.blogs.unicamp.br/socialmente/2010/07/08/pseudociencias/) e [Intelligent Speculation](https://www.intelligentspeculation.com/blog/pseudoscience). Certamente, o exemplo poderia ser mais complexo mas, o nosso objetivo é aprender a construir um fluxograma simples e, que posteriormente, pode ser melhorado. Confira também o fluxograma em `html` no [RPubs](https://rpubs.com/fblpalmeira/1068497)

<img src="https://github.com/fblpalmeira/DiagrammeR/blob/main/data/diagrammer_figure.png">
Figura 1. Fluxograma adaptado dos blogs SocialMente da Unicamp e Intelligent Speculation.
  
-----

# Código

Confira e baixe o código completo aqui:

- [Código - DiagrammeR `.R`](https://github.com/fblpalmeira/DiagrammeR/blob/main/data/diagrammer_pseudoscience.R)


# Instalar o pacote

No `RStudio`, instalar o pacote 'DiagrammeR':

``` r

install.packages("DiagrammeR") # Instalar 

```

# Entendendo a estrutura do código

Após instalar o pacote, vamos abri-lo utilizando a função `Diagrammer::` do pacote `dplyr`, que já vem instalado com o DiagrammeR. A função `grViz` faz a interface com o [Graphviz](https://www.graphviz.org/), um software de visualização de gráficos de código aberto. Para fazer o fluxograma, vamos utilizar a função `digraph`.

``` r

DiagrammeR::grViz("digraph {

```

A estrutura do código é dividida em três funções principais: a do gráfico `graph`, a das caixas `node` e a das linhas `edge`. É dentro de cada uma dessas funções que editamos os argumentos para customizar o fluxograma como, por exemplo:

- No gráfico `graph`, definimos o layout geral (se retrato ou paisagem), a distância entre as caixas, etc.; 
- Nas caixas `node`, definimos os formatos, as cores dos polígonos, etc.; e, 
- Nas linhas `edge`, definimos os tamanhos, os formatos e as cores das setas, entre outras possibilidades.
  
``` r

graph [ordering = in, nodesep = 6, ranksep = 8, layout = dot, rankdir = TB]
node [fontcolor = gray35, fontname = Helvetica, shape = rectangle, style = filled, fillcolor = Linen, fontsize = 500]
edge [color = black, arrowhead = vee, arrowsize = 25, penwidth = 15] 

```

Em seguida, vamos especificar quais serão as caixas e começar a nomeá-las. Neste caso, vamos abrir uma caixa para a 'Ciência' e outra para a 'Pseudociência'. O `\n` é opcional, utilizei para pular uma linha antes e depois da etiqueta, só para aumentar o espaço dentro das caixas. Repare que na função `node` já especificamos a cor das caixas `fillcolor = Linen`. Também, podemos editar a cor de cada caixa aqui, neste caso mudamos para `fillcolor = aliceblue`.

``` r

data1 [label = '\n     Ciência     \n ', fillcolor = aliceblue]
data2 [label = '\n Pseudociência \n ', fillcolor = aliceblue]

```

Agora, vamos especificar que tipo de 'Ciência' nós fazemos. Neste caso, temos duas, uma 'Boa' e uma 'Ruim'.

``` r

sci1 [label = '\n     Boa     \n ', fillcolor = aliceblue]
sci2 [label = '\n     Ruim     \n ', fillcolor = aliceblue]

```

Em seguida, vamos inserir três caixas para a 'Observação' visto que o processo observacional existe tanto na 'Ciência Boa', como na 'Ciência Ruim' e na 'Pseudocência'. Repare que editamos o formato do polígono para `shape = ellipse` para destacar melhor as diferenças e as semelhanças das caixas dentro do fluxograma. 

``` r

obs1 [label = '\n Observação \n ', shape = ellipse]
obs2 [label = '\n Observação \n ', shape = ellipse]
obs3 [label = '\n Observação \n ', shape = ellipse]

```

Assim como na 'Observação', vamos inserir três caixas para as 'Hipóteses' que também são formuladas tanto na 'Ciência Boa', como na 'Ciência Ruim' e na 'Pseudocência'. 

``` r

h1 [label = 'Hipóteses \n com \n fortes premissas', shape = ellipse]
h2 [label = 'Hipóteses \n com \n fortes premissas', shape = ellipse]
h3 [label = 'Hipóteses com \n premissas fracas \n ou inválidas', shape = ellipse]

```

No caso da 'Experimentação', abriremos duas caixas, visto que existem apenas dentro da 'Ciência'. No caso da 'Ciência Boa', temos uma 'Experimentação robusta' e no da 'Ciência Ruim', uma 'Experimentação malfeita ou fraudulenta'. Repare aqui, que editamos o formato e a cor do polígono `shape = diamond, fillcolor = Beige`. 

``` r

exp1 [label = 'Experimentação \n robusta \n ', shape = diamond, fillcolor = Beige]
exp2 [label = 'Experimentação \n malfeita ou \n fraudulenta', shape = diamond, fillcolor = Beige]

```

Agora, vamos abrir apenas uma caixa para a 'Teoria', uma vez que ela existe e é discutida apenas na 'Ciência'. Repare que editamos novamente o formato e a cor da caixa `shape = circle, fillcolor = honeydew`. 

``` r

teo [label = '\n Teoria \n ', shape = circle, fillcolor = honeydew]

```

Abriremos mais duas caixas para a 'Lei', uma para a 'Ciência' e outra para a 'Pseudociência'.

``` r

lei1 [label = '\n    Lei     \n ', shape = cylinder, fillcolor = lightcyan]
lei2 [label = '\n    Lei     \n ', shape = cylinder, fillcolor = lightcyan]

```

Finalizamos a etapa da construção de caixinhas descritas com suas devidas etiquetas! Agora, vamos ligar as caixas com as linhas. Primeiro, vamos ligar as caixas da 'Ciência Boa' e depois as caixas da 'Ciência Ruim'. Como a elaboração da 'Teoria' traz novos questionamentos e nos leva a conduzir novos 'Experimentos' (em um looping quase infinito), vamos acrescentar uma seta de volta da 'Teoria' para o 'Experimento' para ambas as Ciências, Boa e Ruim e destacá-las em vermelho `[dir = back, color = red]`.  
 

``` r

data1 -> sci1 -> obs1 -> h1 -> exp1;
exp1 -> teo [arrowhead = normal, color = red];
exp1 -> teo [dir = back, color = red];

data1 -> sci2 -> obs2 -> h2 -> exp2;
exp2 -> teo [arrowhead = normal, color = red];
exp2 -> teo [dir = back, color = red];

teo -> lei1;

```

Agora, vamos unir as caixas da 'Pseudociência'. Repare que utilizamos a função `[minlen = 2]` para editar o comprimento da linha entre as caixas e ficar esteticamente simétrico com a 'Ciência' facilitando a comparação entre elas. Para finalizar, vamos encerrar o código `}")`.

``` r

data2 -> obs3 [minlen = 2];
obs3 -> h3;
h3 -> lei2 [minlen = 3];

}")

``` 

-----

# Material básico no R

Segue abaixo, uma lista de links com informações que podem nos ajudar na construção e na customização de fluxogramas com o pacote 'DiagrammeR'. 

- https://rich-iannone.github.io/DiagrammeR/articles/graphviz-mermaid.html
- https://www.sesync.org/resources/creating-visualizations-diagrammer
- https://mikeyharper.uk/flowcharts-in-r-using-diagrammer/

-----

# Material complementar no JavaScript

Como o material disponível para o pacote 'DiagrammeR' é escasso, segue abaixo o link das páginas do Graphviz onde contêm informações adicionais que podem nos ajudar na customização do gráfico. Atenção, como esse material complementar faz parte da biblioteca do JavaScritpt, nem todas as funções se aplicam ao pacote do R, mas vale a pena testar!

- Para visualizar os tipos de polígonos: https://graphviz.org/doc/info/shapes.html
- Para visualizar os tipos de linhas: https://graphviz.org/doc/info/arrows.html
- Para visualizar o nome das cores: https://graphviz.org/doc/info/colors.html

-----

# Referência

[Iannone R (2023)](https://CRAN.R-project.org/package=DiagrammeR). _DiagrammeR: Graph/Network Visualization_. R package version 1.0.10, <https://CRAN.R-project.org/package=DiagrammeR>.
