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
<h2 align="center">Sintaxe Abreviada (Shorter Syntax)</h2>
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
<p>Você pode usar o argumento de palavra-chave linewidth ou a abreviação lw para alterar a largura da linha.</p>
<p>O valor é um número flutuante, em pontos:</p>
<p><b>Exemplo:</b></p>
<p>Desenhe uma linha larga de 20,5 pontos:</p>
<pre>
import matplotlib.pyplot as plt
import numpy as np

ypoints = np.array([3, 8, 1, 10])

plt.plot(ypoints, linewidth = '20.5')
plt.show()
</pre>
<p><b>Resultado:</b></p>
<img src="matplotlib_line_lw.png">
<h2 align="center">Múltiplas Linhas (Multiple Lines)</h2>
<p>Você pode plotar quantas linhas desejar, simplesmente adicionando mais funções plt.plot():</p>
<p><b>Exemplo:</b></p>
<p>Desenhe duas linhas especificando uma função plt.plot() para cada linha:</p>
<pre>
import matplotlib.pyplot as plt
import numpy as np

y1 = np.array([3, 8, 1, 10])
y2 = np.array([6, 2, 7, 11])

plt.plot(y1)
plt.plot(y2)

plt.show()
</pre>
<p><b>Resultado:</b></p>
<img src="matplotlib_line_two.png">
<p>Você também pode plotar muitas linhas adicionando os pontos para o eixo x e y para cada linha na mesma função plt.plot().</p>
<p>(Nos exemplos acima, especificamos apenas os pontos no eixo y, o que significa que os pontos no eixo x receberam os valores padrão (0, 1, 2, 3).)</p>
<p>Os valores de x e y são fornecidos em pares:</p>
<p><b>Exemplo:</b></p>
<p>Desenhe duas linhas especificando os valores dos pontos x e y para ambas as linhas:</p>
<pre>
import matplotlib.pyplot as plt
import numpy as np

x1 = np.array([0, 1, 2, 3])
y1 = np.array([3, 8, 1, 10])
x2 = np.array([0, 1, 2, 3])
y2 = np.array([6, 2, 7, 11])

plt.plot(x1, y1, x2, y2)
plt.show()
</pre>
<p><b>Resultado:</b></p>
<img src="matplotlib_line_two.png">
<h1 align="center">Gráficos de Dispersão (Scatter Plots)</h1>
<h2 align="center">Criando Gráficos de Dispersão (Scatter Plots)</h2>
<p>Com o Pyplot, você pode usar a função scatter() para desenhar um gráfico de dispersão.</p>
<p>A função scatter() representa um ponto para cada observação. Ela requer dois arrays de comprimento igual, um para os valores do eixo x e outro para os valores no eixo y:</p>
<p><b>Exemplo:</b></p>
<p>Um gráfico de dispersão simples:</p>
<pre>
import matplotlib.pyplot as plt
import numpy as np

x = np.array([5,7,8,7,2,17,2,9,4,11,12,9,6])
y = np.array([99,86,87,88,111,86,103,87,94,78,77,85,86])

plt.scatter(x, y)
plt.show()
</pre>
<p><b>Resultado:</b></p>
<img src="matplotlib_scatter.png">
<p>A observação no exemplo acima é o resultado de 13 carros passando.</p>
<p>O eixo X mostra a idade do carro.</p>
<p>O eixo Y mostra a velocidade do carro ao passar.</p>
<p>Existem alguma relação entre as observações?</p>
<p>Parece que quanto mais novo o carro, mais rápido ele anda, mas isso poderia ser uma coincidência, afinal, só registramos 13 carros.</p>
<h2 align="center">Comparar Gráficos</h2>
<p>No exemplo acima, parece haver uma relação entre a velocidade e a idade, mas e se plotarmos as observações de outro dia também? O gráfico de dispersão nos dirá algo diferente?</p>
<p><b>Exemplo:</b></p>
<p>Desenhe dois gráficos na mesma figura:</p>
<pre>
import matplotlib.pyplot as plt
import numpy as np

#day one, the age and speed of 13 cars:
x = np.array([5,7,8,7,2,17,2,9,4,11,12,9,6])
y = np.array([99,86,87,88,111,86,103,87,94,78,77,85,86])
plt.scatter(x, y)

