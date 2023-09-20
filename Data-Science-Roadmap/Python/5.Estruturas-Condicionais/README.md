<h1 align="center">Estruturas Condicionais</h1>
<p>Uma estrutura condicional na linguagem Python, como a Python <b>If Else</b>, corresponde a um bloco de código que é iniciado com uma expressão para avaliar se uma determinada condição é verdadeira ou falsa. Com ele, podemos testar se uma variável é igual a zero, por exemplo. O resultado dessa verificação é determinante para a execução das instruções seguintes presentes no escopo da estrutura.</p>
<p>Na prática, será executado uma ou mais instruções se a condição for verdadeira, ou outro bloco de código caso o resultado seja falso. As pessoas programadoras precisam entender como essa estrutura funciona, pois ela é muito utilizada no desenvolvimento de aplicações</p>
<h2 align="center">O que é a estrutura condicional if-else em Python?</h2>
<p>Uma estrutura condicional é aquela que faz uma verificação em uma determinada expressão para identificar se ela atende à condição especificada. A partir do resultado, uma ou mais instruções são executadas. Confira as possibilidades desse comando em Python.</p>
<h2 align="center">If em Python</h2>
<p>Utilizamos o comando <b>if</b> para verificar uma expressão e executar um bloco de código caso a condição definida seja verdadeira. É importante dizer que a instrução <b>if</b> pode ser utilizada sozinha, ou seja, apenas para executar algo se a condição for verdadeira. Observe que devemos utilizar o caractere dois pontos “:” ao final da instrução.</p>
<pre>
if (expressão_for_verdadeira):
 &emsp;&emsp;executar_bloco_de_codigo()
