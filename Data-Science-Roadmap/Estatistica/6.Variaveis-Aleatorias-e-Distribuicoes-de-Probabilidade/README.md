<h1>6. Variáveis Aleatórias e Distribuições de Probabilidade: Esperança Matemática, Variância, Covariância, Coeficiente de Correlação.</h1>
<h2 align="center">Esperança Matemática</h2>
<p>A esperança matemática, também chamada de valor esperado, é uma medida de centralidade de uma variável aleatória. É definida como a soma dos produtos de cada valor possível da variável pela sua respectiva probabilidade.</p>
<p>Em outras palavras, a esperança matemática representa o valor médio "esperado" de uma experiência se ela for repetida muitas vezes.</p>
<p>A esperança matemática é um conceito fundamental na teoria das probabilidades e é usada em uma ampla variedade de aplicações, incluindo:</p>
<ul>
  <li><b>Estatística:</b> para estimar o valor médio de uma população a partir de uma amostra</li>
  <li><b>Finanças:</b> para calcular o retorno esperado de um investimento</li>
  <li><b>Economia:</b> para analisar o comportamento de agentes econômicos</li>
  <li><b>Engenharia:</b> para estimar a confiabilidade de um sistema</li>
</ul>
<p align="center"><b>Exemplos:</b></p>
<p>Suponha que você jogue uma moeda e ganhe R$ 1 se sair cara e R$ 0 se sair coroa. A esperança matemática desse jogo é:</p>
<pre align="center"><b>E(X) = (1 * 0,5) + (0 * 0,5) = 0,5</b></pre>
<p>Ou seja, você pode esperar ganhar R$ 0,50 em média a cada jogo.</p>
<p>Suponha que você jogue um dado e ganhe R$ 2 se sair 6, R$ 1 se sair 5 ou 4, e R$ 0 se sair qualquer outro número. A esperança matemática desse jogo é:</p>
<pre align="center"><b>E(X) = (2 * 1/6) + (1 * 2/6) + (1 * 2/6) = 1,33</b></pre>
<p>Ou seja, você pode esperar ganhar R$ 1,33 em média a cada jogo.</p>
<p>Cálculo da esperança matemática:</p>
<p>A esperança matemática de uma variável aleatória X é calculada pela seguinte fórmula:</p>
<pre align="center"><b>E(X) = ∑x*P(x)</b></pre>
<p>onde:</p>
<ul>
  <li>x é o valor possível da variável aleatória</li>
  <li>P(x) é a probabilidade de x ocorrer</li>
</ul>
<p><b>Propriedades da Esperança Matemática:</b></p>
<p>A esperança matemática tem as seguintes propriedades:</p>
<ul>
  <li>É sempre um número real.</li>
  <li>Se X e Y são variáveis aleatórias independentes, então o valor esperado de X + Y é igual à soma dos valores esperados de X e Y.</li>
  <li>Se a variável aleatória X é um valor constante, então o valor esperado de X é igual ao próprio valor constante.</li>
</ul>
<p><b>Interpretação da Esperança Matemática:</b></p>
<p>A esperança matemática pode ser interpretada de várias maneiras. Uma interpretação é que ela representa o valor médio "esperado" de uma experiência se ela for repetida muitas vezes. Outra interpretação é que ela representa o valor que um jogador pode esperar ganhar em um jogo de azar se ele jogar muitas vezes.</p>
<p>A esperança matemática é uma ferramenta importante na teoria das probabilidades e é usada em uma ampla variedade de aplicações.</p>
<h2 align="center">Variância</h2>
<p>A variância é uma medida de dispersão de uma variável aleatória. Ela é definida como a média dos quadrados das distâncias entre os valores da variável e a sua esperança matemática.</p>
<p>Em outras palavras, a variância mede a "distribuição" dos valores de uma variável aleatória em torno de sua esperança matemática.</p>
<p>A variância é um conceito fundamental na teoria das probabilidades e é usada em uma ampla variedade de aplicações, incluindo:</p>
<ul>
  <li><b>Estatística:</b> para estimar a variabilidade de uma população a partir de uma amostra</li>
  <li><b>Finanças:</b> para avaliar o risco de um investimento</li>
  <li><b>Economia:</b> para analisar a volatilidade de um mercado</li>
  <li><b>Engenharia:</b> para estimar a confiabilidade de um sistema</li>
