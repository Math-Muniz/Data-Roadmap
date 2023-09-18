<h1 align="center"></h1>
<p>No Python, os dicionários são coleções de itens desordenados com uma diferença bem grande quando comparados às outras coleções (lists, sets, tuples, etc): um elemento dentro de um dicionário possui uma chave atrelada a ele, uma espécie de identificador. Sendo assim, é muito utilizado quando queremos armazenar dados de forma organizada e que possuem identificação única (como acontece em bancos de dados).</p>
<p>Um dicionário, portanto, pode ser visto como a figura abaixo:</p>
<img src="Dicionario.png">
<p>Onde cada valor é “atrelado” à uma chave, seu identificador. Vale lembrar que, por necessitar que cada valor possua uma chave relacionada a ele, as chaves dos dicionários devem ser únicas para que possam ser acessadas, também, através do seu índice.</p>
<p>As chaves também não são armazenadas em qualquer ordem, elas apenas são associadas aos valores que pertencem.</p>
<h2 align="center">Declarando Dicionários</h2>
<p>Existem duas formas de se criar um dicionário utilizando o Python. A primeira delas é utilizando chaves ( {} ) e separando os elementos das chaves com dois pontos ( : ) e os outros elementos por vírgula ( , ):</p>
<pre>
nome_do_dicionario = {1: ‘João’, 2: ‘José’}
nome_do_dicionario = {‘nome’: ‘João’, ‘sobrenome’: ‘Silva’}
</pre>
<p>A segunda forma é utilizando o método dict() com o dicionário sendo passado como parâmetro:</p>
<pre>
nome_do_dicionario = dict({1: ‘João’, 2: ‘José’})
nome_do_dicionario = dict({‘nome’: ‘João’, ‘sobrenome’: ‘Silva’})
</pre>
<p>O código acima, criará dois dicionários, o primeiro utilizando as chaves ({}) e separando os elementos das suas chaves com dois pontos (:) e o segundo utilizando o método <b>dict()</b>. As duas formas terão o mesmo resultado:</p>
<p><b>Resultado:</b></p>
<pre>
(class 'dict')
(class 'dict')
</pre>
<h2 align="center">Retornando Elementos pelo Índice</h2>
<p>Para retornar um elemento pelo seu índice de um dicionário, há duas formas. A primeira é passando, entre colchetes ([]) o índice do elemento desejado. Já a segunda é utilizando o método <b>get()</b> com a posição do elemento como parâmetro:</p>
<pre>
meu_dicionario = {1 : 'Fabio', 2 : 'Maria', 3 : 'João', 4 : 'José'}

#get()
print(meu_dicionario[2])
print(meu_dicionario.get(4))
</pre>
<p><b>Resultado:</b></p>
<pre>
Maria
José
</pre>
<h2 align="center">Retornando o Tamanho de um Dicionário</h2>
<p>Para retornar o tamanho de um dicionário, podemos utilizar o método <b>len()</b> e passar o dicionário a ser analisado como parâmetro:</p>
<pre>
meu_dicionario = {1 : 'Fabio', 2 : 'Maria', 3 : 'João', 4 : 'José'}

#len()
print(len(meu_dicionario))
</pre>
<p><b>Resultado:</b></p>
<pre>
4
</pre>
<h2 align="center">Adicionando Elementos em um Dicionário</h2>
<p>Para inserir novos elementos em um dicionário, existem duas formas. A primeira é passar o valor ao índice de um dicionário e a segunda é utilizando o método <b>update()</b>, passando como parâmetro a chave e o elemento a ser adicionado:</p>
<pre>
meu_dicionario = {1 : 'Fabio', 2 : 'Maria', 3 : 'João', 4 : 'José'}

meu_dicionario[5] = 'Joaquina'
print(meu_dicionario)

meu_dicionario.update({6: 'Pedro'})
print(meu_dicionario)
</pre>
<p><b>Resultado:</b></p>
<pre>
{1: 'Fabio', 2: 'Maria', 3: 'João', 4: 'José', 5: 'Joaquina'}
{1: 'Fabio', 2: 'Maria', 3: 'João', 4: 'José', 5: 'Joaquina', 6: 'Pedro'}
</pre>
<h2 align="center">Removendo elementos de um dicionário</h2>
<p>Para remover elementos de um dicionário utilizamos o método <b>pop()</b> seguido do índice do elemento que deve ser removido. Isso fará com que o elemento seja removido, como podemos ver no código abaixo:</p>
<pre>
meu_dicionario = {1 : 'Fabio', 2 : 'Maria', 3 : 'João', 4 : 'José'}

#pop()
meu_dicionario.pop(2)
print(meu_dicionario)
</pre>
<p><b>Resultado:</b></p>
<pre>
{1: 'Fabio', 3: 'João', 4: 'José'}
</pre>
<p><b>Conclusão</b></p>
<p>Os dicionários provêem uma ótima forma para armazenar dados organizados e com um padrão simples de entender, como vimos neste artigo. Saber manipulá-los é fundamental para utilizá-los em nossos projetos.</p>
<h2>Referências:</h2>
<p>https://www.treinaweb.com.br/blog/manipulando-dicionarios-no-python/</p>
