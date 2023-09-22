<h1 align="center">Tratamento de Erros e Exceções</h1>
<p>Em Python, a execução de um programa é sempre encerrada quando se depara com um erro durante sua execução.</p>
<p>Um erro pode ser tanto de sintaxe<b>(Syntax error)</b> quanto uma exceção.</p>
<h2 align="center">Diferença entre Erro de Sintaxe e Exceção</h2>
<p>Um erro de sintaxe(Syntax error) é um erro na escrita do código, esse tipo de erro é fácil de ser detectado, pois a maioria das IDE modernas já avisam ao programador que o código está incorreto.</p>
<p>Abaixo temos um exemplo de um erro de sintaxe:</p>
<pre>
def dividir(a, b):    
&emsp;&emsp;return a b  
 
dividir(2, 10)
</pre>
<p>No exemplo acima o programador esqueceu de colocar o operador de divisão / entre as variáveis a e b, dessa forma, caso esse código seja executado o seguinte erro será exibido no terminal:</p>
<pre>
File "teste.py", line 2 return a b ^SyntaxError: invalid syntax  
</pre>
<p>A seta indica onde o analisador encontrou o erro de sintaxe.</p>
<p>Neste exemplo basta adicionar o operador de divisão / entre a e b e o código seria executado sem problemas.</p>
<pre>
def dividir(a, b):    
&emsp;&emsp;return a / b  

dividir(2, 10)  
</pre>
<p>Uma exceção ocorre quando o código está corretamente escrito, porém, devido a algum fator externo(um parâmetro enviado pelo usuário ou recebido a partir de outro processo) ou até mesmo interno(um caso não previsto), um erro acaba ocorrendo.</p>
<p>Um bom exemplo seria utilizando ainda a função de exemplo anterior, passar como parâmetros os valores 1 e 0, nesse caso, 1 será dividido por 0, e como todos sabem isso é impossível e acaba acontecendo um erro.</p>
<pre>
def dividir(a, b):    
&emsp;&emsp;return a / b  
 
dividir(1, 0)
</pre>
<p>Na execução, ocorre a seguinte exceção:</p>
<pre>
ZeroDivisionError: division by zero
</pre>
<h2 align="center">Emitir uma Exceção Customizada</h2>
<p>O Python por padrão já vem com várias exceções internas, mas em alguns casos é necessário emitir uma exceção especial, muito específica da função ou método em que você esteja trabalhando.</p>
<p>Para emitir a exceção, usamos a instrução <b>raise</b> quando determinada condição acontecer.</p>
<p>Por exemplo, caso a função só trabalhe com valores de a acima de 2, poderemos emitir uma exceção caso a seja menor ou igual(<=, ≤) a 2.</p>
<pre>
def funcao(a):  
&emsp;&emsp;if a <= 2:  
&emsp;&emsp;&emsp;&emsp;raise Exception('O valor de a deve ser maior que 2!')  
&emsp;&emsp;...
</pre>
<p>Chamando a função acima passando o valor de a como 1 teremos a seguinte saída:</p>
<pre>
Traceback (most recent call last):
&emsp;&emsp;File "teste.py", line 6, in <module>
&emsp;&emsp;&emsp;&emsp;funcao(1)
&emsp;&emsp;File "teste.py", line 3, in funcao
&emsp;&emsp;&emsp;&emsp;raise Exception('O valor de a deve ser maior que 2!')
Exception: O valor de a deve ser maior que 2!
</pre>
<h2 align="center">Lidando com o Erro</h2>
<p>Nos exemplos anteriores vimos a diferença de erros e exceções e como emitir uma exceção, porém quando isso ocorre o programa acaba se encerrando, para evitar isso que veremos formas de lidar com as exceções.</p>
<h2 align="center">Executando o Código Apenas Caso o Ambiente Permita (AssertionError)</h2>
<p>Uma das formas de lidar com erros é evitar que o programa execute em determinadas situações.</p>
<p>Por exemplo, caso o programa só funcione em Linux, independentemente do motivo, podemos fazer uma verificação e caso não esteja em um ambiente Linux encerramos o programa avisando o motivo para o usuário.</p>
<p>O <b>Assert</b> significa literalmente uma afirmação, ele afirma que determinada declaração é verdadeira, e caso não seja o programa é encerrado com a mensagem definida, como no exemplo abaixo:</p>
<pre>
import sys  
  
