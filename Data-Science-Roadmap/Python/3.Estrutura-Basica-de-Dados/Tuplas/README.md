<h1 align="center">Tuplas</h1>
<p>Uma tupla é uma estrutura bastante similar a uma lista, com apenas uma diferença: os elementos inseridos em uma tupla não podem ser alterados, diferente de uma lista onde podem ser alterados livremente. Sendo assim, em um primeiro momento, podemos pensar em uma tupla como uma lista que não pode ser alterada, mas não é bem assim…</p>
<p>É certo que as tuplas possuem diversas características das listas, porém os usos são distintos. As listas são destinadas a serem sequências homogêneas, enquanto que as Tuplas são estruturas de dados heterogêneas.</p>
<p>Sendo assim, apesar de bastante similares, a tupla é utilizada para armazenar dados de tipos diferentes, enquanto que a lista é para dados do mesmo tipo.</p>
<h2 align="center">Tuplas x Listas</h2>
<p>As tuplas possuem algumas vantagens com relação às listas, que são:</p>
<ul>
  <li>Como as tuplas são imutáveis, a iteração sobre elas é mais rápida e, consequentemente, possuem um ganho de desempenho com relação às listas;</li>
  <li>Tuplas podem ser utilizadas como chave para um dicionário, já que seus elementos são imutáveis. Já com a lista, isso não é possível;</li>
  <li>Se for necessário armazenar dados que não serão alterados, utilize uma tupla. Isso garantirá que esses sejam protegidos de alterações posteriores.</li>
</ul>
<h2 align="center">Declarando Tuplas</h2>
<p>A sintaxe para criação de uma tupla, assim como uma lista, também é bem simples. Ao invés de se utilizar colchetes (listas), são utilizados parênteses, como podemos ver abaixo:</p>
<pre>
nome_da_tupla1 = (1, 2, 3) #tupla de inteiros
nome_da_tupla2 = (1, "olá", 1.5) #tupla heterogênea
</pre>
<h2 align="center">Contando Elementos em uma Tupla</h2>
<p>Para verificar a quantidade de elementos existentes em uma tupla, podemos utilizar o método <b>count()</b> e enviando o valor que queremos verificar como parâmetro:</p>
<pre>
nome_da_tupla1 = (1, 2, 3) #tupla de inteiros

print(nome_da_tupla1.count(1))
nome_da_tupla1 = (1, 1, 2, 3)
print(nome_da_tupla1.count(1))
</pre>
<p><b>Resultado:</b></p>
<pre>
1
2
</pre>
<h2 align="center">Exibir o Índice de um Determinado Elemento</h2>
<p>Para retornar o índice de um determinado elemento em uma tupla, utilizamos o método <b>index()</b>, enviando o valor que queremos pesquisar como parâmetro:</p>
<pre>
nome_da_tupla1 = (1, 2, 3) /#tupla de inteiros

print(nome_da_tupla1.index(3))
</pre>
<p><b>Resultado:</b></p>
<pre>
2
</pre>
<h2 align="center">Verificar a Existência de um Elemento na Tupla</h2>
<p>Um outro recurso muito utilizado em tuplas é a verificação da existência de um determinado elemento. Para isso, utilizamos o <b>in</b> do Python, como podemos ver abaixo:</p>
<pre>
nome_da_tupla1 = (1, 2, 3) /#tupla de inteiros

print(2 in nome_da_tupla1)
print(22 in nome_da_tupla1)
</pre>
<p><b>Resultado:</b></p>
<pre>
True
False
</pre>
<h2>Referências:</h2>
<p>https://www.treinaweb.com.br/blog/manipulando-tuplas-no-python/</p>