</ul>
<p>Cálculo da Variância:</p>
<p>A variância de uma variável aleatória X é calculada pela seguinte fórmula:</p>
<pre align="center"><b>Var(X) = ∑(x - E(X))^2 * P(x)</b></pre>
<p>onde:</p>
<ul>
  <li>x é o valor possível da variável aleatória</li>
  <li>E(X) é a esperança matemática da variável aleatória</li>
  <li>P(x) é a probabilidade de x ocorrer</li>
</ul>
<p><b>Exemplos:</b></p>
<p>Suponha que você jogue uma moeda e ganhe R$ 1 se sair cara e R$ 0 se sair coroa. A variância desse jogo é:</p>
<pre align="center"><b>Var(X) = (1 - 0,5)^2 * 0,5 + (0 - 0,5)^2 * 0,5 = 0,25</b></pre>
<p>Ou seja, os valores da variável aleatória X estão distribuídos de forma uniforme em torno da sua esperança matemática, com um desvio padrão de aproximadamente 0,5.</p>
<p>Suponha que você jogue um dado e ganhe R$ 2 se sair 6, R$ 1 se sair 5 ou 4, e R$ 0 se sair qualquer outro número. A variância desse jogo é:</p>
<pre align="center"><b>Var(X) = (2 - 1,5)^2 * 1/6 + (1 - 1,5)^2 * 2/6 + (1 - 1,5)^2 * 2/6 = 0,8333</b></pre>
<pre align="center"><b>σ = √(0,8333) ≈ 0,92</b></pre>
<p>Ou seja, os valores da variável aleatória X estão distribuídos de forma mais dispersa em torno da sua esperança matemática, com um desvio padrão de aproximadamente 0,92.</p>
<p><b>Aplicações:</b></p>
<ul>
  <li>Estimar a incerteza em um experimento científico</li>
  <li>Comparar a variabilidade de duas populações</li>
  <li>Prever o valor de uma variável a partir do valor de outra variável</li>
</ul>
<h2 align="center">Covariância</h2>
<p>A covariância é uma medida de associação entre duas variáveis aleatórias. Ela é definida como a média dos produtos das distâncias entre os valores das duas variáveis e as suas respectivas esperanças matemáticas.</p>
<p>Em outras palavras, a covariância mede a tendência de duas variáveis aleatórias variarem juntas.</p>
<p>A covariância pode ser positiva, negativa ou nula. Uma covariância positiva indica que as duas variáveis tendem a aumentar ou diminuir juntas. Uma covariância negativa indica que as duas variáveis tendem a aumentar ou diminuir em direções opostas. Uma covariância nula indica que não há associação entre as duas variáveis.</p>
<p><b>Cálculo da Covariância:</b></p>
<p>A covariância de duas variáveis aleatórias X e Y é calculada pela seguinte fórmula:</p>
<pre><b>Cov(X, Y) = ∑(x - E(X))(y - E(Y)) * P(x, y)</b></pre>
<p>Onde:</p>
<ul>
  <li>x é o valor possível da variável aleatória X</li>
  <li>E(X) é a esperança matemática da variável aleatória X</li>
  <li>y é o valor possível da variável aleatória Y</li>
  <li>E(Y) é a esperança matemática da variável aleatória Y</li>
  <li>P(x, y) é a probabilidade de x e y ocorrerem simultaneamente</li>
