<h1 align="center">Pandas</h1>
<h2 align="center">O que é Pandas?</h2>
<p>Pandas é uma biblioteca do Python usada para trabalhar com Datasets.</p>
<p>Ele tem funções para <b>Analizar, Limpar, Explorar e Manipular Dados.</b></p>
<p>O nome "Pandas" é uma referência a duas coisas "Panel Data", e "Python Data Analysis" sendo criado por Wes McKinney em 2008.</p>
<h2 align="center">Por que usar Pandas?</h2>
<p>Pandas permite que a gente análise Big Data e faça conclusões baseadas em Teorias Estatísticas.</p>
<p>O Pandas pode limpar conjuntos de dados bagunçados e torná-los legíveis e relevantes.</p>
<p>Dados Relevantes são muito importantes em Ciência de Dados.</p>
<pre>
  <p><b>Ciência de Dados:</b> é um ramo da Ciência da Computação onde estudamos como armazenar, utilizar e analisar dados para obter informações a partir deles.</p>
</pre>
<h2 align="center">O que o Pandas pode fazer?</h2>
<p>Pandas te dá respostas sobre dados. Como:</p>
<ul>
  <li>Existe uma correlação entre duas ou mais colunas?</li>
  <li>Qual é o valor Médio?</li>
  <li>Qual é o valor Máximo?</li>
  <li>Qual é o valor Mínimo?</li>
</ul>
<p>Pandas também consegue deletar linhas e colunas que não são relevantes, ou que contenham valores errados, como dados vazios ou nulos. Isso é chamado de Limpeza de Dados.</p>
<h2 align="center">O que o Pandas pode fazer?</h2>
<p>O código fonte do Pandas está localizado neste repositório do github https://github.com/pandas-dev/pandas</p>
<h2 align="center">Cheat Sheet</h2>
<p>Neste link do Github coloquei uma Cheat Sheet (Folha de Truques) sobre a biblioteca Pandas: https://github.com/Math-Muniz/Data-Roadmap/blob/main/Data-Science-Roadmap/Manipulacao-de-Dados/Pandas/Pandas_Cheat_Sheet.pdf</p>
<h1 align="center">Iniciando com o Pandas</h1>
<h2 align="center">Instalação do Pandas</h2>
<p>Se você tiver o Python e o PIP instalados no seu sistema, então a instalação do Pandas é bem fácil.</p>
<p>Instale usando o comando abaixo:</p>
<pre>
C:\Users\Your Name>pip install pandas
</pre>
<p>ou:</p>
<pre>
pip install pandas
</pre>
<p>Se este comando falhar, então tente usar uma distribuição do python que já tenha o Pandas instalado como: Anaconda, Spyder, etc...</p>
<h2 align="center">Import do Pandas</h2>
<p>Uma vez que o Pandas for instalado, import isso em suas aplicaçoes adicionado a palavra-chave import:</p>
<pre>
import pandas
</pre>
<p>Agora o Pandas está pronto para uso.</p>
<p><b>Exemplo:</b></p>
<pre>
import pandas

mydataset = {
&emsp;'cars': ["BMW", "Volvo", "Ford"],
&emsp;'passings': [3, 7, 2]
}

myvar = pandas.DataFrame(mydataset)

print(myvar)
</pre>
<h2 align="center">Pandas as pd</h2>
<p>Pandas é geralmente importado usando o alias pd.</p>
<pre>
<b>Alias:</b> No Python o alias são nomes alternativos para se referir a mesma coisa.
</pre>
<p>Crie um alias com a plavra-chave enquanto estiver importando a biblioteca:</p>
<pre>
import pandas as pd
</pre>
<p>Agora o pacote Pandas pode ser referenciado por pd em vez de pandas.</p>
<p><b>Exemplo:</b></p>
<pre>
import pandas as pd

mydataset = {
&emsp;'cars': ["BMW", "Volvo", "Ford"],
&emsp;'passings': [3, 7, 2]
}

myvar = pd.DataFrame(mydataset)

print(myvar)
</pre>
<p>Perceba no código acima que usei "pd.DataFrame(mydataset)" em vez de "pandas.DataFrame(mydataset)" isso tudo por causa do nosso alias.</p>
<h2 align="center">Checando a Versão do Pandas</h2>
<p>A string de versão é armazenada no atributo __version__.</p>
<p><b>Exemplo:</b></p>
<pre>
import pandas as pd

print(pd.__version__)
</pre>
<h2 align="center">Refêrencias</h2>
<p>https://www.w3schools.com/python/pandas/pandas_intro.asp</p>
<p>https://www.w3schools.com/python/pandas/pandas_getting_started.asp</p>
