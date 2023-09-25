<h1 align="center">Scipy</h1>
<h2 align="center">O que é SciPy?</h2>
<p>SciPy é um conjunto de ferramentas open-source utilizadas principalmente para computação científica de alta performance. Esse conjunto de ferramentas nos fornece um ambiente para trabalho ideal para quem está no mundo de aprendizado de máquina e científico também. Os pacotes básicos de instalação do SciPy são:</p>
<ul>
  <li>NumPy;</li>
  <li>Biblioteca SciPy;</li>
  <li>Matplotlib;</li>
  <li>IPython;</li>
  <li>Pandas;</li>
  <li>Sympy;</li>
  <li>Nose.</li>
</ul>
<p>SciPy é uma biblioteca de computação científica que usa NumPy embaixo.</p>
<p>SciPy significa Scientific Python.</p>
<p>Ele fornece mais funções de utilitário para otimização, estatísticas e processamento de sinais.</p>
<p>Como o NumPy, o SciPy é de código aberto para que possamos usá-lo livremente.</p>
<p>O SciPy foi criado pelo criador do NumPy, Travis Olliphant.</p>
<h2 align="center">Por que usar SciPy?</h2>
<p>Para mim, os motivos principais que tornam esse conjunto bastante poderoso são:</p>
<ul>
  <li>Todos os pacotes de SciPy são muito intuitivos, o tornando também muito fácil de se aprender;</li>
  <li>O SciPy otimizou e adicionou funções que são frequentemente usadas no NumPy e na Data Science;</li>
  <li>O SciPy tem uma comunidade muito ativa.</li>
</ul>
<h2 align="center">Instalação do SciPy</h2>
<pre>
pip install scipy
</pre>
<h2 align="center">Instalação do SciPy</h2>
<pre>
import scipy
</pre>
<p>Exemplo:</p>
<pre>
from scipy import constants

print(constants.liter)
</pre>
<h2 align="center">SciPy Constantes</h2>
<h3 align="center">Constantes no SciPy</h3>
<p>Como o SciPy é mais focado em implementações científicas, ele fornece muitas constantes científicas internas.</p>
<p>Essas constantes podem ser úteis quando você trabalha com a Data Science.</p>
<h3 align="center">Unidades de constante</h3>
<p>Uma lista de todas as unidades no módulo de constantes pode ser vista usando o dir() função.</p>
<pre>
from scipy import constants

print(dir(constants))
</pre>
<h3 align="center">Categorias de unidade</h3>
<p>As unidades são colocadas nessas categorias:</p>
<ul>
  <li>Métrica</li>
  <li>Binário</li>
  <li>Massa</li>
  <li>Ângulo</li>
  <li>Tempo</li>
  <li>Comprimento</li>
  <li>Pressão</li>
  <li>Volume</li>
  <li>Velocidade</li>
  <li>Temperatura</li>
  <li>Energia</li>
  <li>Potência</li>
  <li>Força</li>
</ul>
<h3 align="center">Métrico ( SI ) Prefixos:</h3>
<p>Retorne a unidade especificada em <b>metro</b> ( p. centi retorna 0.01)</p>
<pre>
from scipy import constants

print(constants.yotta)    #1e+24
print(constants.zetta)    #1e+21
print(constants.exa)      #1e+18
print(constants.peta)     #1000000000000000.0
print(constants.tera)     #1000000000000.0
print(constants.giga)     #1000000000.0
print(constants.mega)     #1000000.0
print(constants.kilo)     #1000.0
print(constants.hecto)    #100.0
print(constants.deka)     #10.0
print(constants.deci)     #0.1
print(constants.centi)    #0.01
print(constants.milli)    #0.001
print(constants.micro)    #1e-06
print(constants.nano)     #1e-09
print(constants.pico)     #1e-12
print(constants.femto)    #1e-15
print(constants.atto)     #1e-18
print(constants.zepto)    #1e-21
</pre>
<h3 align="center">Prefixos binários:</h3>
<p>Retorne a unidade especificada em <b>bytes</b> ( p. kibi retorna 1024)</p>
<pre>
from scipy import constants

print(constants.kibi)    #1024
print(constants.mebi)    #1048576
print(constants.gibi)    #1073741824
print(constants.tebi)    #1099511627776
print(constants.pebi)    #1125899906842624
print(constants.exbi)    #1152921504606846976
print(constants.zebi)    #1180591620717411303424
print(constants.yobi)    #1208925819614629174706176
</pre>
<h3 align="center">Massa:</h3>
<p>Retorne a unidade especificada em <b>kg</b> ( p. gram retorna 0.001)</p>
<pre>
from scipy import constants

