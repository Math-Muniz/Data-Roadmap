<h1 align="center">Manipulação de Dados</h1>
<p>Neste capítulo, mostraremos os principais comandos SQL para manipulação dos dados armazenados nas tabelas do banco. Esse capítulo, abordará os comandos DML, disponíveis para inserção, alteração, deleção e seleção de dados.</p>
<h2 align="center">Adicionado, Alterando e Removendo Dados</h2>
<p>Para inserir, alterar ou apagar dados nas tabelas do banco, através de instruções SQL, devemos utilizar os comandos Insert, Update e Delete respectivamente. Através desses três comandos, manipulamos as informações em uma ou mais tabelas do banco de dados.</p>
<h2 align="center">Utilizando a Instrução Insert</h2>
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
<h2 align="center">Inserindo Várias Linhas</h2>
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
<h2 align="center">Utilizando a Instrução Update</h2>
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
<h2 align="center">Utilizando a Instrução Delete</h2>
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
<h2 align="center">Utilizando a Cláusula Where</h2>
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
<p>Em instruções Select, que fazem buscas em duas ou mais tabelas do banco de dados, retornando um grande número de colunas em seu resultado, podem ficar extensas e tediosas para serem montadas.</p>
<p>Para ajudar e facilitar, o IB/FB permite que você especifique um alias (apelido) para cada tabela utilizada dentro da instrução SQL. Normalmente os alias são uma ou duas letras, como por exemplo “C” para Clientes, ou “F” para Fornecedores. Para utilizar um alias dentro de uma instrução Select coloque-o logo após o nome da tabela dentro da cláusula From:</p>
<pre>
SELECT C.CODIGO, C.NOME, C.UF
FROM CIDADES C
ORDER BY C.NOME;
</pre>
<p><b>Nota:</b> O uso de alias não é obrigatório, porém, ele pode facilitar a digitação de instruções SQL mais complexas e melhora o entendimento das mesmas.</p>
<h2 align="center">Utilizando Joins</h2>
<p>Normalmente, você terá que realizar consultas em mais de uma tabela ao mesmo tempo para conseguir extrair as informações que precisa. Em bancos de dados relacionais normalizados, as informações normalmente ficam distribuídas em várias tabelas do banco de dados. Para fazer a busca em várias tabelas através de um único comando Select, precisamos ligá-las através de colunas relacionadas, normalmente especificadas e identificadas através do uso de Foreign Key.</p>
<p>Vamos analisar o seguinte exemplo: Suponhamos que no nosso banco de dados, temos uma tabela de Clientes, a qual possui a coluna Cli_Id que é definida como chave primária da tabela, a qual garante a identificação de cada registro de forma única. Nesse mesmo banco, temos as tabelas de Vendas, Pedidos e Contatos. Cada uma dessas tabelas também possui um campo Cli_Id, o qual foi definido (ou não) utilizando uma Foreign Key ligando a coluna Cli_Id da tabela Clientes.</p>
<p>Para que possamos buscar as informações de um determinado cliente junto com todos os pedidos emitidos para o mesmo, teremos que fazer um join (ligação) entre a tabela de clientes e a de pedidos, para conseguirmos montar o resultado com as colunas que precisamos.</p>
<p><b>Nota:</b> O IB/FB não impede que façamos ligações sem sentido. Podemos, por exemplo, ligar a coluna Cliente.Uf com a coluna Cidade.Pais. O servidor realizará a pesquisa, porém nenhum resultado será retornado, visto que não existem valores combinantes nessas duas colunas.</p>
<h2 align="center">Sintaxe Utilizada para Realização de Join</h2>
<p>Tanto o InterBase quanto o Firebird suportam duas diferentes sintaxes para o uso da instrução Join:</p>
<pre>
SELECT LISTA_DE_COLUNAS
FROM TABELA1, TABELA2
WHERE TABELA.COLUNA1 = TABELA2.COLUNA1;
</pre>
<p>Essa sintaxe faz a união das colunas relacionadas dentro da cláusula Where da instrução Select:</p>
<pre>
SELECT C.CODIGO, C.NOME, E.SIGLA
FROM CIDADES C, ESTADOS E
WHERE C.COD_ESTADO = E.COD_ESTADO;

