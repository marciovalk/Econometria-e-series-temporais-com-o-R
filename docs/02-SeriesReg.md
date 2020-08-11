---
output:
  pdf_document: default
  html_document: default
---


# Séries temporais no contexto de regressão {#streg}

Neste capítulo abordamos regressão no contexto de séries temporais. Começamos 
definindo o que é uma série temporal e introduzimos algumas propriedades teóricas.




## Introdução

Uma série temporal é qualquer conjunto de observações ordenadas no tempo. Alguns
exemplos são citados abaixo:


|    a) Estimativas trimestrais do Produto Interno Bruto (PIB);

|    b) Valores diários da temperatura em Campo Bom;

|    c) Índices diários da bolsa de valores de São Paulo;

|    d) Quantidade anual de chuva na cidade do Porto Alegre;

|    e) Um registro de marés no porto de Santos.

Nos exemplos de a) a d) temos séries temporais discretas, enquanto que e) é um exemplo de série contínua. Podemos obter uma série temporal discreta a partir da amostragem de uma série temporal contínua considerando intervalos de tempos iguais, $\Delta t$. Assim para analisar a série e) será necessário amostrá-la, convertendo-a e observando-a no intervalo de tempo $[0,T]$, supondo uma série discreta com $N$ pontos, em que $N = \Delta t/T$ (T horas). Existem dois enfoques utilizados na análise de séries temporais. Em ambos, o objetivo é construir modelos para estas séries. No primeiro enfoque, a análise é feita no domínio temporal e os modelos propostos são modelos paramétricos (com um número finito de parâmetros). No segundo, a análise é conduzida no domínio de frequências e os modelos propostos são modelos não-paramétricos. Dentre os modelos paramétricos temos, por exemplo, os modelos ARIMA, que serão estudados neste curso nos próximos capítulos. No domínio de frequências temos a análise espectral, que tem inúmeras aplicações em ciências físicas e engenharia, principalmente na engenharia elétrica, e que consiste em decompor a série dada em componentes de frequências e onde a existência do espectro é a característica fundamental. Este tipo de análise não será estudado nestas notas de aulas, para detalhes o aluno deve consultar @watts1968, @koopmans1974, @morettin1978 e @marple1980.



## Exemplos de séries temporais