print(constants.gram)        #0.001
print(constants.metric_ton)  #1000.0
print(constants.grain)       #6.479891e-05
print(constants.lb)          #0.45359236999999997
print(constants.pound)       #0.45359236999999997
print(constants.oz)          #0.028349523124999998
print(constants.ounce)       #0.028349523124999998
print(constants.stone)       #6.3502931799999995
print(constants.long_ton)    #1016.0469088
print(constants.short_ton)   #907.1847399999999
print(constants.troy_ounce)  #0.031103476799999998
print(constants.troy_pound)  #0.37324172159999996
print(constants.carat)       #0.0002
print(constants.atomic_mass) #1.66053904e-27
print(constants.m_u)         #1.66053904e-27
print(constants.u)           #1.66053904e-27
</pre>
<h3 align="center">Ângulo:</h3>
<p>Retorne a unidade especificada em <b>radianos</b> ( p. degree retorna 0.017453292519943295)</p>
<pre>
from scipy import constants

print(constants.degree)     #0.017453292519943295
print(constants.arcmin)     #0.0002908882086657216
print(constants.arcminute)  #0.0002908882086657216
print(constants.arcsec)     #4.84813681109536e-06
print(constants.arcsecond)  #4.84813681109536e-06
</pre>
<h3 align="center">Tempo:</h3>
<p>Retorne a unidade especificada em <b>segundos</b> ( p. hour retorna 3600.0)</p>
<pre>
from scipy import constants

print(constants.minute)      #60.0
print(constants.hour)        #3600.0
print(constants.day)         #86400.0
print(constants.week)        #604800.0
print(constants.year)        #31536000.0
print(constants.Julian_year) #31557600.0
</pre>
<h3 align="center">Comprimento:</h3>
<p>Retorne a unidade especificada em <b>metros</b> ( p. nautical_mile retorna 1852.0)</p>
<pre>
from scipy import constants

print(constants.inch)              #0.0254
print(constants.foot)              #0.30479999999999996
print(constants.yard)              #0.9143999999999999
print(constants.mile)              #1609.3439999999998
print(constants.mil)               #2.5399999999999997e-05
print(constants.pt)                #0.00035277777777777776
print(constants.point)             #0.00035277777777777776
print(constants.survey_foot)       #0.3048006096012192
print(constants.survey_mile)       #1609.3472186944373
print(constants.nautical_mile)     #1852.0
print(constants.fermi)             #1e-15
print(constants.angstrom)          #1e-10
print(constants.micron)            #1e-06
print(constants.au)                #149597870691.0
print(constants.astronomical_unit) #149597870691.0
print(constants.light_year)        #9460730472580800.0
print(constants.parsec)            #3.0856775813057292e+16
</pre>
<h3 align="center">Pressão:</h3>
<p>Retorne a unidade especificada em <b>pascal</b> ( p. psi retorna 6894.757293168361)</p>
<pre>
from scipy import constants

print(constants.atm)         #101325.0
print(constants.atmosphere)  #101325.0
print(constants.bar)         #100000.0
print(constants.torr)        #133.32236842105263
print(constants.mmHg)        #133.32236842105263
print(constants.psi)         #6894.757293168361
</pre>
<h3 align="center">Área:</h3>
<p>Retorne a unidade especificada em <b>metros quadrados</b> ( p. hectare retorna 10000.0)</p>
<pre>
from scipy import constants

print(constants.hectare) #10000.0
print(constants.acre)    #4046.8564223999992
</pre>
<h3 align="center">Volume:</h3>
<p>Retorne a unidade especificada em <b>metros cúbicos</b> ( p. liter retorna 0.001)</p>
<pre>
from scipy import constants

print(constants.liter)            #0.001
print(constants.litre)            #0.001
print(constants.gallon)           #0.0037854117839999997
print(constants.gallon_US)        #0.0037854117839999997
print(constants.gallon_imp)       #0.00454609
print(constants.fluid_ounce)      #2.9573529562499998e-05
print(constants.fluid_ounce_US)   #2.9573529562499998e-05
print(constants.fluid_ounce_imp)  #2.84130625e-05
print(constants.barrel)           #0.15898729492799998
print(constants.bbl)              #0.15898729492799998
</pre>
<h3 align="center">Velocidade:</h3>
<p>Retorne a unidade especificada em <b>metros por segundo</b> ( p. speed_of_sound retorna 340.5)</p>
<pre>
from scipy import constants

print(constants.kmh)            #0.2777777777777778
print(constants.mph)            #0.44703999999999994
print(constants.mach)           #340.5
print(constants.speed_of_sound) #340.5
print(constants.knot)           #0.5144444444444445
</pre>
<h3 align="center">Temperatura:</h3>
<p>Retorne a unidade especificada em <b>Kelvin</b> ( p. zero_Celsius retorna 273.15)</p>
<pre>
from scipy import constants

