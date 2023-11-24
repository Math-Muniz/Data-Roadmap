<h1 align="center">DBSCAN</h1>
<h2 align="center">O que é “Clustering” ?</h2>
<p>Clustering se trata de uma técnica muito utilizada em diferentes campos de análises estatísticas. Análise de imagens, mineração de dados, bioinformática e machine learning são apenas algumas áreas onde esta técnica pode ser aplicada. No campo de Machine Learning, ela faz parte da área de aprendizado não supervisionado.</p>
<img src="grafico-01.webp">
<p>Aplicar a técnica de clustering se resume em agrupar dados que se relacionam. Imagine-se como um comerciante que possui uma boa quantidade de dados sobre seus clientes e pretende com isso segmentá-los para entender suas necessidades individuais. Utilizar um método de clustering parece ser uma ótima iniciativa, pois você conseguirá agrupar os clientes baseados em dados como registros de compras, frequência das compras entre outros. No entanto, para cada problema é necessário escolher o algoritmo de clustering mais interessante de análise.</p>
<h2 align="center">Modelos famosos de Clustering</h2>
<ul>
  <li><b>K-Means</b>- O modelo conhecido como K-Means é um dos mais famosos e importantes nas análises de clustering. O objetivo por trás dele é encontrar um número K de clusters em uma amostra. Ele faz isso definindo centróides, que são sempre atualizados utilizando o valor médio dos pontos próximos daquele cluster. O aprimoramento desses centróides nas iterações do algoritmo são chave para que estes virem referências confiáveis para classificação de novos dados posteriormente.</li>
  <li><b>Clustering Hierárquico</b>- Outro modelo muito conhecido para realizar clustering se trata do Clustering Hierárquico. Este algoritmo trabalha de uma forma parecida com uma árvore de decisão. Na abordagem Top-Down, é criado um único cluster com todos os dados que depois se divide em diversos clusters menores. Já na abordagem Bottom-Up ocorre o inverso, primeiro são gerados diversos clusters pequenos que se juntam em um cluster maior ao final. Em ambas abordagens é gerado um Dendograma, um gráfico responsável por concluir qual o melhor número de clusters para aquela amostra.</li>
</ul>
<h2 align="center">Modelo DBSCAN</h2>
<p>Finalmente, o modelo DBSCAN, sigla dada para “Density-Based Spatial Clustering of Applications with Noise”, possui uma abordagem de agrupamento baseado na densidade. A densidade de pontos em determinada região é responsável pela formação dos clusters. Caso um determinado ponto não obedeça critérios de densidade ou critérios dos limites de distância, este não pode ser classificado em um cluster.</p>
<h3 align="center">Parâmetros</h3>
<p>Os dois parâmetros necessários para aplicação do modelo DBSCAN são:</p>
<ul>
  <li><b>Eps:</b> Raio máximo em que dois pontos podem estar para serem considerados do mesmo cluster.</li>
  <li><b>MinPts:</b> Número mínimo de pontos em uma região necessários para garantir uma densidade desejada.</li>
</ul>