#day two, the age and speed of 15 cars:
x = np.array([2,2,8,1,15,8,12,9,7,3,11,4,7,14,12])
y = np.array([100,105,84,105,90,99,90,95,94,100,79,112,91,80,85])
plt.scatter(x, y)

plt.show()
</pre>
<p><b>Resultado:</b></p>
<img src="matplotlib_scatter_compare.png">
<p><b>Observação:</b> Os dois gráficos são plotados com cores diferentes, por padrão azul e laranja. Você aprenderá a alterar as cores mais tarde neste capítulo.</p>
<p>Comparando os dois gráficos, acredito que é seguro dizer que ambos nos dão a mesma conclusão: quanto mais novo o carro, mais rápido ele anda.</p>
<h2 align="center">Cores</h2>
<p>Comparando os dois gráficos, acredito que é seguro dizer que ambos nos dão a mesma conclusão: quanto mais novo o carro, mais rápido ele anda.</p>
<p><b>Exemplo:</b></p>
<p>Defina sua própria cor para os marcadores:</p>
<pre>
import matplotlib.pyplot as plt
import numpy as np

x = np.array([5,7,8,7,2,17,2,9,4,11,12,9,6])
y = np.array([99,86,87,88,111,86,103,87,94,78,77,85,86])
plt.scatter(x, y, color = 'hotpink')

x = np.array([2,2,8,1,15,8,12,9,7,3,11,4,7,14,12])
y = np.array([100,105,84,105,90,99,90,95,94,100,79,112,91,80,85])
plt.scatter(x, y, color = '#88c999')

plt.show()
</pre>
<p><b>Resultado:</b></p>
<img src="matplotlib_scatter_color.png">
<h2 align="center">Colorir Cada Ponto</h2>
<p>Você pode até definir uma cor específica para cada ponto usando um array de cores como valor para o argumento c:</p>
<p><b>Observação: </b>Você não pode usar o argumento color para isso, apenas o argumento c.</p>
<p><b>Exemplo:</b></p>
<p>Defina sua própria cor para os marcadores:</p>
<pre>
import matplotlib.pyplot as plt
import numpy as np

x = np.array([5,7,8,7,2,17,2,9,4,11,12,9,6])
y = np.array([99,86,87,88,111,86,103,87,94,78,77,85,86])
colors = np.array(["red","green","blue","yellow","pink","black","orange","purple","beige","brown","gray","cyan","magenta"])

plt.scatter(x, y, c=colors)

plt.show()
</pre>
<p><b>Resultado:</b></p>
<img src="matplotlib_scatter_colors2.png">
<h2 align="center">Mapa de Cores</h2>
<p>O módulo Matplotlib possui vários mapas de cores disponíveis.</p>
<p>Um mapa de cores é como uma lista de cores, onde cada cor possui um valor que varia de 0 a 100.</p>
<p>Aqui está um exemplo de um mapa de cores:</p>
<img src="colorbar.png">
<p>Este mapa de cores é chamado 'viridis' e, como você pode ver, varia de 0, que é uma cor roxa, até 100, que é uma cor amarela.</p>
<h3 align="center">Como Usar o Mapa de Cores</h3>
<p>Você pode especificar o mapa de cores com o argumento de palavra-chave cmap com o valor do mapa de cores, neste caso 'viridis', que é um dos mapas de cores incorporados disponíveis no Matplotlib.</p>
<p>Além disso, você deve criar um array com valores (de 0 a 100), um valor para cada ponto no gráfico de dispersão:</p>
<p><b>Exemplo:</b></p>
<p>Crie um array de cores e especifique um mapa de cores no gráfico de dispersão:</p>
<pre>
import matplotlib.pyplot as plt
import numpy as np

x = np.array([5,7,8,7,2,17,2,9,4,11,12,9,6])
y = np.array([99,86,87,88,111,86,103,87,94,78,77,85,86])
colors = np.array([0, 10, 20, 30, 40, 45, 50, 55, 60, 70, 80, 90, 100])

plt.scatter(x, y, c=colors, cmap='viridis')

plt.show()
</pre>
<p><b>Resultado:</b></p>
<img src="matplotlib_scatter_colormap1.png">
<p>Você pode incluir o mapa de cores no desenho incluindo a declaração plt.colorbar():</p>
<p><b>Exemplo:</b></p>
<p>Inclua o mapa de cores real:</p>
<pre>
import matplotlib.pyplot as plt
import numpy as np

