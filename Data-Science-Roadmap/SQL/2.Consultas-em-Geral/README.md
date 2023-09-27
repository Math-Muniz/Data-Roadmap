<h1 align="center">Consultas em Geral</h1>
<p>A linguagem SQL foi criada com o objetivo de padronizar os comandos de manipulação de dados em SGBD’s. Hoje em dia, apesar de a linguagem possuir uma quantidade considerável de extensões e implementações proprietárias, pode-se afirmar que a meta foi alcançada. Conhecendo bem a linguagem é possível acessar os recursos básicos de qualquer banco relacional, como Oracle, SQL Server ou MySQL, sem praticamente nenhuma mudança.</p>
<p>Veremos nesse artigo um pequeno guia de consultas gerais focado no comando <b>SELECT</b>, um dos mais importantes da linguagem SQL.</p>
<h2 align="center">SELECT</h2>
<p>O comando <b>SELECT</b> permite recuperar os dados de um objeto do banco de dados, como uma tabela, view e, em alguns casos, uma stored procedure (alguns bancos de dados permitem a criação de procedimentos que retornam valor). A sintaxe mais básica do comando é:</p>
<pre>
SELECT <lista_de_campos>
FROM <nome_da_tabela></nome_da_tabela></lista_de_campos>
</pre>
<p></p>
<pre>
SELECT CODIGO, NOME FROM CLIENTES
</pre>
<pre>
SELECT * FROM CLIENTES
</pre>
<p>O caractere * representa todos os campos. Apesar de prático, este caractere não é muito utilizado, pois, para o SGBD é mais rápido receber o comando com todos os campos explicitados. O uso do * obriga o servidor a consultar quais são os campos antes de efetuar a busca dos dados, criando mais um passo no processo.</p>
<h2 align="center">WHERE</h2>
<p>A cláusula Where permite ao comando SQL passar condições de filtragem.</p>
<pre>
SELECT CODIGO, NOME FROM CLIENTES
WHERE CODIGO = 10
SELECT CODIGO, NOME FROM CLIENTES
WHERE UF = ‘RJ’
SELECT CODIGO, NOME FROM CLIENTES
WHERE CODIGO >= 100 AND CODIGO <= 500
SELECT CODIGO, NOME FROM CLIENTES
WHERE UF = ‘MG’ OR UF = ‘SP’
</pre>
<p>Os parênteses corretamente utilizados dão mais poder as consultas, conforme exemplo abaixo:</p>
<pre>
SELECT CODIGO, NOME FROM CLIENTES
WHERE UF = ‘RJ’ OR (UF = ‘SP’ AND ATIVO = ‘N’)
</pre>
<p>Neste comando todos os clientes do Rio de Janeiro e apenas os clientes inativos de São Paulo seriam capturados.</p>
<p>Agora veja o exemplo a seguir:</p>
<pre>
SELECT CODIGO, NOME FROM CLIENTES
WHERE (ENDERECO IS NULL) OR (CIDADE IS NULL)
</pre>
<p>Aqui, todos os clientes que não possuem endereço ou cidade cadastrada serão selecionados.</p>
<h2 align="center">FILTRO DE TEXTO</h2>
<p>Para busca parcial de string, o SELECT fornece o operador LIKE. Veja o exemplo abaixo:</p>
<pre>
SELECT CODIGO, NOME FROM CLIENTES
WHERE NOME LIKE ‘MARIA%’
</pre>
<p>Neste comando, todos os clientes cujos nomes iniciam com Maria serão retornados. Se quisermos retornar os nomes que contenham ‘MARIA’ também no meio, podemos alterar para o exemplo a seguir:</p>
<pre>
SELECT CODIGO, NOME FROM CLIENTES
WHERE NOME LIKE ‘%MARIA%’
</pre>
<p>O uso de máscara no início e no fim da string fornece maior poder de busca, mas causa considerável perda de performance. Este recurso deve ser utilizado com critério.</p>
<p><b>Uma observação:</b> em alguns bancos de dados, a máscara de filtro não é representada por %. Consulte a referência do banco para verificar o caractere correto.</p>
<p>Por padrão, a SQL diferencia caixa baixa de caixa alta. Para eliminar essa diferença, utiliza a função UPPER. Veja abaixo:</p>
<pre>
SELECT CODIGO, NOME FROM CLIENTES
WHERE UPPER(NOME) LIKE ‘MARIA %SILVA%’
</pre>
<h2 align="center">ORDENAÇÃO</h2>
<p>A ordenação pode ser definida com o comando ORDER BY. Assim como no comando WHERE, o campo de ordenação não precisa estar listado como campo de visualização.</p>
<pre>
SELECT CODIGO, NOME FROM CLIENTES
ORDER BY NOME
SELECT CODIGO, NOME FROM CLIENTES
ORDER BY UF, NOME
</pre>
<p>A utilização da palavra DESC garante a ordenação invertida:</p>
<pre>
SELECT CODIGO, NOME FROM CLIENTES
ORDER BY NOME DESC
SELECT CODIGO, NOME FROM CLIENTES
ORDER BY UF DESC
</pre>
<h2 align="center">JUNÇÃO DE TABELAS</h2>
<p>O SELECT permite juntar duas ou mais tabelas no mesmo resultado. Isso pode ser feito de várias formas. Uma delas segue abaixo:</p>
<pre>
SELECT CLIENTES.CODIGO, CLIENTES.NOME, PEDIDOS.DATA
FROM CLIENTES, PEDIDOS
WHERE CLIENTES.CODIGO = PEDIDOS.CODCLIENTE
</pre>
<p>Nesta linha as tabelas relacionadas CLIENTES e PEDIDOS são unificadas através do campo chave, em uma operação de igualdade. Repare que os nomes dos campos passam a ser prefixados pelo nome das tabelas, resolvendo duplicidades. Uma versão resumida desse comando pode ser como abaixo:</p>
<pre>
SELECT A.CODIGO, A.NOME, B.DATA, B.VALOR
FROM CLIENTES A, PEDIDOS B
WHERE A.CODIGO = B.CODCLIENTE
</pre>
<p>O uso de aliases no código SQL torna a manutenção mais simples.</p>
<p>No comando abaixo temos várias tabelas unificadas em uma mesma cláusula.</p>
<pre>
SELECT A.CODIGO, A.NOME, B.DATA, B.VALOR, C.QTD, D.DESCRIC
FROM CLIENTES A, PEDIDOS B, ITENS C, PRODUTOS D
WHERE A.CODIGO = B.CODCLIENTE
AND B.CODIGO = C.CODPEDIDO
AND C.CODPRODUTO = D.CODIGO
</pre>
<p>Neste comando unificamos as tabelas relacionadas CLIENTES, PEDIDOS, ITENS e PRODUTOS. Veja mais este exemplo:</p>
<pre>
SELECT A.CODIGO, A.NOME, B.DATA, B.VALOR
FROM CLIENTES A, PEDIDOS B
WHERE A.CODIGO = B.CODCLIENTE
AND A.UF = ‘RJ’
</pre>
<p>Observe que a junção através da igualdade de campos traz como resultado somente os registros que possuem referências nas duas tabelas. Observe o comando abaixo:</p>
<pre>
SELECT A.CODIGO, A.DESCRICAO, B.DESCRICAO
FROM PROUTOS A, COMPONENTES B
WHERE A.CODIGO = B.CODPRODUTO
</pre>
<p>Os produtos que não possuem componentes não são selecionados, caso seja necessário criar uma listagem incluindo também os registros que não possuem correspondência, deve-se utilizar o comando JOIN.</p>
<h2 align="center">JOIN</h2>
<p>A junção de tabelas no comando SELECT também pode ser feita com o comando JOIN. Este comando deve ser utilizado com a palavra reservada INNER ou com a palavra OUTER:</p>
<p><b>INNER:</b> Semelhante ao uso do operador “=” na junção de tabelas. Aqui os registros sem correspondências não são incluídos. Esta cláusula é opcional e pode ser omitida no comando JOIN.</p>
<p><b>OUTER:</b> Os registros que não se relacionam também são exibidos. Neste caso, é possível definir qual tabela será incluída na seleção, mesmo não tendo correspondência.</p>
<p>Para exemplificar, temos as tabelas abaixo:</p>
<p>Observe os exemplos e o resultado produzido:</p>
<pre>
SELECT A.CODIGO, A.DESCRICAO, B.DESCRICAO, B.QTD
FROM PRODUTOS A
INNER JOIN COMPONENTES B
ON (A.CODIGO = B.CODPRODUTO)
</pre>
<p>Este comando pode ser escrito na versão resumida abaixo:</p>
<pre>
SELECT A.CODIGO, A.DESCRICAO, B.DESCRICAO
FROM PRODUTOS A
JOIN COMPONENTES B
ON (A.CODIGO = B.CODPRODUTO)
</pre>
<p>Como mostrado no resultado 1, os produtos que não possuem componentes não são incluídos na seleção.</p>
<pre>
SELECT A.CODIGO, A.DESCRICAO, B.DESCRICAO, B.QTDE
FROM PRODUTOS A
LEFT OUTER JOIN COMPONENTES B
ON (A.CODIGO = B.CODPRODUTO)
</pre>
<p>Neste comando todos os produtos serão incluídos na seleção, independente de possuírem um componente. Observe que a palavra LEFT se refere à primeira tabela do relacionamento.</p>
<pre>
SELECT A.CODIGO, A.DESCRICAO, B.DESCRICAO
FROM COMPONENTES A
RIGHT OUTER JOIN PRODUTOS B
ON (A.CODIGO = B.CODPRODUTO)
</pre>
<p>A ordem das tabelas foi invertida mas o resultado é o mesmo. Observe mais alguns exemplos:</p>
<pre>
SELECT A.CODIGO, A.DESCRICAO, B.DESCRICAO, B.QTDE
FROM PRODUTOS A
JOIN COMPONENTES B
ON (A.CODIGO  = B.CODPRODUTO)
WHERE A.CATEGORIA = 1
</pre>
<p>Agora veja o código q reproduz o resultado 4:</p>
<pre>
SELECT A.CODIGO, A.DESCRICAO, B.DESCRICAO
FROM PRODUTOS A JOIN COMPONENTES B
ON (A.CODIGO = B.CODPRODUTO)
WHERE A.CATEGORIA = 1 OR A.CATEGORIA = 2
ORDER BY A.CATEGORIA, A.DESCRICAO
</pre>
<h2 align="center">FULL OUTER JOIN</h2>
<p>Podemos ainda combinar o uso de INNER e OUTER através do comando FULL OUTER JOIN. Neste caso, todos os registros das duas tabelas envolvidas serão exibidos, tendo ou não relacionamento.</p>
<h2 align="center">UNION</h2>
<p>Existe ainda uma segunda forma de juntar tabelas com o comando SELECT. Através do parâmetro UNION, é possível colar o conteúdo de duas tabelas. Veja o exemplo:</p>
<pre>
SELECT CODIGO, NOME FROM CLIENTES
UNION
SELECT CODIGO. NOME FROM FUNCIONARIOS
</pre>
<p>O resultado deste comando é a listagem de todos os clientes e a listagem de todos os funcionários, dentro do mesmo result set. Repare que no comando JOIN á união é horizontal e no UNION a união é vertical.</p>
<p>Por default, os registros duplicados são eliminados na cláusula UNION. No exemplo anterior, se tivéssemos um cliente com o mesmo nome e código de um funcionário, apenas o registro da primeira tabela seria exibido. Para incluir todos os registros, independente de duplicidade, utilize a palavra ALL:</p>
<pre>
SELECT CODIGO, NOME FROM CLIENTES
UNION ALL
SELECT CODIGO, NOME FROM FUNCIONARIOS
</pre>
<h2 align="center">FUNÇÕES DE AGRUPAMENTO</h2>
<p>Abaixo nós temos as funções básicas de agrupamento:</p>
<ul>
  <li><b>AVG:</b> Retorna a média do campo especificado</li>
  <li><b>SELECT AVG(VALOR) FROM PEDIDOS</li>
  <li><b>MIN/MAX/SUM:</b> Respectivamente retorna o menor valor, o maior e o somatório de um grupo de registros:</li>
  <li>SELECT MIN(VALOR) FROM PEDIDOS</li>
  <li>SELECT MAX(VALOR) FROM PEDIDOS</li>
  <li>SELECT AVG(VALOR) FROM PEDIDOS</li>
  <li><b>COUNT:</b> Retorna a quantidade de itens da seleção</li>
