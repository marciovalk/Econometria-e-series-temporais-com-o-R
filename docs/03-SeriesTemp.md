# Séries Temporais {#st}





O estudo de séries temporais tem por objetivos principais definir o processo gerador de dados, fazer previsões futuras da série, identificar ciclos, tendências e/ou sazonalidades de forma que a decisão que envolve as variáveis em questão seja a mais acurada possível.



## Objetivos {#objetivos}


 Na seção \@ref(objetivos)

Dada uma série temporal $\{Z(t_1 ),\ldots, Z(t_N)\}$, observada nos instantes $t_1,\ldots,t_N$,
podemos estar interessados em:

|    i) Investigar o mecanismo gerador da série temporal;

|    ii) Fazer previsões de valores futuros da série; podendo ser a curto ou longo prazo;

|    iii) Descrever apenas o comportamento da série através de gráficos;

|    iv) Procurar periodicidades relevantes nos dados. Em todos estes casos podemos construir modelos probabilísticos ou estocásticos, tanto no domínio do tempo como no domínio da freqüência, por exemplo: um sinal aleatório com frequência medida em Hz. Devemos construir modelos simples e com menor número de parâmetros possíveis.




## Séries temporais: definição formal

Neste capítulo vamos descrever os conceitos básicos utilizados dentro da teoria dos modelos de séries temporais. Inicialmente vamos introduzir os conceitos de processos estocásticos, média e função de covariância, processo estacionário e função de autocorrelação.

### Processos estocásticos

Seja $T$ um conjunto arbitrário de índices. Um <span style='color: blue;'>_processo estocástico_</span>  é uma família de variáveis aleatórias $\{Z_t\}_{t \in T}$ definidas num mesmo espaço de probabilidades, que denotaremos genericamente por $(\Omega, \mathcal A, P)$. O conjunto de índices $T$ pode ser o conjunto dos números inteiros $\mathbb{Z} = \{0, \pm 1, \pm 2,\cdots\}$, dos naturais $\mathbb{N}=\{1,2,\cdots\}$ ou o conjunto dos números reais $\mathbb{R}$.  Observe ainda que, para cada $t \in T$, $Z_t$ é uma variável aleatória definida sobre $\Omega$, sendo assim de fato  uma função de dois argumentos, do índice $t\in T$ e do ponto $\omega \in \Omega$ que determina o valor do processo no tempo $t$ dado por $Z_t(\omega)$.

Uma série temporal, do ponto de vista teórico, nada mais é do que um processo estocástico para o qual o índice $T$ é $\mathbb{Z}$ ou um subconjunto deste. Do ponto de vista prático porém, uma série temporal é um conjunto de dados indexados no tempo. Esta dualidade de nomenclatura será utilizado em todo o trabalho. Invariavemente, letras maiúsculas, como $Z_1,Z_2,\cdots$ denotarão a série temporal do ponto de vista teórico, isto é, como variáveis aleatórias em um processo estocástico indexado pelo tempo, enquanto letras minúsculas como $z_1,z_2,\cdots$ denotarão a série temporal do ponto de vista prático, isto é, como uma observação das variáveis aleatórias que compõem o processo estocástico. Assim, se do ponto de vista teórico temos a série temporal $\{Z_t\}_{t\in\mathbb{Z}}$, um processo estocástico indexado pelo tempo, uma série temporal do ponto de vista prático significa uma realização $z_1,\cdots,z_n$ do processo $\{Z_t\}$, observados nos tempos $t=1,\cdots,n$. Neste caso, observamos $z_1=Z_1(\omega),\cdots, z_n=Z_n(\omega)$, para um determinado $\omega\in\Omega$ fixo. Embora existam maneiras mais formais e precisas de definir uma série temporal, o ponto de vista aqui adotado, embora aparentemente ambíguo na nomenclatura, servirá bem a nossos propósitos sem causar confusões.

Chamamos atenção ainda que existem condições para que um processo estocástico exista. Estes resultados dependem de uma discussão bastante técnica, bem além das intenções de nossa exposição.



### Especificação de um processo estocástico

Sejam $t_1,t_2,\ldots,t_n$ elementos quaisquer de $T$ e consideremos
\begin{equation}
F(Z_1,\ldots,Z_n; t_1,\ldots, t_n ) = P \{Z(t_1 )\leq z_1,\ldots, Z(t_n) \leq z_n \}
(\#eq:distfindim)
\end{equation}
então, o processo estocástico $Z = \{Z(t), t \in T \}$ estará especificado se as distribuições
finito-dimensionais de \@ref(eq:distfindim), são conhecidas para todo $n\geq 1$.
Contudo, em termos práticos, não conhecemos todas essas distribuições finito-
dimensionais. Estudaremos então certas características associadas a \@ref(eq:distfindim) e que
sejam simples de calcular e interpretar. Uma maneira de especificar o processo $Z$ seria determinar todos os produtos dos
momentos, ou seja,
\begin{equation}
\mu(r_1 ,\ldots, r_n; t_1,\ldots, t_n ) = \mathbb{E \,} Z^{r_1}(t_1 )\ldots Z^{r_n}(t_n)
(\#eq:prodmom)
\end{equation}
ou
\begin{equation}
\mu(\textbf{r},\textbf{t})=\int_{-\infty}^{\infty}\ldots\int_{-\infty}^{\infty}
                      Z^{r_1}_1\ldots Z^{r_n}_1 f(z_1,\ldots,z_n; t_1,\ldots,t_n)dz_1\ldots dz_n
\end{equation}
em que $f(\textbf{Z},\textbf{t})$ é a função de densidade de  $F(\textbf{Z}, \textbf{t})$. Porém o que vai nos interessar são os momentos de baixa ordem, ou seja, os chamados processos estacionários de segunda ordem. Consideramos somente os momentos de primeira e segunda  ordem, que serão apresentados a seguir.




## Médias e covariâncias


Naturalmente, quando estamos trabalhando com um processo estocástico, cada variável aleatória que o compõe possui sua própria distribuição, assim como sua própria massa/densidade de probabilidade e sua própria média/variância. Para um processo estocástico $\{Z_t\}_{t\in\mathbb{Z}}$ definimos, para cada $t\in\mathbb{Z}$, a <span style='color: blue;'>_função média_</span>, $\mu_t$ e a <span style='color: blue;'>_função variância_</span> $\sigma^2_t$ respectivamente por

\begin{align}
\mu_t = \mathbb{E} (Z_t) \quad \mbox{ e }\quad \sigma_t^2=\mbox{Var}(Z_t),
(\#eq:funcmed)
\end{align}
desde que as esperanças envolvidas existam. Chamamos a atenção de que embora as esperanças e variâncias de um processo estocástico existam, estas podem ser infinitas. Este fato trás diversos problemas técnicos na análise de séries temporais e requerem técnicas avançadas de análise que estão fora do escopo deste trabalho. Por este motivo, neste trabalho assumiremos tacitamente que todos os processos estocásticos e variáveis aleatórias possuem esperança e variância finitas.

Outra estrutura importante relacionada a um processo estocástico é o que chamamos de estrutura de dependência do processo. Dependência entre variáveis aleatórias pode ser definida de diversas maneiras diferentes. Neste trabalho estamos especialmente interessados na estrutura de dependência relacionadas com a covariância e a correlação entre as variáveis do processo. Observe que num processo estocástico podemos definir a covariância e a correlação entre quaisquer pares $Z_i$ e $Z_j$ de variáveis, para $i,j\in\mathbb{Z}$. No caso de processos, estas funções recebem o prefixo _auto_ para enfatizar o fato de que as covariâncias/correlações estão sendo calculadas entre as variáveis do processo. Definimos a
<span style='color: blue;'>_função de autocovariância_</span>, abreviada <span style='color: blue;'>_FACV_</span>, como

\begin{equation}
\gamma_Z(t,s) = \mbox{Cov}(Z_t , Z_s ) = E [(Z_t-\mu_t ) (Z_s-\mu_s )]=\mathbb{E} (Z_t Z_s ) - \mu_t \mu_s,\quad \mbox{ para }\quad t, s \in\mathbb{Z}.
(\#eq:funcacov)
\end{equation}

Analogamente. definimos a <span style='color: blue;'>_função de autocorrelação_</span>, abreviada <span style='color: blue;'>_FAC_</span>, por
\begin{equation}
\rho_Z(t,s) = \mbox{Cor}(Z_t , Z_s ) =\frac{\mbox{Cov}(Z_t , Z_s )}{\sqrt{\mbox{Var}(Z_t)\mbox{Var}(Z_s)}} = \frac{\gamma(t,s)}{\sqrt{\gamma(t,t)\gamma(s,s)}}.
(\#eq:funcfac)
\end{equation}
O subscrito "$Z$" nas definições acima são utilizados para reforçar à qual processo estamos nos referindo. Porém, quando não houver perigo de confusão, podemos eliminar a referência ao processo associado e escrever simplesmente $\gamma(t,s)$ e $\rho(t,s)$.

Observe que, em princípio, as funções $\gamma(t,s)$ e $\rho(t,s)$  dependem tanto de $t$ quanto de $s$. Nos casos em que isto acontece, qualquer tipo de inferência baseada em autocovariâncias/autocorrelações se torna impossível sem tomarmos medidas para tornar esta estrutura de dependência mais simples. Algumas técnicas relevantes para isso serão estudadas adiante. De qualquer forma, a teoria clássica de séries temporais lida com casos em que essas quantidades possuem uma dependência temporal simplificada, permitindo o seu estudo. Processos com estas características são de grande importância e serão estudados em detalhes mais adiante. Isto por que, do ponto de vista matemático, tal estrutura é conveniente e permite um tratamento rigoroso e aprofundado da teoria enquanto que do ponto de vista prático, é de fácil percepção, permite a modelagem, inferência, previsão e outros aspectos aplicados relevantes de maneira simples e rápida. Tudo isso contribuiu para a difusão de métodos baseado em autocovariâncias/autocorrelações.


### Propriedades importantes

As seguintes propriedades da função de autocovariância e autocorrelação são análogas às da covariância e correlação ordinárias, mas merecem destaque. Para todo $t,s\in\mathbb{Z}$, com $t\neq s$,

|    1\) $\gamma(t,t) = \mbox{Var}(Z_t)$, \quad  $\rho(t,t) = 1;$

|    2\)  $\gamma(t,s) = \gamma(s,t)$,\quad $\rho(t,s) = \rho(s,t)$.

|    3\) $|\gamma(t,s)|\leq \sqrt{\gamma(t,t)\gamma(s,s)}$,\quad $-1 \leq \rho(t,s)\leq 1.$

A propriedade 3 em particular mostra que a covariância entre duas variáveis está bem definida caso estas tenham variância finita.

Como sabemos a correlação é uma medida da dependência linear entre duas variáveis. Se $\mbox{Cor}(X,Y)=\pm1$, isto significa que existem constantes $\beta_0$ e $\beta_1$ tais que $Y=\beta_0+\beta_1X$. Ou seja, uma variável é exatamente uma função linear da outra. Valores próximos de $\pm 1$ indicam forte  dependência (linear) e valores próximos de 0 indicam fraca dependência (linear).  Se $\rho(t,s) = 0$, $Z_t$ e $Z_s$ são ditas não-correlacionadas, mas note que isso não quer dizer que elas são necessariamente independentes. Agora, se $Z_t$ e $Z_s$ são independentes, então $\rho(t,s) = 0$. Por fim, obviamente $\mbox{Cov}(Z_t,Z_s)=0$ se, e somente se, $Z_t$ e $Z_s$ são não-correlacionadas.

Para analisar as propriedades da covariância de vários modelos de séries temporais, o seguinte resultado será utilizado: se $c_1, c_2,\cdots, c_m$ e $d_1, d_2,\cdots, d_n$ são constantes reais e $t_1, t_2,\cdots, t_m$ e $s_1, s_2,\cdots, s_n$ são índices temporais, então

\begin{equation}
\mbox{Cov}\bigg( \sum_{i=1}^{m}c_iZ_{t_i},\sum_{j=1}^{n}d_jZ_{s_j}\bigg) = \sum_{i=1}^{m}\sum_{j=1}^{n}c_i d_j \mbox{Cov} (Z_{t_i}, Z_{s_j})
(\#eq:covsum)
\end{equation}
podemos dizer que, a covariância entre duas combinações lineares é a soma de todas as covariâncias entre termos de suas combinações lineares. Esta expressão pode ser verificada utilizando as propriedades de esperança e covariância. Como caso especial, podemos obter o seguinte resultado

\begin{equation}
\mbox{Var}\bigg(\sum_{i=1}^{n}c_i Z_{t_i}\bigg)=\sum_{i=1}^{n}c_i^2\mbox{Var}(Z_{t_i})
+ 2\sum_{i=1}^{n-1}\sum_{j={i+1}}^{n}c_ic_j\mbox{Cov}(Z_{t_i}, Z_{t_j}).
(\#eq:covsum2)
\end{equation}



## Estacionariedade


Nesta seção definiremos o fundamental conceito da estacionariedade de uma série temporal. Existem diversas maneiras de se definir o conceito de estacionariedade, de acordo com as técnicas que se pretendem utilizar na análise das séries temporais. Em poucas palavras, uma série temporal é estacionária quando, com o passar do tempo, a série se desenvolve aleatoriamente em torno de uma média constante, refletindo alguma forma de equilíbrio estável. A ideia é de que uma série temporal estacionária $Y$ tende a "_flutuar_" aleatoriamente ao redor de uma média constante. A Figura \@ref(fig:stac) apresenta duas séries estacionárias.


<div class="figure">
<img src="03-SeriesTemp_files/figure-epub3/stac-1.png" alt=" Séries estacionárias: (a) Ruído branco, (b) ARMA(1,2)." width="48%" /><img src="03-SeriesTemp_files/figure-epub3/stac-2.png" alt=" Séries estacionárias: (a) Ruído branco, (b) ARMA(1,2)." width="48%" />
<p class="caption">(\#fig:stac) Séries estacionárias: (a) Ruído branco, (b) ARMA(1,2).</p>
</div>



Entretanto, a maior parte das séries que encontramos na prática apresenta alguma forma de não-estacionariedade. A Figura \@ref(fig:nstac) apresenta algumas séries que apresentam algum tipo de não-estacionariedade que podem resultar de diversas fontes. Algumas das fontes mais comuns de não-estacionariedade de uma série temporal são:

|    a\) a presença de uma tendência determinística (linear, logaritmica, exponencial, etc.) ao redor da qual a série se desenvolve. Geralmente a presença de uma tendência determinística é facilmente reconhecível através do gráfico. Na Figura \@ref(fig:nstac)(a) apresentamos o gráfico de uma série apresentando uma tendência linear.

|    b\) quebra estrutural na série, que pode ser decorrente de uma mudança na média, como representado na Figura \@ref(fig:nstac)(b), ou uma mudança mais sutil, difícil de ser detectada, como por exemplo mudanças na distribuição da série, na variância, no modelo da série, etc.

|    c\) presença do que chamamos de tendência estocástica, como representado na Figura \@ref(fig:nstac)(c). Neste caso a série parece "_vagar_" por um caminho que apresenta mudanças aleatórias de trajetória, sendo que fica difícil determinar o seu comportamento.

|    d\) presença de sazonalidade. Neste caso a sazonalidade provoca uma mudança de nível local fazendo com que a média da série se altere nos períodos sazonais. Um exemplo de série sazonal é dado na Figura \@ref(fig:nstac)(d).



Mais detalhes serão apresentados adiante. A maior parte das séries que encontramos na prática apresenta alguma forma de não-estacionariedade. As séries econômicas apresentam em geral tendências lineares e muito comumente, tendência estocástica. Podemos ter, também, uma forma de não-estacionariedade explosiva, como o crescimento de uma colônia de bactérias.

<div class="figure">
<img src="03-SeriesTemp_files/figure-epub3/nsstac-1.png" alt=" Séries não-estacionárias apresentando: (a) Tendência linear, (b) quebra estrutural representada pela mudança de nível da série, (c) tendência estocástica e (d) sazonalidade." width="48%" /><img src="03-SeriesTemp_files/figure-epub3/nsstac-2.png" alt=" Séries não-estacionárias apresentando: (a) Tendência linear, (b) quebra estrutural representada pela mudança de nível da série, (c) tendência estocástica e (d) sazonalidade." width="48%" /><img src="03-SeriesTemp_files/figure-epub3/nsstac-3.png" alt=" Séries não-estacionárias apresentando: (a) Tendência linear, (b) quebra estrutural representada pela mudança de nível da série, (c) tendência estocástica e (d) sazonalidade." width="48%" /><img src="03-SeriesTemp_files/figure-epub3/nsstac-4.png" alt=" Séries não-estacionárias apresentando: (a) Tendência linear, (b) quebra estrutural representada pela mudança de nível da série, (c) tendência estocástica e (d) sazonalidade." width="48%" />
<p class="caption">(\#fig:nsstac) Séries não-estacionárias apresentando: (a) Tendência linear, (b) quebra estrutural representada pela mudança de nível da série, (c) tendência estocástica e (d) sazonalidade.</p>
</div>





### Estacionariedade forte ou  estrita

Um processo estocástico $Z(t)$ é dito ser um processo <span style='color: blue;'>processo fortemente (ou estritamente) estacionário</span>  se a distribuição conjunta de $Z_{t_1},\cdots, Z_{t_n}$ é a mesma de $Z_{t_1 - k}, Z_{t_2-k},\cdots, Z_{t_n - k}$, para todas as combinações de tempos $t_1, \cdots, t_n$ e para todo $k\in\mathbb{Z}$. Observe que este conceito se traduz em dizer que fixados os tempos $t_1, \cdots, t_n$, ao andarmos $k$ passos à frente homogeneamente no tempo, a distribuição das variáveis não se altera.

Quando $n = 1$, a distribuição de $Z_t$ é igual a distribuição de $Z_{t-k}$ para qualquer $k$, ou seja, os $Z_t$'s são identicamente distribuídos. Isto implica que num processo fortemente estacionário, as funções média ($\mu_t$) e variância ($\sigma^2_t$) são constantes  para todo $t$, isto é,
$\sigma^2=\mbox{Var}(Z_t) = \mbox{Var}(Z_{t-k})$ e $\mu=\mathbb{E} (Z_t ) = \mathbb{E} (Z_{t-k} )$, independentemente de $t$ e $k$. Quando $n = 2$, a distribuição de $(Z_t, Z_s)$ é a mesma de $(Z_{t-k}, Z_{s-k} )$, de onde segue que $\mbox{Cov}(Z_t, Z_s ) = \mbox{Cov}(Z_{t-k}, Z_{s-k} )$, para todo $t,s$ e $k$.

|    Fazendo $k = s$ temos:
\[\gamma(t,s)= \mbox{Cov}(Z_t, Z_s) = \mbox{Cov}(Z_{t-k}, Z_{s-k} )=\mbox{Cov}(Z_{t-s}, Z_{s-s} ) = \mbox{Cov}(Z_{t-s}, Z_0 )=\gamma(t-s,0);\]
e se  $k=t$,
\[ \gamma(t,s)= \mbox{Cov}(Z_{t-t}, Z_{s-t} ) = \mbox{Cov} (Z_0 , Z_{s-t} )= \mbox{Cov} (Z_0 , Z_{t-s} )= \gamma(0,s-t),\]

|    de onde podemos concluir que
\begin{equation*}
\gamma(t,s) = \gamma(0,|t-s|),\quad \mbox{ lembrando que }\ \
|t - s| =\begin{cases}
t - s, & \mbox{ para  } t > s;\\
s - t, & \mbox{ para } s > t.
\end{cases}
\end{equation*}

Analogamente para a função de autocorrelação. Ou seja, num processo fortemente estacionário a covariância entre $Z_t$ e $Z_s$ depende somente da diferença temporal $|t - s|$ e não dos tempos $t$ e $s$. Ou ainda, podemos dizer que a $\mbox{Cov}(Z_t,Z_{t+h})$ depende apenas da distância temporal $h$ entre as variáveis (chamada de <span style='color: blue;'>_defasagem_</span>  ou <span style='color: blue;'>_lag_</span> entre as variáveis), e não do tempo $t$. Isto permite simplificar a notação:


$$ \gamma(h)= \mbox{Cov}(Z_t, Z_{t-h} )=\mbox{Cov}(Z_t, Z_{t+h} )$$
$$ \rho(h)= \mbox{cor}(Z_t, Z_{t-h} )= \mbox{cor}(Z_t, Z_{t+h} ),$$

|  para todo $t,h\in\mathbb{Z}$. As propriedades gerais da _FAC_ e _FACV_ para um processo estacionário são:

|    1\)  $\gamma(0) = \mbox{Var}(Z_t)$, \quad $\rho(0) = 1$;

|    2\) $\gamma(h) = \gamma(-h)$,\quad $\rho(h) = \rho(-h)$;

