<h1 align="center">Funções</h1>
<h2 align="center">Introdução</h2>
<p>Funções são blocos de código que executam funcionalidades específicas.</p>
<p>Normalmente são utilizados para evitar que determinada parte do seu código sejá escrito varias vezes.</p>
<p>Em Python sua sintaxe é definida usando def e atribuindo um nome a ela, veja um exemplo:</p>
<pre>
def funcao():
&emsp;&emsp;print("Bloco de código")
</pre>
<p>Observando essa função, podemos extrair algumas informações, iniciando com a palavra reservada para funções def o nome atribuido à função funcao e os parênteses () utilizado para definição dos dados de entrada da função, também chamados de parâmetros.</p>
<p>Em seguida usa-se dois pontos : e abaixo o bloco de código a ser executado, que neste caso é apenas imprimir de uma string.</p>
<p>Para “chamar” uma função, utilizamos o nome que foi definido, dessa forma:</p>
<pre>
def funcao():
&emsp;&emsp;print("Bloco de código")

funcao()
</pre>
<p>Resultado do código acima:</p>
<pre>
Bloco de código
</pre>
<h2 align="center">Parâmetros</h2>
<p>Além de executar código, funções também podem <b>receber</b> e <b>retornar</b> dados.</p>
<p>Podemos enviar dados para uma função através de seus parâmetros.</p>
<p>Observe o exemplo:</p>
<pre>
def imprime_nome(nome):
&emsp;&emsp;print(f"Nome: {nome}")

imprime_nome("Erickson")
imprime_nome("Renan")
imprime_nome("Daniel")
</pre>
<p>Resultado do código acima:</p>
<pre>
Nome: Erickson
Nome: Renan
Nome: Daniel
</pre>
<p>Quando a função é chamada, passamos uma string como dado de entrada - através do parâmetro nome - que é concatenada e impressa dentro da função.</p>
<p>Caso nenhum valor seja infomado ao chamar a função, um erro será gerado. Por exemplo, o seguinte código:</p>
<pre>
def imprime_nome(nome):
&emsp;&emsp;print(f"Nome: {nome}")

imprime_nome()
</pre>
<p>Ocasionará o seguinte erro:</p>
<pre>
TypeError: imprime_nome() missing 1 required positional argument: 'nome'
</pre>
<p>Podemos resolver esse erro utilizando os “Valores Padrão” e é exatamente isso que veremos agora!</p>
<h2 align="center">Valores Padrão (ou Valores Default)</h2>
<p>A utilização dos valores padrão serve para dar um valor quando quem chamou a função não passar nenhum valor para os parâmetros definidos.</p>
<p>Fazemos isso dessa forma:</p>
<pre>
def flor(flor='Rosa', cor='Vermelha'):
&emsp;&emsp;print("A cor da {flor} é {cor}")

flor()
flor("Orquídea", "Azul")
</pre>
<p>Veja o resultado:</p>
<pre>
A cor da Rosa é Vermelha
A cor da Orquídea é Azul
</pre>
<p>Ou seja, o erro anterior não ocorrou novamente!</p>
<h2 align="center">Chamada de Função Posicional versus Chamada de Função Nomeada</h2>
<p>Quando chamamos uma função, podemos utilizar a localização dos parâmetros para fazer o casamento entre o que foi chamado e o que foi definido na função.</p>
<p>Para entender melhor, veja o exemplo a seguir:</p>
<pre>
def monta_computador(cpu='', armazenamento=0, memoria=0):
&emsp;&emsp;print('A configuração é: \n\t- CPU: {cpu}\n\t- Armazenamento: {armazenamento}Tb\n\t- Memória: {memoria}Gb')

monta_computador('Intel Core i9', 4, 64)
</pre>
<p>A saída será:</p>
<pre>
A configuração é: 
&emsp;&emsp;- CPU: Intel Core i9
&emsp;&emsp;- Armazenamento: 4Tb
&emsp;&emsp;- Memória: 64Gb
</pre>
<p>O programador que escreveu a chamada da função monta_computador está respeitando a posição dos parâmetros, ou seja:</p>
<ul>
  <li>O valor "Intel Core i9" é referente ao primeiro parâmetro (cpu)</li>
  <li>O valor 4 é referente ao segundo parâmetro (armazenamento)</li>
  <li>O valor 64 se refere ao terceiro parâmetro (memoria)</li>
