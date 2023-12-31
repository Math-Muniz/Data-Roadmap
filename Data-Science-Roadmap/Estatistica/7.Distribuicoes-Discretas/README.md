<h1>7. Distribuições Discretas: Distribuição de Bernoulli, Distribuição Binomial, Distribuição de Poisson</h1>
<h2>Distribuição de Bernoulli</h2>
<p>Na prática, há vários experimentos que admitem somente dois tipos de resultados, como sucesso e fracasso, esses experimentos são chamados de Distribuição de Bernoulli.</p>
<p>O sucesso é o que se deseja observar, por exemplo, se o seu interesse for observar a ocorrência de defeito em peças. Uma peça selecionada aleatoriamente, com defeito, seria um resultado do tipo “sucesso” (o resultado “sucesso” não está associado a algo bom, necessariamente).</p>
<p>Considere um problema (experimento) no qual só podem ocorrer dois tipos de resultados, “sucesso” e “fracasso”.</p>
<p><b>Exemplos</b></p>
<ul>
  <li>Uma venda é efetuada ou não por um vendedor em loja física;</li>
  <li>Um cliente pode ser do tipo adimplente ou inadimplente;</li>
  <li>Uma peça fabricada por uma indústria pode ser perfeita ou defeituosa;</li>
  <li>Um consumidor pode devolver ou não um produto comprado;</li>
  <li>Um exame médico pode ter como resultado positivo ou negativo.</li>
</ul>
<p><b>Função de Probabilidade</b></p>
<p>Associando uma variável aleatória x aos possíveis resultados de um determinado experimento, ficaremos com:</p>
<p>x = 1, se o resultado for “sucesso”,</p>
<p>x = 0, se o resultado for “fracasso”.</p>
<p>Assim, a função de probabilidade da Distribuição de Bernoulli será dada por:</p>
<img src="Bernoulli.jpeg">
<p><b>Média e Variância</b></p>
<p>É importante que você saiba que a média e a variância serão obtidas por:</p>
<p>Média = p</p>
<p>Variância = pq</p>
<p>Sendo,</p>
<p>p= probabilidade de sucesso</p>
<p>q= probabilidade de fracasso</p>
<p><b>Mais um exemplo</b></p>
<p>A partir de uma pesquisa no comércio on-line, foi verificado que no período de vendas de Natal, cada cliente que entra no site de determinada loja tem 60% de chance de comprar um produto qualquer. Qual a probabilidade de sucesso e de não comprar produto algum?</p>
<p><b>Solução:</b></p>
<p>Nesse caso, temos uma probabilidade de sucesso (o cliente adquirir um produto qualquer) de 0,6 e uma probabilidade de não comprar produto algum de 0,4 (q = 1 – 0,6).</p>
<p>A repetição de experimentos de Bernoulli independentes dá origem ao modelo Binomial, que você estudará abaixo.</p>
<h2>Distribuição Binomial</h2>
<p>Agora vamos estudar uma variável aleatória específica que gera uma distribuição de probabilidade muito utilizada em problemas do dia a dia de qualquer profissional: a distribuição Binomial.</p>
<p><b>Conceito</b></p>
<p>Uma distribuição de probabilidade binomial resulta de um experimento que satisfaz os seguintes requisitos:</p>
<ul>
  <li>O experimento tem um número finito de tentativas.</li>
  <li>As tentativas devem ser independentes (o resultado de qualquer tentativa individual não afeta as probabilidades nas outras tentativas).</li>
  <li>Cada tentativa deve ter todos os resultados classificados em duas categorias (em geral, chamadas de sucesso e fracasso).</li>
  <li>A probabilidade de sucesso permanece constante em todas as tentativas.</li>
