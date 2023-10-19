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
<h2 align="center">Plotando pontos x e y</h2>
<p>A função plot() é usada para desenhar pontos (marcadores) em um diagrama.</p>
<p>Por padrão, a função plot() desenha uma linha de ponto a ponto.</p>
<p>A função aceita parâmetros para especificar os pontos no diagrama.</p>
<p>O Parâmetro 1 é uma matriz(array) contendo os pontos no eixo x.</p>
<p>O Parâmetro 2 é uma matriz(array) contendo os pontos no eixo y.</p>
<p>Se precisarmos desenhar uma linha de (1, 3) para (8, 10), precisamos passar duas matrizes(array) [1, 8] e [3, 10] para a função plot.</p>
<p><b>Exemplo:</b></p>
<p>Desenhe uma linha em um diagrama da posição (1, 3) até a posição (8, 10):</p>
<pre>
import matplotlib.pyplot as plt
import numpy as np

xpoints = np.array([1, 8])
ypoints = np.array([3, 10])

plt.plot(xpoints, ypoints)
plt.show()
</pre>
<p><b>Resultado:</b></p>
<img src="matplotlib_plotting1.png">
<p>O <b>eixo x</b> é o eixo horizontal.</p>
<p>O <b>eixo y</b> é o eixo vertical.</p>
<h2 align="center">Plotagem Sem Linha</h2>
<p>Para plotar apenas os marcadores, você pode usar a notação de string abreviada 'o', que significa 'anéis'('rings').</p>
<p><b>Exemplo:</b></p>
<p>Desenhe dois pontos no diagrama, um na posição (1, 3) e outro na posição (8, 10):</p>
<pre>
import matplotlib.pyplot as plt
import numpy as np

xpoints = np.array([1, 8])
ypoints = np.array([3, 10])

plt.plot(xpoints, ypoints, 'o')
plt.show()
</pre>
<p><b>Resultado:</b></p>
<img src="matplotlib_plotting2.png">
<p>Você aprenderá mais sobre marcadores no próximo módulo: <b>2.Personalização e Anotações</b>.</p>
<h2 align="center">Múltiplos Pontos</h2>
<p>Você pode plotar quantos pontos desejar, apenas certifique-se de ter o mesmo número de pontos em ambos os eixos.</p>
<p><b>Exemplo:</b></p>
<p>Desenhe uma linha em um diagrama da posição (1, 3) até (2, 8), depois para (6, 1) e finalmente para a posição (8, 10):</p>
<pre>
import matplotlib.pyplot as plt
import numpy as np

xpoints = np.array([1, 2, 6, 8])
ypoints = np.array([3, 8, 1, 10])

plt.plot(xpoints, ypoints)
plt.show()
</pre>
<p><b>Resultado:</b></p>
<img src="matplotlib_plotting3.png">
<h2 align="center">Padrão dos Pontos no Eixo X</h2>
<p>Se não especificarmos os pontos no eixo x, eles receberão os valores padrão 0, 1, 2, 3 etc., dependendo do comprimento dos pontos no eixo y.</p>
<p>Portanto, se pegarmos o mesmo exemplo acima e deixarmos de fora os pontos no eixo x, o diagrama ficará assim:</p>
<p><b>Exemplo:</b></p>
<p>Plotagem sem pontos no eixo x:</p>
<pre>
import matplotlib.pyplot as plt
import numpy as np

ypoints = np.array([3, 8, 1, 10, 5, 7])

plt.plot(ypoints)
plt.show()
</pre>
<p><b>Resultado:</b></p>
<img src="matplotlib_plotting4.png">
<p>Os pontos no eixo x no exemplo acima são [0, 1, 2, 3, 4, 5].</p>
<h1 align="center">Gráficos de Linha (Line Plots)</h1>
<h2 align="center">Estilo da linha (Linestyle)</h2>
<p>Você pode usar o argumento de palavra-chave "linestyle" ou a abreviação "ls" para alterar o estilo da linha plotada:</p>
<p><b>Exemplo:</b></p>
<p>Use uma linha pontilhada:</p>
<pre>
import matplotlib.pyplot as plt
import numpy as np

ypoints = np.array([3, 8, 1, 10])

plt.plot(ypoints, linestyle = 'dotted')
plt.show()
</pre>
<p><b>Resultado:</b></p>
<img src="matplotlib_line_dotted.png">
<p><b>Exemplo:</b></p>
<p>Use uma linha tracejada:</p>
<pre>
plt.plot(ypoints, linestyle = 'dashed')
</pre>
<p><b>Resultado:</b></p>
<img src="matplotlib_line_dashed.png">
<p>You can choose any of these styles:</p>
<table>
  <tr>
    <th>Estilo</th>
    <th>Ou</th>
  </tr>
  <tr>
    <td>'solid' (Sólido)</td>
    <td>'-'</td>
  </tr>
  <tr>
    <td>'dotted' (Pontilhado)</td>
    <td>':'</td>
  </tr>
  <tr>
    <td>'dashed' ('tracejado')</td>
    <td>'--'</td>
  </tr>
  <tr>
    <td>'dashdot' ('tracejado-ponto')</td>
    <td>'-.'</td>
  </tr>
  <tr>
    <td>'None' ('Nenhum')</td>
    <td>'' ou ' '</td>
  </tr>
</table>
<h2 align="center">Shorter Syntax</h2>
<p>O estilo da linha pode ser escrito em uma sintaxe mais curta:</p>
<p>"linestyle" pode ser escrito como "ls".</p>
<p>"dotted" pode ser escrito como ":".</p>
<p>"dashed" pode ser escrito como "--".</p>
<p><b>Exemplo:</b></p>
<p>Sintaxe mais curta:</p>
<pre>
plt.plot(ypoints, ls = ':')
</pre>
<p><b>Resultado:</b></p>
<img src="matplotlib_line_dotted.png">
<h2 align="center">Cor da Linha (Line Color)</h2>
<p>Você pode usar o argumento de palavra-chave "color" ou a abreviação "c" para definir a cor da linha:</p>
<p><b>Exemplo:</b></p>
<p>Defina a cor da linha como vermelho:</p>
<pre>
import matplotlib.pyplot as plt
import numpy as np

ypoints = np.array([3, 8, 1, 10])

plt.plot(ypoints, color = 'r')
plt.show()
</pre>
<p><b>Resultado:</b></p>
<img src="matplotlib_line_red.png">
<p>Você também pode usar <a href="https://www.w3schools.com/colors/colors_hexadecimal.asp">valores de cor hexadecimal:</a></p>
<p><b>Exemplo:</b></p>
<p>Traçar com uma linda linha verde:</p>
<pre>
...
plt.plot(ypoints, c = '#4CAF50')
...
</pre>
<p><b>Resultado:</b></p>
<img src="matplotlib_line_hex.png">
<p>Ou qualquer um dos <a href="https://www.w3schools.com/colors/colors_names.asp">140 nomes de cores suportados.</a></p>
<p><b>Exemplo:</b></p>
<p>Traçar com a cor chamada "hotpink":</p>
<pre>
...
plt.plot(ypoints, c = 'hotpink')
...
</pre>
<p><b>Resultado:</b></p>
<img src="matplotlib_line_hotpink.png">
<h2 align="center">Largura da Linha (Line Width)</h2>
<p></p>
<p></p>
<p><b>Exemplo:</b></p>
<p></p>