SELECT C.CODIGO, C.NOME, CID.NOME, E.NOME
FROM CLIENTES C, CIDADES CID, ESTADOS E
WHERE C.COD_CIDADE = CID.COD_CIDADE
AND CID.COD_ESTADO = E.COD_ESTADO;
</pre>
<p>A segunda sintaxe que pode ser utilizada é a sintaxe que segue o padrão SQL-92. Nessa sintaxe, a união às colunas relacionadas é realizada dentro da cláusula From da instrução Select, deixando assim a cláusula Where apenas para filtros das informações a serem buscadas:</p>
<pre>
SELECT LISTA_DE_COLUNAS
FROM TABELA1
JOIN TABELA2 ON TABELA1.COLUNA1 = TABELA2.COLUNA1
WHERE CONDICOES;
</pre>
<p>Veja alguns exemplos de uso dessa sintaxe padrão SQL-92:</p>
<pre>
SELECT C.CODIGO, C.NOME, E.SIGLA
FROM CIDADES
JOIN ESTADOS ON CIDADES.COD_ESTADO = ESTADOS.COD_ESTADO;

SELECT C.NOME, V.DATA_VENDA, I.QUANTIDADE
FROM CLIENTES C
JOIN VENDAS V ON (V.COD_CLIENTE = C.COD_CLIENTE)
JOIN ITENS I ON (I.COD_VENDA = V.COD_VENDA);
</pre>
<p>Como vimos nos últimos exemplos, podemos incluir colunas de quaisquer das tabelas utilizadas dentro da instrução Select. Nesse tipo de instrução Select, o uso de alias podem facilitar bastante, visto que, em algumas situações poderemos ter colunas de tabelas diferentes com o mesmo nome. Veja o exemplo a seguir:</p>
<pre>
SELECT E.NOME, P.NOME
FROM ESTADOS E
JOIN PAIS P ON E.COD_PAIS = P.COD_PAIS;
</pre>
<p>Na instrução anterior, tanto a tabela Estados, como a tabela Pais possuem um campo denominado Nome. Nessas situações o uso de alias pode ser bastante útil para que possamos identificar cada coluna dentro da instrução Select.</p>
<p><b>Nota:</b> O IB/FB não possui nenhum limite para utilização de Join’s dentro de instruções Select. Você pode unir quantas tabelas forem necessárias para trazer o resultado que precisa.</p>
<h2 align="center">Utilizando Alias para Colunas</h2>
<p>Como em tabelas, podemos também definir um alias para as colunas que são retornadas dentro da instrução Select. Veja a seguir, a sintaxe básica para o uso de alias em colunas:</p>
<pre>
SELECT COLUNA1 AS ALIAS1, COLUNA2 AS ALIAS2
FROM LISTA_DE_TABELAS;
</pre>
<p>O uso de alias em colunas também não são obrigatórias, porém, em determinadas situações podem ser bastante úteis para facilitar a identificação de cada coluna dentro da instrução Select. Veja alguns exemplos a seguir:</p>
<pre>
SELECT E.NOME AS ESTADO, P.NOME AS PAIS
FROM ESTADOS E, PAIS P
WHERE E.COD_PAIS = P.COD_PAIS;
</pre>
<p>O uso do operador As, para definição do alias da coluna não é obrigatório, isso é, você pode definir o alias diretamente após especificar o nome da coluna. Veja o exemplo a seguir:</p>
<pre>
SELECT C.NOME CLIENTE, E.UF ESTADO
FROM CLIENTES C
JOIN ESTADOS E ON C.COD_ESTADO = E.COD_ESTADO
WHERE C.CODIGO = 12;
</pre>
<h2 align="center">Criando Novas Colunas</h2>
<p>Durante a construção de uma instrução Select, podemos derivar novas colunas através das existentes. Veja alguns exemplos de derivação de novas colunas:</p>
<pre>
SELECT NOME || ' , ' || ENDERECO || ' , ' || BAIRRO || ' , ' || CIDADE
FROM CLIENTES
WHERE UF = 'RS';
</pre>
<p>Na instrução anterior, é retornado apenas uma coluna contendo a concatenação das colunas Nome, Endereco, Bairro e Cidade com seus valores separados por vírgula. Através do par de barras verticais (| |) o servidor de banco de dados identifica a concatenação entre colunas ou valores dentro da instrução SQL.</p>
<p><b>Nota:</b> Apenas colunas do tipo Char e VarChar suportam concatenação. Para realizar a concatenação de colunas de outros tipos utilize a função Cast para convertê-las em string antes.</p>
<p>Você também pode realizar operações matemáticas entre colunas existentes na instrução para gerar uma nova coluna com o resultado da operação. Veja o exemplo a seguir:</p>
<pre>
SELECT COD_VENDA, DATA_VENDA - DATA_PRIMEIRO_CONTATO AS TEMPO_PRA_VENDA
FROM VENDAS;
</pre>
<p>Na instrução anterior, criamos uma nova coluna de nome Tempo_pra_Venda, a qual é resultante da subtração das colunas Data_Venda e Data_Primeiro_Contato. O tipo do valor retornado pela coluna Tempo_pra_Venda será numérico trazendo o resultado da subtração das duas datas.</p>
<h2 align="center">Utilizando Funções em Instruções SQL</h2>
<p>O InterBase e o Firebird suportam várias funções internas que podem ser utilizadas dentro de instruções SQL em geral.</p>
<p><b>Nota:</b> Você pode adicionar ou criar suas próprias funções para utilização dentro do IB/FB através de UDF (Funções Definidas pelo Usuário).</p>
<h3 align="center">A Função Cast</h3>
<p>Podemos converter dados de um tipo para outro dentro de uma instrução SQL. Um exemplo de uso dessa função, por exemplo, seria a conversão de uma coluna do tipo numérico para VarChar para que a mesma possa ser concatenada com outra coluna ou valor durante o resultado de uma instrução Select.</p>
<p>Outra situação onde a função Cast pode ser útil, é em instruções de Insert que são geradas a partir de uma instrução Select para inclusão dos dados. Veja abaixo a sintaxe básica da função Cast:</p>
<pre>
CAST (COLUNA_ORIGEM AS NOVO_TIPO)
</pre>
<p>Você pode utilizar a instrução Cast para converter uma string, que possui um formato de data em uma data real, ou ainda, converter strings que possuem apenas valores numéricos em números inteiros ou flutuantes. Veja alguns exemplos de uso da instrução Cast:</p>
<pre>
SELECT CODIGO, CAST(DATA_VENDA AS CHAR(10)), 'VENDA: ' || CAST(NUM_VENDA AS VARCHAR(5))
FROM VENDAS
WHERE DATA_VENDA BETWEEN 'YESTERDAY' AND 'TODAY';
</pre>
<h3 align="center">A Função Upper</h3>
<p>Podemos converter todos os caracteres de uma string para maiúsculo. Essa função pode somente ser utilizada em colunas do tipo Char ou VarChar:</p>
<pre>
SELECT NOME, UPPER(NOME)
FROM CLIENTES;
</pre>
<p>Na instrução anterior, fazemos a comparação do campo cidade com o valor Curitiba, onde, para essa comparação, convertemos todos os valores da coluna Cidade para maiúsculo, garantindo assim que todos os fornecedores cadastrados para a cidade de Curitiba serão retornados no Select.</p>
<p><b>Nota:</b> Para o uso da função Lower, verifique a biblioteca (DLL) que acompanha o InterBase, a qual contem diversas UDF’s para uso.</p>
<p>Tanto o InterBase quanto o Firebird, possuem ainda funções para que possamos agregar valores através de mais de uma linha de uma tabela. Através dessas funções de agregação, podemos coletar valores de várias linhas em uma única linha. Você pode, por exemplo, calcular a média de uma coluna que contem diversos valores, sua soma, maior valor ou menor valor etc.</p>
<h3 align="center">A Função Sum</h3>
<p>Podemos somar todos os valores de uma coluna especifica dentro de uma instrução SQL:</p>
<pre>
SELECT SUM(VALOR)
FROM VENDAS
WHERE COD_CLI = 10;
</pre>
<h3 align="center">A Função Avg</h3>
<p>Podemos calcular a média dos valores armazenados em uma determinada coluna utilizada dentro de uma instrução SQL:</p>
<pre>
SELECT AVG(IDADE)
FROM CLIENTES
WHERE NUM_DEPENDENTES = 2;
</pre>
<h3 align="center">A Função Count</h3>
<p>Podemos retornar o número total de linhas de uma determinada coluna:</p>
<pre>
SELECT COUNT(NOME)
FROM CLIENTES
WHERE DATA_CADASTRO > 'TODAY' – 265;
</pre>
<h3 align="center">A Função Min</h3>
<p>Podemos trazer o menor valor armazenado dentro de uma coluna especifica em uma instrução SQL:</p>
<pre>
SELECT MIN(VALOR)
FROM VENDAS;
</pre>
<h3 align="center">A Função Max</h3>
<p>Podemos trazer o maior valor encontrado dentro de uma coluna listada na instrução SQL:</p>
<pre>
SELECT MAX(QUANTIDADE)
FROM PEDIDOS
WHERE COD_REPRESENTANTE = 1203;
</pre>
<p><b>Nota:</b> Quando você utiliza uma das funções de agregação, o servidor de banco de dados nomeia a coluna com o nome da função. Para renomear a coluna, especifique um alias para a mesma, através do operador As.</p>
<p>Quando utilizamos a função Count, normalmente é para trazer o número total de registros encontrados dentro da instrução SQL passada. Porém, podem surgir casos que você precise trazer a quantidade total dos registros retirando os valores duplicados. Para isso, utilize a função Count em conjunto com o comando Distinct:</p>
<pre>
SELECT COUNT(CIDADE), COUNT(DISTINCT(CIDADE))
FROM CLIENTES;
</pre>
<p>Na instrução anterior, trazemos na primeira coluna o número total de cidades encontradas na tabela Clientes, enquanto que na segunda coluna trazemos apenas o número total de cidades únicas (removendo as duplicadas) encontradas dentro da tabela Clientes.</p>
<h2 align="center">Utilizando a Cláusula Group By</h2>
<p>Através da instrução Group By, podemos agrupar linhas dentro de instruções SQL para aumentar a funcionalidade das funções de agregação disponíveis. Através da linguagem SQL, você pode especificar quais colunas serão utilizadas para o agrupamento dos registros e quais serão utilizadas nos cálculos utilizando as funções de agregação.</p>
<p>A cláusula Group By deve sempre ser inserida após a cláusula Where e sempre antes da cláusula Order By. Como regra obrigatória, as colunas que forem listadas dentro da cláusula Group By devem sempre estar presentes na lista de colunas na cláusula Select da instrução SQL:</p>
<pre>
SELECT COLUNA1, COLUNA2, SUM(COLUNA3)
FROM LISTA_DE_TABELAS
WHERE CONDICOES
GROUP BY COLUNA1, COLUNA2
ORDER BY COLUNA1;
</pre>
<p>Veja alguns exemplos de uso da cláusula Group By:</p>
<pre>
SELECT C.NOME, SUM(V.VALOR)
FROM CLIENTES C, VENDAS V
WHERE V.COD_CLI = C.COD_CLI
GROUP BY C.NOME
ORDER BY C.NOME;
</pre>
<p>Na instrução anterior, trazemos a soma de todas as vendas cadastradas agrupadas e ordenadas por cliente.</p>
<pre>
SELECT E.SIGLA, C.CIDADE, AVG(P.VALOR) AS VALOR_MEDIO
FROM ESTADOS E, CIDADES C, PEDIDOS P
WHERE P.COD_CIDADE = C.COD_CIDADE
AND C.COD_ESTADO = E.COD_ESTADO
GROUP BY E.SIGLA, C.CIDADE
ORDER BY E.SIGLA, C.CIDADE
</pre>
<p>Na instrução anterior, trazemos o valor médio dos pedidos cadastrados agrupados por estado e por cidade.</p>
<pre>
SELECT R.NOME, COUNT(F.NOME)
FROM REGIOES R, FORNECEDORES F
WHERE F.REG_CODIGO = R.REG_CODIGO
GROUP BY R.NOME
ORDER BY R.NOME;
</pre>
<p>Na instrução anterior, trazemos a quantidade total de fornecedores agrupados e ordenados por região.</p>
<h2 align="center">Utilizando a Cláusula Having</h2>
<p>Através da cláusula Having, podemos trazer uma soma ou contagem, mas apenas com os resultados onde o valor retornado pela função de agregação atinja uma determinada condição:</p>
<pre>
SELECT C.NOME, COUNT(V.COD_VENDAS)
FROM VENDAS V, CLIENTES C
WHERE V.COD_CLI = C.COD_CLI
GROUP BY C.NOME;
</pre>
<p>Na instrução anterior, trazemos a quantidade total de vendas agrupadas por cliente. Caso quiséssemos trazer apenas os clientes que tiveram mais de 15 vendas cadastradas, devemos montar a seguinte instrução SQL:</p>
<pre>
SELECT C.NOME, COUNT(V.COD_VENDAS)
FROM VENDAS V, CLIENTES C
WHERE V.COD_CLI = C.COD_CLI
GROUP BY C.NOME
HAVING COUNT(V.COD_VENDAS) > 15;
</pre>
<h2 align="center">Tipos de Joins</h2>
<p>Quando utilizamos um Join para fazer a união de duas ou mais tabelas, afim de trazer o resultado contendo as informações solicitadas, os resultados são incluídos apenas onde os valores unidos aparecem em ambas as tabelas.</p>
<p>Vamos analisar o seguinte exemplo: Suponhamos que em nosso banco de dados, tenhamos duas tabelas, uma com o cadastro de médicos e outra com o cadastro das consultas dos mesmos. Veja a seguinte instrução SQL:</p>
<pre>
SELECT M.NOME, COUNT(C.CODIGO)
FROM MEDICOS M
JOIN CONSULTAS C ON (C.COD_MEDICO = M.COD_MEDICO)
GROUP BY M.NOME;
</pre>
<p>Na instrução SQL anterior, trazemos a quantidade total de consultas para cada médico cadastrado. Este tipo de Join é conhecido como Inner Join, apesar da palavra Inner não ser obrigatória dentro da instrução SQL. E se nós precisássemos trazer os médicos que não possuem nenhuma consulta cadastrada, porém estão cadastrados dentro da tabela Medicos.</p>
<p>A instrução anterior, não trás esses médicos, e sim, apenas os que possuem pelo menos uma consulta cadastrada na tabela Consultas. Para resolver esse problema, devemos realizar um Join do tipo Outer Join. Existem três tipos de Outer Join’s:</p>
<ul>
  <li>Left Outer Join: Inclui todas as linhas da tabela do lado esquerdo da expressão Join;</li>
  <li>Right Outer Join: Inclui todas as linhas da tabela do lado direito da expressão Join;</li>
  <li>Full Outer Join: Inclui todas as linhas de ambas as tabelas utilizadas na expressão.</li>
