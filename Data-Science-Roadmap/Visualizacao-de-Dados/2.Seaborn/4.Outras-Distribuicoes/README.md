<h1 align="center">Outras Distribuições</h1>
<h1 align="center">Distribuição Zipf</h1>
<p>Distribuições Zipf são usadas para amostrar dados com base na Lei de Zipf.</p>
<p><b>Lei de Zipf:</b> Em uma coleção, o termo mais comum é 1/n vezes o termo mais comum. Por exemplo, a quinta palavra mais comum em inglês ocorre aproximadamente 1/5 vezes com a mesma frequência que a palavra mais comum.</p>
<p>Ela possui dois parâmetros:</p>
<ul>
  <li>a - parâmetro de distribuição.</li>
  <li>size - A forma da matriz retornada.</li>
</ul>
<p><b>Exemplo:</b></p>
<p>Desenhe uma amostra para a distribuição Zipf com parâmetro de distribuição 2 e tamanho 2x3:</p>
<pre>
from numpy import random

x = random.zipf(a=2, size=(2, 3))

print(x)
</pre>
<h2 align="center">Visualização da Distribuição Zipf</h2>
<p>Amostra de 1000 pontos, mas plote apenas aqueles com valor < 10 para um gráfico mais significativo.</p>
<p><b>Exemplo:</b></p>
<pre>
from numpy import random
import matplotlib.pyplot as plt
import seaborn as sns

x = random.zipf(a=2, size=1000)
sns.distplot(x[x<10], kde=False)

plt.show()
</pre>
<p><b>Resultado:</b></p>
<img src="zipf">
<h2 align="center">Referências:</h2>
<p>https://www.w3schools.com/python/numpy/numpy_random_zipf.asp</p>