|    3\) $|\gamma(h)|\leq \gamma(0)$, \quad $|\rho(h)|\leq 1$.


Se um processo é estritamente estacionário e tem variância finita, então a _FACV_ depende somente do _lag_ $h$.







### Estacionariedade fraca ou de segunda ordem


A estacionariedade forte é um conceito na maioria das vezes difícil de ser identificado na prática, mas muito conveniente do ponto de vista matemático. Uma outra maneira de se definir a estacionariedade de uma série de forma que a teoria é matematicamente tratável e de fácil detecção em problemas práticos é a seguinte: um processo estocástico $Z_t$ é dito ser <span style='color: blue;'>_fracamente  estacionário ou estacionário de segunda-ordem_</span>  se:

---------------------------------------------------------------------------

> 
|    a\) a função média é constante para todo tempo $t$;
|    b\) $\gamma(t,t-h) = \gamma(0,h)=\gamma(h)$ para todo tempo $t$ e lag $h$.

--------------------------------------------------------------------------

A condição $\gamma(t,t-h) = \gamma(h)$ para todo tempo $t$ e lag $h$ é equivalente a $\rho(t,t-h) = \rho(h)$. Além disso, $\mbox{Var}(Z_t)=\gamma(0)$ não depende de $t$. Como veremos adiante, em processos fracamente estacionários as funções de autocovariância e autocorrelação desempenham papel central no seu estudo. Neste trabalho, sempre que nos referirmos a um processo estacionário, estaremos nos referindo à processos fracamente estacionários.






### Teste para significância das autocorrelações

 Mais adiante quando estudarmos modelagem ARIMA, precisaremos de ferramentas para decidir se uma dada série é não-correlacionada. Para testar a hipótese conjunta de que $\rho(1)=\cdots=\rho(m)=0$ contra a hipótese de que algum $\rho(k)\neq0$, pode-se usar a estatística $Q_{BP}$ desenvolvida por <span style='color: blue;'>Box e Pierce</span>, ou a  estatística $Q_{LB}$ desenvolvida por  <span style='color: blue;'>Ljung-Box</span>, definidas, respectivamente, por:

-------------------------------------------------------------------------------------------------------------

> <span style='color: blue;'>Box e Pierce</span>
\[
 Q_{BP}(m)={n}\sum_{k=1}^{m}\hat{\rho}_k^2(\hat{\varepsilon})
\]
 em que $n$ é o tamanho da amostra (série)  e $m$  é o maior lag considerado na hipótese. A estatística $Q_{BP}$ em grandes amostras tem distribuição qui-quadrado com $m$ graus de  liberdade.

-------------------------------------------------------------------------------------------------------------

<br>

-------------------------------------------------------------------------------------------------------------

> <span style='color: blue;'>Ljung-Box</span>
\[
 Q_{LB}(m)={n(n+2)}\sum_{k=1}^{m}\frac{\hat{\rho}_k^2(\hat{\varepsilon})}{n-k}
\]
a qual se distribui como uma qui-quadrado com $m$ graus de liberdade em
grandes amostras. A estatística $Q_{LB}$ possui maior poder para amostras
pequenas que a estatística $Q_{BP}$.

-------------------------------------------------------------------------------------------------------------

Observe que a hipótese nula do teste é que todas as correlações de lag $1,\cdots,m$ são nulas, para algum $m$ predeterminado, desta forma a escolha do valor de $m$ é fundamental. Quanto maior o $m$, caso não seja possível rejeitar a hipótese nula, menor é a evidencia de que a série testada é correlacionada. Porém, se $m$ for muito grande, dois problemas poderão acontecer: primeiro, se $m$ é muito próximo de $n$ haverão poucos pontos amostrais com distância temporal $m$ o que torna a estimação de $\hat\rho_k(\hat\varepsilon)$ problemática, deteriorando a qualidade do teste; segundo, o poder do teste decresce com o aumento de $m$. Embora não haja consenso na literatura sobre o valor ideal de $m$, sugerimos utilizar $m=20$ para séries com $n\geq50$. Se a série for curta, na literatura encontra-se a sugestão $m=\min(10,n/5)$.




### Função de autocorrelação parcial ( _FACP_ )

A função de autocorrelação parcial ( _FACP_ ) entre as variáveis $Y_t$ e $Y_{t+k}$, denotada por $\alpha(k)$ em processos estacionários, é a correlação entre as variáveis $Y_t$ e $Y_{t+k}$ removida a influência das variáveis intermediárias $Y_{t+1},Y_{t+2},\cdots, Y_{t+k-1}$. Dada uma série temporal $\{Y_t\}_{t=1}^\infty$ estacionária e uma variável aleatória $X$, denotemos por $\Pi_{r,s}(X)$ a projeção de $X$ no subespaço gerado pelas variáveis $Y_{r+1},\cdots,Y_{r+s-1}$. A FACP entre $Y_t$ e $Y_{t+k}$ é dada por
 \[\alpha(k)=\mbox{Cor}\big(Y_t-\Pi_{t,k}(Y_t),Y_{t+k}-\Pi_{t,k}(Y_{t+k})\big), \mbox{ para }k\geq 2,\]
 e $\alpha(1)=\rho(1)$.




A _FACP_ para um processo estacionário com média zero pode ser  obtida a partir da regressão
\begin{equation}
y_{t+k} = \phi_{k1} y_{t+k-1} + \phi_{k2} y_{t+k-2} +\cdots + \phi_{kk} y_{t}+\varepsilon_{t+k},
\end{equation}
da qual podem ser obtidas as equações de _Yule-Walker_.


Multiplicando ambos os lados por $y_{t+k-j}$ e calculando o valor dividindo pela variância, tem-se

\begin{equation*}
\rho_j = \phi_{k1}\rho_{j-1} + \phi_{k2}\rho_{j-2} +\cdots + \phi_{kk} \rho_{k-j}.
\end{equation*}
Então para $j = 1, 2, \ldots, k$, temos:


\begin{eqnarray*}
\rho_1 &=& \phi_{k1}\rho_{0} + \phi_{k2}\rho_{1} +\cdots + \phi_{kk} \rho_{k-1};\\
\rho_2 &=& \phi_{k1}\rho_{1} + \phi_{k2}\rho_{0} +\cdots + \phi_{kk} \rho_{k-2};\\
&\vdots&\\
\rho_k &=& \phi_{k1}\rho_{k-1} + \phi_{k2}\rho_{k-2} +\cdots + \phi_{kk} \rho_{0};\\
\end{eqnarray*}

Para $k = 1$ $\rightarrow$ $\hat{\phi}_{11} = \rho_1$.

Para $k = 2$ $\rightarrow$ $\rho_1 = \phi_{21} + \phi_{22}\rho_1$ e $\rho_2 = \phi_{21}\rho_1 + \phi_{22}$.

Ou podemos escrever a ultima equação em notação matricial:

\begin{equation*}
 \begin{bmatrix}
\rho_1 \\
\rho_2
\end{bmatrix}
=
 \begin{bmatrix}
1&\rho_1 \\
\rho_1&1
\end{bmatrix}
 \begin{bmatrix}
\phi_{21}\\
\phi_{22}
\end{bmatrix}.
\end{equation*}
cuja solução para o estimador de $\phi_{22}$ é dada pela regra de _Cramer_:

