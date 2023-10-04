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
<p></p>
<p><b>Exemplo:</b></p>
<p></p>
<pre>

</pre>
<p><b>Output:</b></p>
<pre>

</pre>
<h3 align="center">MIN (expressão)</h3>
<p></p>
<p><b>Exemplo:</b></p>
<p></p>
<pre>

</pre>
<p><b>Output:</b></p>
<pre>

</pre>
<h3 align="center">SUM (expressão)</h3>
<p></p>
<p><b>Exemplo:</b></p>
<p></p>
<pre>

</pre>
<p><b>Output:</b></p>
<pre>

</pre>
<h3 align="center">GREATEST (valor1, valor2…)</h3>
<p></p>
<p><b>Exemplo:</b></p>
<p></p>
<pre>

</pre>
<p><b>Output:</b></p>
<pre>

</pre>
<h3 align="center">LEAST (valor1, valor2…)</h3>
<p></p>
<p><b>Exemplo:</b></p>
<p></p>
<pre>

</pre>
<p><b>Output:</b></p>
<pre>

</pre>
<h2 align="center">Funções que Devolvem Valores de Caracteres</h2>
<h2 align="center">Funções que Devolvem Valores Numéricos</h2>
<h2 align="center">Funções para o Manejo de Datas</h2>
<h2 align="center">Funções de Conversão</h2>
<h2>Referencias</h2>
<p>https://www.devmedia.com.br/funcoes-sql/4978</p>
<p>http://sigaceivap.org.br:8080/publicacoesArquivos/publicacoesNovo.filepart</p>
<p>https://eufacoprogramas.com/sql-funcoes-com-numeros/</p>
<p>https://acervolima.com/funcao-sign-no-sql-server/</p>