</pre>
<h2 align="center">Else em Python</h2>
<p>O comando <b>else</b> é utilizado para executar um bloco de código, caso o resultado da expressão informada na instrução <b>if</b> seja falso. Vale ressaltar que a instrução <b>else</b> só pode ser utilizada em conjunto com o <b>if</b>. Perceba que também precisamos utilizar o caractere dois pontos após a expressão da instrução <b>if</b> e após o <b>else</b>.</p>
<pre>
if (expressão_for_verdadeira):
&emsp;&emsp;executar_primeiro_bloco_de_codigo()
else:
&emsp;&emsp;executar_segundo_bloco_de_codigo()
</pre>
<h2 align="center">Elif em Python.</h2>
<p>O comando <b>elif</b> é utilizado quando queremos realizar a verificação de outra expressão caso a primeira validação seja falsa.</p>
<pre>
if (expressão_for_verdadeira):
&emsp;&emsp;executar_primeiro_bloco_de_codigo()
elseif (segunda_expressão_for_verdadeira):
&emsp;&emsp;executar_segundo_bloco_de_codigo()
</pre>
<h2 align="center">Como usar as estruturas condicionais em Python: if, elif e else?</h2>
<p>Agora que vimos o que faz cada parte da estrutura condicional Python <b>if</b>, vamos demonstrar como implementá-la. </p>
<h2 align="center">if/else</h2>
<p>No código fonte abaixo, solicitamos que a pessoa usuária informe um valor numérico inteiro entre 0 e 100 e verificamos se ele é maior que 50. Caso o resultado seja verdadeiro, exibimos uma mensagem na tela e se for negativo, exibimos outro tipo de mensagem.</p>
<pre>
a = int(input("Informe um número entre 0 e 100: "))
if a >= 50:
&emsp;&emsp;print ("O número ", a, " é maior ou igual a 50")
else:
&emsp;&emsp;print ("O número ", a, " é menor que 50")
</pre>
<h2 align="center">if/elif/else</h2>
<p>Vamos melhorar um pouco mais o código acima para exibir uma mensagem mais apropriada, caso o valor informado seja igual a 50.</p>
<pre>
a = int(input("Informe um número entre 0 e 100: "))
if a > 50:
&emsp;&emsp;print ("O número ", a, " é maior que 50")
elif a == 50:
&emsp;&emsp;print ("O número informado é igual a 50")
else:
&emsp;&emsp;print ("O número ", a, " é menor que 50")
</pre>
<p>Perceba que utilizamos o <b>elif</b> para verificar se o valor informado é igual a 50. Depois usamos o comando Python <b>else</b> para atender à condição em que o valor é menor que 50 e exibir a mensagem correspondente na tela.</p>
<h2 align="center">Como utilizar as condições lógicas?</h2>
<p>Todas as expressões utilizadas no comando <b>if/else</b> são testadas por meio de condições lógicas semelhantes às expressões matemáticas. Elas fazem a comparação entre duas variáveis ou expressões. Confira quais os operadores podem ser utilizados nesse momento.</p>
<h2 align="center">Igual</h2>
<p>É utilizado para comparar duas variáveis ou expressões e é representado pelo sinal de igual duas vezes “==”.</p>
<pre>
a = 10
if a == 10:
&emsp;&emsp;print("Verdadeiro")
else:
&emsp;&emsp;print("Falso")
#Resultado: Verdadeiro
</pre>
<h2 align="center">Não igual</h2>
<p>A verificação de diferença entre dois termos é feita com a utilização dos símbolos de exclamação e igual “!=”.</p>
<pre>
a = 10
if a != 10:
&emsp;&emsp;print("Verdadeiro")
else:
&emsp;&emsp;print("Falso")
#Resultado: Falso
</pre>
<h2 align="center">Menor que</h2>
<p>O operador menor “<” é utilizado para indicar verificar se o primeiro termo é menor que o segundo.</p>
<pre>
a = 10
b = 20
if a < b:
&emsp;&emsp;print("Verdadeiro")
else:
&emsp;&emsp;print("Falso")
#Resultado: Verdadeiro
</pre>
<h2 align="center">Menor ou igual</h2>
<p>O operador menor ou igual “<=” é utilizado para realizar essa comparação entre o primeiro e o segundo termo.</p>
<pre>
a = 10
b = 10
if a <= b:
&emsp;&emsp;print("Verdadeiro")
else:
&emsp;&emsp;print("Falso")
#Resultado: Verdadeiro
</pre>
<h2 align="center">Maior que</h2>
<p>O operador maior “>” é utilizado para verificar se o primeiro termo é maior que o segundo.</p>
<pre>
a = 10
b = 20
if a > b:
&emsp;&emsp;print("Verdadeiro")
else:
&emsp;&emsp;print("Falso")
#Resultado: Falso
</pre>
<h2 align="center">Maior ou igual</h2>
<p>O operador maior ou igual “>=” é utilizado para realizar essa verificação entre o primeiro e o segundo termo.</p>
<pre>
a = 10
b = 10
if a >= b:
&emsp;&emsp;print("Verdadeiro")
else:
&emsp;&emsp;print("Falso")
#Resultado: Verdadeiro
</pre>
<h2 align="center">Qual a importância da indentação?</h2>
<p>Uma das características importantes da linguagem Python é a indentação. <b>Perceba que na estrutura condicional Python if e else não utilizamos os caracteres chaves “{ … }”</b> para delimitar o bloco como acontece em outras linguagens de programação. Isso porque o que determina o escopo é a indentação. Por esse motivo, é preciso atenção para respeitar essa característica.</p>
<p>Outro cuidado é em relação à quantidade de espaços para fazer a indentação, que deve ser a de quatro caracteres de espaço em branco. <b>Vale ressaltar que se a indentação não for feita corretamente, o compilador entenderá a instrução como parte de fora do bloco de código, o que resultará em falhas no programa.</b></p>
<h2 align="center">Combinando estruturas condicionais: and</h2>
<p>Também podemos avaliar duas ou mais expressões por meio do operador lógico <b>and</b>. Na prática, para que a condição do <b>if</b> seja verdadeira, é preciso que as duas expressões sejam verdadeiras. Veja um código de exemplo:</p>
<pre>
a = 6
if (a <= 10) and ((a % 2) == 0):
&emsp;&emsp;print("O valor", a, "é menor ou igual a 10 e é um número par.")
else:
&emsp;&emsp;print("O valor", a , "não é menor que 10 ou não é par")
# Resultado: O valor 6 é menor ou igual a 10 e é um número par.
</pre>
<p>Perceba que a expressão do comando <b>if</b> é formada por duas outras expressões. Portanto, para que a condição seja verdadeira, é preciso que o valor da variável a seja menor ou igual a 10 e que, ao dividir esse valor por 2, o resultado seja 0, o que indica um número par.</p>
<h2 align="center">Definindo condições separadas: or</h2>
<p>O operador lógico <b>or</b> é utilizado para indicar que, se uma das condições for verdadeira, a expressão toda será verdadeira. Veja um algoritmo de exemplo:</p>
<pre>
a = 12
if (a <= 10) or ((a % 2) == 0):
&emsp;&emsp;print("O valor", a, "é menor ou igual a 10 ou é um número par.")
else:
&emsp;&emsp;print("O valor", a , "não é menor que 10 ou não é par")
# Resultado: O valor 12 é menor ou igual a 10 ou é um número par.
</pre>
<p>Para que a condição do <b>if</b> seja verdadeira no código acima, o valor da variável a dever ser menor ou igual a 10 ou divisível por 2.</p>
<h2 align="center">Usando um If dentro do outro: If aninhado</h2>
<p>O if aninhado é utilizado quando queremos fazer outra verificação após uma determinada condição ser verdadeira. Veja um exemplo:</p>
<pre>
a = 9
if a <= 10:
&emsp;&emsp;if (a % 2) == 0:
&emsp;&emsp;&emsp;&emsp;print("O valor", a, "é menor ou igual a 10 e é um número par.")
&emsp;&emsp;else:
&emsp;&emsp;&emsp;&emsp;print("O valor", a, "é menor ou igual a 10 e é um número ímpar.")
else:
&emsp;&emsp;print("O valor", a , "é maior que 10")
# Resultado: O valor 9 é menor ou igual a 10 e é um número ímpar.
</pre>
<p>No código acima, fizemos a validação para verificarmos se a variável a é menor ou igual a 10. Se a condição for verdadeira, será feito outro teste para verificarmos se o número é par ou ímpar e exibiremos a mensagem correspondente na tela.</p>
<h2 align="center">Executando um If sem conteúdo: pass</h2>
<p>Outra forma de utilizar o comando <b>if</b> é para testar uma determinada condição e não realizar nenhuma ação se ela for verdadeira. O objetivo é evitar que ocorra uma falha no programa. Para isso, utilizamos a declaração <b>pass</b>. Veja um exemplo:</p>
<pre>
a = 10
if a <= 10:
&emsp;&emsp;pass
# Resultado: Nenhuma ação será executada.
</pre>
<p>O comando Python <b>if/else</b> é uma estrutura condicional utilizada para executar um bloco de código se uma determinada condição for verdadeira e executar outro conjunto de instruções caso ela seja falsa. Além disso, ela contém outros recursos para ajudar a construção da lógica do programa, como a possibilidade de utilização de ifs aninhados, o comando elif e a declaração pass.</p>
<h2 align="center">List Comprehensions com if</h2>
<p>Outro lugar onde podemos utilizar as Estruturas Condicionais são nas chamadas List Comprehensions do Python.</p>
<p>Suponha que te peçam para: <b>escrever um código que retorne apenas os números pares de uma sequência de 0 a 10.</b></p>
<p>Veja como isto poderia ser feito em apenas 1 linha de código!</p>
<pre>
list_comp = [numero for numero in range(0, 11) if numero % 2 == 0]
</pre>
<p><b>Resultado:</b></p>
<pre>
[0, 2, 4, 6, 8, 10]
</pre>
<p>Esse é o poder das Estruturas de Repetição em conjunto com as Estruturas Condicionais e ainda List Comprehensions</p>
<h2>Referências</h2>
<p>https://blog.betrybe.com/python/if-else/#:~:text=Uma%20estrutura%20condicional%20na%20linguagem,igual%20a%20zero%2C%20por%20exemplo.</p>
<p>https://pythonacademy.com.br/blog/estruturas-condicionais-no-python</p>