</ul>
<p>Veja a seguir, a instrução SQL para trazer todos os médicos cadastrados, mesmo que não tenham consultas referenciadas a eles:</p>
<pre>
SELECT M.NOME, COUNT(C.CODIGO)
FROM MEDICOS M
LEFT JOIN CONSULTAS C ON (C.COD_MEDICO = M.COD_MEDICO)
GROUP BY M.NOME;
</pre>
<p>Utilizando o Join do tipo Left Join, trazemos todos os registros da tabela Medicos (lado esquerdo da expressão Join), mesmo que alguns deles não possuam registros relacionados na tabela Consultas.</p>
<h2 align="center">Utilizando SubQueries</h2>
<p>Quando utilizamos uma instrução Select, podemos utilizar dentro de sua cláusula Where, outra instrução Select, desde que a mesma retorne apenas um valor simples, ou uma coluna contendo um conjunto de valores que podem ser utilizados para o filtro da instrução Select mais externa.</p>
<p>Quando utilizamos instruções de Select dentro de outra instrução Select, estamos utilizando uma SubQuery. Nos próximos exemplos, vamos utilizar uma instrução Select que retorna um único valor ou uma única coluna para ser utilizada pelo Select principal. No exemplo a seguir, fazemos um Select para trazer todos os produtos de todos os fabricantes que residem em um estado específico:</p>
<pre>
SELECT CODIGO_PRODUTO, DESCRICAO_PRODUTO, VALOR_PRODUTO
FROM PRODUTOS
WHERE CODIGO_FORNECEDOR IN (
&emsp;&emsp;SELECT CODIGO_FORNECEDOR
&emsp;&emsp;FROM FORNECEDORES
&emsp;&emsp;WHERE UF = 'RJ');
</pre>
<p>Na instrução (query) a seguir, fazemos a busca por todos os pedidos que possuem o tipo definido como “Y”, fazendo a busca através da coluna Num_Pedido da tabela:</p>
<pre>
SELECT CODIGO, NUM_PEDIDO, DATA_PEDIDO, TIPO
FROM PEDIDOS
WHERE NUM_PEDIDO = (
&emsp;&emsp;SELECT NUM_PEDIDO
&emsp;&emsp;FROM PEDIDOS
&emsp;&emsp;WHERE TIPO = 'Y');
</pre>
<h2 align="center">Utilizando os operadores All e Any</h2>
<p>Vamos imaginar a seguinte situação: suponhamos que você precise trazer todos os pedidos que são maiores que os pedidos de um cliente específico. Para conseguir fazer essa instrução SQL, você pode utilizar o operador All. Veja o exemplo:</p>
<pre>
SELECT CODIGO, CODIGO_CLIENTE, DATA, VALOR
FROM PEDIDOS
WHERE VALOR > ALL (
&emsp;&emsp;SELECT VALOR
&emsp;&emsp;FROM PEDIDOS
&emsp;&emsp;WHERE CODIGO_CLIENTE = 200);
</pre>
<p>Quando utilizamos a expressão All, o servidor de banco de dados compara todas as linhas retornadas na subquery para verificar o seu valor. Nesse caso, podemos substituir a instrução anterior pela seguinte:</p>
<pre>
SELECT CODIGO, CODIGO_CLIENTE, DATA, VALOR
FROM PEDIDOS
WHERE VALOR > (
&emsp;&emsp;SELECT MAX(VALOR)
&emsp;&emsp;FROM PEDIDOS
&emsp;&emsp;WHERE CODIGO_CLIENTE = 200);
</pre>
<p>Dessa maneira, a subquery gera um único registro trazendo o pedido de maior valor do cliente de código 200. Nesse caso, a comparação será feita em apenas um registro, aumentando consideravelmente a performance da instrução SQL.</p>
<p><b>Nota:</b> Caso você esteja utilizando a expressão All, você pode utilizar a função Min para aumentar a performance da consulta.</p>
<p>Você pode também utilizar dentro de instruções SQL, o operador Any, o qual tem como sinônimo o operador Some:</p>
<pre>
SELECT CODIGO, CODIGO_CLIENTE, DATA, VALOR
FROM PEDIDOS
WHERE VALOR > ANY (
&emsp;&emsp;SELECT VALOR
&emsp;&emsp;FROM PEDIDOS
&emsp;&emsp;WHERE CODIGO_CLIENTE = 200);
</pre>
<p>Nesse caso, retornamos todos os pedidos que são maiores que qualquer pedido feito pelo cliente de código 200. Como no caso da query que utiliza o operador All, esse método não é muito eficiente para realizar a busca, devido as inúmeras comparações que terão que ser realizadas dentro da subquery. Sempre que você utilizar a expressão Any, utilize no lugar a função Min. Caso a expressão seja Any, utilize então a função Max.</p>
<p><b>Nota:</b> SubQuery’s que retornam um único valor são muito eficientes, e, caso tenham um índice vinculado na coluna sendo testada, sua performance será maior ainda. Nos exemplos mostrados, a coluna que precisaria de um índice seria a coluna Valor.</p>
<h2>Referências</h2>
<p>https://www.devmedia.com.br/10-instrucoes-sql-para-manipulacao-de-dados/4832</p>