</ul>
<p><b>Exemplos:</b></p>
<p>Suponha que você jogue uma moeda e ganhe R$ 1 se sair cara e R$ 0 se sair coroa. A covariância entre as duas variáveis aleatórias X (ganhar R$ 1) e Y (sair cara) é:</p>
<pre align="center"><b>Cov(X, Y) = (1 - 0,5)(1 - 0,5) * 0,5 + (0 - 0,5)(0 - 0,5) * 0,5 = 0</b></pre>
<p>Ou seja, as duas variáveis são independentes, pois não há tendência de uma variar com a outra.</p>
<p>Suponha que você jogue um dado e ganhe R$ 2 se sair 6, R$ 1 se sair 5 ou 4, e R$ 0 se sair qualquer outro número. A covariância entre as duas variáveis aleatórias X (ganhar R$ 2) e Y (sair 6) é:</p>
<pre align="center"><b>Cov(X, Y) = (2 - 1,5)(6 - 1,5) * 1/6 + (1 - 1,5)(5 - 1,5) * 2/6 + (1 - 1,5)(4 - 1,5) * 2/6 = 0,25</b></pre>
<p>Ou seja, as duas variáveis têm uma associação positiva, pois tendem a variar juntas.</p>
<p><b>Aplicações:</b></p>
<p>A covariância pode ser usada em uma variedade de aplicações, incluindo:</p>
<li><b>Estatística:</b> para estimar a relação entre duas variáveis</li>
<li><b>Finanças:</b> para avaliar o risco de um investimento</li>
<li><b>Economia:</b> para analisar a correlação entre dois mercados</li>
<li><b>Engenharia:</b> para prever a falha de um sistema</li>
<h2 align="center">Coeficiente de Correlação</h2>
<p>O coeficiente de correlação é uma medida de associação linear entre duas variáveis aleatórias. Ele é definido como a razão entre a covariância das duas variáveis e o produto dos desvios padrão das duas variáveis.</p>
<p><b>Definição</b></p>
<p>O coeficiente de correlação é calculado pela seguinte fórmula:</p>
<img src="https://latex.codecogs.com/png.image?r(X,%20Y)%20=%20\frac{Cov(X,%20Y)}{\sigma_X%20\sigma_Y}" alt="Coeficiente de Correlação">

<p>onde:</p>
<ul>
  <li>r(X, Y) é o coeficiente de correlação entre X e Y</li>
  <li>Cov(X, Y) é a covariância entre X e Y</li>
  <li>σ_X é o desvio padrão de X</li>
  <li>σ_Y é o desvio padrão de Y</li>
</ul>
<p><b>Significado</b></p>
<p>O coeficiente de correlação pode assumir valores entre -1 e 1. Um coeficiente de correlação de +1 indica uma associação linear positiva perfeita, o que significa que as duas variáveis aumentam ou diminuem juntas. Um coeficiente de correlação de -1 indica uma associação linear negativa perfeita, o que significa que as duas variáveis aumentam ou diminuem em direções opostas. Um coeficiente de correlação de 0 indica que não há associação linear entre as duas variáveis.</p>
<p><b>Exemplos</b></p>
<p>Suponha que você tenha dados sobre o peso e a altura de um grupo de pessoas. O coeficiente de correlação entre o peso e a altura será positivo, pois as pessoas geralmente são mais altas quanto mais pesadas forem.</p>
<p>Suponha que você tenha dados sobre o preço de ações de duas empresas. O coeficiente de correlação entre os preços das ações pode ser positivo, negativo ou nulo, dependendo das empresas.</p>
<p><b>Aplicações</b></p>
<p>O coeficiente de correlação pode ser usado em uma variedade de aplicações, incluindo:</p>
<ul>
  <li><b>Estatística:** para identificar a relação entre duas variáveis</li>
  <li><b>Finanças:** para avaliar o risco de um investimento</li>
  <li><b>Economia:** para analisar a correlação entre dois mercados</li>
  <li><b>Engenharia:** para prever a falha de um sistema</li>
</ul>
<h2>Referencias:</h2>
<p>Livro: Probabilidade e Estatística para Engenheiros, 2ª Edição, de Mario Sergio Jorge e João Marcos de Oliveira.</p>
<p>Artigo: Esperança Matemática, de João Marcos de Oliveira.</p>
<p>Probabilidade e Estatística para a Ciência e Engenharia, de Walpole, Myers, Myers e Ye</p>
<p>Estatística Descritiva e Inferência, de Hair, Anderson, Tatham e Black</p>
<p>Probabilidade e Estatística para a Administração, de Hair, Anderson, Tatham e Black</p>



