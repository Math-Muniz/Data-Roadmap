<h1 align="center">Básico</h1>
<p>Vamos começar a estudar agora o Básico da nossa Biblioteca Pandas.</p>
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
<p>Um jeito simples de armazenar big data sets é usar arquivos CSV.(arquivos separados por vírgula)</p>
<p>Os arquivos CSV contêm texto simples e são um formato bem conhecido que pode ser lido por todos, incluindo Pandas.</p>
<p>Nos nossos exemplos iremos usar um arquivo CSV chamado 'data.csv'.</p>
<p>Download data.csv. ou Open data.csv</p>
<p><b>Exemplo:</b></p>
<p>Carregue o arquivo CSV em um DataFrame:</p>
<pre>
import pandas as pd

df = pd.read_csv('data.csv')

print(df.to_string())
</pre>
<p><b>Dica:</b> use to_string() para printar o DataFrame inteiro.</p>
<p>Se você tiver um DataFrame largo com diversas colunas, Pandas só vai te retornar as primeiras 5 linhas e as últimas 5 linhas:</p>
<p><b>Exemplo:</b></p>
<p>Dê print no DataFrame sem o método to_string():</p>
<pre>
import pandas as pd

df = pd.read_csv('data.csv')

print(df)
</pre>
<h3 align="center">Função max_rows</h3>
<p>O número de linhas retornadas é definido nas configurações de opções do Pandas.</p>
<p>Você pode verificar o número máximo de linhas do seu sistema com a instrução pd.options.display.max_rows.</p>
<p><b>Exemplo:</b></p>
<p>Abaixo vamos checar o número máximo de linhas retornadas:</p>
<pre>
import pandas as pd

print(pd.options.display.max_rows) 
</pre>
<p>No meu sistema o número é 60, o que significa que se o DataFrame contiver mais de 60 linhas, a instrução print(df) retornará apenas os cabeçalhos e as primeiras e últimas 5 linhas.</p>
<p>Você pode alterar o número máximo de linhas com a mesma instrução.</p>
<p><b>Exemplo:</b></p>
<p>Aumente o número máximo de linhas e mostre todo o DataFrame:<p>
<pre>
import pandas as pd

pd.options.display.max_rows = 9999

df = pd.read_csv('data.csv')

print(df)
</pre>
<h2 align="center">Leitura de JSON com Pandas</h2>
<h3 align="center">Leia Arquivos em JSON</h3>
<p>Big data sets são frequentemente armazenados ou extraídos como JSON.</p>
<p>JSON é texto simples, mas tem o formato de um objeto e é amplamente conhecido no mundo da programação, incluindo o Pandas.</p>
<p>Em nossos exemplos iremos usar um arquivo JSON chamado 'data.json'.</p>
<p><b>Exemplo:</b></p>
<p>Abaixo vamos carrregar um arquivo JSON em um DataFrame.</p>
<pre>
import pandas as pd

df = pd.read_json('data.json')

print(df.to_string())
</pre>
<p><b>Dica:</b> use to_string() para visualizar o DataFrame inteiro.</p>
<h3 align="center">Dicionário como formato JSON</h3>
<p><b>JSON = Dicionário Python</b></p>
<p>Os objetos JSON têm o mesmo formato que o dicionários em Python.</p>
<p>Se seu código JSON não está em um arquivo, mas em um dicionário Python, você pode carregá-lo diretamente em um DataFrame:</p>
<p><b>Exemplo:</b></p>
<p>Abaixo carregue um dicionário Python em um DataFrame:</p>
<pre>
import pandas as pd

data = {
  "Duration":{
    "0":60,
    "1":60,
    "2":60,
    "3":45,
    "4":45,
    "5":60
  },
  "Pulse":{
    "0":110,
    "1":117,
    "2":103,
    "3":109,
    "4":117,
    "5":102
  },
  "Maxpulse":{
    "0":130,
    "1":145,
    "2":135,
    "3":175,
    "4":148,
    "5":127
  },
  "Calories":{
    "0":409,
    "1":479,
    "2":340,
    "3":282,
    "4":406,
    "5":300
  }
}

df = pd.DataFrame(data)

print(df)
</pre>
<h2 align="center">Analisando DataFrames com Pandas</h2>
<h3 align="center">Visualizando os Dados</h3>
<p>Um dos métodos mais utilizados para obter uma rápida visão geral do DataFrame é o método head().</p>
<p>O método head() retorna os cabeçalhos e um número específico de linhas, começando do topo.</p>
<p><b>Exemplo:</b></p>
<p>Obtenha uma rápida visão geral imprimindo as primeiras 10 linhas do DataFrame:</p>
<pre>
import pandas as pd

df = pd.read_csv('data.csv')

print(df.head(10))
</pre>
<p>Em nossos exemplos abaixo estaremos usando um arquivo CSV chamado 'data.csv'</p>
<p>open <a href="https://www.w3schools.com/python/pandas/data.csv.txt">data.csv</a> in your browser</p>
<p><b></b></p>
<p><b></b></p>
<p></p>
<pre>

</pre>
<p></p>
<p></p>
<p><b></b></p>
<p></p>
<pre>

</pre>
<h3 align="center"></h3>
<p></p>
<p><b></b></p>
<p></p>
<pre>

</pre>
<p><b></b></p>
<pre>

</pre>
<h3 align="center"></h3>
<p></p>
<pre>

</pre>
<p></p>
<pre>

</pre>
<h3 align="center"></h3>
<p></p>
<p></p>
<p></p>
<h2>Referencias</h2>
<p>https://www.w3schools.com/python/pandas/pandas_series.asp</p>
<p>https://www.w3schools.com/python/pandas/pandas_dataframes.asp</p>
<p>https://www.w3schools.com/python/pandas/pandas_csv.asp</p>
<p>https://www.w3schools.com/python/pandas/pandas_json.asp</p>
<p>https://www.w3schools.com/python/pandas/pandas_analyzing.asp</p>