</ul>
<p>Um exemplo de uso é o que pode ser visto abaixo:</p>
<pre>
SELECT COUNT(CODIGO) FROM CLIENTES
</pre>
<h2 align="center">AGRUPAMENTO</h2>
<p>Um poderoso recurso do comando SELECT é o parâmetro GROUPY BY. Através dele podemos retornar informações agrupadas de um conjunto de registros, estabelecendo uma condição de agrupamento. É um recurso muito utilizado na criação de relatórios. Para exemplificar, temos as tabelas CLIENTES E PEDIDOS a seguir.</p>
<pre>
SELECT CODCLIENTE, MAX(VALOR)
FROM PEDIDOS
GROUP BY CODCLIENTE
</pre>
<p>O comando acima retorna o maior valor de pedido de cada cliente. Observe o resultado:</p>
<pre>
SELECT CODCLIENTE, COUNT(*)
FROM PEDIDOS
GROUPY BY CODCLIENTE
</pre>
<p>Abaixo vemos quantos pedidos foram feitos por cada cliente.</p>
<h2 align="center">HAVING</h2>
<p>Através do comando HAVING podemos filtrar a cláusula GROUP BY. Observe o comando abaixo:</p>
<pre>
SELECT CODCLIENTE, COUNT(*)
FROM PEDIDOS
GROUPY BY CODCLIENTE
HAVING COUNT(*) >= 2
</pre>
<p>Somente os clientes com 2 ou mais pedidos serão selecionados. Repare que o HAVING é utilizado, geralmente com alguma função de agrupamento. Para filtros normais, pode-se utilizar o comando WHERE. Observe o exemplo abaixo:</p>
<pre>
SELECT CODCLIENTE, COUNT(*)
FROM PEDIDOS
WHERE DATA > ‘06/10/2002’
GROUPY BY CODCLIENTE
HAVING COUNT(*) >= 2
</pre>
<p>Repare que o cliente número 3 apresentou apenas dois pedidos, visto que o primeiro não possui data maior que 06/10.</p>
<h2>Refêrencias</h2>
<p>https://www.devmedia.com.br/sql-select-guia-para-iniciantes/29530</p>