\begin{equation*}
\hat{\phi}_{22}=\frac{\begin{vmatrix}
1&\rho_1 \\
\rho_1&\rho_2
\end{vmatrix}}
{\begin{vmatrix}
1&\rho_1 \\
\rho_1&1
\end{vmatrix}}
\end{equation*}

Para $k = 3$ temos as equações:
\begin{eqnarray*}
\rho_1 &=& \phi_{31}+ \phi_{32}\rho_1 + \phi_{33}\rho_2\\
\rho_2 &=& \phi_{31} \rho_1 + \phi_{32} + \phi_{33} \rho_1\\
\rho_3 &=& \phi_{31} + \phi_{32} \rho_1 + \phi_{33}.
\end{eqnarray*}

Em notação matricial temos:

\begin{equation*}
 \begin{bmatrix}
\rho_1 \\
\rho_2\\
\rho_3
\end{bmatrix}
=
 \begin{bmatrix}
1&\rho_1 &\rho_2\\
\rho_1&1 &\rho_1\\
\rho_2&\rho_1&1
\end{bmatrix}
 \begin{bmatrix}
\phi_{31}\\
\phi_{32}\\
\phi_{33}
\end{bmatrix}.
\end{equation*}
cuja solução para o estimador de $\phi_{33}$ é dada por:



\begin{equation*}
\hat{\phi}_{33}=\frac{\begin{vmatrix}
1&\rho_1 &\rho_1\\
\rho_1&1 &\rho_2\\
\rho_2&\rho_1&\rho_3
\end{vmatrix}}
{\begin{vmatrix}
1&\rho_1 &\rho_2\\
\rho_1&1 &\rho_1\\
\rho_2&\rho_1&1
\end{vmatrix}},
\end{equation*}
e  assim  sucessivamente.



### Operador de defasagem ou operador _lag_

Em séries temporais é usual trabalhar com operadores que defasam a variável. Definimos então o operador de defasagem $L$ como um operador linear tal que:


------------------------------------------------------------------------

> <span style='color: blue;'>Operador defasagem</span> 
\[
 L^j y_t = y_{t-j}
\]

-----------------------------------------------------------------------



As seguintes propriedades do operador $L$ serão úteis no que segue:

|    1\) O operador lag aplicado a uma constante resulta na própria constante, isto é, $Lc = c$;

|    2\) O operador lag segue a propriedade distributiva em relação à soma
\begin{equation*}
(L^i + L^j) Y_t = L^i Y_t + L^j Y_t = Y_{t-i} + Y_{t-j};
\end{equation*}

|    3\) É válida a propriedade associativa da multiplicação
$$L^i L^j Y_t = L^i (L^j Y_t ) = L^i (Y_{t-j} ) = Y_{t-i-j}.$$
Ou ainda $L^i L^j Y_t = L^{i+j} Y_t = Y_{t-i-j}$;

|    4\) Potências negativas de $L$ significam um operador de avanço,
$L^{-i} Y_t =L^j Y_t$, fazendo $j = -i$. Então $L^{-i} Y_t = L^j Y_t = Y_{t-j} = Y_{t+i}$;

|    5\) Se $|a| < 1$ definimos o operador inverso
\[(1-aL)^{-1} = 1 + aL + a^2 L^2 + \cdots = \sum_{j=0}^\infty (aL)^j.\]
A ação do operador $(1-aL)^{-1}$ em uma variável $Y_t$ é a seguinte:
\[(1-aL)^{-1}(Y_t)=(1 + aL + a^2 L^2 + \cdots)(Y_t)=Y_t+aY_{t-1}+a^2Y_{t-2}+\cdots = \sum_{j=1}^\infty a^jY_{t-j}.\]
\noindent Note ainda que, para uma constante $c\in\mathbb{R}$
\[(1-aL)^{-1}(c)=(1 + aL + a^2 L^2 + \cdots)(c)=(c + aL(c) + a^2 L^2(c) + \cdots)=c\sum_{j=1}^\infty a^j=\frac{c}{1-a}\,.\]

|    6\) Se $|a| > 1$, definimos o operador
\[ -aL( 1-aL)^{-1}=(1 + (aL)^{-1} + (aL)^{-2} +\cdots) \]
A ação do operador $-aL(1-aL)^{-1}$ em uma variável $Y_t$ é a seguinte:
\begin{align*}
(-aL(1-aL)^{-1})(Y_t)&=(1 + (aL)^{-1} + (aL)^{-2} +\cdots)(Y_t)= Y_t+\frac{1}{a}Y_{t+1}+\frac{1}{a^2}Y_{t+2}+\cdots\\
&=\sum_{j=1}^\infty \frac{1}{a^j}Y_{t+j}.
\end{align*}
Para uma constante $c\in\mathbb{R}$, a ação do operador $-aL(1-aL)^{-1}$ é dada por
\[(-aL(1-aL)^{-1})(c)=(1 + (aL)^{-1} + (aL)^{-2} +\cdots)(c)= c+\frac{c}{a}+\frac{c}{a^2}+\cdots=\frac{ca}{1-a}\,.\]






### Ruído branco

Um importante exemplo de processo estacionário é o ruído branco, o qual é definido
como uma sequência de variáveis aleatórias $\{\varepsilon_t \}_{t=-\infty}^{\infty}$ com as
seguintes propriedades:



 <span style='color: blue;'>Ruído Branco</span> 
 
|    1) $\mathbb{E}(\varepsilon_t)=0$, para todo $t\in\mathbb{R}$;

|    2) $\mathbb{E}(\varepsilon_t^2)=\sigma^2$ para todo $t\in\mathbb{R}$;

|    3) $\mathbb{E}(\varepsilon_t\varepsilon_s)=0$, para todo $t\neq s$, com $t,s\in\mathbb{R}$.

Em outras palavras, um ruído branco é uma sequência de variáveis não-correlacionadas com média constante. <span style='color: blue;'> Denotaremos um processo ruído branco por RB($0,\sigma^2$)</span>. Escreveremos ainda $\varepsilon_t\sim RB(0,\sigma_\varepsilon^2)$ para dizer que $\{\varepsilon_t\}_{t}$ é um processo ruído branco com média 0 e variância $\sigma^2_\varepsilon$


Para um ruído branco $\varepsilon_t\sim RB(0,\sigma_\varepsilon^2)$, $\mu_t = \mathbb{E} (\varepsilon_t )=0$ é constante com _FACV_ e _FAC_ dadas por

