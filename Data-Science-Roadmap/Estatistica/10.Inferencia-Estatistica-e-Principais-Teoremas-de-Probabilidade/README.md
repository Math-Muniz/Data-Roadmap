<h1>10. Inferência Estatística e Principais Teoremas de Probabilidade: Teorema de Chebyshev, Lei dos Grandes Números, Teorema Central do Limite, Intervalo de Confiança, Testes de Hipóteses</h1>
<h2 align="center">Teorema de Chebyshev (Desigualdade de Tchebycheff)</h2>
<p>A desigualdade de Chebyshev é um teorema usado em estatística que fornece uma estimativa conservadora (intervalo de confiança) da probabilidade de que uma variável aleatória com variância finita estará a uma certa distância de sua expectativa matemática ou de sua média.</p>
<p>Sua expressão formal é a seguinte:</p>
<img src="Formal-Chebyshev.webp">
<p><b>X = valor estimado</b></p>
<p><b>µ = Expectativa matemática do valor estimado</b></p>
<p><b>Ϭ = desvio padrão do valor esperado</b></p>
<p><b>k = Número de desvios padrão</b></p>
<p>Partindo dessa expressão geral e desenvolvendo a parte que fica dentro do valor absoluto teríamos o seguinte:</p>
<img src="Geral-Chebyshev.webp">
<p>Se prestarmos atenção à expressão anterior, pode-se ver que a parte à esquerda não é mais do que um <b>intervalo de confiança</b>. Isso nos oferece um limite inferior e superior para o valor estimado. Portanto, a <b>Desigualdade de Chebyshev</b> nos diz a probabilidade mínima de que o parâmetro da população esteja dentro de um certo número de desvios-padrão acima ou abaixo de sua média. Ou, dito de outra forma, nos dá a probabilidade de que o parâmetro da população esteja dentro desse intervalo de confiança.</p>
<p>A <b>Desigualdade de Chebyshev</b> fornece limites aproximados para o valor estimado. Apesar de ter um certo grau de imprecisão, é um teorema muito útil, pois pode ser aplicado a uma ampla gama de variáveis ​​aleatórias, independentemente de suas distribuições. A única restrição para poder usar esta desigualdade é que k tem que ser maior que 1 (k> 1).</p>
<p><b>Exemplo</b></p>
<p>Suponha que sejamos administradores de um fundo de investimento. A carteira que estamos administrando tem um retorno médio de 8,14% e um desvio padrão de 5,12%. Para saber, por exemplo, qual porcentagem de nossos retornos são pelo menos 3 desvios-padrão de nossa lucratividade média, simplesmente aplicaríamos a fórmula anterior da expressão 2.</p>
<pre align="center"><b>k = 1,96</b></pre>
<p>Substituindo o valor de k:</p>
<pre align="center"><b>1- (1 / (1,96**2)) = 0,739 = 73,9%</b></pre>
<p>Isso significa que 73,9% dos resultados estão no intervalo de confiança localizado a 1,96 desvios padrão da média.</p>
<p>Vamos fazer o exemplo anterior para valores diferentes de k.</p>
<pre align="center"><b>k = 2,46</b></pre>
<pre align="center"><b>k = 3</b></pre>
<p>Substituindo o valor de k = 2,46:</p>
<pre align="center"><b>1- (1 / (2,46**2)) = 0,835 = 83,5%</b></pre>
<p>Substituindo o valor de k = 3:</p>
<pre align="center"><b>1- (1 / (3**2)) = 0,889 = 88,9%</b></pre>
<p>Existem 83,5% dos dados que estão a uma distância de 2,46 desvios-padrão da média e 88,9% que estão dentro de 3 desvios-padrão da média.</p>
<p>Usando a desigualdade de Chebyshev, é fácil deduzir que quanto maior o valor de K (quanto maior o desvio do valor estimado de sua média), maior a probabilidade de que a variável aleatória esteja dentro do intervalo limitado.</p>
<h2 align="center">Lei dos Grandes Números</h2>
<p>A lei dos grandes números é um teorema fundamental da teoria da probabilidade que indica que, se repetirmos muitas vezes (tendendo ao infinito) o mesmo experimento, a frequência de um determinado evento acontecendo tende a ser uma constante.</p>
<p>Ou seja, a lei dos grandes números indica que se o mesmo teste for realizado repetidamente (por exemplo, jogar uma moeda, jogar uma roleta, etc.), a frequência com que um determinado evento se repetirá (isso ocorre cabeças ou selo, o número 3 sai preto, etc) se aproximará de uma constante. Essa, por sua vez, será a probabilidade desse evento ocorrer.</p>
<p><b>Origem da lei dos grandes números</b></p>
<p>A lei dos grandes números foi mencionada pela primeira vez pelo matemático Gerolamo Cardamo, embora sem qualquer prova rigorosa. Mais tarde, Jacob Bernoulli conseguiu fazer uma demonstração completa em sua obra "Ars Conjectandi" em 1713. Na década de 1830, o matemático Siméon Denis Poisson descreveu em detalhes a lei dos grandes números, que veio aperfeiçoar a teoria. Outros autores também fariam contribuições posteriores.</p>
<p><b>Exemplo da Lei dos Grandes Números</b></p>
<p>Suponha o seguinte experimento: lance um dado comum. Agora vamos considerar o evento em que obtemos o número 1. Como sabemos, a probabilidade de que o número 1 apareça é 1/6 (o dado tem 6 faces, uma delas é uma).</p>
<p>O que a lei dos grandes números nos diz? Diz-nos que à medida que aumentamos o número de repetições da nossa experiência (fazemos mais lançamentos do dado), a frequência com que o evento se repetirá (obtemos 1) ficará mais próxima de uma constante, que terá um valor igual valor à sua probabilidade (1/6 ou 16,66%).</p>
<p>Possivelmente, nos primeiros 10 ou 20 lançamentos, a frequência com que conseguiremos 1 não será de 16%, mas de outro percentual como 5% ou 30%. Mas, à medida que fazemos mais e mais tons (digamos 10.000), a frequência com que o 1 aparece será muito próxima a 16,66%.</p>
<p>No gráfico a seguir, vemos um exemplo de um experimento real em que um dado é jogado repetidamente. Aqui podemos ver como a frequência relativa de desenho de um certo número está mudando.</p>
<p>Conforme indicado pela lei dos grandes números, nos primeiros lançamentos a frequência é instável, mas à medida que aumentamos o número de lançamentos a frequência tende a se estabilizar em um determinado número, que é a probabilidade de o evento ocorrer (neste caso, os números de 1 a 6, pois é o lançamento de um dado).</p>
<img src="Grafico-Lei-dos-Grandes-Numeros.webp">
<p><b>Interpretação Errada da Lei dos Grandes Números</b></p>
<p>Muitas pessoas interpretam mal a lei dos grandes números, acreditando que um evento tende a ser mais importante do que outro. Assim, por exemplo, eles acreditam que como a probabilidade de que o número 1 role em um dado deve ser próxima a 1/6, quando o número 1 não aparece nos primeiros 2 ou 5 lançamentos, é muito provável que no Next. Isso não é verdade, já que a lei dos grandes números só se aplica a muitas repetições, então podemos passar o dia todo jogando um dado e não atingir a frequência de 1/6.</p>
<p>O lançamento de um dado é um evento independente e, portanto, quando um certo número aparece, este resultado não afeta o próximo lançamento. Somente depois de milhares de repetições seremos capazes de verificar que a lei dos grandes números existe e que a frequência relativa de obtenção de um número (em nosso exemplo 1) será de 1/6.</p>
<p>A má interpretação da teoria pode levar as pessoas (especialmente os jogadores) a perder dinheiro e tempo.</p>
<h2 align="center">Teorema Central do Limite</h2>
<p>Acompanhe o texto a seguir para conhecer o Teorema Central do Limite (TCL) e entender sua importância para a análise estatística!Porém, antes de abordar o Teorema em si, é necessário entender o que é uma distribuição amostral.</p>
<p><b>Distribuição Amostral</b></p>
<p>Sabemos que geralmente não temos acesso à população de interesse que estamos estudando e por isso, utilizamos amostras.</p>
<p>Ao retirar amostras <b>com reposição</b>, muito provavelmente elas irão ser diferentes entre si, em maior ou menor magnitude. Assim, se tivermos 5 amostras (de mesmo tamanho), cada uma terá a sua própria média, chamada de <b>média amostral</b>.</p>
<p>Nesse exemplo, teremos então um conjunto de 5 médias amostrais, como mostrado na figura abaixo, em que o retângulo representa a população, e os círculos as amostras:</p>
<img src="Distribuicao-Amostral.png">
<p>Ao <b>repetir o processo de amostragem várias vezes</b>, poderemos agrupar todas as médias amostrais possíveis em uma distribuição de probabilidade ou de frequência:</p>
<img src="Distribuicao-Amostral-das-Medias.png">
<p>O gráfico acima é  chamado de <b>distribuição amostral das médias</b> e terá o formato de uma curva normal se certas condições forem verdadeiras como veremos mais adiante.</p>
<p>Tal como qualquer distribuição, podemos calcular a sua média e o desvio-padrão:</p>
<ul>
  <li>A média da distribuição amostral das médias  <b>(μx̅), será sempre a verdadeira média da população (μ);</b></li>
  <li>E o seu desvio-padrão (conhecido como <b>erro padrão</b> ) será o desvio padrão populacional (σ)  dividido pela raiz quadrada do tamanho da amostra (n).</li>