\BeginKnitrBlock{example}<div class="example"><span class="example" id="exm:exemptemp"><strong>(\#exm:exemptemp) </strong></span>Vamos supor que desejamos medir a temperatura média do ar, de um local,
durante 24 horas, poderíamos obter um gráfico semelhante a figura abaixo:</div>\EndKnitrBlock{example}





<div class="figure" style="text-align: center">
<img src="02-SeriesReg_files/figure-html/figts1-1.png" alt="Temperaturas médias diárias nas cidades de Manaus (MA) e Porto Alegre (POA)" width="90%" />
<p class="caption">(\#fig:figts1)Temperaturas médias diárias nas cidades de Manaus (MA) e Porto Alegre (POA)</p>
</div>



Cada curva do gráfico é chamada de trajetória ou série temporal ou função amostral. No gráfico acima $Z_{(j)}(t)$ é o valor da temperatura no instante $t$, para a $j$-ésima trajetória ($j$-ésimo ponto de observação). Para cada $t$ fixo, teremos os valores de uma variável aleatória $Z(t)$ que terá certa distribuição de probabilidade. Na realidade o que chamamos de série temporal, é uma parte de uma trajetória, dentre muitas que poderiam ter sido observadas. O parâmetro $t$ pode ser função de algum outro parâmetro físico como por exemplo: espaço e volume.

## Regressão com dados de séries temporais

Nesta seção estudaremos modelos de regressão cujas variáveis são séries temporais. O interesse principal recai sobre as condições necessárias para que o estimador de MQO apresente boas propriedades.


### Diferença entre dados de séries temporais  e dados de corte transversal


A primeira diferença entre dados de séries temporais e  dados de corte transversal é que uma série temporal tem uma ordenação temporal. Outra característica,  é que não temos mais independência entre as observações,  ou seja, não temos mais uma amostra aleatória de indivíduos. Logo, para estimar um modelo do  tipo
\begin{equation}
 y_t = \beta_0 + \beta_1 + \beta_2 x_{t1}+ x_{t2} + \ldots+\beta_k x_{tk}+ u_t,
 (\#eq:eq1STR)
\end{equation}
são necessárias novas suposições para que o estimador de MQO tenha boas propriedades.








### Modelos de regressão  de séries temporais



#### Modelos  estáticos

Suponha que temos dados de séries temporais disponíveis  para  duas  variáveis, digamos $y$  e $z$,  em que $y_t$ e $z_t$  são datadas contemporaneamente.  Um modelo que relaciona $y$ a $z$ é:
\begin{equation}
y_t = \beta_0 + \beta_1 z_t + u_t,  \,\,\,\,t=1,2,\ldots,n.
(\#eq:modelstatic)
\end{equation}
O nome "Modelo Estático"  deriva  do  fato de relacionar as variáveis de forma  contemporânea.

\BeginKnitrBlock{example}<div class="example"><span class="example" id="exm:exampcurvphilips"><strong>(\#exm:exampcurvphilips) </strong></span>Um exemplo de  modelo estático é a **curva de Phillips estática**, representada por:
\begin{equation}
inf_t = \beta_0 + \beta_1 desemp_t + u_t,
(\#eq:philcurve)
\end{equation}
em que $inf_t$ é a inflação anual e $desemp_t$ é  a taxa de  desemprego.</div>\EndKnitrBlock{example}

Este modelo é usado  para  estudar a  relação de trocas contemporânea entre  $inf_t$ e $desemp_t$ pressupondo uma \emph{taxa natural de desemprego}  e expectativas inflacionárias constantes.



### Modelos  de defasagem distribuída finita


Em um \emph{modelo de defasagem distribuída finita} (MDD) permite-se que uma ou mais variáveis
afetem $y$ com defasagens
\begin{equation}
y_t = \alpha_0 + \delta_0 z_t+\delta_1 z_{t-1} + \delta_2 z_{t-2} + u_t,
(\#eq:eqmdd2)
\end{equation}
que é  um MDD de \emph{ordem 2}. De modo mais geral, um modelo de defasagem distribuída de ordem $q$ incluirá $q$  defasagens de $z$.

Para interpretar os coeficientes em \@ref(eq:eqmdd2)  suponha  que $z$  seja constante igual a $c$,
em todos os  períodos  de tempo antes de $t$ (\ldots, $z_{t-2}=c$, $z_{t-1}=c$). Em $t$,  $z$ aumenta em  uma  unidade, ou seja, $z_t=c+1$,  e,  em seguida,  retorna ao seu  nível  anterior em $t+1$, isto é,  $z_{t+1}=c$.


Para  enfatizar o  efeito \emph{ceteris  paribus} de  $z$ sobre  $y$, suponhamos  que o termo de erro em  cada período seja zero. Então,
\begin{eqnarray*}
y_{t-1}&=&\alpha_0+\delta_0c+\delta_1c+\delta_2c\\
y_{t}&=&\alpha_0+\delta_0(c+1)+\delta_1c+\delta_2c\\
y_{t+1}&=&\alpha_0+\delta_0c+\delta_1(c+1)+\delta_2c\\
y_{t+2}&=&\alpha_0+\delta_0c+\delta_1c+\delta_2(c+1)\\
y_{t+3}&=&\alpha_0+\delta_0c+\delta_1c+\delta_2c,\\
\end{eqnarray*}
e  assim por diante. Das duas primeiras equações temos
\begin{equation*}
y_t-y_{t-1} =\delta_0,
\end{equation*}
mostra que $\delta_0$ é a mudança imediata em $y$ em razão  do aumento de uma unidade em $z$ no tempo $t$. Denomina-se $\delta_0$ como \emph{propensão de impacto} ou \emph{multiplicador de impacto}.

Da mesma forma,
\begin{equation*}
\delta_1  =  y_{t+1} - y_{t-1},
\end{equation*}
é a  mudança em $y$ após a mudança temporária e
\begin{equation*}
\delta_2  =  y_{t+2} - y_{t-1},
\end{equation*}
é a mudança em $y$ dois períodos após a mudança. Em $t+3$,  $y$ retornou ao seu nível inicial $y_{t+3}=y_{t-1}$.  Isso ocorre porque presumimos que apenas duas defasagens de $z$ aparecem em \@ref(eq:eqmdd2).

Quando traçamos um gráfico de $\delta_j$ como uma função  de $j$ obtemos a \emph{distribuição de defasagem}, que resume o efeito dinâmico  que um aumento temporário em $z$ tem em $y$.

No entanto,  o  aumento em $z$ pode ser permanente. Suponhamos que antes do  tempo $t$ $z$ é constante igual a $c$, ou seja, $z_s=c$,  para $s<t$, e no  tempo $t$, $z$ sofre um aumento permanente de uma unidade no  tempo  $t$,  ou seja, $z_s=c+1$ para $s\geq t$. Novamente,  fazendo os erros iguais  a zero,  temos
\begin{eqnarray*}
y_{t-1}&=&\alpha_0+\delta_0c+\delta_1c+\delta_2c\\
y_{t}&=&\alpha_0+\delta_0(c+1)+\delta_1c+\delta_2c\\
y_{t+1}&=&\alpha_0+\delta_0(c+1)+\delta_1(c+1)+\delta_2c\\
y_{t+2}&=&\alpha_0+\delta_0(c+1)+\delta_1(c+1)+\delta_2(c+1)\\
\end{eqnarray*}
e assim por diante. Com  o  aumento permanente em $z$,  depois de um  período $y$ aumentou $\delta_0+\delta_1$, e depois de  dois períodos, $y$ aumentou $\delta_0+\delta_1+\delta_2$. Isso mostra que a soma dos coeficientes de $z$ atual e  defazadas,
\begin{equation}
 \delta_0+\delta_1+\delta_2
 (\#eq:eqPLP2)
\end{equation}
é a \emph{mudança de  longo prazo} em $y$ quando há um aumento permanente em $z$. A equação \@ref(eq:eqPLP2) é chamada \emph{propensão  de longo prazo (PLP)}.

A generalização para $q$ defasagens é imediata.


## Suposições para modelos com séries temporais
Nesta seção o objetivo é mostrar  como as hipóteses clássicas  devem ser alteradas
para cobrir regressão de séries temporais.


### Inexistência de viés do MQO

Para que as estimativas via MQO dos parâmetros de um modelo de regressão com séries temporais não  sejam viesadas são necessárias a seguintes hipóteses:

<br>

> **_Suposição  TS.1:_**  \emph{(linearidade nos parâmetros)}.
O processo estocástico 
\[\{(x_{t1}, x_{t2},\ldots, y_t):\,\,\, t = 1, 2,\ldots, n\}\]
 segue o modelo linear:
\[y_t = \beta_0 + \beta_1 x_{t1} + \cdots + \beta_k x_{tk}+u_t,\]
em  que $\{u_t:\,\,\,t=1,2,\ldots,n\}$ é a sequência de erros ou perturbações.

<br>

> **_Suposição  TS.2:_** \emph{(Inexistência  de colineariedade Perfeita)}. Na amostra, nenhuma das variáveis independentes é constante  ou  combinação linear perfeita das outras.

<br>

As hipóteses **TS.1** e  **TS.2** são  essencialmente as mesmas daquelas usadas no contexto de
dados de cortes transversais.

<br>

> **_Suposição  TS.3:_** \emph{(Média condicional zero ou exogeneidade estrita)}. O termo de erro em qualquer dado período é não correlacionado com as variáveis explicativas em todos os períodos de tempo,  ou seja $\mathbb{E} (u_t | X) = 0$, para $ t = 1, 2,\ldots, n$.

<br>

Analisando-se a hipótese TS.3, percebemos que ela difere da hipótese clássica.
Observe que a hipótese TS.3 exige que o erro no tempo $t$, $u_t$ seja não  correlacionado
com cada variável explicativa em  \emph{todos} os períodos de  tempo.

Se  em termos de média condicional, temos somente a condição de não correlação somente no  tempo
$t$, da forma
\begin{equation}
\mathbb{E}(u_t|x_{1t},\ldots,x_{tk})=\mathbb{E} (u_t | X_t) = 0,
(\#eq:exoc)
\end{equation}
diz-se que vale a \emph{exogeneidade contemporânea} das variáveis explicativas. Exogeneidade contemporânea só será suficiente em grandes amostras.
\@ref(eq:exoc)



A  hipótese **TS.3** é muito forte e muitas vezes não verificada. Nos seguintes exemplos  podemos ver como ela pode  ser verificada na prática.

<br>

\BeginKnitrBlock{example}<div class="example"><span class="example" id="exm:examphomic"><strong>(\#exm:examphomic) </strong></span>Suponha que  a taxa de homicídios  ($homi_t$) em  uma cidade em termos do número  de  policiais per capita ($polpc_t$)
\[homi_t = \beta_0 + \beta_1 polpc_t + u_t.\]

O termo de  erro $u$ precisaria ser não correlacionados com os valores atuais,os valores passados e futuros de $polpc_t$. Podemos aceitar que $u$ não é correlacionado com valores corrente e valores passados do regressor. Mas é evidente que um aumento em $u$ hoje, provavelmente, levará a políticas que tentem aumentar $polpc_t$ no futuro.  Logo **TS.3** falha.</div>\EndKnitrBlock{example}

Quando  $u$ é correlacionado com o passado dos regressores, podemos resolver o problema incluindo defasagens dos regressores e utilizando  um modelo de defasagem distribuída. Mas não podemos ter, de forma alguma, a influência de $u$ no futuro dos regressores.



\BeginKnitrBlock{theorem}<div class="theorem"><span class="theorem" id="thm:teovies"><strong>(\#thm:teovies) </strong></span> Sob as Hipóteses **ST.1**, **ST.2** e **ST.3** os estimadores de MQO são não viesados condicionados a $X$ e, portanto, também incondicionalmente:
 \begin{equation*}
   \mathbb{E}(\hat{\beta}_j)=\beta_j, \,\,\,j=1,\ldots,k.
 \end{equation*}</div>\EndKnitrBlock{theorem}




### Variância dos estimadores MQO


É necessário mais duas hipóteses para completar o conjunto de hipóteses de Gauss-Markov para
regressões de séries temporais. A primeira delas é familiar da análise de corte transversal.

<br>

> **_Suposição  TS.4:_** \emph{(Homoscedasticidade)}. Condicional a $X$, a variância de $u_t$ é a mesma para todo $t$:
$$Var(u_t | X) = Var(u_t)=\sigma^2,$$ para $ t = 1, 2,\ldots, n$.

<br>

> **_Suposição  TS.5:_** \emph{(Inexistência de Correlação Serial)}.
Condicional a $X$, os erros em dois períodos de tempos diferentes são não correlacionados:
$$Corr(u_t ,u_s| X) =0,$$ para todo $ t \neq s$.


Com este conjunto de condições podemos enunciar o teorema de Gauss-Markov no contexto de séries temporais.

\BeginKnitrBlock{theorem}\iffalse{-91-84-101-111-114-101-109-97-32-100-101-32-71-97-117-115-115-45-77-97-114-107-111-118-93-}\fi{}<div class="theorem"><span class="theorem" id="thm:teogm"><strong>(\#thm:teogm)  \iffalse (Teorema de Gauss-Markov) \fi{} </strong></span>Sob as Hipóteses **ST.1** a **ST.5** os estimadores de MQO são os melhores estimadores lineares não viesados condicionais a $X$, ou seja, são **_BLUE_**.</div>\EndKnitrBlock{theorem}


### Inferência sob as hipóteses do modelo linear clássico

Para que sejam válidos os testes $t$, $F$ e outros testes estatísticos baseadas nos erros padrões é necessário adicionar mais uma hipótese a respeito da distribuição dos erros. Esta hipótese é análoga à hipótese de normalidade usada para análise de corte transversal.



> **_Suposição  TS.6:_** \emph{(Normalidade)}. Os erros $u_t$ são independentes de $X$ e são i.i.d. com distribuição normal com média zero e variância $\sigma^2$
$$u_t\sim\mathcal{N}(0,\sigma^2),$$  para $ t = 1, 2,\ldots, n$.





\BeginKnitrBlock{theorem}<div class="theorem"><span class="theorem" id="thm:teoinfmqo"><strong>(\#thm:teoinfmqo) </strong></span>Sob as hipóteses **TS.1** a **TS.6**, as hipóteses do modelo linear clássico para séries temporais, os estimadores MQO são normalmente distribuídos, condicional em $X$. Além disso, a estatística $t$ tem uma distribuição $t$, e cada estatística $F$ tem uma distribuição $F$.</div>\EndKnitrBlock{theorem}

### Tendência

Quando trabalhamos com séries temporais é necessário saber reconhecer se estas séries contém uma tendência temporal. Ignorar o fato de que duas séries temporais podem ser correlacionadas somente porque ambas estão apresentando uma mesma tendência ao longo do tempo, em vez de uma relação causal, pode levar a conclusões errôneas e a possibilidade de uma regressão espúria. Vejamos o exemplo de uma série temporal com tendência temporal:

<br>



```r
#library(readxl)
#library(ggplot2)
# Dados baixados em 25/06/2020 de
# https://seriesestatisticas.ibge.gov.br/series.aspx?vcodigo=PRECO415&t=custo-medio-m2

custo_medio <- read_excel("Dados/custo_medio_m2.xls")
ggplot(custo_medio, aes(x = data, y = cm)) + 
  geom_line()+ theme_light()+labs( x="", y="Custo médio")
```

<div class="figure" style="text-align: center">
<img src="02-SeriesReg_files/figure-html/figcn-1.png" alt="Custo médio do $m^2$ no Brasil a partir do plano real" width="65%" />
<p class="caption">(\#fig:figcn)Custo médio do $m^2$ no Brasil a partir do plano real</p>
</div>

<br>


Um modelo que captura tendência temporal é:
\begin{equation}
y_t = \alpha_0+ \alpha_1t + e_t, \hspace{1cm} t = 1, 2, \ldots,
(\#eq:tendmodel)
\end{equation}
em que assume-se que $\{e_t\}$ é i.i.d. com $\mathbb{E}(e_t)=0$ e $\mbox{Var}(e_t)=\sigma^2$.
Observe que o parâmetro $\alpha_1$ multiplica o tempo, resultando em uma \emph{tendência temporal linear}. Assim, $\alpha_1$ mede a mudança em $y_t$, de um período para o próximo, motivado pela passagem do tempo, mantendo-se todos os outros fatores fixos.

Outros modelos podem ser usados para capturar tendências temporais, dependendo da situação.
No modelo em que o logaritmo natural de $y_t$ (presumindo que $y_t>0$) apresenta uma tendência temporal linear,

\begin{equation}
\log(y_t) = \beta_0+ \beta_1t + e_t, \hspace{1cm} t = 1, 2, \ldots,
(\#eq:logtend)
\end{equation}
diz-se que $y_t$ tem uma **_tendência exponencial_**.


Outra possibilidade é que em vez de uma tendência temporal linear, poderíamos ter uma
**_tendência temporal quadrática_**,

\begin{equation}
y_t = \beta_0+ \beta_1t +\beta_t^2+ e_t, \hspace{1cm} t = 1, 2, \ldots.
(\#eq:quadtend)
\end{equation}



### Usando variáveis de tendência na análise de regressão

Suponha que existam dois fatores observados, $x_{t1}$ e $x_{t2}$ que afetam $y_t$. Além disso,
existem fatores não observados que estão sistematicamente crescendo ou decrescendo ao longo do tempo.
Um modelo que captura isso é:
\begin{equation}
y_t = \beta_0 + \beta_1x_{t1} + \beta_2x_{t2} + \beta_3t + u_t.
(\#eq:tr2)
\end{equation}
Permitindo uma tendência temporal no modelo, reconhece-se que $y_t$ pode estar crescendo
ou decrescendo ao longo do tempo por razões essencialmente não relacionadas a $x_{t1}$ e $x_{t2}$.

A omissão da variável $t$ pode levar ao viés por omissão de variável, especialmente se $x_{t1}$ ou $x_{t2}$ apresentarem algum tipo de tendência, pois elas podem ser altamente correlacionadas com $t$.


Adicionando um termo de tendência linear em um modelo de regressão é a mesma coisa que usar
série "destendenciada" numa regressão. Os estimadores $\beta_1$ e $\beta_2$ do modelo \@ref(eq:tr2) podem ser obtidos através de um procedimento de "remoção da tendência temporal" das séries originais:



Destendenciar uma série envolve regredir cada variável do modelo em $t$ e uma constante (no caso de \@ref(eq:tr2), regredir $y_t$, $x_{t1}$ e $x_{t2}$ contra $t$ e uma constante).

Os resíduos destas regressões, $\ddot{y}_t$, $\ddot{x}_{t1}$ e $\ddot{x}_{t2}$, constituem uma série temporal sem tendência.

Em seguida, realizar a regressão com variáveis retificada,
\begin{equation}
\ddot{y}_t= \delta_1\ddot{x}_{t1}+\delta_2\ddot{x}_{t2}+v,
(\#eq:varrat)
\end{equation}
(não precisa intercepto, será igual a 0). As estimativas via MQO, $\hat{\delta}_1$ e $\hat{\delta}_2$ serão iguais as estimativas $\hat{\beta}_1$ e $\hat{\beta}_2$ da regressão \@ref(eq:tr2).



## Sazonalidade

Sazonalidade ocorre quando uma série exibe comportamentos semelhantes em determinados períodos. Um exemplo é o **Índice de produção física industrial de bens intermediários*. O objetivo do índice é servir como uma medida aproximada da evolução de curto prazo do valor adicionado da indústria, dado um determinado período de referência (base: média de 2012).





```r
#library(readxl)
#library(plotly)
#Fonte: "IBGE - Pesquisa Industrial Mensal - Produção Física"
prodind <- read_excel("Dados/ProducaoIndustrial.xls")
ggplot(prodind,aes(x=Data, y=intermediarios))+
  geom_line(col="#D95F02")+
  labs(x = "",y="Índice")+
  theme_minimal()
```

<div class="figure" style="text-align: center">
<img src="02-SeriesReg_files/figure-html/figpi-1.png" alt="Produção física industrial de Bens Intermediários" width="85%" />
<p class="caption">(\#fig:figpi)Produção física industrial de Bens Intermediários</p>
</div>


É comum que as séries de dados mensais e trimestrais exibam padrões sazonais, mas isso não é uma regra. Por exemplo, não existe padrão sazonal observável nas taxas de juros ou de inflação. Além disso, séries que exibem padrões sazonais são **_ajustadas sazonalmente_** antes de serem informadas para o público.

Uma série ajustada sazonalmente  é a série que teve os fatores sazonais removidos. Existem vários métodos para isso. Um dos métodos mais simples é incluir um conjunto de variáveis dummies sazonais. Seja o seguinte modelo para dados mensais:

\begin{equation}
y_t = \beta_0 + \delta_1fev_t + \delta_2mar_t + \cdots + \delta_{11}dez_t + \beta_1x_{t1} +\cdots + \beta_kx_{tk} + u_t.
(\#eq:saz1)
\end{equation}
em que $fev_t,mar_t,\cdots,dez_t$ são variáveis dummy indicando se o período de tempo $t$ correspondo ao mês apropriado. Nesta formulação, janeiro é o mês-base  e $\beta_0$ seu intercepto. Se colocarmos janeiro no modelo e um intercepto, teremos um problema de multicolineariedade.

Se não existir sazonalidade em $y_t$, dado que controlamos os regressores $x_{tj}$, então
os coeficientes $\delta_1;\ldots; \delta_{11}$ devem ser todos iguais a zero, o que pode ser testado através de um teste $F$.

Considere o modelo  \@ref(eq:saz1), para $k = 2$, ou seja 2 regressores. Podemos obter os seus estimadores, $\hat{\beta}_1$ e $\hat{\beta}_2$, através do seguinte procedimento:

Regrida a variável dependente, e cada um dos regressores, separadamente, contra
uma constante e as dummies mensais e guarde os resíduos, digamos $\ddot{y}_t$, $\ddot{x}_{t1}$ e $\ddot{x}_{t2}$.

Por exemplo,
\begin{equation*}
\ddot{y}_t = y_t-\hat{\alpha}_0 - \hat{\alpha}_1fev_t - \hat{\alpha}_2mar_t -\cdots - \hat{\alpha}_{11}dez_t.
\end{equation*}
Este é o método para dessazonalizar uma série temporal mensal.

Roda a regressão de $\ddot{y}_t$  contra $\ddot{x}_{t1}$ e $\ddot{x}_{t2}$ sem as dummies mensais.



### Processos de covariância estacionária

Um processo estocástico é covariância estacionária se $\mathbb{E} (x_t)$ é constante, $\mbox{Var}(x_t)$ é constante e para qualquer $t, h\geq 1$, $\mbox{Cov}(x_t,x_{t + h})$ depende apenas em $h$, e não em $t$. Mais adiante abordaremos essa definição com maior profundidade.






### Processos fracamente dependente

Uma série temporal estacionária é fracamente dependente se $x_t$ e $x_{t + h}$ são
"quase independentes", quando $h$ aumenta.

Se, para um processo de covariância estacionária $\mbox{Cor}(x_t, x_{t + h})\rightarrow 0$ quando $h\rightarrow \infty$, dizemos que este processo de covariância estacionária é fracamente dependente.

Essa definição é necessária para usar _Leis dos Grandes Números_ e _Teorema Central do Limite_.

<br>

\BeginKnitrBlock{example}<div class="example"><span class="example" id="exm:Wpg365"><strong>(\#exm:Wpg365) </strong></span>MA(1) pg 356 Wooldridge.</div>\EndKnitrBlock{example}

<br>

\BeginKnitrBlock{example}<div class="example"><span class="example" id="exm:Wpg366"><strong>(\#exm:Wpg366) </strong></span>Exemplo: AR(1) pg 356 Wooldridge.</div>\EndKnitrBlock{example}

\newpage

## Exercícios

<br>

\BeginKnitrBlock{exercise}<div class="exercise"><span class="exercise" id="exr:exsr1"><strong>(\#exr:exsr1) </strong></span>Sobre regressão com séries temporais responda:

|    a) Quais as principais diferenças entre dados transversais e séries temporais?
  
|    b) Explique o que é exogeneidade contemporânea e exogeneidade estrita.

|    c) Comente sobre a diferença entre homocedasticidade e correlação serial.

|    d) A suposição de normalidade dos erros é necessária para se obter estimadores consistentes via MQO? Qual é o objetivo ao se fazer uma suposição para distribuição dos erros?
  </div>\EndKnitrBlock{exercise}

<br>

\BeginKnitrBlock{exercise}\iffalse{-91-97-110-112-101-99-45-50-48-49-48-93-}\fi{}<div class="exercise"><span class="exercise" id="exr:exsr2"><strong>(\#exr:exsr2)  \iffalse (anpec-2010) \fi{} </strong></span>Considere o modelo de regressão linear múltipla com regressores estocásticos $y_t = \beta_1 x_{1t} + \beta_2 x_{2t} + \varepsilon_t$, no qual $\varepsilon_t$ não é autocorrelacionado e tem média e variância condicionais a $x_{1t}$ e $x_{2t}$ iguais a zero e $s^2$, respectivamente. Por simplicidade, suponha que as variáveis são expressas como desvios com relação às respectivas médias.

Responda:

|    a) Se $\beta_2 = 0$ e incluirmos $x_{2t}$ na regressão, o estimador de mínimos quadrados ordinários de $\beta_1$ será viesado?

|    b) Se não conseguirmos observar $x_{1t}$, mas apenas $x_{1t}^*=x_{1t}+u_t$, em que $u_t$ é um erro de medida, e se substituirmos $x_{1t}$ por  $x_{1t}$ na regressão, o estimador de mínimos quadrados ordinários de $\beta_1$ ainda assim será consistente?

|    c) Se $x_{2t} = y_{t-1}$ e relaxarmos a hipótese de que os erros $\varepsilon_t$`s não são autocorrelacionados, o estimador de mínimos quadrados ordinários de $\beta_2$ será consistente, porém não será eficiente?

|    d) Seja $c$ uma constante diferente de zero. Defina $\tilde{y}= cy_t$, $\tilde{x}_{1t}= cx_{1t}$ e  $\tilde{x}_{2t} = cx_{2t}$. Os estimadores de mínimos quadrados ordinários (MQO) em uma regressão de  $\tilde{y}$ contra $\tilde{x}_{1t}$ e $\tilde{x}_{2t}$ coincidem com os estimadores de MQO em uma regressão de $y_t$ contra $x_{1t}$ e $x_{2t}$?

|    e) A variância do estimador de mínimos quadrados ordinários diverge para infinito à medida que a correlação entre $x_{1t}$ e $x_{2t}$ aproxima-se de 1;

|    f) Denote por $\widehat{\varepsilon}_t$ o resíduo da regressão de mínimos quadrados ordinários. A hipótese de que o erro é correlacionado com $x_{1t}$ pode ser testada utilizando a estatística $\frac{1}{T}\sum_{i=1}^{T}x_{1i}\widehat{\varepsilon}_{i}$?
  </div>\EndKnitrBlock{exercise}



<br>

\BeginKnitrBlock{exercise}<div class="exercise"><span class="exercise" id="exr:exsr3"><strong>(\#exr:exsr3) </strong></span>Em uma equação de dados anuais, supondo que
$$jur_t=1,6+0,48inf_t-0,15inf_{t-1}+0,32inf_{t-2}+u_t,$$
em que $jur$ é a taxa de juros e $inf$ é a taxa de inflação.

|    a) Supondo válida a hipótese de exogeneidade estrita, como deve ter sido estimado o modelo acima? Justifique?
  
|    b) Qual é o efeito de curto prazo (propensão de impacto) da taxa de inflação sobre a taxa juros? Qual é o efeito de longo prazo da taxa de inflação sobre a taxa de juros?
  </div>\EndKnitrBlock{exercise}

<br>

\BeginKnitrBlock{exercise}<div class="exercise"><span class="exercise" id="exr:exsr4"><strong>(\#exr:exsr4) </strong></span>Considere uma série temporal de 10 anos contendo PIB (em  R$ ) e número de homicídios (em unidades) em um determinado país. O primeiro modelo estimado foi $pib_t=\beta_0+\beta_1homic_t+u_t$. Os resultados da estimação se encontram na tabela 1. Um segundo modelo foi $pib_t=\beta_0+\beta_1homic_t+\beta_2t+u_t$, em que $t$ é um termo de tendência. Os resultados da estimação desse modelo se encontram na tabela 2:

  
|Tabela 1  | Estimate | Std. Error | t-value  | Pr(>|t|)|
|----------|-------------------------------|-------------------------|----------------------------|-------------------------------------|
| (Intercept)| -3461194.26 | 314948.06  | -10.99   |  0.00|
| homic      |    102.63   | 6.12       | 16.76    |  0.00|
  


<br>
  

| Tabela 2 | Estimate | Std. Error | t-value  | Pr(>|t|)|
|----------|-------------------------------|-------------------------|----------------------------|-------------------------------------|
(Intercept)| 5564710.45 | 2539866.04  | 2.19   |  0.06|
homic      |    -123.64 | 63.59       | -1.94  |  0.09|
t          | 423054.01  | 118647.95   | 3.57   |  0.01|
  




|    a) O coeficiente de $homic$ é significativo no primeiro modelo a 5% de significância? Interprete o valor desse coeficiente.

|    b) O coeficiente de $homic$ é significativo no segundo modelo a 5% de significância? Interprete o valor desse coeficiente.

|    c) O coeficiente de $t$ é significativo no segundo modelo a 5% de significância? Interprete o valor desse coeficiente.

|    d) Explique o resultado (surpreendente) encontrado no primeiro modelo, ressaltando a importância do procedimento adotado no segundo modelo.
</div>\EndKnitrBlock{exercise}

<br>



\BeginKnitrBlock{exercise}<div class="exercise"><span class="exercise" id="exr:exsr5"><strong>(\#exr:exsr5) </strong></span>Considere uma série do PIB brasileiro com início no primeiro trimestre 1996 e fim no segundo bimestre de 2010. Essa série foi decomposta em sua tendência $(t)$ e variáveis dummy para a sazonalidade, em que $S_i = 1$, se a observação pertence ao trimestre $i$ e $S_i = 0$, caso contrário.

|    a) Se tentarmos estimar o modelo $pib_t=\beta_0+\beta_1S_1+\beta_2S_2+\beta_3S_3+\beta_4S_4+\gamma t+u_t$, qual problema encontraremos? Explique porque isso ocorre.

|    b) No modelo $pib_t=\beta_1S_1+\beta_2S_2+\beta_3S_3+\beta_4S_4+\gamma t+u_t$, o que mede cada um dos $\beta$`s?

|    c)  No modelo $pib_t=\beta_0+\beta_2S_2+\beta_3S_3+\beta_4S_4+\gamma t+u_t$, o que mede $\beta_2$?

|    d)  No modelo $pib_t=\beta_0+\gamma t+\beta_2S_2+\beta_3S_3+\beta_4S_4+u_t$, foi estimado e apresentou a seguinte tabela ANOVA (Tabela 3). Faça um teste F para a hipótese nula de que não há sazonalidade. Use
$\alpha=5\%$


| Tabela 3 | Df   | Sum Sq  | Mean Sq|
|----------|-------------------------------|-------------------------|----------------------------|
|t          | 1 | 2287298699531.79  |  2287298699531.79|
|s2         | 1 | 1216754395.49     |  1216754395.49 |
|s3         | 1 | 31129772.60       |  31129772.60   |
|s4         | 1 | 5037536508.88     |  5037536508.88 |
|Residuals  | 53| 106216397798.70   |  2004082977.33 |
</div>\EndKnitrBlock{exercise}


<br>

\BeginKnitrBlock{exercise}<div class="exercise"><span class="exercise" id="exr:exsr6"><strong>(\#exr:exsr6) </strong></span>Considere o modelo $y_t=\alpha_0+\delta_0z_t+\delta_1z_{t-1}+\delta_2z_{t-2}+u_t$.

|    a) Por que devemos considerar a possibilidade de multicolinearidade nesse modelo?

|    b) Reparametrize o modelo de modo a isolar o efeito de longo prazo como coeficiente da variável $z_t$.

|    c) Qual o benefício dessa reparametrização se estivermos interessados em testar a significância do efeito de LP da $z$ sobre $y$?
  </div>\EndKnitrBlock{exercise}


<br>

\BeginKnitrBlock{exercise}<div class="exercise"><span class="exercise" id="exr:exsr7"><strong>(\#exr:exsr7) </strong></span>Considere o seguinte modelo estático $crime_t=\beta_0+\beta_1+pol_t+u_t$, em que $crime_t$ é um índice de criminalidade no período $t$ e $pol_t$ é o número de policiais em $t$.

|    a) Supondo que $pol$ seja estritamente exógeno na equação, como você estimaria $\beta_0$ e $\beta_1$. Quais as propriedades do estimador proposto em termos de viés e consistência?

|    b) Suponha agora que o número de policiais em $t$ seja definido em função do índice de criminalidade do período anterior. A hipótese de exogeneidade estrita continua válida? Justifique.
</div>\EndKnitrBlock{exercise}

<br>

\BeginKnitrBlock{exercise}<div class="exercise"><span class="exercise" id="exr:exsr8"><strong>(\#exr:exsr8) </strong></span>Um modelo de ajustamento parcial é dado por:
$$y^*_t=\beta_0+\beta_1x_t+e_t$$
$$y_t-y_{t-1}=\lambda(y^*_t-y_{t-1}),$$
  em que $y^*_t$ é o nível desejável ou ótimo de $y$, e $y_t$ é o nível efetivo (observado). Por exemplo, $y^*_t$ é o crescimento desejável nos estoques de uma firma e $x_t$ é o crescimento de vendas da firma. O parâmetro $\lambda$ mede a
velocidade do ajustamento e satisfaz $0 < \lambda < 1$.

|    a)  Insira a primeira equação na segunda equação e mostre que podemos escrever $y_t=\alpha_0+\alpha_1 y_{t-1}+\alpha_2 x_t+u_t$. Quem são os $\alpha$s em termos dos $\beta$s e $\lambda$? Quem é $u_t$ em termos de $e_t$?

|    b)  Supondo que $\mathbb{E}(e_t|x_t,y_{t-1})=0$ e todas as séries sejam fracamente dependentes,
como você estimaria os $\alpha$s? É consistente? Justifique sua resposta. O estimador proposto é viciado?

|    c) Seja $\hat{\alpha}_1 = 0,7$ e $\hat{\alpha}_2 = 0,2$. 

    (i) Qual o coeficiente de ajustamento estimado?
  
    (ii) Qual o efeito de CP (curto prazo) de um crescimento das vendas da firma sobre o crescimento de estoques da firma?
  
    (iii) Qual é o efeito de LP (longo prazo)?
  </div>\EndKnitrBlock{exercise}

<br>

\BeginKnitrBlock{exercise}<div class="exercise"><span class="exercise" id="exr:exsr9"><strong>(\#exr:exsr9) </strong></span>Imagine o seguinte modelo: $Y_t = \beta_0 + \beta_1 X_t + u_t$ , onde $Y$ é a demanda por moeda, $X^*$ é a taxa de juros esperada no longo prazo e $u$ é um termo de erro clássico, não correlacionado com $X^*$. Como a variável de expectativa $X^*$ não é diretamente observável, proporemos a seguinte hipótese para formação de expectativas (adaptativas): $X^*_t- X^*_{t-1} = \gamma(X_t- X_{t-1} )$, em que $\gamma$, tal que $0 < \gamma < 1$, é conhecido como coeficiente de expectativas.

|    a) Mostre que podemos escrever esse modelo como $Y_t=\alpha_0+\alpha_1X_t+\alpha_2Y_{t-1}+v_t$. Quem são os $\alpha$s em termos dos $\beta$s e $\gamma$? Quem é $v_t$ em termos de $u_t$?

|    b)  O que podemos dizer a respeito dos estimadores de MQO nesse caso? Justifique.

|    c)  Imagine que no modelo original $u_t$ siga o esquema auto-regressivo de primeira ordem, i.e., $u_t = \rho u_{t-1} + \varepsilon_t$, em que $\rho$ é o coeficiente de autocorrelação e onde $\varepsilon_t$ satisfaz as premissas clássicas. Se $\rho=\lambda$, como você estimaria o modelo? Justifique.

|    d)  As estimativas obtidas no item anterior são não-viciadas? Consistentes? Justifique sua resposta.
</div>\EndKnitrBlock{exercise}


<br>

\BeginKnitrBlock{exercise}<div class="exercise"><span class="exercise" id="exr:exsr10"><strong>(\#exr:exsr10) </strong></span>Seja o processo $y_t = e_t + \alpha_1 e_{t-1}$, em que $e_t \sim iid(0,\sigma^2).$

|    a) Calcule $\mathbb{E}(y_t )$, $\mbox{Var}(y_t )$ e $\mbox{Cov}(y_t , y_{t-h} )$, $h = 1, 2, 3,\ldots$. O processo $y_t$ é de covariância estacionária?

|    b) Calcule as autocorrelações de primeira ordem e de segunda ordem para esse processo. Podemos dizer que o processo é fracamente dependente? Justifique.

|    c) Faça o correlograma (gráfico da função de autocorrelação em função das defasagens) para esse processo.
</div>\EndKnitrBlock{exercise}

<br>

\BeginKnitrBlock{exercise}<div class="exercise"><span class="exercise" id="exr:exsr11"><strong>(\#exr:exsr11) </strong></span>Seja o processo $y_t = c + \rho y_{t-1} + e_t$, em que $e_t \sim iid(0,\sigma^2)$.

|    a) Qual é a condição de estabilidade para esse processo? Calcule $\mathbb{E}(y_t )$ e $\mbox{Var}(y_t )$ considerando válida a condição de estabilidade.

|    b) Para o processo $y_t$ acima temos que $\mbox{Cov}(y_t,y_{t-h} ) = \frac{\rho^h\sigma^2}{1-\rho^2}$, $h = 1, 2, 3,\ldots$. O processo $y_t$ é de covariância estacionária? Justifique.

|    c) Calcule a autocorrelação de ordem $h$ para o processo $y_t$. Faça o correlograma até quatro defasagens para esse processo considerando $\rho = 0,5$.
</div>\EndKnitrBlock{exercise}




