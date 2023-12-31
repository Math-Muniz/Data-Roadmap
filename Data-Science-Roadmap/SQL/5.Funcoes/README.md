<h1 align="center">Funções</h1>
<p>Neste Artigo nos aprofundaremos ainda mais em funções, veremos os diferentes tipos e alguns exemplos das mesmas com SQL.</p>
<h2 align="center">Funções de Valores Simples</h2>
<h3 align="center">ABS(n)</h3>
<p>Retorna um valor absoluto (positivo) de (n), ou seja, altera valores negativos para valores positivos.</p>
<p><b>Exemplo:</b></p>
<p>Extraindo o valor absoluto (positivo) .7 sobre o número especificado (-0.7).</p>
<pre>
SELECT ABS(-0.7);
</pre>
<p><b>Output:</b></p>
<pre>
.7
</pre>
<h3 align="center">CEIL(n)</h3>
<p>Obtém o valor inteiro imediatamente superior ou igual a "n"</p>
<p><b>Exemplo:</b></p>
<p>Vamos extrair o valor superior sobre os números 5 e 6.</p>
<pre>
SELECT CEIL(5.6)
</pre>
<p><b>Output:</b></p>
<pre>
6
</pre>
<h3 align="center">FLOOR(n)</h3>
<p>Devolve o valor inteiro imediatamente inferior ou igual a "n".</p>
<p><b>Exemplo:</b></p>
<p>Vamos extrair o valor inferior sobre os números 5 e 6.</p>
<pre>
SELECT FLOOR(5.6)
</pre>
<p><b>Output:</b></p>
<pre>
5
</pre>
<h3 align="center">MOD(m, n)</h3>
<p>Devolve o resto resultante de dividir "m" entre "n".</p>
<p><b>Exemplo:</b></p>
<p>Retorna o resto da divisão de 15(m) entre 4(n).</p>
<pre>
SELECT MOD(15,4)
</pre>
<p><b>Output:</b></p>
<pre>
3
</pre>
<h3 align="center">NVL(valor, expressão)</h3>
<p>Substitui um valor nulo por outro valor.</p>
<p><b>Exemplo:</b></p>
<p>Vamos fazer uma query abaixo que ao executarmos todos os campos de Sales que forem iguais à NULL serão substituídos por 100.</p>
<pre>
SELECT SUM(NVL(Sales,100)) 
FROM Sales_Data
</pre>
<p><b>Output:</b></p>
<pre>
Sales_Data
100
100
100
100
</pre>
<h3 align="center">POWER(m, exponente)</h3>
<p>Calcula a potência de um número.</p>
<p><b>Exemplo:</b></p>
<p>Vamos calcular a potencia de 2(m) elevado ao exponente 4(n).</p>
<pre>
SELECT POWER(2, 4)
</pre>
<p><b>Output:</b></p>
<pre>
16
</pre>
<h3 align="center">ROUND(numero [, m])</h3>
<p>Arredonda números com o número de dígitos de precisão indicados.</p>
<p><b>Exemplo:</b></p>
<p>Vamos arrendondar o número 15.600054 para duas casas decimais.</p>
<pre>
SELECT ROUND(15.600054[,2])
</pre>
<p><b>Output:</b></p>
<pre>
15.60
</pre>
<h3 align="center">SIGN(valor)</h3>
<p>Esta função é usada para retornar o sinal do número especificado. Retorna 1 se o número for positivo, -1 se o número for negativo e 0 para o número zero.</p>
<p><b>Exemplo:</b></p>
<p>Obtendo o resultado como -1, ou seja, negativo para o número especificado -7.</p>
<pre>
SELECT SIGN(-7);
</pre>
<p><b>Output:</b></p>
<pre>
-1
</pre>
<h3 align="center">SQRT(n)</h3>
<p>Devolve a raiz quadrada de "n".</p>
<p><b>Exemplo:</b></p>
<p>Abaixo vamos calcular a raiz quadrada de 16(n).</p>
<pre>
SELECT SQRT(16)
</pre>
<p><b>Output:</b></p>
<pre>
4
</pre>
<h3 align="center">TRUNC(numero, [m])</h3>
<p>Trunca os números para que tenham "m" decimais.</p>
<p><b>Exemplo:</b></p>
<p>Abaixo vamos truncar o valor 15.6 para que ele tenha 5(m) casas decimais fazendo ele ficar 15.60000.</p>
<pre>
SELECT TRUNC(15.6[,5 ])
</pre>
<p><b>Output:</b></p>
<pre>
15.60000
</pre>
<h3 align="center">VARIANCE(valor)</h3>
<p>Retorna a variância da amostra de registros não NULL em um grupo. Se todos os registros dentro de um grupo forem NULL, um NULL é retornado.</p>
<p><b>Exemplo:</b></p>
<p>Vamos retornar a variância amostral dos valores fornecidos na tabela abaixo, lembrando que o valor NULL vai ser excluido. Portanto, a variação seria calculada apenas para os valores 10, 15, 12 e 14.</p>
<pre>
<table>
  <tr>
    <th>ID</th>
    <th>Valor</th>
  </tr>
  <tr>
    <td>1</td>
    <td>10</td>
  </tr>
  <tr>
    <td>2</td>
    <td>15</td>
  </tr>
  <tr>
    <td>3</td>
    <td>12</td>
  </tr>
  <tr>
    <td>4</td>
    <td>NULL</td>
  </tr>
  <tr>
    <td>5</td>
    <td>14</td>
  </tr>
