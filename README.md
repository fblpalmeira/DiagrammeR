# DiagrammeR

Até pouco tempo atrás, gastava horas e, às vezes, dias para construir os meus fluxogramas no Power Point ou no Canva. Depois que comecei a utilizar o pacote ['DiagrammeR'](https://rich-iannone.github.io/DiagrammeR/), consegui otimizar bastante o tempo que eu gastava nisso. A vantagem de usar esse pacote é que o fluxograma é feito no R utilizando a biblioteca 'mermaid.js' do JavaScript, com uma infraestrutura fornecida pelo htmlwidgets. Pode ser publicado em `.html` e incorporado em documentos R Markdown e Shiny. Também pode ser convertido para outros formato ou exportados como arquivos de imagem. O pacote também possibilita a construção outras visualizações gráficas como a rede de interações. 

Adaptei o fluxograma abaixo (Figura 1), misturando as informações contindas nos blog [SocialMente da Unicamp](https://www.blogs.unicamp.br/socialmente/2010/07/08/pseudociencias/) e [Intelligent Speculation](https://www.intelligentspeculation.com/blog/pseudoscience). O objetivo é compartilhar aqui como construir um fluxograma simples que posteriomente pode ser melhorado. 

<img src="https://github.com/fblpalmeira/DiagrammeR/blob/main/data/diagrammer_figure.png">
Figura 1. Fluxograma adaptado dos blogs Unicamp e Intelligent Speculation.

Confira também, o fluxograma publicado em `.html` no [RPubs](https://rpubs.com/fblpalmeira/1068497)
  
-----

# Código

Confira e abaixe o código completo aqui:

- [Código - DiagrammeR `.R`](https://github.com/fblpalmeira/DiagrammeR/blob/main/data/diagrammer_pseudoscience.R)


# Instalar o pacote

No `RStudio` instalar o pacote 'DiagrammeR':

``` r

install.packages("DiagrammeR") # Instalar 

```

# Entendendo a estrutura do código

Depois de instalar o pacote, vamos abrí-lo é utilizando a função `.Diagrammer::` do pacote 'dplyr', que vem instalado junto o DiagrammeR. A função `.grViz` faz a interface com o [Graphviz](https://www.graphviz.org/), um software de visualização de gráficos de código aberto. A função `.digraph` define o tipo de visualização gráfica, neste caso caso um fluxograma.

``` r

DiagrammeR::grViz("digraph {

```

A estrutura do código é dividida em três funçoes principais: a do gráfico (graph), a das caixas (node) e a das linhas (edge). É dentro de cada uma dessas funções que tem os argumentos que devem ser editados para podermos costumizar o layout do gráfico, como por exemplo:

- No gráfico, podemos definir o layout geral (se retrato ou paisagem) e a distância entre as caixas; 
- Nas caixas, podemos editar os formatos e as cores dos polígonos e 
- Nas linhas, os tamanhos, os formatos e as cores das setas.
  
``` r

graph [ordering = in, nodesep = 6, ranksep = 8, layout = dot, rankdir = TB]
node [fontcolor = gray35, fontname = Helvetica, shape = rectangle, style = filled, fillcolor = Linen, fontsize = 500]
edge [color = black, arrowhead = vee, arrowsize = 25, penwidth = 15] 

```

xxxxxxxxx

``` r

edge [color = black, arrowhead = vee, arrowsize = 25, penwidth = 15] 

```

xxxxxxxxx

``` r

data1 [label = '\n     Ciência     \n ', shape = rect, fillcolor = aliceblue]
data2 [label = '\n Pseudociência \n ', shape = rect, fillcolor = aliceblue]

```

xxxxxxxxx

``` r

```
xxxxxxxxx

``` r

```
xxxxxxxxx

``` r

``` 
-----

# Referências

[Iannone R (2023)](https://CRAN.R-project.org/package=DiagrammeR). _DiagrammeR: Graph/Network Visualization_. R package version 1.0.10, <https://CRAN.R-project.org/package=DiagrammeR>.