\[
\gamma_\varepsilon(h) =\left\{
\begin{array}{cc}
\sigma^2_\varepsilon, & \mbox{ se  } h=0;\\
0, & \mbox{ se } h\neq0.
\end{array}\right.\qquad
\rho_\varepsilon(h) =\left\{\begin{array}{cc}
1, & \mbox{ se  } h=0;\\
0, & \mbox{ se } h \neq 0.
\end{array}\right.
\]

O termo ruído branco resulta do fato que em uma análise de frequência do modelo, podemos mostrar que todas as frequências são iguais. As características de um  processo ruído branco  ficam explícitas quando analisamos o seguinte gráfico




```r
set.seed(5647)
eps=rnorm(200)

plot(eps,type="l",lwd=2,cex.lab=1.4, xlab="Ruído Branco",ylab="", cex.main=1.7,col="cadetblue4")
acf(eps,lwd=2,cex.lab=1.4, xlab=" lag ", main=" ", cex.main=1.7,col="cadetblue4")
pacf(eps,lwd=2,cex.lab=1.4, xlab=" lag ", main=" ", cex.main=1.7,col="cadetblue4",ylim=c(-0.9,0.9))
```

<div class="figure">
<img src="03-SeriesTemp_files/figure-epub3/rbsim-1.png" alt=" Ruído branco gaussiano simulado,FAC amostral e FACP  amostral" width="33%" /><img src="03-SeriesTemp_files/figure-epub3/rbsim-2.png" alt=" Ruído branco gaussiano simulado,FAC amostral e FACP  amostral" width="33%" /><img src="03-SeriesTemp_files/figure-epub3/rbsim-3.png" alt=" Ruído branco gaussiano simulado,FAC amostral e FACP  amostral" width="33%" />
<p class="caption">(\#fig:rbsim) Ruído branco gaussiano simulado,FAC amostral e FACP  amostral</p>
</div>





\BeginKnitrBlock{example}\iffalse{-91-77-233-100-105-97-45-77-243-118-101-108-32-100-101-32-111-114-100-101-109-32-49-93-}\fi{}<div class="example"><span class="example" id="exm:unnamed-chunk-2"><strong>(\#exm:unnamed-chunk-2)  \iffalse (Média-Móvel de ordem 1) \fi{} </strong></span>Este é um exemplo simples de um processo estacionário que não é um ruído branco. Suponha que</div>\EndKnitrBlock{example}
<span style='color: blue;'> Processo MA(1)</span>
 
\[
 Y_t = \varepsilon_t -0.5\varepsilon_{t-1},
\]
onde $\varepsilon_t$ é um RB$(0,\sigma_\varepsilon^2)$.


<span style='color: blue;'> Média do MA(1)</span> 

\[\mu_t= \mathbb{E} (Y_t ) = \mathbb{E} (\varepsilon_t ) - 0.5\mathbb{E} (\varepsilon_{t-1}) = 0\]



<span style='color: blue;'> Variância do MA(1)</span>  

\[\mbox{Var}(Y_t ) = \mbox{Var} (\varepsilon_t - 0.5\varepsilon_{t-1} )= \sigma_\varepsilon^2 + 0.5\sigma_\varepsilon^2 = 1.25\sigma_\varepsilon^2.\]


Quanto à estrutura de covariância/correlação de um MA(1), temos
\begin{align}
\mbox{Cov}(Y_t,&Y_{t+h})=\mbox{Cov}(\varepsilon_t - 0.5\varepsilon_{t-1},\varepsilon_{t+h} - 0.5\varepsilon_{t+h-1})\nonumber\\
&=\mbox{Cov}(\varepsilon_t,\varepsilon_{t+h})-0.5\mbox{Cov}(\varepsilon_t,\varepsilon_{t+h-1})-0.5\mbox{Cov}(\varepsilon_{t-1},\varepsilon_{t+h})+0.25\mbox{Cov}(\varepsilon_{t-1},\varepsilon_{t+h-1})\nonumber\\
&= \gamma_\varepsilon(h)-0.5\gamma_\varepsilon(h-1)-0.5\gamma_\varepsilon(h+1)+0.25\gamma_\varepsilon(h),
(\#eq:gppo)
\end{align}
onde $\gamma_\varepsilon$ denota a função de autocovariancia de $\varepsilon_t$. Da equação \ref(eq:gppo), percebemos que $\mbox{Cov}(Y_t,Y_{t+h})$ só é diferente de zero quando algum dos argumentos das funções à direita da igualdade em \ref(eq:gppo) é zero. Isto ocorre somente quando $h=0$ (resultando em $\mbox{Var}(Y_t)=1.25\sigma_\varepsilon^2$) e quando $|h|=1$ (resultando $-0.5\sigma_\varepsilon^2$). Em outras palavras, $\mbox{Cov}(Y_t,Y_{t+h}   )$ não depende de $t$ e


\[\gamma(k) =\begin{cases} -0.5\sigma_\varepsilon^2, &\mbox{ se } |k|=1; \\
                                0,           & \mbox{ se } |k|>1.
               \end{cases}   \quad \mbox{e} \quad\rho(k) =\begin{cases} -0.4, &\mbox{ se } |k|=1; \\
                                0,           & \mbox{ se } |k|>1.
               \end{cases}   \]
Concluimos que um MA(1) é estacionário.






## Metodologia de Box-Jenkins ou modelagem ARIMA

Na análise de séries temporais, a metodologia de Box-Jenkins, nomeada em homenagem ao estatísticos
George Box e Gwilym Meirion Jenkins, é uma metodologia pensada para a modelagem de séries temporais que é suficientemente simples de forma a atingir um grande público e suficientemente flexível para se aplicar a uma gama grande de problemas. Centrais à metodologia Box-Jenkins são os modelos **_Autorregressivos Integrados de Média Móvel_**, abreviados modelos ARIMA, que representam uma classe grande de modelos capazes de modelar uma variedade de tipos de séries temporais. O intuito é modelar os valores da série temporal em função dos seus valores passados (admitindo um termo de erro) de forma que seja possível fazer previsões para esta série.
O procedimento pode ser resumido em três etapas:

-  Identificação e seleção do modelo. Nesta etapa verificamos se as variáveis são estacionárias, identificando possíveis tendências e/ou sazonalidades na série, removendo-as quando detectadas. Fazemos o uso das funções de autocorrelação e autocorrelação parcial para decidir qual modelo da classe ARIMA é adequado para uma primeira tentativa de modelagem..

-  Estimação dos parâmetros usando algoritmos computacionais para chegar a coeficientes que melhor se adaptam ao modelo ARIMA selecionado. Os métodos mais comuns são a máxima verossimilhança e os  mínimos quadráticos não-lineares.

-  Verificação do ajuste do modelo por meio de testes. Nesta fase, verificamos se o modelo estimado está em conformidade com as especificações do modelo teórico proposto. De suma importância é a análise residual na qual o objetivo é verificar se os resíduos satisfazem a hipótese de serem não-correlacionados. De grande utilidade é o teste Ljung-Box. Se o modelo proposto é inadequado, devemos voltar para a primeira etapa e propor um modelo alternativo.


Um dos modelos mais simples, útil e intuitivo é o modelo autorregressivo. Consideremos  o  caso  mais  simples.



### Modelo autorregressivo  de  ordem 1 AR(1)

<span style='color: blue;'> Processo AR(1)</span>
\[
   Y_t = c + \phi Y_{t-1}+\varepsilon_t,
\]
em que $\varepsilon_t$ é um $RB(0,\sigma_\varepsilon^2)$.
\end{tcolorbox}
Para calcularmos a média e a variância do processo, assumiremos primeiramente que os  momentos incondicionais sejam iguais, de forma que $\mathbb{E} Y_t=\mathbb{E} Y_{t-1}$. Com esta simplificação, fica fácil calcular a média de um processo AR(1):

------------------------------------------------------------

> 
<span style='color: blue;'> A média do processo AR(1)</span>  é
\[
\mu= \mathbb{E} (Y_t)=\mathbb{E}(c) +\phi\mathbb{E} (Y_{t-1})+\mathbb{E}(\varepsilon_t)\quad\Longleftrightarrow\quad \mu=c+\phi\mu+0\quad\Longleftrightarrow\quad\mu=\frac{c}{1-\phi}\,,\]
desde que $\phi\neq 1$. Se $\phi=1$ a equação não possui solução \footnote{mais tarde veremos que para $\phi=1$ o processo é não estacionário e de fato  a média varia com $t$, sendo, portanto, falsa a hipótese inicial de que a média do processo é constante, utilizada para derivar as equações.}. 

------------------------------------------------------------

Desta forma procedemos assumindo que $\phi\neq 1$. Observe ainda que  $\mu=0$,  quando  $c=0$. Para $\phi\neq 1$, a variância de um AR(1), por sua vez, é dada por

------------------------------------------------------------

> 
<span style='color: blue;'> A variância do AR(1)</span>  é
\[
 \mbox{Var}(Y_t)=\mathbb{E}(Y_t^2)-\mu^2=\frac{\sigma^2}{1-\phi^2}.
\]

------------------------------------------------------------

Observe que  se $|\phi|>1$, a variância será negativa, o que é  um absurdo. Neste caso as equações não são compatíveis com nenhum processo.
Quando  $|\phi|=1$,  a variância de $Y_t$ não está definida pois a média não está.

Deste exemplo, é  possível concluir que é necessário estabelecer algumas restrições sobre o modelo para que se possa estimá-lo. Em particular,
uma condição necessária para estimar os coeficientes do modelo é que  $|\phi|<1$.

Com um pouco mais de trabalho, podemos encontrar  o mesmo resultado sem a suposição de que os momentos incondicionais  sejam  iguais. Para isso usamos o operador  defasagem $L$ e suas propriedades para obtermos


\begin{align}
   Y_t = c + \phi Y_{t-1}+\varepsilon_t \quad &\Longleftrightarrow\quad (1-\phi L)Y_t=c+\varepsilon_t\quad \Longleftrightarrow\quad Y_t=(1-\phi L)^{-1}(c)+{(1-\phi L)}^{-1}(\varepsilon_t)\nonumber\\
\qquad &\Longleftrightarrow\qquad Y_t=\mu+\sum_{j=0}^{\infty}\phi^j\varepsilon_{t-j},
(\#eq:arcomomainfinito)
\end{align}
onde escrevemos $\mu=c/(1-\phi)$ por simplicidade. A partir desta representação podemos facilmente obter

\begin{equation*}
\mathbb{E}  Y_t=\mu+\sum_{j=0}^{\infty}\phi^j\mathbb{E}(\varepsilon_{t-j})=\mu
\end{equation*}
e
\begin{align*}
\mbox{Var}(Y_t)&=\mathbb{E}(Y_t-\mu)^2=\mathbb{E}\bigg(\sum_{j=0}^{\infty}\phi^j\varepsilon_{t-j}\bigg)^2=\mathbb{E}\bigg(\sum_{j=0}^\infty\sum_{k=0}^\infty \phi^k\phi^j\varepsilon_{t-j}\varepsilon_{t-k}\bigg)\\
&=\sum_{j=0}^\infty\sum_{k=0}^\infty \phi^{k+j}\mathbb{E}(\varepsilon_{t-j}\varepsilon{t-k})=\sum_{j=0}^{\infty}\phi^{2j}\mathbb{E}(\varepsilon_{t-j}^2)=\frac{\sigma^2_\varepsilon}{1-\phi^2},
\end{align*}
onde a última igualdade segue do fato de que $\mathbb{E}(\varepsilon_{t-j}\varepsilon_{t-k})=\gamma_\varepsilon(j-k)$ que é igual a zero se $j\neq k$, e $\sigma^2_\varepsilon$, se $j=k$. Para $h>0$, a 

-----------------------------------------------------------------------------

> 
<span style='color: blue;'> função de autocovariância de _lag_</span> $h$ é dada por
\begin{eqnarray*}
\gamma(h)&=&\mathbb{E}[(Y_t-\mu)(Y_{t-h}-\mu)]=\mathbb{E}\bigg[\bigg(\sum_{s=0}^{\infty}\phi^s\varepsilon_{t-s}\bigg)
     \bigg(\sum_{k=0}^{\infty}\phi^k\varepsilon_{t-k-h}\bigg)\bigg]\\
&=&\sum_{s=0}^{\infty}\sum_{k=0}^{\infty}\phi^{k+s}\mathbb{E}(\varepsilon_{t-s}\varepsilon_{t-k-h})=\sum_{s=0}^{\infty}\sum_{k=0}^{\infty}\phi^{k+s}\gamma_\varepsilon(s-k-h).
\end{eqnarray*}

---------------------------------------------------------------------------

Observe que $\gamma_\varepsilon(s-k-h)$ só é diferente de zero quando $s-k-h=0$, o que é equivalente a $s=k+h$, assim
\begin{eqnarray*}
\gamma(h)=\sigma^2_\varepsilon\sum_{k=0}^{\infty}\phi^{2k+h}=\sigma^2_\varepsilon(\phi^h+\phi^{h+2}+\phi^{h+4}+\cdots)=\frac{\phi^h}{1-\phi^2}\sigma^2_\varepsilon,
\end{eqnarray*}
Para $h<0$, analogamente obtemos
\[\gamma(h)=\frac{\phi^{-h}}{1-\phi^2}\sigma^2_\varepsilon,\]
ou seja, para $h\neq0$,
\[\gamma(h)=\frac{\phi^{|h|}}{1-\phi^2}\sigma^2_\varepsilon.\]
Como a  média e  as covariâncias não são funções do tempo  o processo é
fracamente estacionário, independente do valor  de  $\phi\in(-1,1)$.   

-----------------------------------------------------------------------------

> 
<span style='color: blue;'>A função de autocorrelação de _lag_</span> _h_  é  dada por
\begin{equation*}
 \rho(h)= \frac{\frac{\phi^|h|}{1-\phi^2}\sigma^2}{\frac{\sigma^2}{1-\phi^2}}=\phi^{|h|}.
\end{equation*}

--------------------------------------------------------------------------------

Além disso, como $|\phi|<1$, a função de autocorrelação é decrescente em $|h|$.





### Passeio aleatório (_Random Walk_)


Quando $\phi=1$ no caso anterior, temos o processo chamado passeio aleatório.
Seja $\{\varepsilon_t\}_{t\in\mathbb{N}}$ um RB$(0, \sigma_\varepsilon^2)$.

<span style='color: blue;'> O Passeio aleatório </span> pode ser representado por 
\[
Z_t = Z_{t-1} + \varepsilon_t,
\]
que pode ser reescrito de uma maneira bem simples. Defina inicialmente
\[Z_1=\varepsilon_1, \qquad Z_2=\varepsilon_1+\varepsilon_2 \leftrightarrow Z_2=Z_1+\varepsilon_2\]
e sucessivamente
\[Z_{k-1}=\varepsilon_1+\cdots+\varepsilon_{k-1}, \qquad Z_k=\varepsilon_1+\cdots+\varepsilon_{k-1}+\varepsilon_k = Z_{k-1}+\varepsilon_k. \]
Com esta representação, o cálculo da média e da variância de $Z_t$ se tornam simples:

<span style='color: blue;'> A média do passeio aleatório </span> é
\[\mu_t= \mathbb{E}(Z_t) =\mathbb{E}(\varepsilon_1 + \varepsilon_2 +\cdots+ \varepsilon_t )= \mathbb{E} (\varepsilon_1 ) + \mathbb{E} (\varepsilon_2 ) +\cdots + \mathbb{E} (\varepsilon_t)= 0 + 0 + \cdots + 0 = 0,\]
e <span style='color: blue;'> a variância do passeio aleatório </span> é
\[\mbox{Var}(Z_t) = \mbox{Var}(\varepsilon_1 + \varepsilon_2 + \cdots + \varepsilon_t ) = \mbox{Var}(\varepsilon_1) + \cdots + \mbox{Var}(\varepsilon_t) = \sigma_\varepsilon^2 + \sigma_\varepsilon^2 + \cdots + \sigma_\varepsilon^2 = t\sigma_\varepsilon^2.\]
Assim concluímos que a variância de um passeio aleatório cresce linearmente com o tempo, sendo portanto um processo não-estacionário. Observe ainda que se $1\leq t\leq s$, a função de autocovariância de um passeio aleatório é dada por
\begin{eqnarray*}
\gamma(t,s) &=&  \mbox{Cov}(Z_t,Z_s)\\
            &=&  \mbox{Cov}(\varepsilon_1 + \varepsilon_2 + \cdots + \varepsilon_t, \varepsilon_1 + \varepsilon_2 + \cdots + \varepsilon_s)\\
            &=& \sum_{i=1}^t\sum_{j=1}^s \mbox{Cov}(\varepsilon_i,\varepsilon_j)\\
            &=&  \mbox{Cov}(\varepsilon_1,\varepsilon_1) + \mbox{Cov}(\varepsilon_2,\varepsilon_2)+ \cdots+ \mbox{Cov}(\varepsilon_t,\varepsilon_t)\\
            &=&  \sigma_\varepsilon^2 + \sigma_\varepsilon^2 + \cdots +\sigma_\varepsilon^2 = t\sigma_\varepsilon^2
\end{eqnarray*}
onde $\mbox{Cov}(\varepsilon_i, \varepsilon_j)=0$ para $i\neq j$.  O mesmo argumento mostra que se $1\leq s \leq t$, teremos $\gamma(t,s)=s\sigma_\varepsilon^2,$ de forma que podemos escrever compactamente $\gamma(s,t)=\min(s,t)\sigma^2$.
A <span style='color: blue;'> função de autocorrelação de um passeio aleatório </span>  é facilmente obtida
\begin{align*}
\rho(t,s)&= \frac{\gamma(s,t)}{\sqrt{\mbox{Var}(X_t)}\sqrt{\mbox{Var}(X_s)}}=\frac{\min(s,t)\sigma_\varepsilon^2}{\sqrt{t\sigma_\varepsilon^2}\sqrt{s\sigma_\varepsilon^2}}=\frac{\min(s,t)}{\sqrt{t}\sqrt{s}}=\left\{\begin{array}{cc}
           \frac{s}{\sqrt{t}\sqrt{s}}=\sqrt{\frac{s}{t}}, & \mbox{ se } 1\leq s\leq t; \\
           \frac{t}{\sqrt{t}\sqrt{s}}=\sqrt{\frac{t}{s}}, & \mbox{ se } 1\leq t\leq s
         \end{array}
\right.\\
&=\sqrt{\frac{\min(s,t)}{\max(s,t)}}.
\end{align*}

Em resumo, a _FACV_ e a _FAC_ de um passeio aleatório são dadas por

------------------------------------------------------------

>
<span style='color: blue;'> FACV do passeio aleatório</span> 
\[
\gamma(t,s) = \min(s,t)\sigma_\varepsilon^2,
\]

------------------------------------------------------------

<br>

------------------------------------------------------------

>
<span style='color: blue;'> FAC do passeio aleatório</span>  
\[
\rho(t,s)=\sqrt{\frac{\min(s,t)}{\max(s,t)}}
\]

------------------------------------------------------------


O passeio aleatório é um exemplo simples que serve de aproximação para diversas situações reais, tais como como o movimento comum de preços e títulos e também a posição de pequenas partículas suspensas dentro de um fluído, chamado movimento Browniano.



```r
set.seed(1231)
eps=rnorm(200)
rw=cumsum(eps)
plot(rw,type="l",lwd=2,cex.lab=1.4, xlab=" tempo",ylab="", main="(a)", cex.main=1.7,col="cadetblue4")
acf(rw,type = "correlation",lag.max = 50,cex.main=1.7,col="cadetblue4",ylab="FAC",lwd=4,main="(b)")
acf(rw,type = "partial" ,lag.max = 50,cex.main=1.7,col="cadetblue4",ylab="FACP",lwd=4,main="(c)")
```

<div class="figure">
<img src="03-SeriesTemp_files/figure-epub3/rw-1.png" alt=" Passeio aleatório simulado (a), FACV amostral (b) e FAC amostral (c)." width="30%" /><img src="03-SeriesTemp_files/figure-epub3/rw-2.png" alt=" Passeio aleatório simulado (a), FACV amostral (b) e FAC amostral (c)." width="30%" /><img src="03-SeriesTemp_files/figure-epub3/rw-3.png" alt=" Passeio aleatório simulado (a), FACV amostral (b) e FAC amostral (c)." width="30%" />
<p class="caption">(\#fig:rw) Passeio aleatório simulado (a), FACV amostral (b) e FAC amostral (c).</p>
</div>






### Modelos autorregressivos de ordem $p$, AR($p$)

O processo autorregressivo de ordem $p$ é definido como

------------------------------------------------------------

>
<span style='color: blue;'> O processo AR(_p_)</span>  
\[ Y_t=\phi_1Y_{t-1}+\cdots+\phi_pY_{t-p}+\varepsilon_t=\sum_{j=1}^{p}\phi_jY_{t-j} + \varepsilon_t.\]

------------------------------------------------------------

<br>

Escrevendo $Y_t$ em função do operador _lag_, obtemos

------------------------------------------------------------

>
<span style='color: blue;'> Definição com o operador _lag_</span>  
\begin{align*}
Y_t=\phi_1L(Y_t)+\phi_2L^2(Y_t)\cdots+\phi_pL^p(Y_t)+\varepsilon_t \quad &\Longleftrightarrow \quad (1-\phi_1L-\phi_2L^2-\cdots-\phi_pL^p)Y_t=\varepsilon_t \\
\quad &\Longleftrightarrow \quad  \Phi_p(L)Y_t=\varepsilon_t,
\end{align*}

------------------------------------------------------------

onde $\Phi_p(L)=1-\phi_1L-\phi_2L^ 2-\cdots-\phi_pL^p$. O polinômio $\Phi_p(\cdot)$ será importante no estudo da estacionariedade e causalidade de processos ARMA, que veremos adiante.

<br>



#### Alguns processos ARMA simulados




```r
set.seed(12322)
ar1=arima.sim(n=200,model=list(ar=0.5))
plot(ar1,type="l",lwd=2,cex.lab=1.4, xlab=" tempo",ylab="", main="(a)", cex.main=1.7,col="cadetblue4")
acf(ar1,type = "correlation",lag.max = 50,cex.main=1.7,col="cadetblue4",ylab="FAC",lwd=4,main="(b)")
acf(ar1,type = "partial" ,lag.max = 50,cex.main=1.7,col="cadetblue4",ylab="FACP",lwd=4,main="(c)")
```

<div class="figure">
<img src="03-SeriesTemp_files/figure-epub3/ar105-1.png" alt="AR(1) simulado com coeficiente $\phi_1=0.5$ (a), FACV amostral (b) e FAC amostral (c)." width="33%" /><img src="03-SeriesTemp_files/figure-epub3/ar105-2.png" alt="AR(1) simulado com coeficiente $\phi_1=0.5$ (a), FACV amostral (b) e FAC amostral (c)." width="33%" /><img src="03-SeriesTemp_files/figure-epub3/ar105-3.png" alt="AR(1) simulado com coeficiente $\phi_1=0.5$ (a), FACV amostral (b) e FAC amostral (c)." width="33%" />
<p class="caption">(\#fig:ar105)AR(1) simulado com coeficiente $\phi_1=0.5$ (a), FACV amostral (b) e FAC amostral (c).</p>
</div>


<br>


```r
set.seed(12322)
ar1m=arima.sim(n=200,model=list(ar=-0.5))
plot(ar1m,type="l",lwd=2,cex.lab=1.4, xlab=" tempo",ylab="", main="(a)", cex.main=1.7,col="cadetblue4")
acf(ar1m,type = "correlation",lag.max = 50,cex.main=1.7,col="cadetblue4",ylab="FAC",lwd=4,main="(b)")
acf(ar1m,type = "partial" ,lag.max = 50,cex.main=1.7,col="cadetblue4",ylab="FACP",lwd=4,main="(c)")
```

<div class="figure">
<img src="03-SeriesTemp_files/figure-epub3/arm105-1.png" alt="AR(1) simulado com coeficiente $\phi_1=-0.5$ (a), FACV amostral (b) e FAC amostral (c)." width="33%" /><img src="03-SeriesTemp_files/figure-epub3/arm105-2.png" alt="AR(1) simulado com coeficiente $\phi_1=-0.5$ (a), FACV amostral (b) e FAC amostral (c)." width="33%" /><img src="03-SeriesTemp_files/figure-epub3/arm105-3.png" alt="AR(1) simulado com coeficiente $\phi_1=-0.5$ (a), FACV amostral (b) e FAC amostral (c)." width="33%" />
<p class="caption">(\#fig:arm105)AR(1) simulado com coeficiente $\phi_1=-0.5$ (a), FACV amostral (b) e FAC amostral (c).</p>
</div>


<br>



```r
set.seed(12322)
ar108=arima.sim(n=200,model=list(ar=-0.5))
plot(ar108,type="l",lwd=2,cex.lab=1.4, xlab=" tempo",ylab="", main="(a)", cex.main=1.7,col="cadetblue4")
acf(ar108,type = "correlation",lag.max = 50,cex.main=1.7,col="cadetblue4",ylab="FAC",lwd=4,main="(b)")
acf(ar108,type = "partial" ,lag.max = 50,cex.main=1.7,col="cadetblue4",ylab="FACP",lwd=4,main="(c)")
```

<div class="figure">
<img src="03-SeriesTemp_files/figure-epub3/ar108-1.png" alt="AR(1) simulado com coeficiente $\phi_1=0.8$ (a), FACV amostral (b) e FAC amostral (c)." width="33%" /><img src="03-SeriesTemp_files/figure-epub3/ar108-2.png" alt="AR(1) simulado com coeficiente $\phi_1=0.8$ (a), FACV amostral (b) e FAC amostral (c)." width="33%" /><img src="03-SeriesTemp_files/figure-epub3/ar108-3.png" alt="AR(1) simulado com coeficiente $\phi_1=0.8$ (a), FACV amostral (b) e FAC amostral (c)." width="33%" />
<p class="caption">(\#fig:ar108)AR(1) simulado com coeficiente $\phi_1=0.8$ (a), FACV amostral (b) e FAC amostral (c).</p>
</div>

<br>



```r
set.seed(12322)
ar2=arima.sim(n=200,model=list(ar=c(0.5,-0.7)))
plot(ar2,type="l",lwd=2,cex.lab=1.4, xlab=" tempo",ylab="", main="(a)", cex.main=1.7,col="cadetblue4")
acf(ar2,type = "correlation",lag.max = 50,cex.main=1.7,col="cadetblue4",ylab="FAC",lwd=4,main="(b)")
acf(ar2,type = "partial" ,lag.max = 50,cex.main=1.7,col="cadetblue4",ylab="FACP",lwd=4,main="(c)")
```

<div class="figure">
<img src="03-SeriesTemp_files/figure-epub3/ar2-1.png" alt="AR(2) simulado com coeficiente $\phi_1=0.5$ e $\phi_1=-0.7$  (a), FACV amostral (b) e FAC amostral (c)." width="33%" /><img src="03-SeriesTemp_files/figure-epub3/ar2-2.png" alt="AR(2) simulado com coeficiente $\phi_1=0.5$ e $\phi_1=-0.7$  (a), FACV amostral (b) e FAC amostral (c)." width="33%" /><img src="03-SeriesTemp_files/figure-epub3/ar2-3.png" alt="AR(2) simulado com coeficiente $\phi_1=0.5$ e $\phi_1=-0.7$  (a), FACV amostral (b) e FAC amostral (c)." width="33%" />
<p class="caption">(\#fig:ar2)AR(2) simulado com coeficiente $\phi_1=0.5$ e $\phi_1=-0.7$  (a), FACV amostral (b) e FAC amostral (c).</p>
</div>

<br>


```r
set.seed(12322)
ar3=arima.sim(n=200,model=list(ar=c(0.5,-0.7,0.6)))
plot(ar3,type="l",lwd=2,cex.lab=1.4, xlab=" tempo",ylab="", main="(a)", cex.main=1.7,col="cadetblue4")
acf(ar3,type = "correlation",lag.max = 50,cex.main=1.7,col="cadetblue4",ylab="FAC",lwd=4,main="(b)")
acf(ar3,type = "partial" ,lag.max = 50,cex.main=1.7,col="cadetblue4",ylab="FACP",lwd=4,main="(c)")
```

<div class="figure">
<img src="03-SeriesTemp_files/figure-epub3/ar3-1.png" alt="AR(3) simulado com coeficiente $\phi_1=0.5$, $\phi_2=-0.7$ e $\phi_3=0.6$   (a), FACV amostral (b) e FAC amostral (c)." width="33%" /><img src="03-SeriesTemp_files/figure-epub3/ar3-2.png" alt="AR(3) simulado com coeficiente $\phi_1=0.5$, $\phi_2=-0.7$ e $\phi_3=0.6$   (a), FACV amostral (b) e FAC amostral (c)." width="33%" /><img src="03-SeriesTemp_files/figure-epub3/ar3-3.png" alt="AR(3) simulado com coeficiente $\phi_1=0.5$, $\phi_2=-0.7$ e $\phi_3=0.6$   (a), FACV amostral (b) e FAC amostral (c)." width="33%" />
<p class="caption">(\#fig:ar3)AR(3) simulado com coeficiente $\phi_1=0.5$, $\phi_2=-0.7$ e $\phi_3=0.6$   (a), FACV amostral (b) e FAC amostral (c).</p>
</div>







### Modelo de médias-móveis, MA(_q_)
Chamamos de médias-móveis de ordem $q$ o processo definido por:

------------------------------------------------------------

>
<span style='color: blue;'> O processo MA(_q_)</span>  
\[
Y_t= \varepsilon_t + \theta_1 \varepsilon_{t-1} + \theta_2 \varepsilon_{t-2} +\cdots + \theta_q \varepsilon_{t-q}
\]
em que $\varepsilon_t$ é um $RB(0,\sigma_\varepsilon^2)$.

------------------------------------------------------------

Esta terminologia vem do fato que $Y_t$ é obtido aplicando-se os pesos  $1,-\theta_1, -\theta_2, \cdots, -\theta_q$, às variáveis   $\varepsilon_t - \varepsilon_{t-1} - \varepsilon_{t-2} -\cdots - \varepsilon_{t-q}$ e então movendo os mesmos pesos 1 unidade do tempo a frente e aplicando-lhes a $\varepsilon_{t+1} - \varepsilon_{t} - \varepsilon_{t-1} -\cdots - \varepsilon_{t-q+1}$ para obter $Y_{t+1}$.

Usando  o operador $L$, podemos reescrever o modelo MA($q$) como


\begin{equation}
Y_t= \Theta_q(L)\varepsilon_t,
(\#eq:maqL)
\end{equation}


\begin{equation}
\Theta_q(L)=1+ \theta_1L + \theta_2L^2  +\cdots + \theta_qL^q.
(\#eq:ThetaL)
\end{equation}



### O modelo MA(1)

Para $q=1$, obtemos o  modelo:
\begin{equation}
Y_t = \varepsilon_t + \theta_1 \varepsilon_{t-1},
(\#eq:ma1)
\end{equation}
onde $\varepsilon_t$ é um $RB(0,\sigma_\varepsilon^2)$. Segue que

------------------------------------------------------------

>
<span style='color: blue;'> Média do MA(1)</span>  
\[\mathbb{E} (Y_t ) = \mathbb{E}(\varepsilon_t + \theta_1 \varepsilon_{t-1})=\mathbb{E}(\varepsilon_t) + \theta_1 \mathbb{E}(\varepsilon_{t-1})=0.\]

------------------------------------------------------------

<br>

------------------------------------------------------------

>
<span style='color: blue;'>A variância do MA(1)</span>  
\[\mbox{Var}(Y_t )=\mbox{Var}(\varepsilon_t + \theta_1 \varepsilon_{t-1} )= \sigma_\varepsilon^2+\theta_1^2\sigma_\varepsilon^2=(1+\theta_1^2)\sigma_\varepsilon^2.\]

------------------------------------------------------------

<br>
Temos ainda que a função de autocovariância de _lag_ _h_ é:

------------------------------------------------------------

>
<span style='color: blue;'> _FACV_ do MA(1)</span> 
\begin{eqnarray*}
\gamma(h) &=& \mbox{Cov}(Y_t , Y_{t+h} )\\
         &=& \mbox{Cov}(\varepsilon_t + \theta_1 \varepsilon_{t-1}, \varepsilon_{t+h} + \theta_1 \varepsilon_{t+h-1} )\\
         &=& \mbox{Cov}(\varepsilon_t,\varepsilon_{t+h})+\theta_1\mbox{Cov}(\varepsilon_{t}, \varepsilon_{t+h-1})+\theta_1\mbox{Cov}(\varepsilon_{t-1}, \varepsilon_{t+h})+\theta_1^2\mbox{Cov}(\varepsilon_{t-1}, \varepsilon_{t+h-1})\\
         &=&\gamma_\varepsilon(h)+\theta_1\gamma_\varepsilon(h-1)+\theta_1\gamma_\varepsilon(h+1)+\theta_1^2\gamma_\varepsilon(h).
\end{eqnarray*}

------------------------------------------------------------

<br>

Neste caso $\gamma(h)$ só é diferente de 0 quando algum dos argumentos de $\gamma_\varepsilon$ for igual a 0, o que acontece somente quando $h=0$ ou $h=1$ ou $h=-1$. Para $h=0$ obtemos a variância. Para $h=1$ e $h=-1$ obtemos $\gamma(1)=\gamma(-1)=\theta_1$ e para $|h| \geq 2$ teremos $\gamma(h) = 0$.
Desta forma,

------------------------------------------------------------

>
<span style='color: blue;'> _FACV_  _FAC_ e do MA(1)</span> 
\[
\gamma(h)=\begin{cases}
         (1+\theta_1^2)\sigma_\varepsilon^2 &\mbox{  se  }\,\,\,\,\,  h=0;\\
          \theta_1&\mbox{  se  }\,\,\,\,\,  |k|=1;\\
            0&\mbox{  se  }\,\,\,\,\,  |k|\geq 2,\\
        \end{cases}\qquad
 \rho(h)=\begin{cases}
         1&\mbox{  se  }\,\,\,\,\,  k=0;\\
          \frac{\theta}{1+\theta^2}&\mbox{  se  }\,\,\,\,\,  |k|=1;\\
            0&\mbox{  se  }\,\,\,\,\,  |k|\geq 2.\\
        \end{cases}
\]

------------------------------------------------------------



###  Propriedades do modelo MA($q$)

Seja $\varepsilon_t\sim RB(0,\sigma_\varepsilon^2)$ e considere o modelo MA$(q)$
\[ Y_t= \varepsilon_t + \theta_1 \varepsilon_{t-1} + \theta_2 \varepsilon_{t-2} +\cdots+ \theta_q \varepsilon_{t-q}.\]
Definindo $\theta_0=1$, podemos reescrever o modelo MA$(q)$ compactamente como
 \[ Y_t= \sum_{k=0}^q \theta_k\varepsilon_{t-k}.\]

A partir daí podemos obter facilmente a média e a variância de $Y_t$, assim como sua estrutura de autocovariancia e autocorrelação. Primeiramente

------------------------------------------------------------

>
<span style='color: blue;'> Média do MA(_q_)</span> 
\[\mathbb{E} (Y_t ) = \mathbb{E}\Big(\sum_{k=0}^q \theta_k\varepsilon_{t-k}\Big)=\sum_{k=0}^q \theta_k\mathbb{E}(\varepsilon_{t-k})= 0\]


------------------------------------------------------------

<br>

------------------------------------------------------------

>
<span style='color: blue;'>A variância do MA(_q_)</span>  
\begin{eqnarray*}
\mbox{Var}(Y_t) &=& \mbox{Var}\Big(\sum_{k=0}^q \theta_k\varepsilon_{t-k}\Big) = \sum_{k=0}^q \theta_k^2\mbox{Var}(\varepsilon_{t-k}) = \sigma_\varepsilon^2\sum_{k=0}^q \theta_k^2\\
&=& (1 + \theta_1^2 +\cdots +\theta_q^2)\sigma_\varepsilon^2.
\end{eqnarray*}
------------------------------------------------------------

<br>

------------------------------------------------------------

>
<span style='color: blue;'> _FACV_ do MA(_q_)</span> 
\begin{align*}
  \gamma(h)&=\mbox{Cov}(Y_t,Y_{t-h} )\\
  &= \mbox{Cov}\Big(\sum_{k=0}^q \theta_k\varepsilon_{t-k},\sum_{j=0}^q \theta_j\varepsilon_{t-h-j}\Big)\\
  &=\sum_{k=0}^q \sum_{j=0}^q\theta_k\theta_j\mbox{Cov}(\varepsilon_{t-k},\varepsilon_{t-h-j})\\
  &=\sum_{k=0}^q \sum_{j=0}^q\theta_k\theta_j\gamma_\varepsilon(k-h-j)
\end{align*}
note que $\gamma_\varepsilon(k-h-j)\neq 0$ somente quando $k-h-j=0$, ou seja, se $j=k-h$.

------------------------------------------------------------

<br>


 Além disso, se $|h|>q$, não é possível acontecer $k-h-j=0$. Desta forma, se $|h|\leq q$,
 
\[  \gamma(h)=\sum_{k=0}^q \theta_k\theta_{k-h}\gamma_\varepsilon(0)=\sigma_\varepsilon^2\sum_{k=0}^q \theta_k\theta_{k-h}.\]
Concluimos que

------------------------------------------------------------

>
<span style='color: blue;'> _FACV_ e _FAC_ do MA(_q_)</span> 
\[\gamma(h)=\left\{
\begin{array}{cc}
   \sigma_\varepsilon^2\displaystyle{\sum_{k=0}^q \theta_k\theta_{k-h}},  & \mbox{ se } |h|\leq q;\\
  0, &  \mbox{ se } |h|> q,
\end{array}
\right. \quad \mbox{ e } \quad \rho(h)=\left\{
\begin{array}{cc}
   \displaystyle{\frac{\sum_{k=0}^q \theta_k\theta_{k-h}}{\sum_{j=0}^q \theta_j^2}},  & \mbox{ se } |h|\leq q;\quad\\
  0, &  \mbox{ se } |h|> q.
\end{array}\right.\]

--------------------------------------------------------------

<br>


```r
# MA(1) Simulado
set.seed(12322)
ma1_1=arima.sim(n=200,model=list(ma=c(1)))
plot(ma1_1,type="l",lwd=2,cex.lab=1.4, xlab=" tempo",ylab="", main="(a)", cex.main=1.7,col="cadetblue4")
acf(ma1_1,type = "correlation",lag.max = 50,cex.main=1.7,col="cadetblue4",ylab="FAC",lwd=4,main="(b)")
acf(ma1_1,type = "partial" ,lag.max = 50,cex.main=1.7,col="cadetblue4",ylab="FACP",lwd=4,main="(c)")
```

<div class="figure">
<img src="03-SeriesTemp_files/figure-epub3/ma11-1.png" alt="MA(1) simulado com coeficiente $\theta_1=1$, (a) FACV amostral (b) e FAC amostral (c)." width="33%" /><img src="03-SeriesTemp_files/figure-epub3/ma11-2.png" alt="MA(1) simulado com coeficiente $\theta_1=1$, (a) FACV amostral (b) e FAC amostral (c)." width="33%" /><img src="03-SeriesTemp_files/figure-epub3/ma11-3.png" alt="MA(1) simulado com coeficiente $\theta_1=1$, (a) FACV amostral (b) e FAC amostral (c)." width="33%" />
<p class="caption">(\#fig:ma11)MA(1) simulado com coeficiente $\theta_1=1$, (a) FACV amostral (b) e FAC amostral (c).</p>
</div>

<br>


```r
# MA(1) Simulado
set.seed(12322)
ma1_m08=arima.sim(n=200,model=list(ma=c(-0.8)))
plot(ma1_m08,type="l",lwd=2,cex.lab=1.4, xlab=" tempo",ylab="", main="(a)", cex.main=1.7,col="cadetblue4")
acf(ma1_m08,type = "correlation",lag.max = 50,cex.main=1.7,col="cadetblue4",ylab="FAC",lwd=4,main="(b)")
acf(ma1_m08,type = "partial" ,lag.max = 50,cex.main=1.7,col="cadetblue4",ylab="FACP",lwd=4,main="(c)")
```

<div class="figure">
<img src="03-SeriesTemp_files/figure-epub3/ma1m08-1.png" alt="MA(1) simulado com coeficiente $\theta_1=-0.8$, (a) FACV amostral (b) e FAC amostral (c)." width="33%" /><img src="03-SeriesTemp_files/figure-epub3/ma1m08-2.png" alt="MA(1) simulado com coeficiente $\theta_1=-0.8$, (a) FACV amostral (b) e FAC amostral (c)." width="33%" /><img src="03-SeriesTemp_files/figure-epub3/ma1m08-3.png" alt="MA(1) simulado com coeficiente $\theta_1=-0.8$, (a) FACV amostral (b) e FAC amostral (c)." width="33%" />
<p class="caption">(\#fig:ma1m08)MA(1) simulado com coeficiente $\theta_1=-0.8$, (a) FACV amostral (b) e FAC amostral (c).</p>
</div>

<br>


```r
# MA(1) Simulado
set.seed(1234)
ma1_m0804=arima.sim(n=300,model=list(ma=c(-0.8,0.4)))
plot(ma1_m0804,type="l",lwd=2,cex.lab=1.4, xlab=" tempo",ylab="", main="(a)", cex.main=1.7,col="cadetblue4")
acf(ma1_m0804,type = "correlation",lag.max = 50,cex.main=1.7,col="cadetblue4",ylab="FAC",lwd=4,main="(b)")
acf(ma1_m0804,type = "partial" ,lag.max = 50,cex.main=1.7,col="cadetblue4",ylab="FACP",lwd=4,main="(c)")
```

<div class="figure">
<img src="03-SeriesTemp_files/figure-epub3/ma1m0804-1.png" alt="MA(2) simulado com coeficiente $\theta_1=-0.8$ e $\theta_1=0.4$, (a) FACV amostral (b) e FAC amostral (c)." width="33%" /><img src="03-SeriesTemp_files/figure-epub3/ma1m0804-2.png" alt="MA(2) simulado com coeficiente $\theta_1=-0.8$ e $\theta_1=0.4$, (a) FACV amostral (b) e FAC amostral (c)." width="33%" /><img src="03-SeriesTemp_files/figure-epub3/ma1m0804-3.png" alt="MA(2) simulado com coeficiente $\theta_1=-0.8$ e $\theta_1=0.4$, (a) FACV amostral (b) e FAC amostral (c)." width="33%" />
<p class="caption">(\#fig:ma1m0804)MA(2) simulado com coeficiente $\theta_1=-0.8$ e $\theta_1=0.4$, (a) FACV amostral (b) e FAC amostral (c).</p>
</div>

<br>


```r
# MA(1) Simulado
set.seed(12341)
ma1_m080414=arima.sim(n=300,model=list(ma=c(-0.8,0.4,1.4)))
plot(ma1_m080414,type="l",lwd=2,cex.lab=1.4, xlab=" tempo",ylab="", main="(a)", cex.main=1.7,col="cadetblue4")
acf(ma1_m080414,type = "correlation",lag.max = 50,cex.main=1.7,col="cadetblue4",ylab="FAC",lwd=4,main="(b)")
acf(ma1_m080414,type = "partial" ,lag.max = 50,cex.main=1.7,col="cadetblue4",ylab="FACP",lwd=4,main="(c)")
```

<div class="figure">
<img src="03-SeriesTemp_files/figure-epub3/ma1m080414-1.png" alt="MA(2) simulado com coeficiente $\theta_1=-0.8$, $\theta_1=0.4$ e $\theta_1=1.4$, (a) FACV amostral (b) e FAC amostral (c)." width="33%" /><img src="03-SeriesTemp_files/figure-epub3/ma1m080414-2.png" alt="MA(2) simulado com coeficiente $\theta_1=-0.8$, $\theta_1=0.4$ e $\theta_1=1.4$, (a) FACV amostral (b) e FAC amostral (c)." width="33%" /><img src="03-SeriesTemp_files/figure-epub3/ma1m080414-3.png" alt="MA(2) simulado com coeficiente $\theta_1=-0.8$, $\theta_1=0.4$ e $\theta_1=1.4$, (a) FACV amostral (b) e FAC amostral (c)." width="33%" />
<p class="caption">(\#fig:ma1m080414)MA(2) simulado com coeficiente $\theta_1=-0.8$, $\theta_1=0.4$ e $\theta_1=1.4$, (a) FACV amostral (b) e FAC amostral (c).</p>
</div>






### Modelo ARMA($p$,$q$)

Um  modelo mais geral é dado pela aglutinação dos modelos AR e MA em um único modelos, ao qual chamamos Modelos Autoregressivos de Média Móveis, abreviado ARMA. Um processo $\{Y_t\}_t$ é um ARMA$(p,q)$ se pode ser escrito como

onde $\varepsilon_t\sim RB(0,\sigma_\varepsilon^2)$, $\phi_1,\cdots,\phi_p\in\mathbb{R}$ são os coeficientes da parte AR e $\theta_1,\cdots\theta_q\in\mathbb{R}$ são os coeficientes da parte MA do processo. Utilizando os polinômios AR e MA vistos anteriormente, podemos escrever um processo ARMA$(p,q)$ de uma forma compacta e elegante.

------------------------------------------------------------

>
<span style='color: blue;'> O modelo ARMA(_p_,_q_)</span> 
\begin{equation}
Y_t=\phi_1Y_{t-1}+\cdots+\phi_pY_{t-p}+\theta_1\varepsilon_{t-1}+\cdots+\theta_q\varepsilon_{t-q} + \varepsilon_t
(\#eq:mARMA2)
\end{equation}
em que $\varepsilon_t\sim RB(0,\sigma_\varepsilon^2)$, $\phi_1,\cdots,\phi_p\in\mathbb{R}$ são os coeficientes da parte AR e $\theta_1,\cdots\theta_q\in\mathbb{R}$ são os coeficientes da parte MA do processo. 

------------------------------------------------------------

<br>

Utilizando os polinômios AR e MA vistos anteriormente, podemos escrever um processo ARMA$(p,q)$ de uma forma compacta e elegante.

 \[\Phi_p(L)Y_t=\Theta_q(L)\varepsilon_t,\]
em  que $\varepsilon_t$ é um $RB(0,\sigma_\varepsilon^2)$, $\Phi_p(L)$ e $\Theta_p(L)$  são polinômios da parte AR e MA (respectivamente) dados por
\[\Phi_p(L)=1-\phi_1L-\phi_2L^ 2-\cdots-\phi_pL^p  \quad\mbox{e}\quad  \Theta_q(L)=1+ \theta_1L + \theta_2L^2  +\cdots + \theta_qL^q.\]


<br>

\BeginKnitrBlock{example}\iffalse{-91-32-77-111-100-101-108-111-32-65-82-77-65-40-50-44-51-41-32-93-}\fi{}<div class="example"><span class="example" id="exm:arma23"><strong>(\#exm:arma23)  \iffalse ( Modelo ARMA(2,3) ) \fi{} </strong></span>O Modelo ARMA(2,3) é escrito como

\begin{eqnarray*}
\Phi_2(L)y_t&=&\Psi_3(L)\varepsilon_t\\
(1-\phi_1L-\phi_2L^2)y_t&=&(1+\theta_1L+\theta_2L^2+\theta_3L^3)\varepsilon_t\\
y_t&=&\phi_1y_{t-1}+\phi_2y_{t-2}+\varepsilon_t+\theta_1\varepsilon_{t-1}+\theta_2\varepsilon_{t-2}+\theta_3\varepsilon_{t-3}.
\end{eqnarray*}</div>\EndKnitrBlock{example}

#### Exemplos ARMA simulados


\BeginKnitrBlock{example}\iffalse{-91-67-97-117-115-97-108-105-100-97-100-101-32-100-111-32-112-114-111-99-101-115-115-111-32-65-82-40-49-41-93-}\fi{}<div class="example"><span class="example" id="exm:causar1"><strong>(\#exm:causar1)  \iffalse (Causalidade do processo AR(1)) \fi{} </strong></span>O modelo AR(1):

\[
y_t = \phi y_{t-1} + e_t,
\]

pode ser escrito como
 \[
 y_t = e_t + \phi e_{t-1} + \phi^2 e_{t-2} + \cdots + \phi^{k-1}e_{t-(k-1)} + \phi^ky_{t-k},
\]
em que para $k$ grande tem-se

\begin{eqnarray*}
y_t & = & e_t + \phi e_{t-1} + \phi^2 e_{t-2} + \ldots\\
   & = & \psi_0 e_t + \psi_1 e_{t-1} + \psi_2 e_{t-2} + \ldots,
\end{eqnarray*}
em  que $|\phi| < 1$ e $\psi_j = \phi^j$. O  que acontece com a  variância de $y_t$? Assim, essa  representação somente faz sentido se
$\sum_{j=0}^{\infty}\psi_j<\infty$,  o que ocorre se, e somente  se, $|\phi|<1$.</div>\EndKnitrBlock{example}



### Causalidade

O  conceito de <span style='color: blue;'> causalidade </span> consiste em escrever um processo AR($q$) como um MA($\infty$).

---------------------------------------------------------------------------

> 
Um  processo linear  $\{Y_t \}$ é <span style='color: blue;'> CAUSAL </span> (estritamente, uma função causal de  $\{\varepsilon_t \}$) se existem reais $\psi_0,\psi_1,\cdots$ satisfazendo $\sum_{j=0}^{\infty}|\psi_j|<\infty$ e tais que
\begin{align}
Y_t = \psi_0\varepsilon_t + \psi_1\varepsilon_{t-1} + \psi_2 \varepsilon_{t-2} + \cdots = \sum_{k=0}^\infty\psi_k\varepsilon_{t-k}= \Psi(L)\varepsilon_t,
(\#eq:causaldef)
\end{align}
onde denotamos
\[
\Psi(L) = \psi_0 + \psi_1 L + \psi_2 L^2 + \cdots = \sum_{k=0}^\infty\psi_kL^k.
\]

---------------------------------------------------------------------------




O modelo AR(1) é dado por:

\[
Y_t = \phi Y_{t-1} + \varepsilon_t,
\]
para $|\phi|<1$ e $\varepsilon_t\sim RB(0,\sigma^2_\varepsilon)$. Na Seção \@ref(sec:subar1) obtivemos a representação (com $c=0$)
\[Y_t = \sum_{j=0}^\infty \phi^j\varepsilon_{t-j}.\]
Identificando-se $\psi_j= \phi^j$, obtemos que $Y_t$ possui a representação \@ref(eq:causaldef) e observando que, como $|\phi|<1$,
\[\sum_{j=0}^{\infty}|\psi_j|=\sum_{j=0}^{\infty}|\phi|^j=\frac1{1-|\phi|}<\infty,\]
segue que um AR(1) com $|\phi|<1$ é causal.

Obviamente todo modelo MA$(q)$ é causal, dado que se
\[Y_t=\varepsilon_t+\theta\varepsilon_{t-1}+\cdots+\theta_q\varepsilon_{t-q},\]
com $\varepsilon_t\sim RB(0, \sigma_\varepsilon^2)$, tomamos $\psi_0=1$, $\psi_j=\theta_j$, para $j=1,\cdots,q$ e $\psi_j=0$ para $j>q$, temos que a representação \@ref(eq:causaldef) é satisfeita e, evidentemente, $\sum_{j=0}^\infty|\psi|_j=1+|\theta_1|+\cdots+|\theta_q|<\infty$.


<br>


### Invertibilidade

Mostramos que um processo AR pode ser reescrito como um processo MA de ordem infinita através de pesos $\psi_j$'s. Podemos nos perguntar quando (e se) é possível escrever um processo MA como
um autorregressivo.

<br>

-------------------------------------------------------

> 
Um processo  linear  $\{Y_t \}$  é dito ser <span style='color: blue;'> INVERTÍVEL </span>  (estritamennte, uma função invertível de $\{\varepsilon_t \}$) se existem reais $\mbox{Var}phi_1,\mbox{Var}phi_2,\cdots$ satisfazendo $\sum_{j=0}^{\infty}|\mbox{Var}phi_j|<\infty$ e tais que
\begin{align}
\varepsilon_t = \mbox{Var}phi_0Y_t+\mbox{Var}phi_1Y_{t-1}+\mbox{Var}phi_2Y_{t-2}+\cdots =\sum_{k=0}^\infty\mbox{Var}phi_kY_{t-k}=\Phi(L)Y_t,
(\#eq:invertdef)
\end{align}
onde denotamos
\[
\Phi(L) = \mbox{Var}phi_0 + \mbox{Var}phi_1 L + \mbox{Var}phi_2 L^2 + \cdots = \sum_{k=0}^\infty\mbox{Var}phi_kL^k.
\]

-----------------------------------------------



<br>

\BeginKnitrBlock{example}\iffalse{-91-73-110-118-101-114-116-105-98-105-108-105-100-97-100-101-32-100-111-32-112-114-111-99-101-115-115-111-32-77-65-40-49-41-93-}\fi{}<div class="example"><span class="example" id="exm:invma1"><strong>(\#exm:invma1)  \iffalse (Invertibilidade do processo MA(1)) \fi{} </strong></span>Considere o modelo MA(1)

\[
Y_t = \varepsilon_t -\theta \varepsilon_{t-1},
\]
em  que $\varepsilon_t$ é um $RB(0,\sigma^2)$. Reescrevendo a equação acima
como
\[
\varepsilon_t = Y_t + \theta \varepsilon_{t-1}
\]
e substituindo $t$ por $t - 1$
e $\varepsilon_{t-1}$ na equação modificada, temos:
\begin{eqnarray*}
\varepsilon_t &=& Y_t + \theta(Y_{t-1} + \theta \varepsilon_{t-2})\\
    &=& Y_t + \theta Y_{t-1} + \theta^2Y_{t-2}
\end{eqnarray*}
Se $|\theta| < 1$, podemos continuar a substituição e obter:
\begin{eqnarray*}
  \varepsilon_t  &=& Y_t + \theta Y_{t-1} + \theta^2Y_{t-2}+\cdots = \sum_{j=0}^\infty\theta^jY_{t-j}.
\end{eqnarray*}

Assim, da mesma forma como foi feito para o AR(1), tomando $\mbox{Var}\phi_j=\theta^j$, segue que, se $|\theta| < 1$, a representação \eqref{invert_def} é satisfeita e $\sum_{j=0}^\infty|\mbox{Var}\phi_j|=\frac1{1-|\theta|}<\infty$ de onde concluimos que o modelo MA(1) é invertível. Em outras palavras, um modelo MA(1) pode ser invertido (transformado) para um AR($\infty$), sempre que $|\theta|<1$.
</div>\EndKnitrBlock{example}




### Polinômio característico

Nos exemplos mostrados acima tratamos da causalidade e invertibilidade dos casos
AR(1) e MA(1) em particular. Para os casos mais gerais AR($p$) e MA($q$) utilizamos os
chamados **_polinômios característicos_** para decidir se os processos são causais e/ou invertíveis.

Para um modelo geral AR($p$), definimos o **_polinômios característicos AR_** 
como
\[
\Phi(z) = 1 - \phi_1 z -\phi_2 z^2-\cdots-\phi_p z^p, \ \ z\in\mathbb{C}
\]
<br>

\BeginKnitrBlock{theorem}<div class="theorem"><span class="theorem" id="thm:soluest"><strong>(\#thm:soluest) </strong></span>Uma (única) solução **estacionária** para $\Phi(L)y_t = e_t$ existe se, e  somente, as  raízes de $\Phi(z)$ **não pertence ao círculo de raio um**, ou  seja,

\begin{equation*}
|z| = 1 \rightarrow \Phi(z) = 1 - \phi_1 z - \cdots - \phi_p z^p \neq 0.
\end{equation*}

O processo AR($p$) é **causal** se, e  somente  se as raízes de $\Phi(z)$ estão **fora do círculo unitário**, ou seja,

\[
|z| \leq 1 \rightarrow \Phi(z) = 1 - \phi_1 z - \cdots - \phi_p z^p \neq 0.
\]</div>\EndKnitrBlock{theorem}


<br>

Para um modelo geral MA($q$), definimos o <span style='color: blue;'> polinômio característico MA </span> como
\begin{equation*}
\Theta(z) = 1 + \theta_1 z +\theta_2 z^2+\cdots+\theta_q z^q.
\end{equation*}

<br>

\BeginKnitrBlock{theorem}<div class="theorem"><span class="theorem" id="thm:invert"><strong>(\#thm:invert) </strong></span>Um processo MA($q$) é invertível se, e somente  se, as raízes de $\Theta(z)$ estão fora do círculo
unitário,  isto é,

\begin{equation*}
z\in\mathbb{C} : |z|\leq  1 \mathbb{R}ightarrow \Theta(z) = 1 + \theta_1 z +\theta_2 z^2+\cdots+\theta_q z^q\neq 0.
\end{equation*}</div>\EndKnitrBlock{theorem}

<br>

\BeginKnitrBlock{remark}<div class="remark">\iffalse{} <span class="remark"><em>Observação. </em></span>  \fi{}Um processo ARMA será invertível e estacionário se a parte AR o for, e será invertível se a parte MA o for.</div>\EndKnitrBlock{remark}





### Estacionariedade e causalidade de um processo ARMA


Para um  processo  ARMA, as condições para causalidade, invertibilidade e estacionariedade são dadas no seguinte teorema.

<br>

\BeginKnitrBlock{theorem}<div class="theorem"><span class="theorem" id="thm:causaarma"><strong>(\#thm:causaarma) </strong></span>Se $\Phi(\cdot)$ e  $\Theta(\cdot)$ não possuem fatores em comum, existe
uma única solução estacionária  $\{Y_t\}$ para $\Phi(L)Y_t = \Theta(L)\varepsilon_t$
se, e somente se,

\begin{equation*}
z\in\mathbb{C} : |z| = 1 \mathbb{R}ightarrow \Phi(z) = 1 - \phi_1 z - \cdots - \phi_p z^p \neq 0.
\end{equation*}


Esse  processo ARMA($p,q$) é causal se, e somente se,
\begin{equation*}
z\in\mathbb{C} : |z| \leq 1 \mathbb{R}ightarrow \Phi(z) = 1 - \phi_1 z - \cdots - \phi_p z^p \neq 0.
\end{equation*}

Será invertível  se, e somente se

\begin{equation*}
z\in\mathcal{C} : |z|\leq  1 \mathbb{R}ightarrow \Theta(z) = 1 + \theta_1 z +\theta_2 z^2+\cdots+\theta_q z^q\neq 0.
\end{equation*}
</div>\EndKnitrBlock{theorem}




## Exercícios



\BeginKnitrBlock{exercise}<div class="exercise"><span class="exercise" id="exr:pest"><strong>(\#exr:pest) </strong></span>Defina processo estocástico e ilustre graficamente. Explique o que é a realização de um processo estocástico e por que séries econômicas podem ser entendidas como geradas por um processo estocásticos.</div>\EndKnitrBlock{exercise}

<br>

\BeginKnitrBlock{exercise}<div class="exercise"><span class="exercise" id="exr:stce"><strong>(\#exr:stce) </strong></span> Seja $\{y_t\}^T_{t=1}$ uma série temporal. Quais características essa série deve apresentar para ser considerada uma série de covariância estacionária?</div>\EndKnitrBlock{exercise}


<br>

\BeginKnitrBlock{exercise}<div class="exercise"><span class="exercise" id="exr:defrb"><strong>(\#exr:defrb) </strong></span>Faça os seguintes items:

|    a\) Defina o que é um processo ruído branco.

|    b\) Defina o que é um processo independente e identicamente distribuído (i.i.d.).

|    c\) Defina ruído branco Gaussiano.

|    d\) Qual a relação entre ruído branco, ruído branco Gaussiano e processo i.i.d.?

|    e\) Esses processos são estacionários?
</div>\EndKnitrBlock{exercise}

<br>

\BeginKnitrBlock{exercise}<div class="exercise"><span class="exercise" id="exr:ma1"><strong>(\#exr:ma1) </strong></span>Considere um processo MA(1):
$y_t=e_t+\alpha_1e_{t-1};$ onde $e_t \sim RB(0,\sigma^2_e)$.

|    a\) Calcule a média e variância de $y_t$.

|    b\) Calcule as autocovariâncias de $lags$ 1 e 2 para a série $y_t$.

|    c\) Esse processo é estacionário? (Justifique sua resposta usando os valores encontrados nos itens anteriores juntamente com o conceito de estacionariedade definido na Questão 1).

|    d\) Comente a afirmativa: ``Todo processo MA($q$), onde $q < \infty,$ é estacionário''.

|    e\) Suponha que $\alpha_1=0.5$. O processo é invertível?
  
|    f\) Calcule a autocorrelação de ordem 1 para o processo do item anterior e faça o gráfico da FAC com 5 $lags$.
</div>\EndKnitrBlock{exercise}


<br>

\BeginKnitrBlock{exercise}<div class="exercise"><span class="exercise" id="exr:ma2"><strong>(\#exr:ma2) </strong></span> Considere um processo MA(2): $y_t=e_t+\alpha_1e_{t-1}+\alpha_2e_{t-2};$ onde $e_t \sim
RB(0,\sigma^2_e)$.

|    a\) Calcule a média e variância de $y_t$.

|    b\) Calcule as autocovariâncias de $lags$ 1, 2 e 3 para a série $y_t$.

|    c\) Esse processo é estacionário? (Justifique sua resposta usando os valores encontrados nos itens anteriores juntamente com o conceito de estacionariedade definido na Questão 1).

|    d\) Suponha que $\alpha_1=0.65$ e que $\alpha_2=-0.20$. O processo é invertível?
  
|    e\) Calcule a autocorrelação de ordem 1 e 2 para o processo do item anterior e faça o gráfico da FAC com 5 $lags$.
</div>\EndKnitrBlock{exercise}

<br>

\BeginKnitrBlock{exercise}<div class="exercise"><span class="exercise" id="exr:p1p2"><strong>(\#exr:p1p2) </strong></span>Considere os seguintes processos
\[y_t=e_t+\theta e_{t-1} \quad\mbox{e} \quad y_t=e_t+\frac{1}{\theta}e_{t-1},\] onde $e_t \sim
iid(0,\sigma^2_e)$ e $\theta \neq 0$.

|    a\) Os processos acima possuem as mesmas autocorrelações? Verifique.

|    b\) Os processos acima são invertíveis? Verifique.
</div>\EndKnitrBlock{exercise}


<br>

\BeginKnitrBlock{exercise}<div class="exercise"><span class="exercise" id="exr:ar1"><strong>(\#exr:ar1) </strong></span>Considere um processo AR(1):
$y_t=5+0.9y_{t-1}+e_t$, onde $e_t \sim RB(0,\sigma^2_e)$.


|    a\) Esse processo é estacionário? Verifique.

|    b\) Calcule as autocorrelações de ordem 1, 2 e 3 para esse processo. Faça um esboço do gráfico da FAC para esse processo com 5 $lags$.

|    c\) O que significa o coeficiente de $y_{t-1}$ num processo AR(1)?
  
|    d\) Faça um gráfico da FACP desse processo com 5 $lags$.
</div>\EndKnitrBlock{exercise}

<br>

```{exercise ar123} Para os seguintes itens, responda:

|    a\) Explique como se comportam os gráficos da FAC e da FACP em processos AR($p$) e em processos MA($q$).

|    b\) Esboce os gráficos da FAC e FACP para os seguintes processos: AR(1), AR(3), MA(2) e MA(3).

```


<br>

```{exercise exarmafac} Para os seguintes itens, responda:

|    a\) Supondo que $E(y_t)=\mu$ e que $y_t=c_0+\beta_1y_{t-1}+e_t+\alpha_1e_{t-1}$, calcule o valor de $c_0$ em termos de $\mu$ e $\beta_{1}$.

|    b\) Explique como se comportam os gráficos da FAC e da FACP em processos ARMA($p,q$).

|    c\) Esboce os gráficos da FAC e FACP para um processos ARMA(1,1).

```

<br>

\BeginKnitrBlock{exercise}<div class="exercise"><span class="exercise" id="exr:exarmamet"><strong>(\#exr:exarmamet) </strong></span>Explique os passos que devem ser seguidos para a modelagem de uma série temporal na metodologia ARMA.</div>\EndKnitrBlock{exercise}

<br>

\BeginKnitrBlock{exercise}\iffalse{-91-65-78-80-69-67-32-50-48-49-52-45-53-93-}\fi{}<div class="exercise"><span class="exercise" id="exr:a145"><strong>(\#exr:a145)  \iffalse (ANPEC 2014-5) \fi{} </strong></span>Suponha que $Y_t$ seja representado pelo seguinte processo autorregressivo de primeira ordem:
\[Y_t = 10 + 0,6 Y_{t-1} + e_t ,\]
em que et é um ruído branco que satisfaz as condições: $\mathbb{E}(e_t)=0,$ $\mathbb{E}(e_t^2)=\sigma^2$, $\mathbb{E}(e_te_s)=0$ para $t\neq s.$ Suponha também que $Y_0=0$. Obtenha $\mathbb{E}(Y_t)$ para $t=2$.</div>\EndKnitrBlock{exercise}

<br>

\BeginKnitrBlock{exercise}\iffalse{-91-65-78-80-69-67-32-50-48-49-52-45-49-48-93-}\fi{}<div class="exercise"><span class="exercise" id="exr:a1410"><strong>(\#exr:a1410)  \iffalse (ANPEC 2014-10) \fi{} </strong></span>Considere o seguinte processo:
\[Y_t=\rho Y_{t-1}+e_t,\,\,\,\, t=1,2,\cdots,\]
em que $Y_0=0$ e $e_t$ é um ruído branco que satisfaz as condições: $\mathbb{E}(e_t)=0$, $\mathbb{E}(e_t^2)=\sigma^2$, $\mathbb{E}(e_te_s)=0$
para $t\neq s$.
São corretas as afirmativas:
  
|    0\) Se $\rho=1$, $\mathbb{E}(Y_t)=0$ para todo $t$;

|    1\) Se $\rho=1$, $\mbox{Var}(Y_t)= t$ para todo $t$;

|    2\) Se $\rho=1$, $\mathbb{E}(Y_{t+h}/Y_t)>Y_t$ para todo $h\geq 1$;

|    3\) Se $|\rho|<1$, $\mbox{Var}(Y_t)= 1$;

|    4\) Se $|\rho|<1$, $\mathbb{E}(Y_{t+h}/Y_t)= \rho^h Y_t$ para todo $h\geq 1$.
</div>\EndKnitrBlock{exercise}

<br>

\BeginKnitrBlock{exercise}\iffalse{-91-65-78-80-69-67-32-50-48-49-51-45-49-48-93-}\fi{}<div class="exercise"><span class="exercise" id="exr:a1310"><strong>(\#exr:a1310)  \iffalse (ANPEC 2013-10) \fi{} </strong></span>Julgue as seguintes afirmativas:
  
|    0\) O passeio aleatório com drift, $y_t = c + y_{t-1} + \varepsilon_t$, $y_0 = 0$, em que $\varepsilon_t$ é um ruído branco, com média zero e variância $\sigma^2$, é um processo estacionário de segunda ordem se $c = 0$.

|    1\) O processo MA(1), $yt = \varepsilon_t + \theta_1 \varepsilon_{t-1}$ , em que $\varepsilon_t$ é um ruído branco, com média zero e variância $\sigma^2$, é estacionário de segunda ordem se, e somente se, a raiz do polinômio $1 + \theta_1x$ cair fora do círculo unitário.

|    2\) O processo MA(1), $y_t = \varepsilon_t -\theta_1 \varepsilon_{t-1}$ , em que $\varepsilon_t$ é um ruído branco, com média zero e variância $\sigma^2$, é inversível se, e somente se, $|\theta_1| < 1$.

|    3\) O processo AR(2), $y_t = \phi_1y_{t-1} + \phi_2y_{t-2} + \varepsilon_t$, em que $\varepsilon_t$ é um ruído branco, com média zero e variância $\sigma^2$, é estacionário de segunda ordem se
\[|\phi_2| < 1,\,\,\,\, \phi_2 - \phi_1 < 1\,\,\,\,\mbox{ e }\,\,\,\,\, \phi_2 + \phi_1 < 1.\]

|    4\) No passeio aleatório, $y_t = y_{t-1} + \varepsilon_t$, $y_0 = 0$, em que $\varepsilon_t$ é um ruído branco, com média zero e variância $\sigma^2$, a variância de $y_t$ varia com $t$.
</div>\EndKnitrBlock{exercise}

<br>

\BeginKnitrBlock{exercise}\iffalse{-91-65-78-80-69-67-32-50-48-49-51-45-49-51-93-}\fi{}<div class="exercise"><span class="exercise" id="exr:a1313"><strong>(\#exr:a1313)  \iffalse (ANPEC 2013-13) \fi{} </strong></span>Considere o seguinte processo $x_t = \mu + e_t + \alpha_1 e_{t-1}$, para $t=1,2,\cdots$, no qual $e_t$ é uma sequência i.i.d com média 0 e variância $\sigma_e^2$ .
Julgue as seguintes afirmativas:
  
|    0\) $\mbox{Var}[ x_t ] = (1 + \alpha_1^2 )\sigma_e^2$.

|    1\) $\mbox{Cov}( x_t , x_{t +h} ) = 0$, $h > 1$.

|    2\) $\mathbb{E}[ x_t ] = \mu + t$.

|    3\) O processo descrito acima é estacionário em covariância.

|    4\) A função de autocorrelação deste processo é: $\rho_1 =\frac{\alpha_1}{1+\alpha_1^2}$ e $\rho_j=0$ para $j>1$.
</div>\EndKnitrBlock{exercise}

<br>

\BeginKnitrBlock{exercise}\iffalse{-91-65-78-80-69-67-32-50-48-49-50-45-48-56-93-}\fi{}<div class="exercise"><span class="exercise" id="exr:a128"><strong>(\#exr:a128)  \iffalse (ANPEC 2012-08) \fi{} </strong></span>Suponha que $Yt$ seja descrito por um processo auto-regressivo de ordem 3, isto é,
\[Y_t = Y_{t-1} - 0,50Y_{t-3} + u_t\]
e que
\[u_t | Y_{t - j}\sim N(0,\sigma^2),\,\,\,\, \forall j > 0.\]
Calcule a correlação entre $Y_t$ e $Y_{t-2}$. Multiplique o resultado por 100.</div>\EndKnitrBlock{exercise}

<br>

\BeginKnitrBlock{exercise}\iffalse{-91-65-78-80-69-67-32-50-48-49-49-45-49-49-93-}\fi{}<div class="exercise"><span class="exercise" id="exr:a1111"><strong>(\#exr:a1111)  \iffalse (ANPEC 2011-11) \fi{} </strong></span>Julgue as seguintes afirmativas:
  
|    0\) O processo AR(2), $y_t = \rho_1 y_{t-1} + \rho_2 y_{t-2} + \varepsilon_t$ , em que $\varepsilon_t$ é um ruído branco com média zero e variância $\sigma^2$, é estacionário de segunda ordem se e somente se as raízes do polinômio $x^2-\rho_1 x +\rho_2$ estão fora do círculo unitário.

|    1\) No processo MA(2), $y_t = \varepsilon_t + \theta_1\varepsilon_{t-1} + \theta_2 \varepsilon_{t-2}$ , em que $\varepsilon_t$ é um ruído branco com média zero e variância $\sigma^2$, a covariância entre $y_t$ e $y_{t-3}$ é igual a zero.

|    2\) No passeio aleatório com drift, $y_t = c + y_{t-1} + \varepsilon_t$, $y_0 = 0$, em que $\varepsilon_t$ é um ruído branco com média zero e variância $\sigma^2,$ a média de $y_t$ varia com $t$.

|    3\) No processo MA(1), $y_t = \varepsilon_t + \theta_1 \varepsilon_{t-1}$ , em que $\varepsilon_t$ é um ruído branco com média zero e variância $\sigma^2$, a correlação entre $y_t$ e $y_{t-1}$ é menor ou igual a 0,5 em valor absoluto.

|    4\) O processo ARMA(1,1), $y_t = \rho y_{t-1} + \varepsilon_t + \theta \varepsilon_{t-1}$ , em que $\varepsilon_t$ é um ruído branco com média zero e variância $\sigma^2$, é estacionário de segunda ordem se e somente se $|\rho| < 1$ e $|\theta| < 1$.
</div>\EndKnitrBlock{exercise}



<br>

\BeginKnitrBlock{exercise}\iffalse{-91-65-78-80-69-67-32-50-48-48-57-45-49-53-93-}\fi{}<div class="exercise"><span class="exercise" id="exr:a0915"><strong>(\#exr:a0915)  \iffalse (ANPEC 2009-15) \fi{} </strong></span>É correto afirmar que:
  
|    0\) No processo AR(1), $y_t = \phi_0 + \phi_1 y_{t-1} + e_t$, em que $\phi_1 < 1$ e $e_t$ é um ruído branco de média nula e variância $\sigma^2$, a média de $y_t$ será igual a $\phi_0$.

|    1\) O processo MA(1), $y_t = e_t + \theta e_{t-1}$, em que $e_t$ é um ruído branco de média nula e variância constante, será estacionário mesmo que $\theta > 1$.

|    2\) Seja a função de autocorrelação do processo AR(1) definido no item (0) dada por $\rho_j$. É correto afirmar que $\rho_j = \phi_1^j$.

|    3\) O processo AR(2), $y t = \phi_0 + \phi_1 y_{t-1} + \phi_2 y_{t-2} + e_t$, em que $e_t$ é um ruído branco de média nula e variância $\sigma^2$, será estacionário de segunda ordem se, e somente se, $\phi_1 < 1$ e $\phi_2 < 1$.

