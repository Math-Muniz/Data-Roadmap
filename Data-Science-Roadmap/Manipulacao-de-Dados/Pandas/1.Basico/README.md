<h1 align="center">Básico</h1>
<p>Vamos começar a estudar agora o Básico do Pandas.</p>
<h2 align="center">Pandas Series</h2>
<h3 align="center">O que é Series?</h3>
<p>A Pandas Series é como uma coluna em uma tabela.</p>
<p>É uma matriz unidimensional que armazena dados de qualquer tipo.</p>
<p><b>Exemplo:</b></p>
<p>Abaixo vamos criar uma Pandas Series simples apartir de uma lista:</p>
<pre>
import pandas as pd

a = [1, 7, 2]

myvar = pd.Series(a)

print(myvar)
</pre>
<h3 align="center">Labels</h3>
<p>Se nada mais for especificado, os valores serão rotulados com seu número de índice. O primeiro valor tem índice 0, o segundo valor tem índice 1, etc.</p>
<p>Este <b>label</b> pode ser usado para acessar um valor especificado.</p>
<p><b>Exemplo:</b></p>
<p>Abaixo vamos retornar o primeiro valor do Pandas Series que está no índice 0:</p>
<pre>
print(myvar[0])
</pre>
<h3 align="center">Criando Labels</h3>
<p>Com o argumento index, você pode nomear seus próprios labels.</p>
<p><b>Exemplo:</b></p>
<p>Criando nosso próprio label:</p>
<pre>
import pandas as pd

a = [1, 7, 2]

myvar = pd.Series(a, index = ["x", "y", "z"])

print(myvar)
</pre>
<p>Depois de criar labels, você pode acessar um item consultando o label.</p>
<p><b>Exemplo:</b></p>
<p>Retornaremos abaixo o valor de "y":</p>
<pre>
print(myvar["y"])
</pre>
<h3 align="center">Objetos Chave/Valores como Series</h3>
<p>Você também pode usar um objeto chave/valor, como um dicionário, ao criar uma Series.</p>
<p><b>Exemplo:</b></p>
<p>Abaixo vamos criar um Pandas Series simples a partir de um dicionário:</p>
<pre>
import pandas as pd

calories = {"day1": 420, "day2": 380, "day3": 390}

myvar = pd.Series(calories)

print(myvar)
</pre>
<p><b>Nota:</b> As chaves do dicionário viraram os labels.</p>
<p>Para selecionar apenas alguns itens do dicionário, use o argumento index e especifique apenas os itens que deseja incluir na Series.</p>
<p><b>Exemplo:</b></p>
<p>Crie uma Series usando apenas dados do "day1" e "day2":</p>
<pre>
import pandas as pd

calories = {"day1": 420, "day2": 380, "day3": 390}

myvar = pd.Series(calories, index = ["day1", "day2"])

print(myvar)
</pre>
<h3 align="center">DataFrames</h3>
<p>Os conjuntos de dados no Pandas são geralmente tabelas multidimensionais, chamadas DataFrames.</p>
<p>Series é como uma coluna, já um DataFrame é a tabela inteira.</p>
<p><b>Exemplo:</b></p>
<p>Criaremos um DataFrame apartir de duas Series:</p>
<pre>
import pandas as pd

data = {
  "calories": [420, 380, 390],
  "duration": [50, 40, 45]
}

myvar = pd.DataFrame(data)

print(myvar)
</pre>
<h2 align="center">Pandas DataFrames</h2>
<h3 align="center">O que é DataFrame?</h3>
<p>Um Pandas DataFrame é uma estrutura de dados bidimensional, como um array bidimensional ou uma tabela com linhas e colunas.</p>
<p><b>Exemplo:</b></p>
<p>Criaremos abaixo um Pandas DataFrame simples:</p>
<pre>
import pandas as pd

data = {
  "calories": [420, 380, 390],
  "duration": [50, 40, 45]
}

#load data into a DataFrame object:
df = pd.DataFrame(data)

print(df) 
</pre>
<p><b>Resultado:</b></p>
<pre>
    calories  duration
0       420        50
1       380        40
2       390        45
</pre>
<h2>Referencias</h2>
<p>https://www.w3schools.com/python/pandas/pandas_series.asp</p>
<p>https://www.w3schools.com/python/pandas/pandas_dataframes.asp</p>