</ul>
<p>Lembre-se que: a distribuição amostral será obtida sempre a partir de uma  <b>estatística da amostra</b>, como a <b>média, a proporção e a variância</b>.</p>
<p><b>O que diz o Teorema Central do Limite (TCL) ?</b></p>
<p>Agora que estamos familiarizados com o conceito de distribuição amostral, podemos abordar o TCL. O uso do Teorema dependerá de <b>como é a forma da distribuição populacional</b> dos nossos dados. Nesse caso há duas situações possíveis:</p>
<p><b>a) A população é normalmente distribuída</b></p>
<p>Imagine que estamos analisando variáveis cuja população já é conhecida por ter uma  distribuição normal, como altura, peso, frequência cardíaca, etc.</p>
<p>Nesse caso, vamos observar que depois de fazer a amostragem com reposição, a distribuição amostral das médias obtida <b>também será normal.</b> E isso não é uma coincidência!<b> Sempre que a população for normal, a distribuição das médias também será normalmente distribuída, independentemente do tamanho da amostra.</b></p>
<p>Esse cenário é o ‘melhor’ que podemos encontrar e <b>nesse caso o Teorema Central do Limite não é necessário.</b></p>
<img src="Populacao-Normal.png">
<p><b>b) A população não é normalmente distribuída ou não sei como é a distribuição populacional</b></p>
<p>É muito comum, porém, que sequer saibamos qual é a forma da distribuição populacional que estamos lidando ou que os dados não são normalmente distribuídos. Então é aqui que o Teorema Central do Limite se aplica! </p>
<p>O Teorema nos explica que se a distribuição da população de origem for desconhecida ou assimétrica, uniforme, etc, ao retirarmos amostras suficientemente grandes – acima de 30 elementos : n >=30 –  a distribuição amostral das médias será aproximadamente normal.</p>
<p>Assim, podemos dizer que o Teorema “funciona” em geral, se tivermos amostras de tamanho mínimo igual a  30 elementos. Entretanto, vale mencionar que em alguns casos, esse número pode ser diferente dependendo da forma da distribuição populacional que estamos lidando.</p>
<p>Por exemplo:</p>
<ul>
  <li>Em distribuições em que  quase não há outliers (de cauda ‘leve’), amostras com 20 elementos já podem ser o suficiente para que o Teorema seja observado;</li>
  <li>De forma contrária, em distribuição de cauda ‘pesada’, isto é, com muitos valores atípicos (grande assimetria), amostras com 100 elementos podem ser necessárias para que o Teorema comece a ser observado. </li>
