<h1 align="center">Trabalhando com Múltiplos Gráficos</h1>
<h2 align="center">Exibir Múltiplos Gráficos</h2>
<p>Com a função subplot(), é possível desenhar vários gráficos em uma única figura:</p>
<p><b>Exemplo:</b></p>
<p>Desenhe 2 gráficos:</p>
<pre>
import matplotlib.pyplot as plt
import numpy as np

#plot 1:
x = np.array([0, 1, 2, 3])
y = np.array([3, 8, 1, 10])

plt.subplot(1, 2, 1)
plt.plot(x,y)

#plot 2:
x = np.array([0, 1, 2, 3])
y = np.array([10, 20, 30, 40])

plt.subplot(1, 2, 2)
plt.plot(x,y)

plt.show()
</pre>
<p><b>Resultado:</b></p>
<img src="matplotlib_subplots1.png">
<h2 align="center">A Função subplot()</h2>
<p>A função subplot() recebe três argumentos que descrevem o layout da figura.</p>
<p>O layout é organizado em linhas e colunas, que são representadas pelo primeiro e segundo argumento.</p>
<p>O terceiro argumento representa o índice do gráfico atual.</p>
<pre>
plt.subplot(1, 2, 1)
#A figura possui 1 linha, 2 colunas, e este gráfico é o primeiro gráfico.
</pre>
<pre>
plt.subplot(1, 2, 2)
#A figura possui 1 linha, 2 colunas, e este gráfico é o segundo gráfico.
</pre>
<p>Portanto, se desejarmos uma figura com 2 linhas e 1 coluna (significando que os dois gráficos serão exibidos um em cima do outro em vez de lado a lado), podemos escrever a sintaxe da seguinte maneira:</p>
<p><b>Exemplo:</b></p>
<p>Desenhe 2 gráficos um em cima do outro:</p>
<pre>
import matplotlib.pyplot as plt
import numpy as np

#plot 1:
x = np.array([0, 1, 2, 3])
y = np.array([3, 8, 1, 10])

plt.subplot(2, 1, 1)
plt.plot(x,y)

#plot 2:
x = np.array([0, 1, 2, 3])
y = np.array([10, 20, 30, 40])

plt.subplot(2, 1, 2)
plt.plot(x,y)

plt.show()
</pre>
<p><b>Resultado:</b></p>
<img src="matplotlib_subplots2.png">
<p>É possível desenhar quantos gráficos desejar em uma única figura, basta descrever o número de linhas, colunas e o índice do gráfico.</p>
<p><b>Exemplo:</b></p>
<p>Desenhe 6 gráficos:</p>
<pre>
import matplotlib.pyplot as plt
import numpy as np

x = np.array([0, 1, 2, 3])
y = np.array([3, 8, 1, 10])

plt.subplot(2, 3, 1)
plt.plot(x,y)

x = np.array([0, 1, 2, 3])
y = np.array([10, 20, 30, 40])

plt.subplot(2, 3, 2)
plt.plot(x,y)

x = np.array([0, 1, 2, 3])
y = np.array([3, 8, 1, 10])

plt.subplot(2, 3, 3)
plt.plot(x,y)

x = np.array([0, 1, 2, 3])
y = np.array([10, 20, 30, 40])

plt.subplot(2, 3, 4)
plt.plot(x,y)

x = np.array([0, 1, 2, 3])
y = np.array([3, 8, 1, 10])

plt.subplot(2, 3, 5)
plt.plot(x,y)

x = np.array([0, 1, 2, 3])
y = np.array([10, 20, 30, 40])

plt.subplot(2, 3, 6)
plt.plot(x,y)

plt.show()
</pre>
<p><b>Resultado:</b></p>
<img src="matplotlib_subplots3.png">
<h2 align="center">Título</h2>
<p>É possível adicionar um título a cada gráfico com a função title():</p>
<p><b>Exemplo:</b></p>
<p>2 gráficos, com títulos:</p>
<pre>
import matplotlib.pyplot as plt
import numpy as np

#plot 1:
x = np.array([0, 1, 2, 3])
y = np.array([3, 8, 1, 10])

plt.subplot(1, 2, 1)
plt.plot(x,y)
plt.title("SALES")

#plot 2:
x = np.array([0, 1, 2, 3])
y = np.array([10, 20, 30, 40])

plt.subplot(1, 2, 2)
plt.plot(x,y)
plt.title("INCOME")

plt.show()
</pre>
<p><b>Resultado:</b></p>
<img src="matplotlib_subplots4.png">
<h2 align="center">Título Principal</h2>
<p>Você pode adicionar um título para a figura inteira com a função suptitle():</p>
<p><b>Exemplo:</b></p>
<p>Adicione um título para a figura inteira:</p>
<pre>
import matplotlib.pyplot as plt
import numpy as np

#plot 1:
x = np.array([0, 1, 2, 3])
y = np.array([3, 8, 1, 10])

plt.subplot(1, 2, 1)
plt.plot(x,y)
plt.title("SALES")

#plot 2:
x = np.array([0, 1, 2, 3])
y = np.array([10, 20, 30, 40])

plt.subplot(1, 2, 2)
plt.plot(x,y)
plt.title("INCOME")

plt.suptitle("MY SHOP")
plt.show()
</pre>
<p><b>Resultado:</b></p>
<img src="matplotlib_subplots5.png">