</table>
</pre>
<pre>
SELECT VARIANCE(Valor) FROM exemplo;
</pre>
<p><b>Output:</b></p>
<pre>
≈ 4.92
</pre>
<h2 align="center">Funções de Grupos de Valores</h2>
<h3 align="center">AVG(n)</h3>
<p>Calcula o valor médio de "n" ignorando os valores nulos.</p>
<p><b>Exemplo:</b></p>
<p>Vamos calcular o valor médio (média) da nossa tabela exemplo que está acima.</p>
<pre>
SELECT AVG(Valor) FROM exemplo;
</pre>
<p><b>Output:</b></p>
<pre>
12.75
</pre>
<h3 align="center">COUNT (* | Expressão)</h3>
<p>Conta o número de vezes que a expressão avalia algum dado com valor não nulo. A opção "*" conta todas as filas selecionadas.</p>
<p><b>Exemplo:</b></p>
<p>Abaixo vamos usar a função COUNT para avaliar quantos dados não nulos temos na nossa tabela exemplo usando a opção "*" para selecionar tudo para nossa contagem.</p>
<pre>
SELECT COUNT(*) FROM exemplo WHERE Valor IS NOT NULL;
</pre>
<p><b>Output:</b></p>
<pre>
4
</pre>
<h3 align="center">MAX (expressão)</h3>
<p>Calcula o valor máximo.</p>
<p><b>Exemplo:</b></p>
<p>Vamos selecionar o valor máximo da nossa tabela exemplo.</p>
<pre>
SELECT MAX(Valor) FROM exemplo
</pre>
<p><b>Output:</b></p>
<pre>
15
</pre>
<h3 align="center">MIN (expressão)</h3>
<p>Calcula o valor mínimo.</p>
<p><b>Exemplo:</b></p>
<p>Vamos selecionar o valor mínimo da nossa tabela exemplo.</p>
<pre>
SELECT MIN(Valor) FROM exemplo
</pre>
<p><b>Output:</b></p>
<pre>
10
</pre>
<h3 align="center">SUM (expressão)</h3>
<p>Obtém a soma dos valores da expressão.</p>
<p><b>Exemplo:</b></p>
<p>Agora vamos usar a função SUM para somarmos os valores da nossa tabela exemplo (10, 12, NULL, 14, 15).</p>
<pre>
SELECT SUM(Valor) FROM exemplo
</pre>
<p><b>Output:</b></p>
<pre>
41
</pre>
<h3 align="center">GREATEST (valor1, valor2…)</h3>
<p>Obtém o maior valor da lista.</p>
<p><b>Exemplo:</b></p>
<p>Vamos usar o GREATEST para tentar encontrar o maior valor entre os valores 10, 15, 12, 14 que usamos na nossa tabela exemplo.</p>
<pre>
SELECT GREATEST(10, 15, 12, 14) FROM exemplo;
</pre>
<p><b>Output:</b></p>
<pre>
15
</pre>
<h3 align="center">LEAST (valor1, valor2…)</h3>
<p>Obtém o menor valor da lista.</p>
<p><b>Exemplo:</b></p>
<p>Vamos usar o LEAST para tentar encontrar o menor valor entre os valores 10, 15, 12, 14 que usamos na nossa tabela exemplo.</p>
<pre>
SELECT LEAST(10, 15, 12, 14) FROM exemplo;
</pre>
<p><b>Output:</b></p>
<pre>
10
</pre>
<h2 align="center">Funções que Devolvem Valores de Caracteres</h2>
<h3 align="center">CHR(n)</h3>
<p>Devolve o caractere cujo valor em binário é equivalente a "n".</p>
<p><b>Exemplo:</b></p>
<p>Suponha que você queira encontrar o caractere cujo valor binário é 65, que corresponde ao caractere "A" na tabela ASCII. Você pode usar a função CHR da seguinte maneira:</p>
<pre>
SELECT CHR(65);
</pre>
<p><b>Output:</b></p>
<pre>
A
</pre>
<h3 align="center">CONCAT (cad1, cad2)</h3>
<p>Devolve "cad1" concatenada com "cad2".</p>
<p><b>Exemplo:</b></p>
<p>Vamos concatenar abaixo a palavra 'Olá' com a palavra 'Mundo'.</p>
<pre>
SELECT CONCAT('Olá', ' Mundo');
</pre>
<p><b>Output:</b></p>
<pre>
Olá Mundo
</pre>
<h3 align="center">LOWER (cad)</h3>
<p>Devolve a cadeia "cad" em minúsculas.</p>
<p><b>Exemplo:</b></p>
<p>Vamos agora usar nossa função LOWER para transformar nosso as letras do nosso texto abaixo em minúsculas.</p>
<pre>
SELECT LOWER('Texto EM Minúsculas');
</pre>
<p><b>Output:</b></p>
<pre>
texto em minúsculas
</pre>
<h3 align="center">UPPER (cad)</h3>
<p>Devolve a cadeia "cad" em maiúsculas.</p>
<p><b>Exemplo:</b></p>
<p>Vamos agora usar nossa função UPPER para transformar nosso as letras do nosso texto abaixo em maiúsculas.</p>
<pre>
SELECT UPPER('Texto em Maiúsculas');
</pre>
<p><b>Output:</b></p>
<pre>
TEXTO EM MAIÚSCULAS
</pre>
<h3 align="center">INITCAP (cad)</h3>
<p>Converte a cadeia "cad" a tipo título.</p>
<p><b>Exemplo:</b></p>
<p>Vamos agora usar a função INITCAP para transformar as primeiras letras de cada palavra em maiúsculas ficando num tipo título.</p>
<pre>
SELECT INITCAP('isso é um Exemplo de INitCAP');
</pre>
<p><b>Output:</b></p>
<pre>
Isso É Um Exemplo De Initcap
</pre>
<h3 align="center">LPAD (cad1, n[,cad2])</h3>
<p>Adiciona caracteres à esquerda da cadeia até que tenha uma certa longitude.</p>
<p><b>Exemplo:</b></p>
<p>Vamos usar a função LPAD agora para adicionar o '0' a esquerda do '42' até termos '5' caracteres no total.</p>
<pre>
SELECT LPAD('42', 5, '0');
</pre>
<p><b>Output:</b></p>
<pre>
00042
</pre>
<h3 align="center">RPAD (cad1, n[,cad2])</h3>
<p>Adiciona caracteres à direita até que tenha uma certa longitude.</p>
<p><b>Exemplo:</b></p>
<p>Vamos agora usar a função RPAD para adicionar '!' a direita do 'Olá' até termos '7' caracteres no total.</p>
<pre>
SELECT RPAD('Olá', 7, '!');
</pre>
<p><b>Output:</b></p>
<pre>
Olá!!!!
</pre>
<h3 align="center">LTRIM (cad [,set])</h3>
<p>Suprime um conjunto de caracteres à esquerda da cadeia.</p>
<p><b>Exemplo:</b></p>
<p>Neste exemplo, a função LTRIM remove todos os espaços em branco à esquerda da cadeia de caracteres.</p>
<pre>
SELECT LTRIM('   Espaços à esquerda');
</pre>
<p><b>Output:</b></p>
<pre>
'Espaços à esquerda'
</pre>
<h3 align="center">RTRIM (cad [,set])</h3>
<p>Suprime um conjunto de caracteres à direita da cadeia.</p>
<p><b>Exemplo:</b></p>
<p>Neste exemplo, a função RTRIM remove todos os espaços em branco à direita da cadeia de caracteres.</p>
<pre>
SELECT RTRIM('Direita espaços    ');
</pre>
<p><b>Output:</b></p>
<pre>
'Direita espaços'
</pre>
<h3 align="center">REPLACE (cad, cadeia_busca [, cadeia_substitucao])</h3>
<p>Substitui um caractere ou caracteres de uma cadeia com 0 ou mais caracteres.</p>
<p><b>Exemplo:</b></p>
<p>Neste exemplo, a função REPLACE substitui a cadeia de caracteres 'mundo' pela cadeia 'amigo' na string de entrada.</p>
<pre>
SELECT REPLACE('Olá, mundo!', 'mundo', 'amigo');
</pre>
<p><b>Output:</b></p>
<pre>
'Olá, amigo!'
</pre>
<h3 align="center">SUBSTR (cad, m [,n])</h3>
<p>Obtém parte de uma cadeia.</p>
<p><b>Exemplo:</b></p>
<p>Neste exemplo, a função SUBSTR extrai uma substring da string de entrada, começando na posição 6 ('é') e com um comprimento de 7 caracteres ('é uma s').</p>
<pre>
SELECT SUBSTR('Esta é uma string', 6, 7);
</pre>
<p><b>Output:</b></p>
<pre>
'é uma s'
</pre>
<h3 align="center">TRANSLATE (cad1, cad2, cad3)</h3>
<p>Converte caracteres de uma cadeia em caracteres diferentes, segundo um plano de substituição marcado pelo usuário.</p>
<p><b>Exemplo:</b></p>
<p>Neste exemplo, a função TRANSLATE substitui os caracteres da primeira cadeia 'elo' pelos caracteres correspondentes da segunda cadeia '123'.</p>
<pre>
SELECT TRANSLATE('Hello', 'elo', '123');
</pre>
<p><b>Output:</b></p>
<pre>
'H1223'
</pre>
<h2 align="center">Funções que Devolvem Valores Numéricos</h2>
<h3 align="center">ASCII(cad)</h3>
<p>Devolve o valor ASCII da primeira letra da cadeia "cad".</p>
<p><b>Exemplo:</b></p>
<p>No exemplo abaixo, vamos procurar usando a função ASCII para retornar o valor ASCII do caractere 'A', que é 65.</p>
<pre>
SELECT ASCII('A');
</pre>
<p><b>Output:</b></p>
<pre>
65
</pre>
<h3 align="center">INSTR (cad1, cad2 [, comeco [,m]])</h3>
<p>Permite uma busca de um conjunto de caracteres em uma cadeia, mas não suprime nenhum caractere depois.</p>
<p><b>Exemplo:</b></p>
<p>Usaremos a função INSTR que retorna a posição da primeira ocorrência da string 'World' dentro da string 'Hello, World', que é 8.</p>
<pre>
SELECT INSTR('Hello, World', 'World');
</pre>
<p><b>Output:</b></p>
<pre>
8
</pre>
<h3 align="center">LENGTH (cad)</h3>
<p>Devolve o número de caracteres de cad.</p>
<p><b>Exemplo:</b></p>
<p>Usaremos a função LENGTH retorna o comprimento (número de caracteres) da string 'Database', que é 8.</p>
<pre>
SELECT LENGTH('Database');
</pre>
<p><b>Output:</b></p>
<pre>
8
</pre>
<h2 align="center">Funções para o Manejo de Datas</h2>
<h3 align="center">SYSDATE</h3>
<p>Retorna a data e hora atuais do sistema.</p>
<p><b>Exemplo:</b></p>
<p>Vamos selecionar a data e hora atual do sistema que estamos usando.</p>
<pre>
SELECT SYSDATE;
</pre>
<p><b>Output:</b></p>
<pre>
2023-10-04 13:27:45
</pre>
<h3 align="center">ADD_MONTHS (data, n)</h3>
<p>Devolve a data "data" incrementada em "n" meses.</p>
<p><b>Exemplo:</b></p>
<p>Vamos adicionar 3 meses a nossa data.</p>
<pre>
SELECT ADD_MONTHS('2023-10-04', 3);
</pre>
<p><b>Output:</b></p>
<pre>
2024-01-04
</pre>
<h3 align="center">LASTDAY (data)</h3>
<p>Devolve a data do último dia do mês que contém "data".</p>
<p><b>Exemplo:</b></p>
<p>Vamos ver qual o último dia do mês de outubro abaixo.</p>
<pre>
SELECT LASTDAY('2023-10-04')
</pre>
<p><b>Output:</b></p>
<pre>
2023-10-31
</pre>
<h3 align="center">MONTHS_BETWEEN (data1, data2)</h3>
<p>Devolve a diferença em meses entre as datas "data1" e "data2".</p>
<p><b>Exemplo:</b></p>
<p>Vamos ver a diferença em meses entre a data '2023-12-31' e '2023-09-12'.</p>
<pre>
SELECT MONTHS_BETWEEN('2023-12-31', '2023-09-12');
</pre>
<p><b>Output:</b></p>
<pre>
3.45161290322581
</pre>
<h3 align="center">NEXT_DAY (data, cad)</h3>
<p>Devolve a data do primeiro dia da semana indicado por "cad" depois da data indicada por "data".</p>
<p><b>Exemplo:</b></p>
<p>Vamos ver qual seria a próxima sexta-feira apartir da data '2023-10-04'.</p>
<pre>
SELECT NEXT_DAY('2023-10-04', 'FRIDAY');
</pre>
<p><b>Output:</b></p>
<pre>
2023-10-06
</pre>
<h2 align="center">Funções de Conversão</h2>
<h3 align="center">TO_CHAR</h3>
<p>Transforma um tipo DATE ou NUMBER em uma cadeia de caracteres.</p>
<p><b>Exemplo:</b></p>
<p></p>
<pre>
SELECT TO_CHAR(SYSDATE, 'DD-MM-YYYY HH24:MI:SS');
</pre>
<p><b>Output:</b></p>
<pre>
04-10-2023 13:27:45
</pre>
<h3 align="center">TO_DATE</h3>
<p>Transforma um tipo NUMBER ou CHAR em DATE.</p>
<p><b>Exemplo:</b></p>
<p>Agora vamos transformar '04-10-2023' colocando o ano na frente, seguido pelo mês e por último o dia.</p>
<pre>
SELECT TO_DATE('04-10-2023', 'YYYY-MM-DD');
</pre>
<p><b>Output:</b></p>
<pre>
2023-10-04
</pre>
<h3 align="center">TO_NUMBER</h3>
<p>Transforma uma cadeia de caracteres em NUMBER.</p>
<p><b>Exemplo:</b></p>
<p>Vamos converter a string '42' em um número.</p>
<pre>
SELECT TO_NUMBER('42');
</pre>
<p><b>Output:</b></p>
<pre>
42
</pre>
<h2>Referencias</h2>
<p>https://www.devmedia.com.br/funcoes-sql/4978</p>
<p>http://sigaceivap.org.br:8080/publicacoesArquivos/publicacoesNovo.filepart</p>
<p>https://eufacoprogramas.com/sql-funcoes-com-numeros/</p>
<p>https://acervolima.com/funcao-sign-no-sql-server/</p>
<p>https://chat.openai.com/</p>