assert ('linux' in sys.platform), "Este programa só pode ser executado em um ambiente Linux!"  
  
print("Data Roadmap")
</pre>
<p>Executando o código no Windows, teremos a seguinte saída:</p>
<pre>
Traceback (most recent call last):
&emsp;&emsp;File "teste.py", line 3, in <module>
&emsp;&emsp;&emsp;&emsp;assert ('linux' in sys.platform), "Este programa só pode ser executado em um ambiente Linux!"
AssertionError: Este programa só pode ser executado em um ambiente Linux!
</pre>
<p>Agora caso executemos esse código no Linux, teremos a seguinte saída:</p>
<pre>
Data Roadmap
</pre>
<h2 align="center">Dando Alternativas Caso Ocorra Exceções (Try/Except)</h2>
<p>Nem sempre não executar o código seja a melhor opção, às vezes podemos lidar melhor e resolver essa exceção, para esses casos que utilizaremos essas duas instruções(<b>try</b> e <b>except</b>).</p>
<p>Essas instruções são usadas para capturar e lidar com o erro.</p>
<p>As instruções no bloco <b>try</b> são executadas como parte padrão do código, e caso ocorra algum erro ou exceção, o bloco <b>except</b> é então executado.</p>
<p>O exemplo abaixo exemplifica a utilização dessas duas instruções:</p>
<pre>
import sys  
  
  
def funcao():  
&emsp;&emsp;assert ('linux' in sys.platform), "Este programa só pode ser executado em um ambiente Linux!"  
&emsp;&emsp;print("Data Roadmap")  
  
try:  
&emsp;&emsp;&emsp;&emsp;funcao()  
except:  
&emsp;&emsp;&emsp;&emsp;...
</pre>
<p>Nesse exemplo, temos algumas saídas possíveis.</p>
<p>Caso execute em uma máquina Linux:</p>
<pre>
Data Roadmap
</pre>
<p>Caso execute em uma máquina Windows:</p>
<pre>

</pre>
<p>A maneira como foi lidado com o erro foi não fazendo nada caso ele acontessesse(... não executa nada).</p>
<p>Por isso quando executamos o código no Windows temos uma saída vazia, porém o programa não foi encerrado.</p>
<p>Podemos exibir uma mensagem caso ocorra a exceção, alertando o usário de algo por exemplo.</p>
<pre>
import sys  
  
  
def funcao():  
&emsp;&emsp;assert ('linux' in sys.platform), "Este programa só pode ser executado em um ambiente Linux!"  
&emsp;&emsp;print("Data Roadmap")  
  
try:  
&emsp;&emsp;&emsp;&emsp;funcao()  
except:  
&emsp;&emsp;&emsp;&emsp;print("funcao não foi executado pois não se encontra em um ambiente Linux!")
</pre>
<p>Agora, executando novamente ainda teremos duas saídas possíveis.</p>
<p>Caso execute em uma máquina Linux:</p>
<pre>
Data Roadmap
</pre>
<p>Caso execute em uma máquina Windows:</p>
<pre>
funcao não foi executado pois não se encontra em um ambiente Linux!
</pre>
<p>Quando ocorre uma exceção em um programa que executa esta função, o programa continuará, apenas irá informar sobre o fato de que a execução da função não foi bem-sucedida.</p>
<p>Outra forma de exibir que ocorreu uma exceção é mostrando a mensagem de erro, sem emitir o erro, para isso poderiamos capturar a mensagem fazendo da seguinte forma:</p>
<pre>
import sys  
  
  
def funcao():  
&emsp;&emsp;assert ('linux' in sys.platform), "Este programa só pode ser executado em um ambiente Linux!"  
&emsp;&emsp;print("Data Roadmap")  
  