x = np.array([5,7,8,7,2,17,2,9,4,11,12,9,6])
y = np.array([99,86,87,88,111,86,103,87,94,78,77,85,86])
colors = np.array([0, 10, 20, 30, 40, 45, 50, 55, 60, 70, 80, 90, 100])

plt.scatter(x, y, c=colors, cmap='viridis')

plt.colorbar()

plt.show()
</pre>
<p><b>Resultado:</b></p>
<img src="matplotlib_scatter_colormap2.png">
<h3 align="center">Mapas de Cores Disponíveis</h3>
<p>Você pode escolher qualquer um dos mapas de cores incorporados:</p>
<table>
  <tr>
    <th>Name</th>
    <th>Reverse</th>
  </tr>
  <tr>
    <td>Accent</td>
    <td>Accent_r</td>
  </tr>
  <tr>
    <td>Blues</td>
    <td>Blues_r</td>
  </tr>
  <tr>
    <td>BrBG</td>
    <td>BrBG_r</td>
  </tr>
  <tr>
    <td>BuGn</td>
    <td>BuGn_r</td>
  </tr>
  <tr>
    <td>BuPu</td>
    <td>BuPu_r</td>
  </tr>
  <tr>
    <td>BuGn</td>
    <td>BuGn_r</td>
  </tr>
  <tr>
    <td>CMRmap</td>
    <td>CMRmap_r</td>
  </tr>
  <tr>
    <td>Dark2</td>
    <td>Dark2_r</td>
  </tr>
  <tr>
    <td>GnBu</td>
    <td>GnBu_r</td>
  </tr>
  <tr>
    <td>Greens</td>
    <td>Greens_r</td>
  </tr>
  <tr>
    <td>Greys</td>
    <td>Greys_r</td>
  </tr>
  <tr>
    <td>OrRd</td>
    <td>OrRd_r</td>
  </tr>
  <tr>
    <td>Oranges</td>
    <td>Oranges_r</td>
  </tr>
  <tr>
    <td>PRGn</td>
    <td>PRGn_r</td>
  </tr>
  <tr>
    <td>Paired</td>
    <td>Paired_r</td>
  </tr>
  <tr>
    <td>Pastel1</td>
    <td>Pastel1_r</td>
  </tr>
  <tr>
    <td>BuGn</td>
    <td>BuGn_r</td>
  </tr>
  <tr>
    <td>Pastel2</td>
    <td>Pastel2_r</td>
  </tr>
  <tr>
    <td>PiYG</td>
    <td>PiYG_r</td>
  </tr>
  <tr>
    <td>PuBu</td>
    <td>PuBu_r</td>
  </tr>
  <tr>
    <td>PuBuGn</td>
    <td>PuBuGn_r</td>
  </tr>
  <tr>
    <td>PuOr</td>
    <td>PuOr_r</td>
  </tr>
  <tr>
    <td>PuRd</td>
    <td>PuRd_r</td>
  </tr>
  <tr>
    <td>Purples</td>
    <td>Purples_r</td>
  </tr>
  <tr>
    <td>RdBu</td>
    <td>RdBu_r</td>
  </tr>
  <tr>
    <td>RdGy</td>
    <td>RdGy_r</td>
  </tr>
  <tr>
    <td>RdPu</td>
    <td>RdPu_r</td>
  </tr>
  <tr>
    <td>RdYlBu</td>
    <td>RdYlBu_r</td>
  </tr>
  <tr>
    <td>RdYlGn</td>
    <td>RdYlGn_r</td>
  </tr>
  <tr>
    <td>Reds</td>
    <td>Reds_r</td>
  </tr>
  <tr>
    <td>Set1</td>
    <td>Set1_r</td>
  </tr>
  <tr>
    <td>Set2</td>
    <td>Set2_r</td>
  </tr>
  <tr>
    <td>Set3</td>
    <td>Set3_r</td>
  </tr>
  <tr>
    <td>Spectral</td>
    <td>Spectral_r</td>
  </tr>
  <tr>
    <td>Wistia</td>
    <td>Wistia_r</td>
  </tr>
  <tr>
    <td>YlGn</td>
    <td>YlGn_r</td>
  </tr>
  <tr>
    <td>YlGnBu</td>
    <td>YlGnBu_r</td>
  </tr>
  <tr>
    <td>YlOrBr</td>
    <td>YlOrBr_r</td>
  </tr>
  <tr>
    <td>YlOrRd</td>
    <td>YlOrRd_r</td>
  </tr>
  <tr>
    <td>afmhot</td>
    <td>afmhot_r</td>
  </tr>
  <tr>
    <td>autumn</td>
    <td>autumn_r</td>
  </tr>
  <tr>
    <td>binary</td>
    <td>binary_r</td>
  </tr>
  <tr>
    <td>bone</td>
    <td>bone_r</td>
  </tr>
  <tr>
    <td>brg</td>
    <td>brg_r</td>
  </tr>
  <tr>
    <td>bwr</td>
    <td>bwr_r</td>
  </tr>
  <tr>
    <td>cividis</td>
    <td>cividis_r</td>
  </tr>
  <tr>
    <td>cool</td>
    <td>cool_r</td>
  </tr>
  <tr>
    <td>coolwarm</td>
    <td>coolwarm_r</td>
  </tr>
  <tr>
    <td>copper</td>
    <td>copper_r</td>
  </tr>
  <tr>
    <td>cubehelix</td>
    <td>cubehelix_r</td>
  </tr>
  <tr>
    <td>flag</td>
    <td>flag_r</td>
  </tr>
  <tr>
    <td>gist_earth</td>
    <td>gist_earth_r</td>
  </tr>
  <tr>
    <td>gist_gray</td>
    <td>gist_gray_r</td>
  </tr>
  <tr>
    <td>gist_heat</td>
    <td>gist_heat_r</td>
  </tr>
  <tr>
    <td>gist_ncar</td>
    <td>gist_ncar_r</td>
  </tr>
  <tr>
    <td>gist_rainbow</td>
    <td>gist_rainbow_r</td>
  </tr>
  <tr>
    <td>gist_stern</td>
    <td>gist_stern_r</td>
  </tr>
  <tr>
    <td>gist_yarg</td>
    <td>gist_yarg_r</td>
  </tr>
  <tr>
    <td>gnuplot</td>
    <td>gnuplot_r</td>
  </tr>
  <tr>
    <td>gnuplot2</td>
    <td>gnuplot2_r</td>
  </tr>
  <tr>
    <td>gray</td>
    <td>gray_r</td>
  </tr>
  <tr>
    <td>hot</td>
    <td>hot_r</td>
  </tr>
  <tr>
    <td>hsv</td>
    <td>hsv_r</td>
  </tr>
  <tr>
    <td>inferno</td>
    <td>inferno_r</td>
  </tr>
  <tr>
    <td>jet</td>
    <td>jet_r</td>
  </tr>
  <tr>
    <td>magma</td>
    <td>magma_r</td>
  </tr>
  <tr>
    <td>nipy_spectral</td>
    <td>nipy_spectral_r</td>
  </tr>
  <tr>
    <td>ocean</td>
    <td>ocean_r</td>
  </tr>
  <tr>
    <td>pink</td>
    <td>pink_r</td>
  </tr>
  <tr>
    <td>plasma</td>
    <td>plasma_r</td>
  </tr>
  <tr>
    <td>prism</td>
    <td>prism_r</td>
  </tr>
  <tr>
    <td>rainbow</td>
    <td>rainbow_r</td>
  </tr>
  <tr>
    <td>seismic</td>
    <td>seismic_r</td>
  </tr>
  <tr>
    <td>spring</td>
    <td>spring_r</td>
  </tr>
  <tr>
    <td>summer</td>
    <td>summer_r</td>
  </tr>
  <tr>
    <td>tab10</td>
    <td>tab10_r</td>
  </tr>
  <tr>
    <td>tab20</td>
    <td>tab20_r</td>
  </tr>
  <tr>
    <td>tab20b</td>
    <td>tab20b_r</td>
  </tr>
  <tr>
    <td>tab20c</td>
    <td>tab20c_r</td>
  </tr>
  <tr>
    <td>terrain</td>
    <td>terrain_r</td>
  </tr>
  <tr>
    <td>twilight</td>
    <td>twilight_r</td>
  </tr>
  <tr>
    <td>twilight_shifted</td>
    <td>twilight_shifted_r</td>
  </tr>
  <tr>
    <td>viridis</td>
    <td>viridis_r</td>
  </tr>
  <tr>
    <td>winter</td>
    <td>winter_r</td>
  </tr>
</table>
