<h1 align="center">Gráficos Básicos com Matplotlib</h1>
<h1 align="center">Pyplot</h1>
<p>A maioria das utilidades do Matplotlib está no submódulo pyplot e geralmente é importada com o apelido "plt":</p>
<pre>
import matplotlib.pyplot as plt
</pre>
<p>Agora, o pacote Pyplot pode ser referenciado como "plt".</p>
<p><b>Exemplo:</b></p>
<p>Agora usando o Pyplot desenhe uma linha em um diagrama da posição (0,0) até a posição (6,250):</p>
<pre>
import matplotlib.pyplot as plt
import numpy as np

xpoints = np.array([0, 6])
ypoints = np.array([0, 250])

plt.plot(xpoints, ypoints)
plt.show()
</pre>
<p><b>Resultado:</b></p>
<img src="matplotlib_pyplot.png">
<h1 align="center">Plotting</h1>