try:  
&emsp;&emsp;&emsp;&emsp;funcao()  
except AssertionError as error:  
&emsp;&emsp;&emsp;&emsp;print(error)
</pre>
<p>Agora, executando novamente continuamos tendo duas saídas possíveis.</p>
<p>Caso execute em uma máquina Linux:</p>
<pre>
Data Roadmap
</pre>
<p>Caso execute em uma máquina Windows:</p>
<pre>
Este programa só pode ser executado em um ambiente Linux!
</pre>
<p>No exemplo anterior, você chamou uma função que você mesmo escreveu.</p>
<p>Quando você executou a função, você capturou o AssertionError e imprimiu na tela.</p>
<p>Mas isso pode ser feita com qualquer função, abaixo um exemplo utilizando a função open() para abrir um aquivo</p>
<pre>
try:
&emsp;&emsp;with open('file.log') as file:
&emsp;&emsp;&emsp;&emsp;read_data = file.read()
except:
&emsp;&emsp;print("Não foi possível abrir o aquivo file.log")
</pre>
<p>Executando o programa sem o arquivo file.log na pasta, temos a seguinte saída:</p>
<pre>
Não foi possível abrir o aquivo file.log
</pre>
<p>Também podemos capturar essa exceção e exibir na tela(uma lista com todas as exceções pode ser encontrada na documentação do Python):</p>
<pre>
try:
&emsp;&emsp;with open('file.log') as file:
&emsp;&emsp;&emsp;&emsp;read_data = file.read()
except FileNotFoundError as fnf_error:
&emsp;&emsp;print(fnf_error)
</pre>
<p>Executando o programa sem o arquivo file.log na pasta, temos a seguinte saída:</p>
<pre>
[Errno 2] No such file or directory: 'file.log'
</pre>
<p>Podemos também tratar duas exeções que podem ocorrer no mesmo bloco de código dentro de try.</p>
<p>No exemplo abaixo estamos unindo os exemplos anteriores em um só.</p>
<pre>
import sys  
  
  
def funcao():  
&emsp;&emsp;assert ('linux' in sys.platform), "Este programa só pode ser executado em um ambiente Linux!"  
&emsp;&emsp;print("Data Roadmap")  
  
try:  
&emsp;&emsp;&emsp;&emsp;funcao()  
&emsp;&emsp;&emsp;&emsp;with open('file.log') as file:
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;read_data = file.read()
except AssertionError as error:  
&emsp;&emsp;&emsp;&emsp;print(error)
except FileNotFoundError as fnf_error:
&emsp;&emsp;&emsp;&emsp;print(fnf_error)
</pre>
<p>Se o arquivo não existir, e este código for executado em uma máquina Windows, a saída será:</p>
<pre>
Este programa só pode ser executado em um ambiente Linux!
</pre>
<p>Agora se o arquivo não existir, e este código for executado em uma máquina Linux, a saída será:</p>
<pre>
[Errno 2] No such file or directory: 'file.log'
</pre>
<p>Caso o arquivo existir, e este código for executado em uma máquina Linux, a saída será:</p>
<pre>
Data Roadmap
</pre>
<p>Com isso, podemos entender que:</p>
<ul>
  <li>O código dentro do bloco <b>try</b> será executado até encontrar a primeira exceção.</li>
  <li>O código dentro do bloco <b>except</b> será responsável por lidar com essa exceção.</li>
  <li>Você pode antecipar várias exceções e diferenciar como o programa deve responder a elas.</li>
  <li>Você pode usar um <b>except</b> genérico para todas as exceções possíveis, embora isso seja completamente não recomendado.</li>
</ul>
<h2 align="center">Cláusula Else</h2>
<p>Podemos usar a instrução <b>else</b> para executar um bloco de código extra quando não ocorrer nenhuma das exceções previstas.</p>
<p>Usando o exemplo anterior, podemos adicionar um <b>else</b> e teremos a seguinte situação:</p>
<pre>
import sys  
  
  
def funcao():  
&emsp;&emsp;assert ('linux' in sys.platform), "Este programa só pode ser executado em um ambiente Linux!"  
&emsp;&emsp;print("Data Roadmap")  
  
