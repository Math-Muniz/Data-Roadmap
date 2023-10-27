<h1 align="center">Distribuições de Probabilidade</h1>
<h1 align="center">Distribuição Logística (Logistic Distribution)</h1>
<p>A Distribuição Logística é usada para descrever o crescimento.</p>
<p>É amplamente usada em aprendizado de máquina em regressão logística, redes neurais, etc.</p>
<p>Possui três parâmetros:</p>
<ul>
  <li><b>loc</b> - média, onde está o pico. Padrão 0.</li>
  <li><b>scale</b> - desvio padrão, a planicidade da distribuição. Padrão 1.</li>
  <li><b>size</b> - A forma do conjunto retornado.</li>
</ul>
<p><b>Exemplo:</b></p>
<p>Desenhe amostras de uma distribuição logística de 2x3 com média 1 e desvio padrão 2.0:</p>
<pre>
from numpy import random

x = random.logistic(loc=1, scale=2, size=(2, 3))

print(x)
</pre>
<h2 align="center">Visualização da Distribuição Logística</h2>
<p><b>Exemplo:</b></p>
<pre>
from numpy import random
import matplotlib.pyplot as plt
import seaborn as sns

sns.distplot(random.logistic(size=1000), hist=False)

plt.show()
</pre>
<p><b>Resultado:</b></p>
<img src="logistic.png">
<h2 align="center">Diferença entre Distribuição Logística e Normal</h2>
<p>Ambas as distribuições são quase idênticas, mas a distribuição logística tem mais área sob as caudas, o que significa que representa uma maior possibilidade de ocorrência de um evento mais afastado da média.</p>
<p>Para um valor maior de escala (desvio padrão), as distribuições normais e logísticas são quase idênticas, exceto pelo pico.</p>
<p><b>Exemplo:</b></p>
<pre>
from numpy import random
import matplotlib.pyplot as plt
import seaborn as sns

sns.distplot(random.normal(scale=2, size=1000), hist=False, label='normal')
sns.distplot(random.logistic(size=1000), hist=False, label='logistic')

plt.show()
</pre>
<p><b>Resultado:</b></p>
<img src="logistic2.png">
