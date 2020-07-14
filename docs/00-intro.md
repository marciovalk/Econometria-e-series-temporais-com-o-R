# Séries temporais



Dados de séries temporais são obeservações de um evento ou fenômeno ao longo do tempo. Os intervalos de observações devem ser igualmente espaçados. Geralmente são anos, trimestres, meses, semanas, dias, horas, minutos e segundos. Mas outros tipos de espaçamentos entre observações também são comuns. Como é o caso do [Censo Demográfico](<https://www.ibge.gov.br/estatisticas/sociais/populacao/22827-censo-2020-censo4.html>). 

No Figura \@ref(fig:tsint00) apresentamos alguns exemplos de sériestemporais com diferentes intervalos de observações.

<div class="figure" style="text-align: center">
<img src="00-intro_files/figure-epub3/tsint00-1.png" alt="Séries temporais com diferentes intervalos de observações" width="45%" /><img src="00-intro_files/figure-epub3/tsint00-2.png" alt="Séries temporais com diferentes intervalos de observações" width="45%" /><img src="00-intro_files/figure-epub3/tsint00-3.png" alt="Séries temporais com diferentes intervalos de observações" width="45%" /><img src="00-intro_files/figure-epub3/tsint00-4.png" alt="Séries temporais com diferentes intervalos de observações" width="45%" />
<p class="caption">(\#fig:tsint00)Séries temporais com diferentes intervalos de observações</p>
</div>



Uma série temporal com observações a cada dez anos é a da população brasileira. 


## Breve introdução ao R {#intro}

Das linguagems de programação voltadas a manipulação, vizualização e análises de dados, o R é umas das mais difundidas entre a comunidade Estatística. Outras linguagens, como o Python, tem um apelo maior quando se trata de ciência de dados, no seu sentido mais amplo.

## Apresentação da linguagem R 

R é uma linguagem de programação caracterizada como Software Livre sob os termos da _General Public License (GNU)_ da _Free Software Foundation_ no formato _open source_. É voltada a manipulação, análise e vizualização de dados e tem como característica o aspecto colaborativo, sendo que as ferramentas desenvolvidas são compartilhadas online pelos desenvolvedores, podendo ter acesso a elas qualquer pessoa, sem restrições. Uma breve história do R pode ser encontrada no [wikipedia](https://pt.wikipedia.org/wiki/R_(linguagem_de_programa%C3%A7%C3%A3o)).



## Instalando o R

Para instalar no computador, O R deve ser baixado do  [CRAN](https://cran.r-project.org/).



<div class="figure">
<img src="Figuras/CRAN.png" alt="Comprehensive R archive network (CRAN)" width="90%" />
<p class="caption">(\#fig:cran)Comprehensive R archive network (CRAN)</p>
</div>

Se o sistema operacional for Linux, uma versão _base_ do R ja vem instalada. No cado de outros sistemas operacionais, como o Windows, é necessário instalar o R [base](https://cran.r-project.org/bin/windows/base/). 


## Instalando o RStudio

Como quase toda linguagem _Open Source_ a utilização se dá por meio de linhas de comando. Para tornar a linguagem mais amigável aos usuários, várias IDEs (_integrated development environment_) são utilizadas. No caso do R, a mais desenvolvida e utilizada é o [RStudio](https://rstudio.com/products/rstudio/). 

Uma versão _Free_ do RStudio para o seu desktop pode ser baixado de [https://rstudio.com/products/rstudio/download/](https://rstudio.com/products/rstudio/download/).

Depois de instalar o R, o RStudio já estará integrado ao R e terá uma interface intuitiva e amigável ao usuário. 

> Ainda assim, é importante ressaltar que na linguagem R não encontraremos _botões_ para realizar as análises. 

<br>

<div class="figure">
<img src="Figuras/RStudio.png" alt="Interface do RStudio" width="90%" />
<p class="caption">(\#fig:rstudio)Interface do RStudio</p>
</div>

## Diretório de trabalho

Um ação importante que deve ser realizada pelo usuário é _setar o diretório_ de trabalho.  Para isso existem diferentes formas. Uma delas é usando a função _setwd()_ .


Outra opção é através do _Go to directory_ que está disponível no Workspace do RStudio, conforme figura \@ref(fig:rstudio2). Nessa opção o usuário escolhe o diretório de trabalho e depois usando a opção _set as working directory_ esse diretório será "_settado_" como diretório de trabalho. 

<br>

> Todas os arquivos gerados, como figuras serão salvos nesse diretório. Para abrir um conjunto de dados, por exemplo, será muito mais simples se este também estiver salvo no mesmo diretório ou um subdiretório. Além disso, toda vez que o RStudio for reinicializado, esse procedimento terá que ser refeito. 



## RStudio Cloud

Outra forma simples e prática para usar o R e o RStudio é usar o [RStudio Cloud](https://rstudio.cloud/). 

<br>

> _THE MISSION
We created RStudio Cloud to make it easy for professionals, hobbyists, trainers, teachers and students to do, share, teach and learn data science_. [@rstudiocloud]

<br>

<div class="figure">
<img src="Figuras/RStudioCloud.png" alt="Rstudio Cloud" width="90%" />
<p class="caption">(\#fig:rstudiocloud)Rstudio Cloud</p>
</div>

<br>

Na núvem é possível usar o RStudio utilizando um login através da conta google, ou criar gratuitamente uma conta. Uma vez logado, escolhendo a opção _project_ o usuário terá uma versão do RStudio perfeitamente funcional, que pode ser utilizada até no smartphone. Obviamente, é necessário ter conexão com a internet para que a ferramenta possa ser utilizada. 

<br>

<div class="figure">
<img src="Figuras/RStudioCloud2.png" alt="Rstudio Cloud" width="90%" />
<p class="caption">(\#fig:rstudiocloud2)Rstudio Cloud</p>
</div>



## Instalação de pacotes 

Na versão _base_ do R, uma série de ferramentas, funções e métodos estatísticos são disponibilizados. Além disso, alguns pacotes também compõe a versão _base_ do R. Depois de instalado, o usuário pode verificar quais pacotes estão instalados acessando o ícone _Packages_ n





## Funcionalidades básicas 

### Operações
### Operadores lógicos

## Variáveis no R

### Operações

## Vetores

### Operações com vetores


## Matrizes    

### Operações com Matrizes

## Uso do for (loop)

## Funções






