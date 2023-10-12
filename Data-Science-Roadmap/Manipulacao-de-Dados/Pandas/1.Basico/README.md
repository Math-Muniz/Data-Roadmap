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
<h3 align="center">Localização de Linhas</h3>
<p>Como você pode ver no resultado acima, o DataFrame é como uma tabela com linhas e colunas.</p>
<p>Pandas usam o atributo <b>loc</b> para retornar uma ou mais linhas especificadas</p>
<p><b>Exemplo:</b></p>
<p>Retornaremos a linha 0 abaixo:</p>
<pre>
#se refere a linha do indice:
print(df.loc[0])
</pre>
<p><b>Resultado:</b></p>
<pre>
calories    420
duration     50
Name: 0, dtype: int64
</pre>
<p><b>Nota:</b> Esse exemplo retorna uma Series do Pandas.</p>
<p><b>Exemplo:</b></p>
<p>Retorna a linha 0 e 1:</p>
<pre>
#Use uma lista de indices:
print(df.loc[[0, 1]])
</pre>
<p><b>Resultado:</b></p>
<pre>
    calories  duration
0       420        50
1       380        40
</pre>
<p><b>Nota:</b> Quando usamos [], o resultado é um Pandas DataFrame.</p>
<h3 align="center">Índices Nomeados</h3>
<p>Com o argumento index, você pode nomear seus próprios índices.</p>
<p><b>Exemplo:</b></p>
<p>Adicione uma lista de nomes para dar um nome a cada linha abaixo:</p>
<pre>
import pandas as pd

data = {
  "calories": [420, 380, 390],
  "duration": [50, 40, 45]
}

df = pd.DataFrame(data, index = ["day1", "day2", "day3"])

print(df)
</pre>
<p><b>Resultado:</b></p>
<pre>
      calories  duration
day1       420        50
day2       380        40
day3       390        45
</pre>
<h3 align="center">Localização de Índices Nomeados</h3>
<p>Use o índice nomeado no atributo <b>loc</b> para retornar as linhas especificadas.</p>
<p><b>Exemplo:</b></p>
<p>Retorne abaixo o "day2":</p>
<pre>
#refere-se ao índice nomeado:
print(df.loc["day2"])
</pre>
<p><b>Resultado:</b></p>
<pre>
calories    380
duration     40
Name: day2, dtype: int64
</pre>
<h3 align="center">Carregar arquivos em um DataFrame</h3>
<p>Se seus conjuntos de dados estiverem armazenados em um arquivo, o Pandas poderá carregá-los em um DataFrame.</p>
<p><b>Exemplo:</b></p>
<p>Carregue um arquivo separado por vírgula (arquivo CSV) em um DataFrame:</p>
<pre>
import pandas as pd

df = pd.read_csv('data.csv')

print(df) 
</pre>
<h2 align="center">Leitura de CSV com Pandas</h2>
<h3 align="center">Leia Arquivos em CSV</h3>
<h2>Referencias</h2>
<p>https://www.w3schools.com/python/pandas/pandas_series.asp</p>
<p>https://www.w3schools.com/python/pandas/pandas_dataframes.asp</p>
<p>https://www.w3schools.com/python/pandas/pandas_csv.asp</p>
<p>https://www.w3schools.com/python/pandas/pandas_json.asp</p>
<p>https://www.w3schools.com/python/pandas/pandas_analyzing.asp</p>
