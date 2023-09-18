<h1 align="center">Sets</h1>
<p>Os sets são uma coleção de itens desordenada, parcialmente imutável e que não podem conter elementos duplicados. Por ser parcialmente imutável, os sets possuem permissão de adição e remoção de elementos.</p>
<p>Além disso, os sets são utilizados, normalmente, com operações matemáticas de união, interseção e diferença simétrica, conforme veremos nos próximos tópicos.</p>
<p>Neste artigo, veremos como manipular os sets com os principais métodos disponibilizados pela API de Collections do Python.</p>
<h2 align="center">Declarando Sets</h2>
<p>Para declarar um set no Python é bem simples. Seus elementos devem estar entre chaves ({}) ou utilizando o método <b>set()</b> do próprio Python, como podemos ver abaixo:</p>
<pre>
 # Declaração de um set
meu_set = {1, 2, 3, 4, 1}
print(type(meu_set))

meu_set_2 = set([1, 2, 8, 9, 10])
print(type(meu_set_2))
</pre>
<p>O código acima, criará dois sets, o primeiro utilizando as chaves ({}) e separando os elementos por vírgula (,) e o segundo utilizando o método set(). As duas formas terão o mesmo resultado:</p>
<pre>
(class 'set')
(class 'set')
</pre>
<h2 align="center">Adicionando, Atualizando e Removendo Elementos dos Sets</h2>
<p>Os sets permitem as operações de adição, atualização e remoção de elementos. Para isso, existe um método para cada funcionalidade, como podemos ver abaixo:</p>
<pre>
meu_set = {1, 2, 3, 4, 1}

meu_set.add(2) # Adicionando elementos
print("Adição", meu_set)

meu_set.update([3, 4, 5, 6]) # Atualizando set
print("Atualição", meu_set)

meu_set.discard(2) # Atualizando set
print("Remoção", meu_set)
</pre>
<p>Como podemos ver no trecho de código acima, o método <b>add()</b> é responsável por adicionar um elemento ao set, desde que ele já não esteja adicionado, pois os sets não permitem elementos duplicados.</p>
<p>Já o método <b>update()</b> permite atualizar os sets e adicionar os elementos (que não estejam duplicados) em sua estrutura.</p>
<p>Por fim, o método <b>discard()</b> permite a remoção de um elemento do set.</p>
<p><b>Resultado:</b></p>
<pre>
Adição {1, 2, 3, 4}
Atualização {1, 2, 3, 4, 5, 6}
Remoção {1, 3, 4, 5, 6}
</pre>
<h2 align="center">Operações Matemáticas com Sets</h2>
<p>Os sets, além das operações de manipulação vistas anteriormente, permitem operações matemáticas como união, interseção, diferença e diferença simétrica, conforme veremos abaixo.</p>
<pre>
meu_set = {1, 2, 3, 4, 1}
meu_set_2 = set([1, 2, 8, 9, 10])

print("União")
print(meu_set | meu_set_2) # União
print(meu_set.union(meu_set_2))

print("Interseção")
print(meu_set & meu_set_2) # Interseção
print(meu_set.intersection(meu_set_2))

print("Diferença")
print(meu_set - meu_set_2) # Diferença
print(meu_set.difference(meu_set_2))

print("Diferença Simétrica")
print(meu_set ^ meu_set_2) # Diferença Simétrica
print(meu_set.symmetric_difference(meu_set_2))
</pre>
<p><b>Resultado:</b></p>
<pre>
União
{1, 2, 3, 4, 8, 9, 10}
{1, 2, 3, 4, 8, 9, 10}
Interseção
{1, 2}
{1, 2}
Diferença
{3, 4}
{3, 4}
Diferença Simétrica
{3, 4, 8, 9, 10}
{3, 4, 8, 9, 10}
</pre>
<p>Na união ( | ), todos os elementos dos dois sets serão “unidos” em um, formando um único set com todos os elementos, sem repetí-los, claro.</p>
<p>Na Interseção ( & ), apenas os elementos que estiverem nos dois sets restarão.</p>
<p>Já na diferença ( - ), restarão apenas os elementos que estiverem em um dos set, mas não no segundo.</p>
<p>Por fim, na diferença simétrica ( ^ ), apenas os elementos que estiverem nos dois sets, porém que não se repitam, serão exibidos.</p>
