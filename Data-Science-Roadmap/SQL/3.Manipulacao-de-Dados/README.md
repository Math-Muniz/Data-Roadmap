<h1 align="center">Manipulação de Dados</h1>
<p>Neste capítulo, mostraremos os principais comandos SQL para manipulação dos dados armazenados nas tabelas do banco. Esse capítulo, abordará os comandos DML, disponíveis para inserção, alteração, deleção e seleção de dados.</p>
<h2 align="center">Adicionado, Alterando e Removendo Dados</h2>
<p>Para inserir, alterar ou apagar dados nas tabelas do banco, através de instruções SQL, devemos utilizar os comandos Insert, Update e Delete respectivamente. Através desses três comandos, manipulamos as informações em uma ou mais tabelas do banco de dados.</p>
<h2 align="center">Utilizando a instrução Insert</h2>
<p>Através da instrução Insert, podemos adicionar uma ou mais linhas para uma tabela do banco de dados:</p>
<pre>
INSERT INTO NOME_DA_TABELA (coluna1, coluna2, coluna3, ....colunaN)
VALUES (valor1, valor2, valor3, ..., valorN);
</pre>
<p>No parâmetro Nome_da_Tabela, podemos especificar tanto o nome de uma tabela do banco de dados, como também de uma View atualizável. Caso você não especifique o nome das colunas que receberão valores dentro da instrução Insert, o servidor de banco de dados utilizará todas as colunas da tabela informada. Veja alguns exemplos de uso da instrução Insert:</p>
<pre>
INSERT INTO CLIENTES (CODIGO, NOME, SEXO) VALUES (1, 'Natália da Silva', 'F');
INSERT INTO CIDADES (CODCIDADE, CODPAIS, NOMECIDADE, DDD) VALUES (4, 55, 'Curitiba', '31');
INSERT INTO ITENS VALUES (1, 13, 200.87);
</pre>
<p><b>Nota:</b> Antes de inserir um registro em uma tabela, que possui chave estrangeira, verifique se o valor que será inserido na coluna relacionada, existe na coluna chave primária da outra tabela.</p>
<p>Dentro da seção da instrução Values, podemos utilizar os seguintes valores em conjunto, ou não, com as seguintes funções:</p>
<ul>
  <li>Valores gerais como números, strings ou data;</li>
  <li><b>Função Cast:</b> Para converter um valor de um tipo para outro durante a operação de inserção;</li>
  <li><b>Função Upper:</b> Para converter uma string que está sendo inserida para maiúscula;</li>
  <li><b>Função Gen_Id:</b> Normalmente utilizada com Generators para geração de um valor único;</li>
  <li><b>Valor Null:</b> Para inserção de nulo para a coluna durante a operação de inserção do registro;</li>
  <li><b>User:</b> Comando utilizado para inserir o nome do usuário conectado no banco de dados;</li>
  <li><b>Variável:</b> Podemos inserir variáveis ou parâmetros através de Stored Procedures ou Triggers;</li>
</ul>
<h2 align="center">Inserindo várias linhas</h2>
<p>Através da instrução Insert, podemos inserir várias linhas a partir de um único comando:</p>
<pre>
INSERT INTO NOME_DA_TABELA_DESTINO (
&emsp;&emsp;coluna1, coluna2, coluna3, ...., colunaN)
SELECT (coluna1, coluna2, coluna3, ..., colunaN)
FROM NOME_DA_TABELA_ORIGEM;
</pre>
<p>A instrução Select, precisa ter o mesmo número de colunas listadas da expressão Insert. Caso o nome das colunas não seja informado, o Select precisa retornar um resultado que possua o mesmo número de colunas que a tabela onde os dados serão inseridos. Veja mais alguns exemplos a seguir:</p>
<pre>
INSERT INTO CIDADE_BR
SELECT * FROM CIDADE;

INSERT INTO ITENS (CODIGO, NF, QUANT)
SELECT (CODIGO, NUM_NF, QUANT)
FROM ITENS_VALIDOS
WHERE NUM_NF = 15;

