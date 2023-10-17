<h1 align="center">Limpeza de Dados com Pandas</h1>
<h2 align="center">Limpeza de Dados</h2>
<p>A Limpeza de Dados significa corrigir dados incorretos ou ruins no seu conjunto de dados.</p>
<p>Dados ruins podem ser:</p>
<ul>
  <li>Células Vazias ou Nulas</li>
  <li>Dados em Formatos Incorretos</li>
  <li>Dados Errados</li>
  <li>Dados Duplicados</li>
</ul>
<p>Neste tutorial você vai aprender a como lidar com todos esses tipos de dados ruins.</p>
<h2 align="center">Nosso Conjunto de Dados</h2>
<p>Aqui iremos usar esse conjunto de dados abaixo:</p>
<pre>
    Duration          Date  Pulse  Maxpulse  Calories
0         60  '2020/12/01'    110       130     409.1
1         60  '2020/12/02'    117       145     479.0
2         60  '2020/12/03'    103       135     340.0
3         45  '2020/12/04'    109       175     282.4
4         45  '2020/12/05'    117       148     406.0
5         60  '2020/12/06'    102       127     300.0
6         60  '2020/12/07'    110       136     374.0
7        450  '2020/12/08'    104       134     253.3
8         30  '2020/12/09'    109       133     195.1
9         60  '2020/12/10'     98       124     269.0
10        60  '2020/12/11'    103       147     329.3
11        60  '2020/12/12'    100       120     250.7
12        60  '2020/12/12'    100       120     250.7
13        60  '2020/12/13'    106       128     345.3
14        60  '2020/12/14'    104       132     379.3
15        60  '2020/12/15'     98       123     275.0
16        60  '2020/12/16'     98       120     215.2
17        60  '2020/12/17'    100       120     300.0
18        45  '2020/12/18'     90       112       NaN
19        60  '2020/12/19'    103       123     323.0
20        45  '2020/12/20'     97       125     243.0
21        60  '2020/12/21'    108       131     364.2
22        45           NaN    100       119     282.0
23        60  '2020/12/23'    130       101     300.0
24        45  '2020/12/24'    105       132     246.0
25        60  '2020/12/25'    102       126     334.5
26        60    2020/12/26    100       120     250.0
27        60  '2020/12/27'     92       118     241.0
28        60  '2020/12/28'    103       132       NaN
29        60  '2020/12/29'    100       132     280.0
30        60  '2020/12/30'    102       129     380.3
31        60  '2020/12/31'     92       115     243.0
</pre>
<p>Esse conjunto de dados contém algumas células vazias ("Date" na linha 22, e "Calories" na linha 18 e 28).</p>
<p>Esse conjunto de dados contém um formato incorreto ("Date" na linha 26).</p>
<p>Esse conjunto de dados contém dados errados ("Duration" na linha 7).</p>
<p>Esse conjunto de dados contém duplicadas (linha 11 e 12).</p>
<h1 align="center">Limpando Células Vazias com Pandas</h2>
<h2 align="center">Células Vazias</h2>
<p>Células vazias podem potencialmente fornecer um resultado incorreto ao analisar dados.</p>
<h2 align="center">Removendo Linhas</h2>
<p>Uma maneira de lidar com células vazias é remover linhas que as contenham.</p>
<p>Isso geralmente é aceitável, uma vez que conjuntos de dados podem ser muito grandes, e remover algumas linhas não terá um grande impacto no resultado.</p>
<p><b>Exemplo:</b></p>
<p>Retorne um novo DataFrame sem células vazias:</p>
<pre>
import pandas as pd

df = pd.read_csv('data.csv')

new_df = df.dropna()

print(new_df.to_string())
</pre>
<p><b>Observação:</b> Por padrão, o método dropna() retorna um novo DataFrame e não altera o original.</p>
<p>Se você deseja alterar o DataFrame original, use o argumento inplace = True:</p>
<p><b>Exemplo:</b></p>
<p>Vamos abaixo remover todas linhas com valores nulos:</p>
<pre>
import pandas as pd

df = pd.read_csv('data.csv')

df.dropna(inplace = True)

print(df.to_string())
</pre>
<p><b>Observação:</b> Agora, o dropna(inplace = True) NÃO retornará um novo DataFrame, mas removerá todas as linhas que contêm valores NULL(Nulos) do DataFrame original.</p>
<h2 align="center">Substituindo Valores Vazios</h2>
<p>Outra forma de lidar com células vazias é inserir um novo valor no lugar delas.</p>
<p>Dessa forma, você não precisa excluir linhas inteiras apenas por causa de algumas células vazias.</p>
<p>O método fillna() nos permite substituir células vazias por um valor:</p>
<p><b>Exemplo:</b></p>
<p>Substitua os valores NULL(Nulos) pelo número 130:</p>
<pre>
import pandas as pd

df = pd.read_csv('data.csv')

df.fillna(130, inplace = True)
</pre>
<h3 align="center">Substituir Apenas em Colunas Específicas</h3>
<p>O exemplo anterior substitui todas as células vazias em todo o DataFrame.</p>
<p>Para substituir apenas os valores vazios em uma coluna específica, especifique o nome da coluna do DataFrame:</p>
<p><b>Exemplo:</b></p>
<p>Substitua os valores NULL(Nulos) na coluna "Calories" pelo número 130:</p>
<pre>
import pandas as pd

df = pd.read_csv('data.csv')

df["Calories"].fillna(130, inplace = True)
</pre>
<h2 align="center">Substituindo usando Média, Mediana ou Moda</h2>
<p>Uma maneira comum de substituir células vazias é calcular o valor da média, mediana ou do valor da moda da coluna.</p>
<p>O Pandas utiliza os métodos <b>mean(), median() e mode()</b> para calcular os respectivos valores de uma coluna especificada:</p>
<p><b>Exemplo:</b></p>
<p>Calcule a <b>Média</b> e substitua quaisquer valores vazios por ela:</p>
<pre>
import pandas as pd

df = pd.read_csv('data.csv')

x = df["Calories"].mean()

df["Calories"].fillna(x, inplace = True)
</pre>
<p><b>Média</b> = o valor médio (a soma de todos os valores dividida pelo número de valores).</p>
<p><b>Exemplo:</b></p>
<p>Calcule a <b>Mediana</b> e substitua quaisquer valores vazios por ela:</p>
<pre>
import pandas as pd

df = pd.read_csv('data.csv')

x = df["Calories"].median()

df["Calories"].fillna(x, inplace = True)
</pre>
<p><b>Mediana</b> = o valor do meio, após ordenar todos os valores em ordem crescente.</p>
<p><b>Exemplo:</b></p>
<p>Calcule a <b>Moda</b> e substitua quaisquer valores vazios por ela:</p>
<pre>
import pandas as pd

df = pd.read_csv('data.csv')

x = df["Calories"].mode()[0]

df["Calories"].fillna(x, inplace = True)
</pre>
<p><b>Moda</b> = o valor que aparece com mais frequência.</p>
<h2 align="center">Referências</h2>
<p>https://www.w3schools.com/python/pandas/pandas_cleaning.asp</p>
<p>https://www.w3schools.com/python/pandas/pandas_cleaning_empty_cells.asp</p>
