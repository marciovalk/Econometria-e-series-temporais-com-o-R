# Séries temporais



Dados de séries temporais são obeservações de um evento ou fenômeno ao longo do tempo. Os intervalos de observações devem ser igualmente espaçados. Geralmente são anos, trimestres, meses, semanas, dias, horas, minutos e segundos. Mas outros tipos de espaçamentos entre observações também são comuns. Como é o caso do [Censo Demográfico](<https://www.ibge.gov.br/estatisticas/sociais/populacao/22827-censo-2020-censo4.html>). 

No Figura \@ref(fig:tsint00) apresentamos alguns exemplos de sériestemporais com diferentes intervalos de observações.

<div class="figure" style="text-align: center">
<img src="00-intro_files/figure-html/tsint00-1.png" alt="Séries temporais com diferentes intervalos de observações" width="45%" /><img src="00-intro_files/figure-html/tsint00-2.png" alt="Séries temporais com diferentes intervalos de observações" width="45%" /><img src="00-intro_files/figure-html/tsint00-3.png" alt="Séries temporais com diferentes intervalos de observações" width="45%" /><img src="00-intro_files/figure-html/tsint00-4.png" alt="Séries temporais com diferentes intervalos de observações" width="45%" />
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

Outra forma simples e prática para usar o `R` e o RStudio é usar o [RStudio Cloud](https://rstudio.cloud/). 

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

Na versão _base_ do `R`, uma série de ferramentas, funções e métodos estatísticos são disponibilizados. Além disso, alguns pacotes também compõe a versão _base_ do `R`. Depois de instalado, o usuário pode verificar quais pacotes estão instalados acessando o ícone _Packages_ em _Tools_ ou digitando  *installed.packages()* no _console_.  

Para instalar um novo pacote, o usuário pode acessar  o ícone _Packages_ e depois clicar em _Install_ ou digitar no console _install.packages("nome do pacote")_ . Como exemplo, podemos instalar o pacote usado para vizualização de dados chamado _ggplot2_. 



```r
install.packages("ggplot2")
```

### Carregando pacotes

Importante para usuários iniciantes na linguagem `R` é entender a diferença entre instalar pacotes e carregar pacotes. Uma vez instalado, o pacote estará a disposição do usuário sempre que ele precisar, mas é necessário carregá-lo. É comum deixar um comando nos _scripts_ para que cada vez que seja necessário usar alguma função específica de um pacote, ele primeiro seja carregado. O comando usado é o _library()_ mas pode ser feito acessando o espaço que chamando de **Tools**, clicar em _Packages_ e marcar o pacote desejado para carregá-lo. 


```r
library(ggplot2)
```

## Ajuda

Para um usuário iniciante no `R` é fundamental saber como resolver problemas diversos que certamente vão surgir durante a instalação de um pacote, uso de uma função, criação de um gráfico, manipulação de dados, etc. Muitas coisas no `R` são feitas por tentativa e erro, mas o conhecimento é acumulativo e problemas similares, poderão ter uma solução mais rápida. Uma das grandes vantagens da utilização do `R` é que a comunidade é bastante ativa. Existem diferentes formas de conseguir ajuda e vou elencá-las em ordem de importância, segundo a forma utilização desse autor:

- > Google
- > Stack Overflow
- > Help do R ( `help()` ou `?`)


### Google

Para um iniciante em `R` coisas simples como calcular a raíz quadrada de um número pode ser difícil. Nesses caso o google é muito útil. 
<br>

<div class="figure">
<img src="Figuras/sqrt.png" alt="Rstudio Cloud" width="90%" />
<p class="caption">(\#fig:sq1)Rstudio Cloud</p>
</div>

Um pouco de conhecimento de inglês aumenta consideravelmente as opções de ajuda no google. 


### Stack Overflow

Quando o problema parecer um pouco mais complexo, uma opção é colocar a pergunta no google junto com *Stack Overflow*. Isso provavelmente direcionará o usuário para  [Stack Overflow em Português](https://pt.stackoverflow.com/) ou [Stack Overflow ](https://stackoverflow.com/) que são sites de Pergunta e Resposta utilizados por todas as linguagens de programação. 

<div class="figure">
<img src="Figuras/sqrt3.png" alt="Rstudio Cloud" width="90%" />
<p class="caption">(\#fig:sq3)Rstudio Cloud</p>
</div>

<br> 

<div class="figure">
<img src="Figuras/sqrt2.png" alt="Rstudio Cloud" width="90%" />
<p class="caption">(\#fig:sq2)Rstudio Cloud</p>
</div>


### Help do `R`
Se o usuário já sabe qual função  deve ser usada, então a documentação do `R` é bem útil. 


```r
?sqrt
help(sqrt)
```
Dicas para uso do `Help`

- Pode-se ir direto aos exemplos que estão no final;
- Identificar os parâmetros (*Arguments*);
- Funções relacionadas podem ajudar, dependendo da necessida.
- *Vignettes*, que são tutorias mais completos, mas somente alguns pacotes possuem. Esses textos podem ser acessados com a função vignette(package = 'nomeDoPacote'). Por exemplo, vignette(package = 'ggplot2')




## Funcionalidades básicas 

Para maior agilidade é importante que o usuário conheça algumas teclas de atalho. Apertando simultaneamente **_Alt + Shift + K_** o usuário tem acesso à uma grande quantidade de atalhos. Ou clicado em _Tools_ no menu de ícones do RStudio. 
Um comando de atalho que destacaria por ser extremamaente útil é o **_Ctrl + Enter_**. Esse comando executa a linha do _script_ em que o cursor está.

Para começar, usaremos o `R` como uma calculadora simples. Execute o código a seguir diretamente do console do RStudio ou no RStudio, escrevendo-os em um script e executando-os usando **_Ctrl + Enter_**.

### Operações básicas

#### As quatro operações 

| Operação      | código `R`| Resultado |
|:-------------:|:-------:|:---------:|
| $3 + 2$       | `3 + 2` | 5 |
| $3 - 2$       | `3 - 2` | 1 |
| $3 \cdot2$    | `3 * 2` | 6 |
| $3 / 2$       | `3 / 2` | 1.5 |


```r
x <- 10
y <- 2

x+y
```

```
## [1] 12
```

```r
x-y
```

```
## [1] 8
```

```r
x*y
```

```
## [1] 20
```

```r
x/y
```

```
## [1] 5
```
#### Exponenciação 

| Operação      | código `R`| Resultado |
|:-------------:|:-------:|:---------:|
| $3^2$        | `3 ^ 2`         | 9         |
| $2^{(-3)}$   | `2 ^ (-3)`      | 0.125      |
| $100^{1/2}$  | `100 ^ (1 / 2)` | 10 |
| $\sqrt{100}$ | `sqrt(100)`     | 10     |


```r
x^y         # x=10 e y=2
```

```
## [1] 100
```


#### Logarítimos  

Observe que não existe  `ln()` no `R`.  Usa-se `log()` para significar logarítimo natural. Para as demais bases, é necessário especificar a base desejada. 

| Operação      | código `R`| Resultado |
|:------------:|:---------------:|:-----------------:|
| $\log(e)$         | `log(exp(1))`       | 1       |
| $\log_{10}(100)$ | `log10(100)`       | 2       |
| $\log_{2}(16)$     | `log2(16)`           | 4           |
| $\log_{4}(16)$    | `log(16, base = 4)` | 2 |


```r
log(x)        # x=10
```

```
## [1] 2.302585
```

```r
log(x,base=y) # y=2
```

```
## [1] 3.321928
```

#### Constantes matemáticas  

| Constante     | código `R`| Resultado |
|:------------:|:---------------:|:-----------------:|
| $\pi$        | `pi`            | 3.1415927            |
| $e$          | `exp(1)`        | 2.7182818        |



```r
log(exp(1)) 
```

```
## [1] 1
```

```r
exp(1)^y     # y=2
```

```
## [1] 7.389056
```

### Operadores lógicos


| Operador | Significado              | Exemplo              | Resultado |
|:---------|:---------------------:|:---------------------:|:-------:|
| `x < y`  | `x` menor do que `y`                | `3 < 42`               | TRUE               |
| `x > y`  | `x` maior do que `y`             | `3 > 42`               | FALSE               |
| `x <= y` | `x` menor ou igual à `y`    | `3 <= 42`              | TRUE              |
| `x >= y` | `x` menor ou igual à`y` | `3 >= 42`              | FALSE              |
| `x == y` | `x` igual à `y`                  | `3 == 42`              | FALSE              |
| `x != y` | `x` diferente de `y`             | `3 != 42`              | TRUE              |
| `!x`     | não `x`                          | `!(3 > 42)`            | TRUE            |
| `x | y`  | `x` ou `y`                       | `(3 > 42) | TRUE`      | TRUE      |
| `x & y`  | `x` e `y`                      | `(3 < 4) & ( 42 > 13)` | TRUE |

#### Operador lógico _if()_
Dentro dessa classe de operadores, podemos destacar o operador _if()_. É comum usar esse operador para testar condições únicas ou múltiplas na instrução _if()_ ou  _ifelse()_. Operadores lógicos em `R` podem ser aplicados a vetores numéricos ou complexos ou objetos booleanos, que são **TRUE** ou **FALSE** (à eles são reservados os _atalhos_ **T** e **F**).




```r
A=4
B=2
if(A>B){
  print("A é maior do que B")
  }else{
    print("A não é maior do que B")
  }
```

```
## [1] "A é maior do que B"
```


```r
A=4
B=6
if(A>B){
  print("A é maior do que B")
  }else{
    print("A não é maior do que B")
  }
```

```
## [1] "A não é maior do que B"
```


Outra forma simples de usar o operador é:


```r
A=4
B=6
A>B
```

```
## [1] FALSE
```
#### Operador lógico _ifelse()_

O operador _ifelse( "1", "2" , "3")_ possui 3 entradas. Na primeira "1", deve-se colocar a condição a ser testada. Em "2" o resultado caso a condição testada seja verdadeira e em "3" o resultado, caso a condição testada seja falsa. 



```r
A=4
B=6
#ifelse(A>=B,"Verdadeiro","FALSO")
```




#### Operadores de atribuição

Os operadores de atribuição são provavelmente a família de operadores que você mais usará enquanto
trabalha com `R`. Como o nome desse grupo implica, eles são usados para atribuir objetos, como
valores numéricos, _strings_, vetores, modelos e plotagens para um nome (variável). Isso inclui
operadores como a seta para trás (<-) ou o sinal de igual (=)


```r
str <- "Em Brasília, 19 horas!" # String
int <- 10 # Inteiro
vet <- c(1,2,3,4) # Vetor
```

<br>

Para visualizar a variável, podemos simplesmente digitá-la ou usar a função *print()*
 

```r
str
```

```
## [1] "Em Brasília, 19 horas!"
```

```r
#ou
print(str)
```

```
## [1] "Em Brasília, 19 horas!"
```

<br>

Para visualizar mais de uma variável, podemos usar "c()" para "juntar as variáveis"


```r
c(str,int)
```

```
## [1] "Em Brasília, 19 horas!" "10"
```

```r
# ou
print(c(str,int))
```

```
## [1] "Em Brasília, 19 horas!" "10"
```

> _Esse exemplo pode ser repetido usando "=" no lugar de "<-"_


<br> 

### Tipos de dados
`R`  possui um número básico de *tipos* de dados. Enquanto o `R`é uma _linguagem fortemente tipada_ (não exige do usuário muito conhecimento sobre diferentes tipos de dados) é útil conhecer os tipos disponíveis. 



- Numeric
    - Também conhecido como duplo. O tipo padrão ao lidar com números.
    - Exemplos: `1`,` 1,0`, `42,5`
- Integer
    - Exemplos: `1L`,` 2L`, `42L`
- Complex
    - Exemplo: `4 + 2i`
- Logical
    - Dois valores possíveis: `TRUE` e `FALSE`
    - Você também pode usar `T` e`F`, mas isso *não* é recomendado.
    - `NA` também é considerado lógico.
- Character
    - Exemplos: `" a "`, `" Statistics "`, `" 1 mais 2. "`
- Categorical or `factor`
    - Uma mistura de número inteiro e caractere. Uma variável `fator` atribui um rótulo a um valor numérico.
    - Por exemplo, `fator (x = c (0,1), labels = c (" male "," female ")))` atribui a string *male* aos valores numéricos `0` e a string *female* ao valor `1`.



### Valores especiais

Assim como `TRUE` e `FALSE`, existem outros *valores* reservados à situações específicas.


- `NA` (*Not Available*) representa dado faltante (não disponível), ou que que é chamado em estatística de *missing data*.
- `NaN` (*Not a Number*) são gerados quando temos uma indefinições matemáticas, como sqrt(-1) e 0/0. 
- `Inf` (*Infinito*) é usado quando o valor numérico é muito grande (limite). Por exemplo, `exp(2000)`.
- `NULL` significa ausência de informação. Parecido com o `NA`, mas conceitualmente mais usado na lógica de programação. 

As funções `is.na()`, `is.nan()`, `is.infinite()` e `is.null()`podem ser usadas para verificar se um objeto possui algum valor com essa caraterística. 


## Estrutura dos dados

`R` também possui um número básico de *estrutura* de dados. Essa estrutura de dados pode ser **homogênea** ( setodos os elementos são do mesmo tipo de dados) ou **heterogênea** (se os elementos podem ter mais de um tipo de dados).


| Dimensão | **Homogênea** | **Heterogênea** |
|:---------:|:---------------:|:-----------------:|
| 1         | Vector          | List              |
| 2         | Matrix          | Data Frame        |
| 3+        | Array           |    nested Lists   |



### Vetores

Muitas operações em `R` usam **vetores**. Um vetor contém um conjunto de objetos de tipos identicos e são indexados começando na posição `1`. A maneira mais comum para se criar um vetor é usar a função `c()`, o que é uma abreviação de `combine()`. Ela combina uma lista de elementos separados por `,`.  Por exemplo,


```r
c(1,2)
```

```
## [1] 1 2
```

Ou podemos combinar outros objetos, desde que sejam do mesmo tipo.


```r
A=c(1,2)
B=c(3,4,5)
c(A,B)
```

```
## [1] 1 2 3 4 5
```

Os objetos não precisam ser numéricos. Por exemplo,


```r
A="Amarelo"  # objeto da classe "character"
class(A)
```

```
## [1] "character"
```

```r
B="Azul"
c(A,B)
```

```
## [1] "Amarelo" "Azul"
```
Embora tenham muitas `letras` nesse objeto combinado `c(A,B)`, na verdade só existem dois elementos, {"Amarelo", "Azul"}. Para acessá-los, usamos o colchete `[]`. 

#### Subconjuntos de vetores


Para subconjunto de um vetor, ou seja, para escolher apenas alguns elementos dele, usamos colchetes, `[]`. Aqui vemos que `AA[1]` retorna o primeiro elemento e `AA[2]` retorna o segundo elemento:



```r
A="Amarelo"
B="Azul"
AA=c(A,B)
AA[1]
```

```
## [1] "Amarelo"
```

```r
AA[2]
```

```
## [1] "Azul"
```

Qunado o vetor é maior, podemso usar um conjunto de indices para acessar o valores correspondentes no vetor.


```r
x=c(35,42,47,54,70,75)
x[c(1,3,6)]     # Acessa as posições 1, 3 e 6 do vetor
```

```
## [1] 35 47 75
```

```r
x[-4]           # Acessa todas as posições do vetor, menos a posição 4
```

```
## [1] 35 42 47 70 75
```



Muitas vezes queremos criar um vetor baseado em uma sequência de números. No `R` o operador `:` é usado como uma opção `de : até `. Dessa forma é possível usá-lo em diferentes situações. 



```r
c(1:10) # vetor com números de 1 à 10
```

```
##  [1]  1  2  3  4  5  6  7  8  9 10
```

```r
1:10    # vetor com números de 1 à 10
```

```
##  [1]  1  2  3  4  5  6  7  8  9 10
```

Outros vetores de objetos são possíveis de criar 


```r
LETTERS[1:4] # maiúsculas
```

```
## [1] "A" "B" "C" "D"
```

```r
letters[1:4] # minuscúlas
```

```
## [1] "a" "b" "c" "d"
```

#### Função `paste()`

Com a função `paste()` podemos concatenar objetos de tipos diferentes e armazená-los em um vetor.


```r
paste("Porco_", letters[1:4], sep="")   # Underline no Porco e sem espaço no sep
```

```
## [1] "Porco_a" "Porco_b" "Porco_c" "Porco_d"
```

```r
paste("Porco", letters[1:4], sep="_")   # Underline no sep
```

```
## [1] "Porco_a" "Porco_b" "Porco_c" "Porco_d"
```

```r
p=paste("Porco", letters[1:4], sep="_") # Armazenando no vetor p
p[2]                                    # Acessando a posição 2 do vetor p
```

```
## [1] "Porco_b"
```

Note que escalares não existem no `R`. Eles são vetores de tamanho `1`.



```r
2
```

```
## [1] 2
```

#### Função `seq()` 
Se quisermos criar uma sequência que não se limite a números inteiros e que aumente 1 por vez, podemos usar a função `seq()`.


```r
seq(from = -0.5, to = 1.8, by = 0.1)
```

```
##  [1] -0.5 -0.4 -0.3 -0.2 -0.1  0.0  0.1  0.2  0.3  0.4  0.5  0.6  0.7  0.8  0.9
## [16]  1.0  1.1  1.2  1.3  1.4  1.5  1.6  1.7  1.8
```


#### Função `rep()` 


Outra operação comum para criar um vetor é `rep()`, que pode repetir um único valor várias vezes.


```r
rep("A", times = 10)
```

```
##  [1] "A" "A" "A" "A" "A" "A" "A" "A" "A" "A"
```

```r
rep(1, 10)
```

```
##  [1] 1 1 1 1 1 1 1 1 1 1
```


A função `rep()` pode ser usada para repetir um vetor várias vezes.


```r
x=c("O","A")
rep(x, 3)
```

```
## [1] "O" "A" "O" "A" "O" "A"
```


#### Função `length()`

Uma função importante é à que identifica o tamanho do vetor, que é a função  `length()`.


```r
x=1:5
length(x)
```

```
## [1] 5
```

```r
y=rep(x,6)
length(y)
```

```
## [1] 30
```


#### Resumo

temos quatro formas de criar vetores

- `c()`
- `:`
- `seq()`
- `rep()`




#### Operações com vetores

O `R` é capaz de executar muitas operações em vetores e escalares.


```r
x = 1:10  # Um vetor
x + 1     # Soma um escalar à cada elemento do vetor
```

```
##  [1]  2  3  4  5  6  7  8  9 10 11
```

```r
2 * x     # Multiplica todos os elementos por 2
```

```
##  [1]  2  4  6  8 10 12 14 16 18 20
```

```r
2 ^ x     # Eleva 2 na potência correspondente a cada elemento de x
```

```
##  [1]    2    4    8   16   32   64  128  256  512 1024
```

```r
sqrt(x)   # Calcula a raíz quadrada de cada elemento de x
```

```
##  [1] 1.000000 1.414214 1.732051 2.000000 2.236068 2.449490 2.645751 2.828427
##  [9] 3.000000 3.162278
```

```r
log(x)    # Calcula o log natural de cada elemento de x
```

```
##  [1] 0.0000000 0.6931472 1.0986123 1.3862944 1.6094379 1.7917595 1.9459101
##  [8] 2.0794415 2.1972246 2.3025851
```

We see that when a function like `log()` is called on a vector `x`, a vector is returned which has applied the function to each element of the vector  `x`.



#### Operadores lógicos com vetores

Em `R`, operadores lógicos também funcionam com vetores:


```r
x = c(5,3,1,9,27,90)
```


```r
x == 9
```

```
## [1] FALSE FALSE FALSE  TRUE FALSE FALSE
```

```r
x != 9
```

```
## [1]  TRUE  TRUE  TRUE FALSE  TRUE  TRUE
```

```r
x > 9
```

```
## [1] FALSE FALSE FALSE FALSE  TRUE  TRUE
```

```r
x < 9
```

```
## [1]  TRUE  TRUE  TRUE FALSE FALSE FALSE
```


```r
x == 9 & x != 9
```

```
## [1] FALSE FALSE FALSE FALSE FALSE FALSE
```

```r
x == 9 | x != 9
```

```
## [1] TRUE TRUE TRUE TRUE TRUE TRUE
```

Outra operação importante que podemos destacar


```r
x[x > 9]
```

```
## [1] 27 90
```

```r
x[x != 9]
```

```
## [1]  5  3  1 27 90
```



```r
sum(x > 9)
```

```
## [1] 2
```

```r
as.numeric(x > 9)
```

```
## [1] 0 0 0 0 1 1
```

Usamos a função `sum()` em um vetor de valores lógicos `TRUE` e `FALSE` ( resultado de `x>3`) e resultado foi um valor numérico. A operação apenas *contou* quantos vezes `x>3` resultou em `TRUE`. Durante a chamada de `sum()`, o `R` primeiro *coerce* (*força*)  automaticamente o lógico para numérico, em que `TRUE` é `1` e `FALSE` é `0`. Essa coerção do lógico para o numérico acontece na maioria das operações matemáticas.

#### Função `which()`


```r
# which (dondição de x) retorna verdadeiro / falso
# cada índice de x em que a condição é verdadeira
x = c(5,3,1,9,27,90)
which(x > 9)
```

```
## [1] 5 6
```

```r
x[which(x > 9)]
```

```
## [1] 27 90
```

```r
max(x)
```

```
## [1] 90
```

```r
which(x == max(x))
```

```
## [1] 6
```

```r
which.max(x)
```

```
## [1] 6
```

### Tarefa 2

1. Crie um vetor preenchido com 10 números sorteados na distribuição uniforme discreta em {1,2,3,4,5,6} (dica: use a função `sample()`) e armazene-os em `x`.
1. Usando o subconjunto lógico como acima, obtenha todos os elementos de `x` maiores que 2 e armazene-os em` y`.
1. Usando a função `which`, armazene os *índices* de todos os elementos de `x` que são maiores que 2 em `iy`.
1. Verifique se `y` e `x[iy]` são idênticos.




### Matrizes

O `R` também pode ser usado para cálculos de **matriz**. Matrizes têm linhas e colunas contendo um único tipo de dados. Em uma matriz, a ordem das linhas e colunas é importante. (Isso não se aplica à *dataframe*, que é um outro tipo de dado que veremos mais adiante).

Matrizes podem ser criadas usando a função `matrix`.


```r
x = 12:1
x
```

```
##  [1] 12 11 10  9  8  7  6  5  4  3  2  1
```

```r
X = matrix(x, nrow = 3, ncol = 4)
X
```

```
##      [,1] [,2] [,3] [,4]
## [1,]   12    9    6    3
## [2,]   11    8    5    2
## [3,]   10    7    4    1
```

Note que o `R` é **case sensitive** (`x` vs `X`).

Por padrão, a função `matrix` preenche seus dados na matriz coluna por coluna. Mas também podemos dizer ao `R` para preencher as linhas:


```r
W = matrix(x, nrow = 3, ncol = 4, byrow = TRUE)
W
```

```
##      [,1] [,2] [,3] [,4]
## [1,]   12   11   10    9
## [2,]    8    7    6    5
## [3,]    4    3    2    1
```

Também podemos criar uma matriz de uma dimensão especificada onde cada elemento é o mesmo, neste caso, `0`.


```r
Y = matrix(0, 2, 3)
Y
```

```
##      [,1] [,2] [,3]
## [1,]    0    0    0
## [2,]    0    0    0
```


#### Matriz diagonal
Para criar uma matriz diagonal podemos usar a função `diag()`


```r
diag(4)   # cria matriz identidade 4x4
```

```
##      [,1] [,2] [,3] [,4]
## [1,]    1    0    0    0
## [2,]    0    1    0    0
## [3,]    0    0    1    0
## [4,]    0    0    0    1
```

```r
diag(4,5) # cria uma matriz digonal 4x4, em que os elementos da diagonal são 5
```

```
##      [,1] [,2] [,3] [,4] [,5]
## [1,]    4    0    0    0    0
## [2,]    0    4    0    0    0
## [3,]    0    0    4    0    0
## [4,]    0    0    0    4    0
## [5,]    0    0    0    0    4
```

Como vetores, matrizes podem ser acessadas usando colchetes, `[]`. No entanto, como as matrizes são bidimensionais, precisamos especificar uma linha e uma coluna ao fazer o subconjunto.

```r
X
```

```
##      [,1] [,2] [,3] [,4]
## [1,]   12    9    6    3
## [2,]   11    8    5    2
## [3,]   10    7    4    1
```

```r
X[1, 2] # primeira linha e na segunda coluna
```

```
## [1] 9
```
 Também podemos acessar uma linha ou coluna inteira.


```r
X[1, ]
```

```
## [1] 12  9  6  3
```

```r
X[, 2]
```

```
## [1] 9 8 7
```

#### Elementos da matriz
Também podemos usar vetores para acessar subconjunto com mais de uma linha ou coluna por vez. Aqui acessamos à primeira e terceira coluna da segunda linha:


```r
X[2, c(1, 3)] # segunda linha, primeira e terceira coluna
```

```
## [1] 11  5
```


```r
X[c(2,1), c(1, 3)] # segunda e priemira linha, primeira e terceira coluna
```

```
##      [,1] [,2]
## [1,]   11    5
## [2,]   12    6
```


#### Funções `rbind()` e  `cbind`
As matrizes também podem ser criadas combinando vetores como colunas, usando `cbind`, ou combinando vetores como linhas, usando `rbind`.


```r
x = 1:4
rev(x)
```

```
## [1] 4 3 2 1
```

```r
rep(1,4)
```

```
## [1] 1 1 1 1
```


```r
rbind(x, rev(x), rep(1, 4))
```

```
##   [,1] [,2] [,3] [,4]
## x    1    2    3    4
##      4    3    2    1
##      1    1    1    1
```


```r
cbind(col_1 = x, col_2 = rev(x), col_3 = rep(1, 4))
```

```
##      col_1 col_2 col_3
## [1,]     1     4     1
## [2,]     2     3     1
## [3,]     3     2     1
## [4,]     4     1     1
```

Ao usar `rbind` e` cbind`, você pode especificar nomes de "argumentos" que serão usados como nomes de colunas.


#### Operações com Matrizes
O `R` pode então ser usado para realizar cálculos de matriz.


```r
x = 1:12
y = 12:1
X = matrix(x, 3, 4)
Y = matrix(y, 3, 4)
X
```

```
##      [,1] [,2] [,3] [,4]
## [1,]    1    4    7   10
## [2,]    2    5    8   11
## [3,]    3    6    9   12
```

```r
Y
```

```
##      [,1] [,2] [,3] [,4]
## [1,]   12    9    6    3
## [2,]   11    8    5    2
## [3,]   10    7    4    1
```


```r
X + Y   # Soma elemento por elemento
```

```
##      [,1] [,2] [,3] [,4]
## [1,]   13   13   13   13
## [2,]   13   13   13   13
## [3,]   13   13   13   13
```

```r
X - Y   # Subtração elemento por elemento
```

```
##      [,1] [,2] [,3] [,4]
## [1,]  -11   -5    1    7
## [2,]   -9   -3    3    9
## [3,]   -7   -1    5   11
```

```r
X * Y   # Multiplicação elemento por elemento
```

```
##      [,1] [,2] [,3] [,4]
## [1,]   12   36   42   30
## [2,]   22   40   40   22
## [3,]   30   42   36   12
```

```r
X / Y   # Divisão elemento por elemento
```

```
##            [,1]      [,2]     [,3]      [,4]
## [1,] 0.08333333 0.4444444 1.166667  3.333333
## [2,] 0.18181818 0.6250000 1.600000  5.500000
## [3,] 0.30000000 0.8571429 2.250000 12.000000
```


Note que `X * Y` **não** é multiplicação de matrizes. É multiplicação de *elemento por elemento*. (O mesmo para `X/Y`).

Para a multiplicação de matrizes usa-se `%*%`. Outras funções para operações com matrizes são `t()`, que fornece a transposição de uma matriz e `solve()`, que retorna a inversa de uma matriz quadrada, se for invertível.


```r
x = 1:9
y = 9:1
X = matrix(x, 3, 3)
Y = matrix(y, 3, 3)
X %*% Y
```

```
##      [,1] [,2] [,3]
## [1,]   90   54   18
## [2,]  114   69   24
## [3,]  138   84   30
```

```r
t(X)
```

```
##      [,1] [,2] [,3]
## [1,]    1    2    3
## [2,]    4    5    6
## [3,]    7    8    9
```

### Arrays

Um vetor é um `array` unidimensional. Uma matriz é um `array` bidimensional. Em `R`, o usuário pode criar `arrays` de dimensionalidade arbitrária `N`. Por exemplo:


```r
A = 1:16
B = array(data = A,dim = c(4,2,2))
C = array(data = A,dim = c(4,2,2,3))  # Recicla A=1:16
B
```

```
## , , 1
## 
##      [,1] [,2]
## [1,]    1    5
## [2,]    2    6
## [3,]    3    7
## [4,]    4    8
## 
## , , 2
## 
##      [,1] [,2]
## [1,]    9   13
## [2,]   10   14
## [3,]   11   15
## [4,]   12   16
```


Note que `B` são simplesmente *duas*  matrizes (4,2) armazenadas como *páginas* em um mesmo objeto/variável. Similarmente, `C` teria duas *páginas* e mais 3 registros em uma quarta dimensão. E assim por diante.

Para acessar esses elementos, o procedimento é similar ao de uma matriz ou um vetor, cuidando para indexar cada dimensão:


```r
B[ ,1,1]    # Todos os elementos da col 1, página 1 
```

```
## [1] 1 2 3 4
```

```r
B[2:3, , ]  # Linhas 2:3 de todas as páginas e colunas
```

```
## , , 1
## 
##      [,1] [,2]
## [1,]    2    6
## [2,]    3    7
## 
## , , 2
## 
##      [,1] [,2]
## [1,]   10   14
## [2,]   11   15
```

```r
B[2,2, ]    # linha 2, coluna 2 de todas as páginas.
```

```
## [1]  6 14
```


#### Tarefa 3

1. Crie um vetor contendo `1,2,3,4,5` chamado-o de v.
1. Crie uma matriz (2,5) `m` contendo os dados `1,2,3,4,5,6,7,8,9,10`. A primeira linha deve ser "1,2,3,4,5".
1. Realize a multiplicação da matriz de `m` com `v`. Use o comando `%*%`. Qual a dimensão da saída?
1. Por que `v%*% m` não funciona?


### Listas


Uma lista é uma estrutura de dados unidimensional *heterogênea*. Portanto, é indexado como um vetor com um único valor inteiro (ou com um nome), mas cada elemento pode conter um elemento de qualquer tipo. As listas são semelhantes a um objeto `python` ou `julia`.





Muitas estruturas e saídas do `R` são listas. As listas são objetos extremamente úteis e versáteis; portanto, é interessante entender sua utilização:


```r
# Listas simples sem nomes nas entradas
list(12, "Bom dia", TRUE)
```

```
## [[1]]
## [1] 12
## 
## [[2]]
## [1] "Bom dia"
## 
## [[3]]
## [1] TRUE
```

```r
# Listas com nome para cada entrada
lista1 = list(
  a = c(1, 2, 3, 4),
  b = TRUE,
  c = "Bom dia!",
  d = function(arg = 10) {print("Em Brasília, 19h!")},
  e = diag(4)
)
```


Os elementos das listas podem ser acesados usando duas sintaxes, o operador `$` e colchetes `[]`. O operador `$` retorna um elemento **nomeado** de uma lista. A sintaxe `[]` retorna uma **lista**, enquanto a `[[]]` retorna um **elemento** de uma lista.

- `lista1[1]` retorna uma lista que contém o primeiro elemento
- `lista1[[1]]`  retorna o primeiro elemento da lista, neste caso, um vetor.


```r
# elementos da lista
lista1$e
```

```
##      [,1] [,2] [,3] [,4]
## [1,]    1    0    0    0
## [2,]    0    1    0    0
## [3,]    0    0    1    0
## [4,]    0    0    0    1
```

```r
lista1[[1:2]]
```

```
## [1] 2
```

```r
lista1[c("e", "a")]
```

```
## $e
##      [,1] [,2] [,3] [,4]
## [1,]    1    0    0    0
## [2,]    0    1    0    0
## [3,]    0    0    1    0
## [4,]    0    0    0    1
## 
## $a
## [1] 1 2 3 4
```

```r
lista1["e"]
```

```
## $e
##      [,1] [,2] [,3] [,4]
## [1,]    1    0    0    0
## [2,]    0    1    0    0
## [3,]    0    0    1    0
## [4,]    0    0    0    1
```

```r
lista1[["e"]]
```

```
##      [,1] [,2] [,3] [,4]
## [1,]    1    0    0    0
## [2,]    0    1    0    0
## [3,]    0    0    1    0
## [4,]    0    0    0    1
```

```r
lista1$d
```

```
## function(arg = 10) {print("Em Brasília, 19h!")
```

```r
lista1$d(arg = 1)
```

```
## [1] "Em Brasília, 19h!"
```

#### Tarefa 4 {-}

1. Copie e cole o código acima para `list1` na sua sessão do `R`. Lembre-se de que `list` pode conter qualquer tipo de objeto `R`. Como por exemplo, outra lista! Portanto, crie uma nova lista `lista2` que tenha dois campos: o primeiro campo chamado `"Isso"` com o conteúdo da string `"é impressionante"` e um segundo campo chamado `"lista"` que contém `lista1`.
1. Acessar os elementos é como em uma lista simples, apenas com várias camadas agora. Obtenha o elemento `c` de `lista1` em `lista2`!
1. Componha uma nova string com primeiro elemento em `lista2`, o elemento sob o rótulo `"Isso"`. Use a função `paste` para imprimir `R é impressionante` na tela.



## Programação básica

Nesta seção, ilustramos alguns conceitos gerais relacionados à programação.

### Variáveis

 Na programação, uma variável  denota um *objeto*. Outra maneira de dizer isso é que uma variável é um nome ou um *label* para algo:


```r
x = 2
y = "doce"
z = function(x){log(x)}
```


Aqui, `x` se refere ao valor `2`, `y` refere-se a *string* "doce" e `z` é o nome de uma função que calcula $\log{x}$. Observe que o argumento `x` da função é diferente do `x` que acabamos de definir.


```r
x
```

```
## [1] 2
```

```r
z(9)
```

```
## [1] 2.197225
```

```r
z(x)
```

```
## [1] 0.6931472
```



### Laços (*Loops*), `for` e `while`


Laços (*Loops*) são uma construção de programação muito importante. Como o nome sugere, em um *loop*, a programação *repetidamente* circula um conjunto de instruções, até que alguma condição diga para parar. Uma construção muito poderosa, porém simples, é que o programa pode *contar quantas etapas* já executou - o que pode ser importante saber para muitos algoritmos. Uma forma de fazer um *loop* é o usando o `for` . 

#### Uso do `for()`

Por exemplo, para executar uma tarefa 3 vezes, usamos 



```r
for (i in 1:3){
  print(i)
}
```

```
## [1] 1
## [1] 2
## [1] 3
```

A iteração pode ser feita sobre um vetor qualquer de objetos


```r
for (i in c("milho","soja","trigo")){
  print(paste("Produção de ",i))  # a função paste() conecta as strings
}
```

```
## [1] "Produção de  milho"
## [1] "Produção de  soja"
## [1] "Produção de  trigo"
```

Podemos fazer *loops* dentro de *loops* (*nested loops*)


```r
for (i in 2:3){
  # primeiro: para cada i
  for (j in c("milho","soja","trigo")){
    # segundo: para cada j 
    print(paste("Usar",i,"Kg de",j,"na fórmula."))
  }
}
```

```
## [1] "Usar 2 Kg de milho na fórmula."
## [1] "Usar 2 Kg de soja na fórmula."
## [1] "Usar 2 Kg de trigo na fórmula."
## [1] "Usar 3 Kg de milho na fórmula."
## [1] "Usar 3 Kg de soja na fórmula."
## [1] "Usar 3 Kg de trigo na fórmula."
```

#### Uso do `while()`

A função `while()`, como o próprio nome sugre, é usada para executar uma tarefa até que uma certa condição aconteça, ou enquanto certa condição não aconteça.



```r
Kg=27
while(Kg<30){
  print(paste("Peso é",Kg)) # Enquanto peso é menor do que 30, executa
  Kg=Kg+1 # Enquanto peso é menor do que 30, soma 1 no peso atual
}
```

```
## [1] "Peso é 27"
## [1] "Peso é 28"
## [1] "Peso é 29"
```


## Funções

Até agora, usamos funções, mas na verdade não discutimos alguns de seus detalhes. Uma função é um conjunto de instruções que o `R` executa para nós, como as coletadas em um arquivo *script*. O bom é que as funções são muito mais flexíveis que os scripts, pois podem depender de *argumentos de entrada*, que alteram a maneira como a função se comporta. Aqui está como definir uma função:


```r
nome_da_funcao <- function(arg1,arg2=valor_padrao){
  # corpo da função
  # faça coisas com arg1 e arg2
  # a última linha será retornada
}
```

Um exemplo de uma função símples


```r
 fun1<- function(seu_nome = "Baby"){
  paste("Seja bem vindo ao R,",seu_nome)
  # pode-se escrever também
  # return(paste("Seja bem vindo ao R,",seu_nome))
}
#chamando a função sem nenhum argumento, o argumento seu_nome padrão será Baby
fun1()
```

```
## [1] "Seja bem vindo ao R, Baby"
```

Agora tente com o seu nome:


```r
fun1("Rabicó")
```

```
## [1] "Seja bem vindo ao R, Rabicó"
```

Just typing the function name returns the actual definition to us, which is handy sometimes:


```r
fun1
```

```
## function(seu_nome = "Baby"){
##   paste("Seja bem vindo ao R,",seu_nome)
##   # pode-se escrever também
##   # return(paste("Seja bem vindo ao R,",seu_nome))
## }
## <bytecode: 0x000000000c70a7c0>
```

Funções são maneiras de dizer ao `R` o que deve ser feito. É como se ensinássemos uma tarefa ao software para que ele passe a executá-la sempre que solicitado. Um dica para não acumular erros durante a programação é dividir o *script* em várias funções. Quando se tem um conjunto de funções que realiza um conjunto de tarefas mais amplas, pode-se juntar tudo em um pacote (`package`), submeter ao `CRAN` para disponibilizar à comunidade. 

#### Tarefa 6 {-}

1. Escreva um _loop_ `for` para escrever o seu nome, letra por letra. Comece com um vetor com as letras do seu nome. 
1. Modifique esse *loop* para que cada iteração leve aproximadamente um segundo. Você pode conseguir isso adicionando o comando `Sys.sleep(1)` abaixo da linha que imprime "iteração i nome_parcial", em que `i` é a correspondente iteração no _loop_.

## Operador `Pipe` 

Para manipulação de dados é interessante conhecer a lógia do operador `pipe`,  `%>%`. Vários pacotes são construídos em cima dessa lógica, que busca encadear ações do `R` de uma forma mais compreensível. Vamos instalar o pacote `magrittr` para começar a usar `%>%`.


```r
install.packages("magrittr")
library(magrittr)
```

```
## Warning: package 'magrittr' was built under R version 3.6.3
```

```
## 
## Attaching package: 'magrittr'
```

```
## The following object is masked from 'package:tidyr':
## 
##     extract
```

Vejamos como funciona.

```r
sin(cos(pi))
pi%>%cos%>%sin
```

Ambas as expressões acima são equivalentes. Parece redundante e que não se tem nehuma vantagem ao usar o `%>%`. No entanto, para um caso envolvendo dados reais, podemos verificar sua utilidade




```r
library(ggplot2)
library(dplyr)
head(fogo)
```

```
##   year state   month number       date
## 1 1998  Acre Janeiro      0 1998-01-01
## 2 1999  Acre Janeiro      0 1999-01-01
## 3 2000  Acre Janeiro      0 2000-01-01
## 4 2001  Acre Janeiro      0 2001-01-01
## 5 2002  Acre Janeiro      0 2002-01-01
## 6 2003  Acre Janeiro     10 2003-01-01
```

```r
fogo$date=as.Date(fogo$date)
fogo%>%na.omit%>%dplyr::filter(month=="Setembro"&state=="Rondonia")%>%ggplot(aes(x = date, y = number)) + geom_line() +theme_minimal()+ labs(x = "Data", 
       y = "Números de Incêndios",
       title = "Focos de incêndio em Rondônia nos meses de Setembro") 
```

<img src="00-intro_files/figure-html/unnamed-chunk-63-1.png" width="672" />
