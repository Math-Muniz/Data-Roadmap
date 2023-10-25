<h1 align="center">Seaborn</h1>
<h2 align="center">Visualize Distribuições com o Seaborn</h2>
<p>O Seaborn é uma biblioteca que utiliza o Matplotlib por baixo para plotar gráficos.</p>
<img src="">
<h2 align="center">Instale o Seaborn</h2>
<p>Se você já tem o Python e o PIP instalados em seu sistema, instale o Seaborn usando este comando:</p>
<pre>
C:\Users\Your Name>pip install seaborn
</pre>
<p>Se você estiver usando o Jupyter, instale o Seaborn usando este comando:</p>
<pre>
C:\Users\Your Name>!pip install seaborn
</pre>
<h2 align="center">Distplots</h2>
<p>Distplot é uma abreviação de gráfico de distribuição. Ele recebe como entrada um array e plota uma curva correspondente à distribuição dos pontos no array.</p>
<h2 align="center">Importar o Matplotlib</h2>
<p>Importe o objeto pyplot do módulo Matplotlib em seu código usando a seguinte declaração:</p>
<pre>
import matplotlib.pyplot as plt
</pre>
<p>Você pode aprender mais sobre o módulo Matplotlib em nosso <a href="https://github.com/Math-Muniz/Data-Roadmap/tree/main/Data-Science-Roadmap/Visualizacao-de-Dados/1.Matplotlib">Tutorial de Matplotlib</a>.</p>
<h2 align="center">Importar o Seaborn</h2>
<p>Importe o módulo Seaborn em seu código usando a seguinte declaração:</p>
<pre>
import seaborn as sns
</pre>
<h2 align="center">Plotando um Distplot</h2>
<p><b>Exemplo:</b></p>
<pre>
import matplotlib.pyplot as plt
import seaborn as sns

sns.distplot([0, 1, 2, 3, 4, 5])

plt.show()
</pre>
<h2 align="center">Plotando um Distplot Sem o Histograma</h2>
<p><b>Exemplo:</b></p>
<pre>
import matplotlib.pyplot as plt
import seaborn as sns

sns.distplot([0, 1, 2, 3, 4, 5], hist=False)

plt.show()
</pre>
<p><b>Observação:</b> Usaremos sns.distplot(arr, hist=False) para visualizar distribuições aleatórias neste tutorial.</p>
