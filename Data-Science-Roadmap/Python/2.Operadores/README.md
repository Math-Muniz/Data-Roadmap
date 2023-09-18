<h1>Operadores</h1>
<p>Os operadores são usados na construção de expressões, as quais contém um número variado de operandos. Por exemplo, na expressão a + b, temos o operador de aritmético + e operandos são as variáveis a e b.</p>
<p>Na linguagem Python temos a seguinte separação entre os diferentes tipos de operadores:</p>
<ul>
  <li>Operadores Aritméticos</li>
  <li>Operadores de Atribuição</li>
  <li>Operadores de Comparação</li>
  <li>Operadores Lógicos</li>
  <li>Operadores de Identidade</li>
  <li>Operadores de associação</li>
</ul>
<p>A seguir veremos cada um deles.</p>
<p><b>Operadores Aritméticos</b></p>
<p>Os operadores aritméticos são utilizados na execução de operações matemáticas, tais como a soma e a subtração, por exemplo. Vejamos na <b>Tabela 1</b> a lista deles.</p>
<img src="Operadores-Aritmeticos.png">
<p>O <b>Código 1</b> mostra um exemplo com os operadores aritméticos usados no Python.</p>
<pre>
numero_1 = 5
numero_2 = 2

soma = numero_1 + numero_2
subtracao = numero_1 - numero_2
multiplicacao = numero_1 * numero_2
divisao = numero_1 / numero_2
divisao_inteira = numero_1 // numero_2
modulo = numero_1 % numero_2
exponenciacao = numero_1 ** numero_2

print(soma) # 7
print(subtracao) # 3
print(multiplicacao)  # 10
print(divisao) # 2.5
print(divisao_inteira) # 2
print(modulo)  # 1
print(exponenciacao) # 25
</pre>
<p>Uma característica importante a ser observada quando falamos dos operadores matemáticos é a precedência. Essa característica é relativa à ordem da execução deles e acontece quando mais de um operador está presente numa expressão. Segue a precedência dos operadores no Python.</p>
<p>1. As expressões contidas em parênteses têm a precedência maior na linguagem Python. Isso permite que uma expressão execute antes de outra. Ex.:</p>
<pre>print((2 + 5) * 3) # O resultado será 21</pre>
<p>2. Após os parênteses, o próximo operador com maior precedência é o de exponenciação. Ex.:</p>
<pre>print( 1 + 5**2 ) # O resultado será 26</pre>
<p>3. Multiplicação e divisão têm precedência sobre a adição e subtração: como já é conhecido na matemática, divisão e multiplicação são executadas antes das operações de adição e subtração. Ex.:</p>
<pre>print(5 * 3 + 8) # O resultado será 23</pre>
<p>4. Ordem de precedência é avaliada da esquerda para a direita. Portanto, após os operadores anteriores, a sequência da execução será da esquerda para a direita. Ex.:</p>
<pre>print(8 + 5 - 10) # O resultado será 3</pre>
<p><b>Operadores de Atribuição</b></p>
<p>Os operadores de atribuição atribuem valor a uma variável. Na <b>Tabela 2</b> temos uma lista desses operadores.</p>
<img src="Operadores-Atribuicao.png">
<p>No <b>Código 2</b> temos um exemplo do uso de operadores de atribuição.</p>
<pre>numero_1 = 5

numero_1 += 5

print(numero_1) # O resultado será 10</pre>
<p>Acima, vemos que a variável numero_1 recebe na linha 3 o valor dela mesmo somado a 5. Isso fará com que o resultado impresso na linha 5 seja igual a 10.</p>
<p><b>Operadores de Comparação</b></p>
<p>Os operadores de comparação são usados para comparar valores, o que vai retornar True ou False, dependendo da condição. A seguir, na <b>Tabela 3</b> temos exemplos de alguns usados no Python.</p>
<img src="Operadores-Comparacao.png">
<p>Usando a comparação que é feita com esses operadores, podemos criar condições para os códigos. No exemplo abaixo, vemos como isso acontece na prática:</p>
<pre>numero_1 = 2
numero_2 = 4

soma = numero_1 + numero_2

if soma < 10:
    print("soma não é maior que 10")
else:
    print("soma é maior ou igual a 10")</pre>
<p>Como podemos ver no <b>Código 3</b>, duas variáveis são somadas e esse resultado é atribuído à variável soma. Na linha 6, fazemos uma comparação dessa variável verificando se ela é menor do que 10. Vejamos a seguir, uma operação que faz comparação de igualdade entre duas variáveis:</p>
<pre>soma_1 = 7 + 8
soma_2 = 10 + 5

if soma_1 == soma_2:
    print("Os resultados são iguais")
else:
    print("Os resultados são diferentes")</pre>
<p>No <b>Código 4</b>, criamos duas variáveis e comparamos seus valores, o que pode resultar em dois resultados distintos. Dessa forma, podemos criar estruturas condicionais com o auxílio desses operadores.</p>
<p><b>Operadores Lógicos</b></p>
<h2>Referências</h2>
<p>https://www.devmedia.com.br/operadores-no-python/40693</p>