try:  
&emsp;&emsp;&emsp;&emsp;funcao()  
&emsp;&emsp;&emsp;&emsp;with open('file.log') as file:
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;read_data = file.read()
except AssertionError as error:  
&emsp;&emsp;&emsp;&emsp;print(error)
except FileNotFoundError as fnf_error:
&emsp;&emsp;&emsp;&emsp;print(fnf_error)
else:
&emsp;&emsp;print("Nenhum erro ocorreu!")
</pre>
<p>Se o arquivo não existir, e este código for executado em uma máquina Windows, a saída será:</p>
<pre>
Este programa só pode ser executado em um ambiente Linux!
</pre>
<p>Agora se o arquivo não existir, e este código for executado em uma máquina Linux, a saída será:</p>
<pre>
[Errno 2] No such file or directory: 'file.log'
</pre>
<p>Caso o arquivo existir, e este código for executado em uma máquina Linux, a saída será:</p>
<pre>
Data Roadmap
Nenhum erro ocorreu!
</pre>
<p>Como o programa não encontrou nenhuma exceção, a cláusula <b>else</b> foi executada e exibiu a mensagem.</p>
<h2 align="center">Cláusula Finally</h2>
<p>Também podemos colocar mais um bloco de código que sempre será executado, independente de ocorrer exceções ou não, isso é feito utilizando a cláusula <b>finally</b>.</p>
<p>Ainda com o exemplo anterior, podemos adicionar uma mensagem de encerramento do bloco:</p>
<pre>
import sys  
  
  
def funcao():  
&emsp;&emsp;assert ('linux' in sys.platform), "Este programa só pode ser executado em um ambiente Linux!"  
&emsp;&emsp;print("Data Roadmap")  
  
try:  
&emsp;&emsp;&emsp;&emsp;funcao()  
&emsp;&emsp;&emsp;&emsp;with open('file.log') as file:
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;read_data = file.read()
except AssertionError as error:  
&emsp;&emsp;&emsp;&emsp;print(error)
except FileNotFoundError as fnf_error:
&emsp;&emsp;&emsp;&emsp;print(fnf_error)
else:
&emsp;&emsp;print("Nenhum erro ocorreu!")
finally:
&emsp;&emsp;print("Encerrando o bloco!")
</pre>
<p>Se o arquivo não existir, e este código for executado em uma máquina Windows, a saída será:</p>
<pre>
Este programa só pode ser executado em um ambiente Linux!
Encerrando o bloco!
</pre>
<p>Agora se o arquivo não existir, e este código for executado em uma máquina Linux, a saída será:</p>
<pre>
[Errno 2] No such file or directory: 'file.log'
Encerrando o bloco!
</pre>
<p>Caso o arquivo existir, e este código for executado em uma máquina Linux, a saída será:</p>
<pre>
Data Roadmap
Nenhum erro ocorreu!
Encerrando o bloco!
</pre>
<p>Tudo dentro do bloco <b>finally</b> será executado. Indepentemente se encontrou uma exceção ou se entrou na cláusula <b>else</b>.</p>
<h2 align="center">Conclusão</h2>
<p>Neste artigo foi visto sobre oque é uma exceção e sua diferença para um erro de sintaxe.</p>
<p>Foi visto também como se emitir uma exceção customizada e como lidar com as exceções quando elas ocorrerem.</p>
<p>Resumindo, temos as seguintes cláusulas para se lidar com exceções:</p>
<ul>
  <li><b>raise</b>: permite lançar(ou emitir) uma exceção a qualquer momento.</li>
  <li><b>assert</b>: permite verificar se uma determinada condição é atendida e lançar uma exceção se não for.</li>
  <li><b>try</b>: todas as instruções são executadas até que uma exceção seja encontrada.</li>
  <li><b>except</b>: é usado para capturar e manipular as exceções encontradas na cláusula <b>try</b>.</li>
  <li><b>else</b>: permite preparar um bloco de código que deve ser executado somente quando nenhuma exceção for encontrada na cláusula <b>try</b>.</li>
  <li><b>finally</b>: permite preparar um bloco de código que deve ser executado sempre, com ou sem exceções encontradas anteriormente.</li>
</ul>
<h2>Referências:</h2>
<p>https://www.covildodev.com.br/artigo/tratamento-de-erros-python</p>