|    4\) No modelo ARMA(1,1), $y_t = \phi_0 + \phi_1 y_{t-1} + e_t + \theta e_{t-1}$ , em que $e_t$ é um ruído branco de média nula e variância constante ($\sigma^2$), a variância de $y_t$ é dada por $\frac{\sigma^2(1+\theta^2)}{1-\phi^2}$.
</div>\EndKnitrBlock{exercise}


<br>

\BeginKnitrBlock{exercise}<div class="exercise"><span class="exercise" id="exr:s200"><strong>(\#exr:s200) </strong></span>Considere uma série temporal com 200 observações. A Figura \@ref(fig:exarma) mostra a evolução da série ao longo do tempo. A tabela a seguir fornece as autocorrelações, $\rho$´s, e autocorrelações parciais, $\phi$s, estimados a partir dessa série.</div>\EndKnitrBlock{exercise}

<div class="figure">
<img src="03-SeriesTemp_files/figure-epub3/exarma-1.png" alt="Série temporal simulada" width="95%" />
<p class="caption">(\#fig:exarma)Série temporal simulada</p>
</div>

<br>

|$k$ | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 
|-----|-------|--------|----------|--------|--------|---------|------------|-----------|-----------|-----------------------|
|$\rho_k$ | 0.51 | 0.13 | 0.01 | 0.04 | 0.03 | 0.00 | 0.04 | 0.02 | 0.08 | 0.01 |
|$\phi_{k,k}$ | 0.51 | -0.18 | 0.03 | 0.06 | -0.03 | -0.00 | 0.07 | -0.05 | 0.13 | -0.11 |

<br>

|    a\) Analisando a Figura \@ref(fig:exarma) a série parece ser estacionária? Explique.

|    b\) Faça o gráfico da FAC e FACP para esse processo.

