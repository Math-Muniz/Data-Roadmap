<h1 align="center">Distribuições Fundamentais</h1>
<h1 align="center">Distribuição (Gaussiana) Normal (Normal Distribution)</h1>
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
<h1 align="center">Distribuição Binomial (Binomial Distribution)</h1>
<p>A Distribuição Binomial é uma Distribuição Discreta.</p>
<p>Ela descreve o resultado de cenários binários, por exemplo, o lançamento de uma moeda, que resultará em cabeça ou coroa.</p>
<p>Ela possui três parâmetros:</p>
<ul>
  <li><b>n</b> - número de tentativas.</li>
  <li><b>p</b> - probabilidade de ocorrência de cada tentativa (por exemplo, para o lançamento de uma moeda, 0.5 cada).</li>
  <li><b>size</b> - A forma do array retornado.</li>
</ul>
<p><b>Distribuição Discreta:</b> A distribuição é definida em um conjunto separado de eventos, por exemplo, o resultado do lançamento de uma moeda é discreto, pois pode ser apenas cabeça ou coroa, enquanto a altura das pessoas é contínua, pois pode ser 170, 170,1, 170,11 e assim por diante.</p>
<p><b>Exemplo:</b></p>
<p>Dado 10 tentativas de lançamento de moeda, gere 10 pontos de dados:</p>
<pre>
from numpy import random

x = random.binomial(n=10, p=0.5, size=10)

print(x)
</pre>
<h2 align="center">Visualização da Distribuição Binomial</h2>
<p><b>Exemplo:</b></p>
<pre>
from numpy import random
import matplotlib.pyplot as plt
import seaborn as sns

sns.distplot(random.binomial(n=10, p=0.5, size=1000), hist=True, kde=False)

plt.show()
</pre>
<p><b>Resultado:</b></p>
<img src="binomial.png">
<h2 align="center">Diferença Entre Distribuição Normal e Binomial</h2>
<p>A principal diferença é que a distribuição normal é contínua, enquanto a binomial é discreta, mas se houver dados suficientes, ela será bastante semelhante à distribuição normal com determinados loc e escala.</p>
<p><b>Exemplo:</b></p>
<pre>
from numpy import random
import matplotlib.pyplot as plt
import seaborn as sns

sns.distplot(random.normal(loc=50, scale=5, size=1000), hist=False, label='normal')
sns.distplot(random.binomial(n=100, p=0.5, size=1000), hist=False, label='binomial')

plt.show()
</pre>
<p><b>Resultado:</b></p>
<img src="binomial2.png">
<h1 align="center">Distribuição Poisson (Poisson Distribution)</h1>
<p>A Distribuição de Poisson é uma Distribuição Discreta.</p>
<p>Ela estima quantas vezes um evento pode ocorrer em um período de tempo especificado. Por exemplo, se alguém come duas vezes por dia, qual é a probabilidade de que ele coma três vezes?</p>
<p>Ela possui dois parâmetros:</p>
<ul>
  <li><b>lam </b>- taxa ou número conhecido de ocorrências, por exemplo, 2 para o problema acima.</li>
  <li><b>size </b>- A forma do conjunto retornado.</li>
</ul>
<p><b>Exemplo:</b></p>
<p>Gere uma distribuição aleatória 1x10 para uma ocorrência de 2:</p>
<pre>
from numpy import random

x = random.poisson(lam=2, size=10)

print(x)
</pre>
<h2 align="center">Visualização da Distribuição de Poisson</h2>
<p><b>Exemplo:</b></p>
<pre>
from numpy import random
import matplotlib.pyplot as plt
import seaborn as sns

sns.distplot(random.poisson(lam=2, size=1000), kde=False)

plt.show()
</pre>
<p><b>Resultado:</b></p>
<img src="poisson1.png">
<h2 align="center">Diferença Entre a Distribuição Normal e de Poisson</h2>
<p>A distribuição normal é contínua, enquanto a de Poisson é discreta.</p>
<p>Mas podemos ver que, semelhante à distribuição binomial para uma distribuição de Poisson suficientemente grande, ela se tornará semelhante a uma distribuição normal com determinado desvio padrão e média.</p>
<p><b>Exemplo:</b></p>
<pre>
from numpy import random
import matplotlib.pyplot as plt
import seaborn as sns

sns.distplot(random.normal(loc=50, scale=7, size=1000), hist=False, label='normal')
sns.distplot(random.poisson(lam=50, size=1000), hist=False, label='poisson')

plt.show()
</pre>
<p><b>Resultado:</b></p>
<img src="poisson2.png">
<h2 align="center">Diferença Entre a Distribuição Binomial e de Poisson</h2>
<p>A distribuição binomial possui apenas dois resultados possíveis, enquanto a distribuição de Poisson pode ter resultados possíveis ilimitados.</p>
<p>Mas, para <b>n</b> muito grande e <b>p</b> próximo de zero, a distribuição binomial é quase idêntica à distribuição de Poisson, de modo que <b>n * p</b> é quase igual a <b>lam</b>.</p>
<p><b>Exemplo:</b></p>
<pre>
from numpy import random
import matplotlib.pyplot as plt
import seaborn as sns

sns.distplot(random.binomial(n=1000, p=0.01, size=1000), hist=False, label='binomial')
sns.distplot(random.poisson(lam=10, size=1000), hist=False, label='poisson')

plt.show()
</pre>
<p><b>Resultado:</b></p>
<img src="poisson3.png">
<h1 align="center">Distribuição Uniforme (Uniform Distribution)</h1>
<p>Usada para descrever a probabilidade em que cada evento tem chances iguais de ocorrer.</p>
<p>Por exemplo, a geração de números aleatórios.</p>
<p>Possui três parâmetros:</p>
<ul>
  <li><b>a</b> - limite inferior - padrão 0.0.</li>
  <li><b>b</b> - limite superior - padrão 1.0.</li>
  <li><b>size</b> - A forma do conjunto retornado.</li>
</ul>
<p><b>Exemplo:</b></p>
<p>Crie uma amostra de distribuição uniforme de 2x3:</p>
<pre>
from numpy import random

x = random.uniform(size=(2, 3))

print(x)
</pre>
<h2 align="center">Visualização da Distribuição Uniforme</h2>
<p><b>Exemplo:</b></p>
<pre>
from numpy import random
import matplotlib.pyplot as plt
import seaborn as sns

sns.distplot(random.uniform(size=1000), hist=False)

plt.show()
</pre>
<p><b>Resultado:</b></p>
<img src="uniform.png">
<h2 align="center">Refêrencias:</h2>
<p>https://www.w3schools.com/python/numpy/numpy_random_normal.asp</p>
<p>https://www.w3schools.com/python/numpy/numpy_random_binomial.asp</p>
<p>https://www.w3schools.com/python/numpy/numpy_random_poisson.asp</p>
<p>https://www.w3schools.com/python/numpy/numpy_random_uniform.asp</p>
