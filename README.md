# DiagrammeR

Quando precisava, sempre fazia os meus fluxogramas utilizando o Power Point e, mais recentemente, o Canva. Gastava horas e, às vezes, dias para fazê-los. Depois que comecei a utilizar o pacote ['DiagrammeR'](https://rich-iannone.github.io/DiagrammeR/), consegui otimizar bastante o tempo que eu gastava nisso. A vantagem de usar esse pacote é que o fluxograma é feito no R utilizando o JavaScript, com uma infraestrutura fornecida pelo htmlwidgets. Pode ser publicado em [`.html`], incluindo documentos em R Markdown e Shiny.

Adaptei o fluxograma abaixo (Figura 1), misturando as informações contindas nos blog [SocialMente da Unicamp](https://www.blogs.unicamp.br/socialmente/2010/07/08/pseudociencias/) e [Intelligent Speculation](https://www.intelligentspeculation.com/blog/pseudoscience). O objetivo é compartilhar aqui como construir um fluxograma simples que posteriomente pode ser melhorado. 

<img src="https://github.com/fblpalmeira/DiagrammeR/blob/main/data/diagrammer_figure.png">
Figura 1. Fluxograma adaptado dos blogs Unicamp e Intelligent Speculation.

Confira também, o fluxograma publicado em [`.html`] no [RPubs](https://rpubs.com/fblpalmeira/1068497)
  
-----

# Código

- [Código - DiagrammeR `.R`](https://github.com/fblpalmeira/DiagrammeR/blob/main/data/diagrammer_pseudoscience.R)

No `RStudio` instalar e abrir o pacote 'DiagrammeR':

``` r

install.packages("DiagrammeR") # Instalar 
library(DiagrammeR) # Abrir 

```



-----

# Referências

[Iannone R (2023)](https://CRAN.R-project.org/package=DiagrammeR). _DiagrammeR: Graph/Network Visualization_. R package version 1.0.10, <https://CRAN.R-project.org/package=DiagrammeR>.
