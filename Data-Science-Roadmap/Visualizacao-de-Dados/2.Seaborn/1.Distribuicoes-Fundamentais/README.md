<h1 align="center">Distribuições Fundamentais</h1>
<h1 align="center">Distribuição (Gaussiana) Normal</h1>
<p>A Distribuição Normal é uma das distribuições mais importantes.</p>
<p>Também é chamada de Distribuição Gaussiana em homenagem ao matemático alemão Carl Friedrich Gauss.</p>
<p>Ela se ajusta à distribuição de probabilidade de muitos eventos, como Pontuações de QI, Batimentos Cardíacos, etc.</p>
<p>Use o método random.normal() para obter uma Distribuição de Dados Normal.</p>
<p>Ela possui três parâmetros:</p>
<ul>
  <li><b>loc</b> - (Média) onde o pico do sino se encontra.</li>
  <li><b>scale</b> - (Desvio Padrão) o quão achatada a distribuição gráfica deve ser.</li>
  <li><b>size</b> - A forma do array retornado.</li>
</ul>
<p><b>Exemplo:</b></p>
<p>Gere uma distribuição normal aleatória de tamanho 2x3:</p>
<pre>
from numpy import random

x = random.normal(size=(2, 3))

print(x)
</pre>
<p><b>Exemplo:</b></p>
<p>Gere uma distribuição normal aleatória de tamanho 2x3 com média 1 e desvio padrão de 2:</p>
<pre>
from numpy import random

x = random.normal(loc=1, scale=2, size=(2, 3))

print(x)
</pre>
<h2 align="center">Visualização de uma Distribuição Normal</h2>
<p><b>Exemplo:</b></p>
<pre>
from numpy import random
import matplotlib.pyplot as plt
import seaborn as sns

sns.distplot(random.normal(size=1000), hist=False)

plt.show()
</pre>
<p><b>Resultado:</b></p>
<img src="normal.png">
<p><b>Observação:</b> A curva de uma Distribuição Normal também é conhecida como a Curva em Forma de Sino devido à sua forma de sino.</p>