</ul>
<p><b>Indo para a prática</b></p>
<p>Para exemplificar, vamos falar do número de vezes que sai o número 5 no lançamento de dois dados. Observe que nesse caso temos satisfeitos os quatro requisitos da definição de probabilidade binomial:</p>
<p>O lançamento de dois dados pode ser interpretado como dois (número finito) lançamentos. O resultado do primeiro lançamento do dado não interfere no resultado do segundo lançamento, por isso são classificados como independentes.</p>
<p>Cada lançamento pode resultar em um sucesso (sair 5) ou em um fracasso (sair um número diferente de 5).</p>
<p>A probabilidade de sair 5 é sempre igual a 1/6 em cada um dos lançamentos.</p>
<p>Em qualquer distribuição binomial, a probabilidade de ocorrência de sucessos em um conjunto de tentativas pode ser calculada a partir da expressão seguinte:</p>
<img src="Binomial.jpeg">
<p>Sendo,</p>
<p>p= a probabilidade de sucesso em uma tentativa;</p>
<p>q= a probabilidade de fracasso em uma tentativa;</p>
<p>n= o número de tentativas;</p>
<p>x= a quantidade de sucesso nas n tentativas.</p>
<p><b>Exemplo</b></p>
<p>No lançamento de dois dados não viciados, qual é a probabilidade de ocorrência de exatamente UM resultado igual a 5?</p>
<p>Solução:</p>
<p>Nesse exemplo, temos que n=2 (dois lançamentos), x=1 (um sucesso), p=1/6 e q= 1 – 1/6 = 5/6.</p>
<p>Aplicando a equação A, temos:</p>
<img src="Exemplo.jpeg">
<h2>Distribuição de Poisson</h2>
<p>Hoje veremos uma clássica distribuição: a Distribuição de Poisson.</p>
<p><b>Conceito</b></p>
<p>A distribuição de Poisson é uma distribuição de probabilidade discreta que se aplica a ocorrências de eventos ao longo de intervalos especificados. A variável aleatória x é o número de ocorrências do evento no intervalo. O intervalo pode ser de tempo, distância, área, volume ou alguma unidade simular. A probabilidade de ocorrência de x vezes em um intervalo é dada pela fórmula:</p>
<img src="Poisson.jpeg">
<p>Em que e≃2,7182.</p>
<p>Para que a fórmula anterior possa ser aplicada, devemos trabalhar com um evento situado em algum intervalo, além de garantir que cada ocorrência seja aleatória, independente e uniformemente distribuída nesse intervalo.</p>
<p><b>Aplicações</b></p>
<p>Já falamos sobre as condições de usar a fórmula, mas para deixar mais claro, vamos reforçar as aplicações dessa distribuição. As distribuições de Poisson são comumente usadas para dois propósitos principais:</p>
<p>Prevendo quantas vezes um evento ocorrerá dentro de um período de tempo escolhido. Essa técnica pode ser usada para diferentes aplicações de análise de risco, como estimativa de preço de seguro residencial.</p>
<p>Estimar a probabilidade de ocorrência de um evento, dada a frequência com que aconteceu no passado (por exemplo, a probabilidade de haver um corte de energia nos próximos dois meses).</p>
<p>As distribuições de Poisson nos permitem confiar no tempo médio entre a ocorrência de diferentes eventos. Eles não podem, no entanto, nos dizer o momento exato em que um evento pode ocorrer.</p>
<p><b>Características</b></p>
<p>As principais características que descrevem os processos de Poisson são:</p>
<ul>
  <li>Dois eventos não podem ocorrer simultaneamente.</li>
  <li>A taxa média entre a ocorrência do evento é constante geral.</li>
  <li>Os eventos são independentes um do outro (se um acontecer, isso não tem nenhuma influência sobre a probabilidade de outro evento ocorrer).</li>
  <li>Os eventos podem ocorrer em qualquer número de vezes (dentro do período considerado).</li>
</ul>
<p><b>Exemplo</b></p>
<p>Na construção de um prédio residencial, ocorreram, nos últimos 42 dias, 17 acidentes de trabalho. Selecionando-se ao acaso um determinado dia, dentre os 42 avaliados, qual é a probabilidade de ter ocorrido 3 acidentes nesse dia?</p>
<p>Para responder a essa pergunta, considere uma distribuição de Poisson com média igual a:</p>
<p>λ=17/42=0,4048 acidentes.</p>
<p>Sendo assim,</p>
<img src="Exemplo2.jpeg">
<h2>Referências</h2>
<p>https://blog.proffernandamaciel.com.br/distribuicao-de-bernoulli/</p>
<p>https://blog.proffernandamaciel.com.br/distribuicao-de-probabilidade-binomial/</p>