</ul>
<img src="Populacao-Nao-Normal.png">
<p>De forma geral, <b>quanto maior for a amostra, mais próxima da normal a distribuição amostral das médias será.</b></p>
<p>No esquema abaixo, na primeira imagem temos uma distribuição populacional assimétrica à direita. Suponha que inicialmente foram retiradas 5.000 amostras, cada uma com <b>5 elementos.</b> Em seguida foram calculadas as médias e como resultado, obtemos uma distribuição amostral das médias ainda ligeiramente assimétrica.</p>
<p>Mas se retirássemos as mesmas 5.000 amostras, porém cada qual com <b>30 elementos</b>, percebemos que a distribuição das médias se torna perfeitamente simétrica e normal. E se retirássemos 5.000 amostras, cada qual com <b>100 elementos</b>, a distribuição das médias é normal e ainda menos dispersa (mais concentrada em torno da média).</p>
<img src="Amostras.jpg">
<p><b>Se quiser fazer suas propróprias simulações e visualizar o TCL para diferentes distribuições populacionais, acesse sites como Seeing Theory e Stat Crunch.</b></p>
<p><b>Qual a importância do TCL?</b></p>
<p>Ao utilizarmos amostras, nosso objetivo final é fazer <b>inferências a respeito dos reais parâmetros da população.</b> Para isso, usamos ferramentas como intervalos de confiança e teste de hipóteses que partem da suposição da normalidade dos dados.</p>
<p>Desse modo, mesmo que os nossos dados sejam de uma população com distribuição desconhecida ou que não seja normalmente distribuída, ainda assim poderemos fazer tais análises uma vez que o Teorema Central do Limite é verdadeiro.</p>
<h2 align="center">Intervalo de Confiança</h2>
<h2 align="center">Testes de Hipóteses</h2>
<h2 align="center">Referências</h2>
<p>https://pt.economy-pedia.com/11039359-chebyshev-inequality</p>
<p>https://pt.economy-pedia.com/11038376-law-of-the-big-numbers</p>
<p>https://blog.proffernandamaciel.com.br/teorema_central_limite/</p>