|    c\) Calcule o critério para decisão quanto à significância das autocorrelações estimadas e represente esse critério nos gráficos da FAC e FACP.

|    d\) Qual(is) modelo(s) você propõe para ajustar essa série temporal? Justifique.


<br>

\BeginKnitrBlock{exercise}<div class="exercise"><span class="exercise" id="exr:exprev"><strong>(\#exr:exprev) </strong></span>Usando a esperança condicional, calcule as previsões 1, 2 e 3 passos a frente $(\widehat{y}_T(1)$, $\widehat{y}_T(2)$, $\widehat{y}_T(3))$ para os seguintes processos:

|    a\)  AR(1);

|    b\)  AR(2);

|    c\)  MA(1);

|    d\)  MA(3);

|    e\)  ARMA(1,1);

|    f\)  ARMA(2,2).
</div>\EndKnitrBlock{exercise}



<br>

\BeginKnitrBlock{exercise}<div class="exercise"><span class="exercise" id="exr:exprev200"><strong>(\#exr:exprev200) </strong></span>Abaixo (Figura 2) encontram-se os gráficos da FAC e FACP calculados para uma série
$\{y_t\}^{200}_{t=1}$.</div>\EndKnitrBlock{exercise}

<br>

<div class="figure">
<img src="03-SeriesTemp_files/figure-epub3/exarmapf-1.png" alt="FAC e FACP de uma série temporal simulada" width="45%" /><img src="03-SeriesTemp_files/figure-epub3/exarmapf-2.png" alt="FAC e FACP de uma série temporal simulada" width="45%" />
<p class="caption">(\#fig:exarmapf)FAC e FACP de uma série temporal simulada</p>
</div>

<br>

|    a\) Analisando a Figura \@ref(fig:exarmapf) a série parece ser estacionária? Explique.

|    b\) Usando os gráficos da FAC e FACP, qual(is) modelo(s) você propõe para ajustar essa série temporal? Justifique. (Note que o primeiro $lag$ é o 1 em ambos os gráficos).







