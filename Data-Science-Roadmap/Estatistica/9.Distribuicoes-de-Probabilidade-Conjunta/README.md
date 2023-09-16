<h1>9. Distribuições de Probabilidade Conjunta: Distribuição Conjunta de Variáveis Discretas, Distribuição Conjunta de Variáveis Contínuas.</h1>
<p>Nesta seção, discutiremos as Distribuições de Probabilidade Conjunta, que são utilizadas para descrever o comportamento simultâneo de duas ou mais variáveis aleatórias em um experimento probabilístico. Existem dois tipos principais de distribuições conjuntas:</p>
<h2 align="center">Distribuição Conjunta de Variáveis Discretas</h2>
<p>A Distribuição Conjunta de Variáveis Discretas é usada quando estamos lidando com duas ou mais variáveis aleatórias discretas, ou seja, aquelas cujos valores são contáveis. Ela descreve a probabilidade conjunta de todas as combinações possíveis de valores dessas variáveis.</p>
<p><strong>Fórmula:</strong> A função de probabilidade conjunta para duas variáveis discretas X e Y é geralmente representada como P(X = x, Y = y), onde x e y são valores específicos das variáveis. A soma de todas essas probabilidades deve ser igual a 1.</p>
<p><strong>Aplicações:</strong></p>
<ul>
  <li>Análise de jogos de azar, como dados ou cartas.</li>
  <li>Modelagem de sistemas de filas em teoria das filas.</li>
  <li>Análise de desempenho de sistemas de comunicação.</li>
</ul>
<p><strong>Exemplo com Resolução:</strong></p>
<p>Suponha que temos duas variáveis aleatórias X e Y, que representam o resultado de dois dados lançados. A tabela a seguir mostra a função de probabilidade conjunta P(X = x, Y = y) para todas as combinações possíveis:</p>
<table border="1">
  <tr>
    <th>X\Y</th>
    <th>1</th>
    <th>2</th>
    <th>3</th>
    <th>4</th>
    <th>5</th>
    <th>6</th>
  </tr>
  <tr>
    <td>1</td>
    <td>1/36</td>
    <td>1/36</td>
    <td>1/36</td>
    <td>1/36</td>
    <td>1/36</td>
    <td>1/36</td>
  </tr>
  <!-- Adicione outras linhas da tabela conforme necessário -->
</table>
<h2 align="center">Distribuição Conjunta de Variáveis Contínuas</h2>
<p>A Distribuição Conjunta de Variáveis Contínuas é usada quando temos duas ou mais variáveis aleatórias contínuas, ou seja, aquelas cujos valores podem assumir qualquer valor em um intervalo contínuo. Ela descreve a probabilidade conjunta de eventos em uma faixa contínua.</p>
<p><strong>Fórmula:</strong> Para variáveis contínuas, usamos uma função de densidade de probabilidade conjunta, geralmente denotada por f(x, y), onde x e y são as variáveis contínuas. A integral da função de densidade de probabilidade conjunta sobre toda a faixa de interesse é igual a 1.</p>
<p><strong>Aplicações:</strong></p>
<ul>
  <li>Modelagem de distribuição de renda e riqueza em economia.</li>
  <li>Análise de distribuição de pontos em um espaço 2D.</li>
  <li>Previsão de movimento de partículas em física.</li>
</ul>
<p><strong>Exemplo com Resolução:</strong></p>
<p>Suponha que temos duas variáveis aleatórias contínuas X e Y com a seguinte função de densidade conjunta:</p>
<pre>f(x, y) = kxy, onde 0 < x < 1, 0 < y < 1, e k é uma constante de normalização.</pre>
<p>Para encontrar o valor de k, integramos essa função sobre o intervalo de interesse:</p>
<!-- Insira a integral aqui -->
<p>Resolvendo a integral, obtemos:</p>
<pre align="center">k * (1/2) * (1/2) = 1</pre>
<pre align="center">k = 4</pre>
<p>Portanto, a função de densidade de probabilidade conjunta é:</p>
<pre align="center">f(x, y) = 4xy, onde 0 < x < 1, 0 < y < 1.</pre>
<p><strong>Referências:</strong></p>
<ul>
  <li>Livro: "Probability and Statistics for Engineers and Scientists" de Sheldon M. Ross.</li>
  <li>Livro: "Probabilidade e Estatística" de Murray Spiegel.</li>
  <li>Livro: "Introduction to Probability" de Joseph K. Blitzstein e Jessica Hwang.</li>
  <li>Material de cursos acadêmicos de probabilidade e estatística.</li>
</ul>