INSERT INTO CLIENTES (CODIGO, NOME, FONE, ENDERECO)
SELECT (COD_CLI, NOME, FONE_CLI, END_CLI)
FROM CLIENTES_INATIVOS;
</pre>
<h2 align="center">Utilizando a instrução Update</h2>
<p>Para alterar os valores armazenados em registros existentes na tabela, devemos utilizar o comando Update:</p>
<pre>
UPDATE NOME_DA_TABELA
SET COLUNA1 = VALOR1, COLUNA2 = VALOR2, COLUNA3 = VALOR3, ...., COLUNAN = VALORN
WHERE CONDICOES;
</pre>
<p>Como no comando Insert, podemos utilizar diversos tipos de valores e funções dentro da instrução Update. Normalmente utilizamos a instrução Update em conjunto com a cláusula Where, para que apenas uma, ou um conjunto de registros sejam atualizados.</p>
<p><b>Atenção:</b> Caso a instrução Update seja utilizada sem uma cláusula Where, a atualização ocorrerá em todos os registros armazenados dentro da tabela.</p>
<p>Você pode utilizar a instrução Where em conjunto com os operadores e palavras chaves para limitar o número de registros a serem atualizados constantes na tabela abaixo:</p>
<table border="1">
  <thead>
      <tr>
          <th>Expressão</th>
          <th>Descrição</th>
      </tr>
  </thead>
  <tbody>
      <tr>
          <td>= Valor</td>
          <td>Igual a um determinado valor</td>
      </tr>
      <tr>
          <td>&lt; Valor</td>
          <td>Menor que um determinado valor</td>
      </tr>
      <tr>
          <td>>= Valor</td>
          <td>Maior ou igual a um determinado valor</td>
      </tr>
      <tr>
          <td>&lt;&gt; Valor</td>
          <td>Diferente de um determinado valor</td>
      </tr>
      <tr>
          <td>BETWEEN valor1 AND valor2</td>
          <td>Entre uma faixa de valores informada</td>
      </tr>
      <tr>
          <td>LIKE Valor</td>
          <td>Que contenha um determinado valor (%)</td>
      </tr>
      <tr>
          <td>IN (valor1, valor2, valor3, ..., valor4)</td>
          <td>Que contenha um dos elementos da lista</td>
      </tr>
      <tr>
          <td>IS NULL</td>
          <td>Verifica se o valor da coluna é nulo</td>
      </tr>
      <tr>
          <td>IS NOT NULL</td>
          <td>Verifica se o valor da coluna não é nulo</td>
      </tr>
      <tr>
          <td>STARTING WITH Valor</td>
          <td>Que contenha uma string case sensitive</td>
      </tr>
      <tr>
          <td>CONTAINING Valor</td>
          <td>Que contenha uma string case insensitive</td>
      </tr>
  </tbody>
</table>
<p>Veja a seguir, alguns exemplos de uso da instrução Update:</p>
<pre>
UPDATE CLIENTES
SET CIDADE = 'Curitiba', UF = 'PR'
WHERE COD_REF = 20;

UPDATE ITENS SET VALOR = 0.00
WHERE VALOR IS NULL;

UPDATE VENDAS
SET ATIVO = 'N'
WHERE DATA_VENDA BETWEEN '01.01.1992' AND '12.10.1995';

UPDATE PRODUTOS
SET TIPO = 'H', ATIVO = 'S', COD_FORNECEDOR = 100
WHERE COD_REF IN (1, 5, 10, 11);

UPDATE PRECOS
SET VALOR_TOTAL = VALOR_TOTAL * 1.1
WHERE (QUANTIDADE * VALOR_UNITARIO) > 1000;
</pre>
<h2 align="center">Atualizando várias linhas através de outra tabela</h2>
<p>Utilizando a instrução Update, podemos também alterar registros de uma tabela a partir de valores armazenados em outra tabela do banco de dados. Veja o exemplo seguir:</p>
<pre>
UPDATE PRODUTO
SET VALOR = VALOR + 100
WHERE COD_FORNECEDOR IN (
&emsp;&emsp;SELECT COD_FORNECEDOR
&emsp;&emsp;FROM FORNECEDOR
&emsp;&emsp;WHERE UF = 'SP');
</pre>
<p>Na instrução SQL anterior, aumentamos em 100 reais o valor de todos os produtos onde o código do fornecedor for igual aos códigos dos fornecedores cadastrados na tabela Fornecedor que sejam do estado de São Paulo.</p>
<h2 align="center">Utilizando a instrução Delete</h2>
<p>Para remover um ou mais registros de uma tabela devemos utilizar o comando Delete. Veja a seguir, sua sintaxe básica:</p>
<pre>
DELETE FROM NOME_DA_TABELA WHERE CONDICOES;
</pre>
<p>No parâmetro Condicoes devemos especificar o conjunto de registros que serão apagados da tabela informada no parâmetro Nome_Da_Tabela.</p>
<p><b>Atenção:</b> Caso nenhuma condição seja passada durante o uso do comando Delete, todos os registros da tabela serão apagados.</p>
<p>Como mostrado no comando Update, a cláusula Where pode ser utilizada com diversos operadores e palavras chaves para limitar o número de registros que serão apagados da tabela. Veja a seguir, alguns exemplos de uso da instrução Delete:</p>
<pre>
DELETE FROM CLIENTES
WHERE SEXO = 'M';

DELETE FROM PRODUTOS
WHERE TIPO = 1;

