<h1 align="center">Listas</h1>
<p>Uma lista é a estrutura de dados mais básica do Python e armazena os dados em sequência, onde cada elemento possui sua posição na lista, denominada de índice. O primeiro elemento é sempre o índice zero e a cada elemento inserido na lista esse valor é incrementado.</p>
<p>No Python, uma lista pode armazenar qualquer tipo de dado primitivo (string, inteiro, float, etc).</p>
<h2 align="center">Declarando Listas</h2>
<p>A declaração de listas no Python é bem simples. Basicamente, devemos informar, entre colchetes ([]) o conteúdo da lista separados em vírgulas (,):</p>
<pre>
lista_simples_inteiro = [1, 2, 3, 8, 14, 4, 5]
listas_simples_string = ["Olá", "Mundo"]
lista_simples_mesclada = [1, 2, 3, "Olá, mundo", True, 1.5]
</pre>
<p>Nos exemplos acima, estamos declarando três listas com diferentes tipos de dados. Vale lembrar que uma lista pode conter diferentes tipos de dados, porém não é recomendado a utilização de uma lista para armazenar dados de diferentes tipos em uma mesma estrutura. Nestes casos, a Tupla é a estrutura de dados mais recomendada.</p>
<h2 align="center">Imprimindo Listas</h2>
<p>A impressão de listas no Python é muito simples. Basicamente, utilizamos o método <b>print()</b> e enviamos o nome da lista de queremos imprimir como parâmetro:</p>
<pre>
lista_simples_inteiro = [1, 2, 3, 8, 14, 4, 5]
listas_simples_string = ["Olá", "Mundo"]
lista_simples_mesclada = [1, 2, 3, "Olá, mundo", True, 1.5]

print(lista_simples_inteiro)
print(listas_simples_string)
print(lista_simples_mesclada)
</pre>
<p><b>Resultado:</b></p>
<pre>
[1, 2, 3, 8, 14, 4, 5]
['Olá', 'Mundo']
[1, 2, 3, 'Olá, mundo', True, 1.5]
</pre>
<h2 align="center">Inserindo Elementos na Lista</h2>
<p>A inserção de elementos em uma lista pode ser feito por dois métodos, o <b>append()</b> e o <b>insert()</b>. O método <b>append()</b> insere o elemento sempre no final da lista, já o <b>insert()</b> irá inserir o elemento em uma posição específica:</p>
<pre>
lista_simples_inteiro = [1, 2, 3, 8, 14, 4, 5]

print(lista_simples_inteiro)

/# Append()
lista_simples_inteiro.append(6)
print(lista_simples_inteiro)

/# Insert()
lista_simples_inteiro.insert(2, 100)
print(lista_simples_inteiro)
</pre>
<p><b>Resultado:</b></p>
<pre>
[1, 2, 3, 8, 14, 4, 5]
[1, 2, 3, 8, 14, 4, 5, 6]
[1, 2, 100, 8, 14, 4, 5, 6]
</pre>
<p>Pode-se notar que o método <b>append()</b> inseriu o valor 6 no final da lista, já o método insert() inseriu o elemento 100 na posição 2 da lista.</p>
<h2 align="center">Retornando Tamanho da Lista</h2>
<p>Para retornar o tamanho de uma lista no Python, podemos utilizar o método <b>len()</b> e passar a lista como parâmetro</p>
<pre>
lista_simples_inteiro = [1, 2, 3, 8, 14, 4, 5]

print(lista_simples_inteiro)

/# Len()
print(len(lista_simples_inteiro))
</pre>
<p><b>Resultado:</b></p>
<pre>
[1, 2, 3, 8, 14, 4, 5]
7
</pre>
<h2 align="center">Removendo Elementos na Lista</h2>
<p>Para remover elementos de uma lista, utilizamos o método remove(), passando o elemento que queremos excluir da lista como parâmetro</p>
<pre>
lista_simples_inteiro = [1, 2, 3, 8, 14, 4, 5]

print(lista_simples_inteiro)

/# Remove()
lista_simples_inteiro.remove(5)
print(lista_simples_inteiro)
</pre>
<p><b>Resultado:</b></p>
<pre>
[1, 2, 3, 8, 14, 4, 5]
[1, 2, 3, 8, 14, 4]
</pre>
<h2 align="center">Dividindo listas</h2>
<p>No Python, há duas formas de “cortar” listas. A primeira é utilizando os colchetes ([]) para determinar o intervalo do “corte” e a segunda é utilizando o método <b>slice()</b>, passando o intervalo como parâmetro:</p>
<pre>
lista_simples_inteiro = [1, 2, 3, 8, 14, 4, 5]

print(lista_simples_inteiro)

print(lista_simples_inteiro[0:4]) # Cortar lista da posição 0 a 4 (sem incluir a 4)
print(lista_simples_inteiro[1:]) # Cortar lista da posição 1 em diante
print(lista_simples_inteiro[:3]) # Cortar lista do início até a posição 3 (sem incluir a 3)
nova_lista = lista_simples_inteiro[:3] # Criar uma nova lista com base no corte de outra lista
print(nova_lista)

intervalo = slice(1, 4) # Cortar a lista a partir da posição 1 até a 4 (sem incluir a 4)
print(lista_simples_inteiro[intervalo])
</pre>
<p><b>Resultado:</b></p>
<pre>
[1, 2, 3, 8, 14, 4, 5]
[1, 2, 3, 8]
[1, 2, 8, 14, 4, 5]
[1, 2, 3]
[1, 2, 3]
[2, 3, 8]
</pre>
<p><b>Conclusão</b></p>
<p>As listas são uma ótima forma para armazenar elementos, como vimos neste artigo. Saber manipulá-las é fundamental para que possamos desenvolver nossos projetos e utilizar os melhores recursos da linguagem. Porém, no Python, as listas não são as únicas estruturas de dados existentes.</p>
<h2>Referências:</h2>
<p>https://www.treinaweb.com.br/blog/manipulando-listas-no-python/</p>