print(constants.zero_Celsius)      #273.15
print(constants.degree_Fahrenheit) #0.5555555555555556
</pre>
<h3 align="center">Energia:</h3>
<p>Retorne a unidade especificada em <b>Joules</b> ( p. calorie retorna 4.184)</p>
<pre>
from scipy import constants

print(constants.eV)            #1.6021766208e-19
print(constants.electron_volt) #1.6021766208e-19
print(constants.calorie)       #4.184
print(constants.calorie_th)    #4.184
print(constants.calorie_IT)    #4.1868
print(constants.erg)           #1e-07
print(constants.Btu)           #1055.05585262
print(constants.Btu_IT)        #1055.05585262
print(constants.Btu_th)        #1054.3502644888888
print(constants.ton_TNT)       #4184000000.0
</pre>
<h3 align="center">Poder:</h3>
<p>Retorne a unidade especificada em <b>watts</b> ( p. horsepower retorna 745.6998715822701)</p>
<pre>
from scipy import constants

print(constants.hp)         #745.6998715822701
print(constants.horsepower) #745.6998715822701
</pre>
<h3 align="center">Força:</h3>
<p>Retorne a unidade especificada em <b>Newton</b> ( p. kilogram_force retorna 9.80665)</p>
<pre>
from scipy import constants

print(constants.dyn)             #1e-05
print(constants.dyne)            #1e-05
print(constants.lbf)             #4.4482216152605
print(constants.pound_force)     #4.4482216152605
print(constants.kgf)             #9.80665
print(constants.kilogram_force)  #9.80665
</pre>
<h2 align="center">Scipy Optimizers</h2>
<h3 align="center">Otimizadores no SciPy</h3>
<p>Otimizadores são um conjunto de procedimentos definidos no SciPy que encontram o valor mínimo de uma função ou a raiz de uma equação.</p>
<h3 align="center">Otimizando funções</h3>
<p>Essencialmente, todos os algoritmos do Machine Learning nada mais são do que uma equação complexa que precisa ser minimizada com a ajuda de dados fornecidos.</p>
<h3 align="center">Raízes de uma equação</h3>
<p>O NumPy é capaz de encontrar raízes para polinômios e equações lineares, mas não consegue encontrar raízes para não equações lineares, como esta:</p>
<pre>
x + cos(x)
</pre>
<p>Para isso, você pode usar o SciPy's optimze.root função.</p>
<p>Esta função usa dois argumentos necessários:</p>
<p><b>Diversão</b> - uma função representando uma equação.</p>
<p><b>x0</b> - um palpite inicial para a raiz.</p>
<p>A função retorna um objeto com informações sobre a solução.</p>
<p>A solução real é fornecida no atributo x do objeto retornado:</p>
<p><b>Exemplo</b></p>
<p>Encontre raiz da equação x + cos(x):</p>
<pre>
from scipy.optimize import root
from math import cos

def eqn(x):
&emsp;&emsp;return x + cos(x)

myroot = root(eqn, 0)

print(myroot.x)
</pre>
<p><b>Solução</b></p>
<pre>
[-0.73908513]
</pre>
<h3 align="center">Minimizando uma função</h3>
<p>Uma função, neste contexto, representa uma curva, as curvas têm pontos altos e pontos baixos.</p>
<p>Pontos altos são chamados maxima.</p>
<p>Pontos baixos são chamados mínimos.</p>
<p>O ponto mais alto de toda a curva é chamado máximos globais, enquanto o resto deles é chamado maxima local.</p>
<p>O ponto mais baixo de toda a curva é chamado mínimos globais, enquanto o resto deles é chamado mínimos locais.</p>
<h3 align="center">Encontrando mínimos</h3>
<p>Nós podemos usar scipy.optimize.minimize() função para minimizar a função.</p>
<p>O minimize() A função usa os seguintes argumentos:</p>
<p><b>Diversão</b> - uma função representando uma equação.</p>
<p><b>x0</b> - um palpite inicial para a raiz.</p>
<p><b>Método</b> - nome do método a ser usado. Valores legais:</p>
<pre>
'CG'
'BFGS'
'Newton-CG'
'L-BFGS-B'
'TNC'
'COBYLA'
'SLSQP'
</pre>
<p><b>Retorno de Chamada</b> - função chamada após cada iteração de otimização.</p>
<p><b>Opções</b> - um dicionário que define parâmetros extras:</p>
<pre>
{
&emsp;&emsp;&emsp;&emsp;"disp": boolean - print detailed description
&emsp;&emsp;&emsp;&emsp;"gtol": number - the tolerance of the error
  }
</pre>

<h2>Refêrencias</h2>
<p>https://www.w3schools.com/python/scipy/scipy_intro.php</p>
<p>https://www.ferrari.pro.br/home/documents/FFerrari-ecosistema-python.pdf</p>
<p>https://machinelearningbrasil.wordpress.com/2015/01/14/introducao-a-python-e-scipy-para-aprendizado-de-maquina/</p>