DELETE FROM TEMPORARIA;

DELETE FROM VENDAS
WHERE DATA_VENDA BETWEEN '01.01.2000' AND '31.12.2003';

DELETE FROM PRODUTOS
WHERE COD_FORNECEDOR IN (
&emsp;&emsp;SELECT COD_FORNECEDOR
&emsp;&emsp;FROM FORNECEDOR
&emsp;&emsp;WHERE COD_CIDADE = 5);
</pre>
<p>Caso você precise apagar registros de uma tabela relacionada com outra, ou outras tabelas do banco de dados, você precisará primeiro apagar todos os registros da tabela filha, que possui o valor de referencia da chave estrangeira, para só depois excluir o registro da tabela pai, a qual possui o valor da chave primária.</p>
<p>O servidor de banco de dados não permite que registros fiquem órfãos dentro da tabela, através da exclusão de registros primários dos quais eles dependem e estão relacionados através de uma Foreign Key.</p>
<p><b>Nota:</b> Você pode utilizar a cláusula Delete Cascade durante a definição da Foreign Key para permitir que, ao excluir um registro pai, todos os registros vinculados a ele sejam apagados automaticamente.</p>
<h2 align="center">Buscando Dados</h2>
<p>Através do comando Select, podemos realizar pesquisas e extrair informações das tabelas do banco de dados. Sem dúvida alguma a instrução Select é uma das mais importantes instruções SQL. Utilizando o comando Select, podemos buscar dados de uma ou mais tabelas do banco de dados, onde para isso contamos com inúmeros operadores que permitem que façamos essas buscas.</p>
<p>Usando os operadores disponíveis em conjunto dentro de uma instrução SQL, podemos fazer qualquer tipo de busca dentro das tabelas do banco de dados. Segue a seguir, a sintaxe básica da instrução Select:</p>
<pre>
SELECT LISTA_DE_COLUNAS
FROM LISTA_DE_TABELAS
WHERE CONDICOES
GROUP BY LISTA_DE_COLUNAS
ORDER BY LISTA_DE_COLUNAS;
</pre>
<p>Dentro de uma instrução Select, podemos buscar informações de colunas presentes e um ou mais tabelas relacionadas dentro do banco. No parâmetro Lista_de_Colunas, logo após a palavra reservada Select, podemos listar todas as colunas que queremos buscar da tabela.</p>
<p>Caso seja colocado o caractere asterisco (*), o servidor de banco de dados trará todas as colunas disponíveis dentro da tabela especificada na cláusula From. No parâmetro Lista_de_Tabelas devemos especificar o nome das tabelas que faremos a busca das informações. Veja alguns exemplos básicos de uso da instrução Select:</p>
<pre>
SELECT CODIGO, NOME
FROM CLIENTES;

SELECT * FROM CIDADES;

SELECT CODIGO, NOME, ENDERECO, FONE, BAIRRO, CIDADE, UF
FROM FORNECEDORES;

SELECT PROD_ID, PROD_DESCRICAO, FOR_NOME
FROM PRODUTOS, FORNECEDORES
WHERE PRODUTOS.FOR_ID = FORNECEDORES.FOR_ID;
</pre>
<p>Quanto você utiliza uma instrução Select para extrair informações contidas em duas ou mais tabelas, normalmente essas tabelas possuem pelo menos uma coluna fazendo o relacionamento entre elas.</p>
<p><b>Nota:</b> Você pode fazer o relacionamento entre duas tabelas durante uma instrução Select, independente de essas tabelas possuírem uma constraint de Foreign Key, ou não.</p>
<h2 align="center">Listando as Colunas</h2>
<p>Para listar as colunas que deseja trazer no resultado da instrução Select, informe-as logo após a palavra chave Select separando-as por vírgulas. Veja o exemplo a seguir:</p>
<pre>
SELECT CODIGO, NOME
FROM FUNCIONARIOS;
</pre>
<p>Caso você queira trazer todas as colunas de uma determinada tabela, você pode como comentado anteriormente, utilizar o caractere asterisco (*). Através dele, o servidor retornará todas as colunas da tabela em questão mostrando-as na ordem em que estão posicionadas dentro da tabela.</p>
<p>Caso você não utilize a cláusula Where para fazer algum filtro na instrução Select, o servidor de banco de dados retornará todas colunas e todos os registros da tabela. Veja o exemplo a seguir:</p>
<pre>
SELECT * FROM EMPRESAS;