</ul>
<p>Essa é uma chamada de função posicional, ou seja: que respeita a ordem dos parâmetros.</p>
<p>Outra forma de fazer essa chamada de função é utilizar os nomes dos parâmetros!</p>
<p>Dessa forma, não é necessário respeitar a ordem de definição dos parâmetros!</p>
<p>Veja o mesmo exemplo, mas agora utilizando os nomes dos parâmetros:</p>
<pre>
monta_computador(memoria=64, armazenamento=4, cpu='Intel Core i9')
</pre>
<p>A saída será a mesma, pois como utilizamos os nomes, o Python saberá qual valor referência qual parâmetro!</p>
<h2 align="center">Parâmetro *args</h2>
<p>Caso você queira desenvolver uma função que recebe um número variável de parâmetros, você pode utilizar o parâmetro *args!</p>
<p>Dessa forma, a função receberá os argumentos em forma de Tupla e você poderá processá-los com um loop for por exemplo!</p>
<p>Veja o código abaixo para entender melhor:</p>
<pre>
def maior_30(*args):
&emsp;&emsp;print(args)
&emsp;&emsp;print(type(args))

&emsp;&emsp;for num in args:
&emsp;&emsp;&emsp;&emsp;if num > 30:
&emsp;&emsp;&emsp;&emsp;print(num)


maior_30(10, 20, 30, 40, 50, 60)
</pre>
<p>A função acima irá receber todos os valores passados para função no parâmetro *args e irá iterar sobre eles com um loop for.</p>
<p>Veja a saída:</p>
<pre>
(10, 20, 30, 40, 50, 60)
<class 'tuple'>
40
50
60
</pre>
<h2 align="center">Parâmetro **kwargs</h2>
<p>Agora, se quiser desenvolver uma função com número variado de parâmetros nomeados, utilize **kwargs.</p>
<p>Dessa forma, todos os dados passados à função serão guardados nessa variável **kwargs, em formato de um dicionário.</p>
<p>Oberve como podemos obter a chave a valor deles percorrendo os itens deste dicionário:</p>
<pre>
def dados_pessoa(**kwargs):
&emsp;&emsp;print(type(kwargs))
    
&emsp;&emsp;for chave, valor in kwargs.items():
&emsp;&emsp;&emsp;&emsp;print(f"{chave}: {valor}")

dados_pessoa(nome='João', idade=35, carreira='Desenvolvedor Fullstack')
</pre>
<p>Na saída podemos observar o tipo de dado que a função recebeu e a estrutura construida para percorrer o dicionário:</p>
<pre>
<class 'dict'>
nome: João
idade: 35
carreira: Desenvolvedor Fullstack
</pre>
<h2 align="center">Funções com retorno de dados</h2>
<p>As funções também podem retornar valores através da palavra reservada return.</p>
<p>Veja o exemplo:</p>
<pre>
def soma_dois_numeros(valor1, valor2):
&emsp;&emsp;soma = valor1 + valor2
&emsp;&emsp;return soma

valor_soma = soma_dois_numeros(32, 15)
print(valor_soma)
print(soma_dois_numeros(50, 10))
</pre>
<p>Saída com o retorno da soma dos valores introduzidos na função:</p>
<pre>
47
60
</pre>
<h2 align="center">Funções com retorno múltiplos</h2>
<p>Funções também podem retornar múltiplos dados. Veja o exemplo:</p>
<pre>
def soma_dois_numeros_e_calcula_media(valor1, valor2):
&emsp;&emsp;soma = valor1 + valor2
&emsp;&emsp;media = (valor1 + valor2)/2
    
&emsp;&emsp;return soma, media

valor_soma = soma_dois_numeros_e_calcula_media(32, 15)
print(valor_soma)
print(soma_dois_numeros_e_calcula_media(50, 10))
</pre>
<p>A saída será:</p>
<pre>
(47, 23.5)
(60, 30.0)
</pre>
<h2 align="center">Palavra reservada pass</h2>
<p>Caso você deseje definir uma função sem corpo nenhum, ou seja, sem código, saiba que isso irá disparar o erro IndentationError, pois funções não podem estar vazias.</p>
<p>Porém se por algum motivo precisar use a palavra reservada pass, da seguinte forma:</p>
<pre>
def funcao():
&emsp;&emsp;pass
</pre>
<h2 align="center">Função de uma linha</h2>
<p>Python possibilita a criação de funções com apenas uma linha de código. Veja os exemplo a seguir:</p>
<pre>
#Definição das funções
def soma(valor1, valor2): return valor1 + valor2
def divisao(valor1, valor2): return valor1 / valor2
def multiplicacao(valor1, valor2): return valor1 * valor2

#Chamada das funções
print(soma(1, 5))
print(divisao(8, 2))
print(multiplicacao(8, 2))
</pre>
<p>O resultado do código acima será:</p>
<pre>
6
4.0
16
</pre>
<h2 align="center">Conclusão</h2>
<p>Nesse post vimos como podemos criar Funções em Python, que nada mais é que “pedaço de código nomeado”.</p>
<p>Vimos a sintaxe para sua criação, parâmetros, retorno, chamada e muito mais!</p>
<h2 align="center">Referências:</h2>
<p>https://pythonacademy.com.br/blog/funcoes-em-python</p>
