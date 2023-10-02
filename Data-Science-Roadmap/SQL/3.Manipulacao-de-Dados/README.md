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
<h2>Referências</h2>
<p>https://www.devmedia.com.br/10-instrucoes-sql-para-manipulacao-de-dados/4832</p>