SELECT * FROM EMPRESAS
WHERE UF = 'SP';
</pre>
<p>Quando você lista as colunas dentro da instrução Select, elas não precisam seguir a ordem em que estão armazenadas dentro da tabela, isso é, em um banco relacional a ordem das colunas não é importante, a não ser que você esteja utilizando essa instrução Select para fazer inserção de dados através de um Insert, por exemplo. O IB/FB possui a palavra reservada Distinct para que possamos aplicar nas colunas da instrução Select para remover valores duplicados.</p>
<p>Quando fazemos um Select sem a palavra Distinct, o servidor de banco de dados retorna os valores na ordem em que eles estão armazenados dentro da tabela em questão. Quando utilizamos à instrução Distinct o servidor agrupa os valores retornados pelo Select.</p>
<p>Para que possamos agrupar os valores duplicados dentro da instrução Select, para que o comando Distinct possa removê-los, devemos utilizar a cláusula Order By no final da instrução Select. Através da cláusula Order By podem ordenar o resultado do Select seguindo os valores de uma ou mais colunas disponíveis dentro do mesmo. Veja alguns exemplos a seguir:</p>
<pre>
SELECT DISTINCT NOME
FROM CLIENTES
ORDER BY NOME;

SELECT CODIGO, NOME, CIDADE
FROM FORNECEDORES
ORDER BY CIDADE, NOME;
</pre>
<p>Quando utilizamos a cláusula Order By, podemos utilizar os comandos Ascending (ASC) ou Descending (DESC) para especificar a ordem a qual a coluna será mostrada. Por padrão, se nenhum dos dois comandos for utilizado, o servidor retorna sempre seguindo a ordem ascendente dos valores das colunas. Veja a seguir, alguns exemplos de uso da cláusula Order By em conjunto com os comandos ASC e DESC:</p>
<pre>
SELECT NOME, UF
FROM CIDADE
ORDER BY NOME DESC;

SELECT CODIGO, DATA_VENDA, VALOR
FROM VENDAS
ORDER BY DATA_VENDA DESC, CODIGO ASC;

SELECT *
FROM EMPRESAS
ORDER BY UF ASC, CIDADE ASC, NOME DESC;
</pre>
<h2 align="center">Utilizando a cláusula Where</h2>
<p>Através da cláusula Where, podemos limitar o número de registros (linhas) retornados pela instrução Select. Como visto durante a explicação das cláusulas Update e Delete, podemos utilizar diversos operadores diferentes para fazer o filtro das informações a serem retornadas. Veja alguns exemplos:</p>
<pre>
SELECT * FROM CLIENTES
WHERE UF = 'PR';
</pre>
<p>Na instrução anterior, trazemos apenas os clientes que são do estado do Paraná.</p>
<pre>
SELECT CODIGO_VENDA, DATA_VENDA, VALOR_VENDA
FROM VENDAS
WHERE DATA_VENDA BETWEEN '01.01.2004' AND '31.12.2004';
</pre>
<p>Na instrução anterior, trazemos todas as vendas realizadas dentro do ano de 2004.</p>
<pre>
SELECT * FROM PRODUTOS
WHERE PROD_TIPO = 'A' OR PROD_TIPO = 'B';
</pre>
<p>Na instrução anterior, trazemos todos os produtos que são do tipo A ou B. A cláusula Where suporta ainda o uso de expressões aritméticas:</p>
<pre>
SELECT * FROM PEDIDOS
WHERE DATA_PEDIDO = 'TODAY' – 15;
</pre>
<p>Na instrução anterior, trazemos todos os pedidos que foram emitidos quinze dias atrás. Caso a coluna que faz parte da cláusula Where possuir um índice, o servidor irá utilizá-lo, se necessário para aumentar à performance na busca as informações. Entretanto, o IB/FB é capaz de utilizar índices apenas para certos tipos de condições Where. Veja algumas situações a seguir:</p>
<pre>
SELECT * FROM CIDADES
WHERE NOME = 'Curitiba';
</pre>
<p>Na instrução anterior, o índice na coluna span Nome pode ser utilizado pelo servidor, pois estamos buscando por um valor exato para fazer o filtro.</p>
<pre>
SELECT * FROM CIDADES
WHERE NOME LIKE '%José%';
</pre>
<p>Já na instrução anterior, o servidor não é capaz de utilizar um índice para acelerar a busca, pois o valor que estamos procurando aparece no meio da coluna. Dessa maneira, o servidor espera por valores aleatórios nos dois lados da coluna, não tendo assim, como utilizar um índice.</p>
<pre>
SELECT * FROM CIDADES
WHERE NOME STARTING WITH 'São';
</pre>
<p>Na instrução anterior, o servidor utiliza um índice, pois o mesmo possui uma combinação exata de valores no início da coluna para realizar a busca de forma indexada.</p>
<h2 align="center">Utilizando Alias para Tabelas</h2>
<h2>Referências</h2>
<p>https://www.devmedia.com.br/10-instrucoes-sql-para-manipulacao-de-dados/4832</p>
