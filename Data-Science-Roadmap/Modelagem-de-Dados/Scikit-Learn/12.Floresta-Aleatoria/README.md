<h1 align="center">Floresta Aleatória (Random Forest)</h1>
<p>Random Forest é um algoritmo de aprendizado de máquina amplamente utilizado, desenvolvido por Leo Breiman e Adele Cutler, que combina a saída de múltiplas árvores de decisão para obter um único resultado. Sua facilidade de uso e flexibilidade impulsionaram sua adoção, pois lida tanto com problemas de classificação quanto de regressão. Neste artigo, vamos entender como o algoritmo Random Forest funciona, como ele difere de outros algoritmos e como usá-lo.</p>
<h2 align="center">O que é o Algoritmo Floresta Aleatória (Random Forest)?</h2>
<p>A ampla popularidade do algoritmo Random Forest advém de sua natureza amigável ao usuário e adaptabilidade, permitindo lidar efetivamente tanto com problemas de classificação quanto de regressão. A força do algoritmo reside em sua capacidade de lidar com conjuntos de dados complexos e mitigar o overfitting, tornando-o uma ferramenta valiosa para várias tarefas preditivas em aprendizado de máquina.</p>
<p>Uma das características mais importantes do algoritmo Random Forest é que ele pode lidar com conjuntos de dados contendo variáveis contínuas, como no caso da regressão, e variáveis categóricas, como no caso da classificação. Ele apresenta um desempenho melhor para tarefas de classificação e regressão. Neste tutorial, vamos entender o funcionamento do Random Forest e implementar o algoritmo em uma tarefa de classificação.</p>
<h2 align="center">Analogia da Vida Real do Random Forest</h2>
<p>Vamos explorar uma analogia da vida real para entender melhor esse conceito. Um estudante chamado X deseja escolher um curso após o ensino médio, e está confuso sobre a escolha do curso com base em suas habilidades. Então, ele decide consultar várias pessoas, como primos, professores, pais, estudantes universitários e trabalhadores. Ele faz a eles diversas perguntas, como por que deveria escolher esse curso, oportunidades de emprego com esse curso, taxa do curso, etc. Finalmente, após consultar várias pessoas sobre o curso, ele decide fazer o curso sugerido pela maioria.</p>
<img src="r1.png">
<h2 align="center">Funcionamento do Algoritmo Random Forest</h2>
<p>Antes de entender o funcionamento do algoritmo de random forest em aprendizado de máquina, devemos examinar a técnica de aprendizado em conjunto. A técnica de aprendizado em conjunto simplesmente significa combinar vários modelos. Assim, uma coleção de modelos é usada para fazer previsões em vez de um modelo individual.</p>
<p>O aprendizado em conjunto utiliza dois tipos de métodos:</p>
<h3 align="center">Boosting</h3>
<p>Isso combina aprendizes fracos em aprendizes fortes, criando modelos sequenciais de forma que o modelo final tenha a maior precisão. Por exemplo, ADA BOOST, XG BOOST.</p>
<h3 align="center">Bagging</h3>
<p>Isso cria um subconjunto de treinamento diferente a partir de dados de treinamento amostrais com reposição, e a saída final é baseada na votação majoritária. Por exemplo, Random Forest.</p>
<img src="r2.png">
<p>Como mencionado anteriormente, o Random Forest opera segundo o princípio do Bagging. Agora, vamos aprofundar e entender o Bagging em detalhes.</p>
<h3 align="center">Bagging</h3>
<p>Bagging, também conhecido como Bootstrap Aggregation, serve como a técnica de aprendizado em conjunto no algoritmo Random Forest. Aqui estão as etapas envolvidas no Bagging:</p>
<ul>
  <li><b>Seleção do Subconjunto:</b> O Bagging começa escolhendo uma amostra aleatória, ou subconjunto, de todo o conjunto de dados.</li>
  <li><b>Amostragem Bootstrap:</b> Em seguida, cada modelo é criado a partir dessas amostras, chamadas de Amostras Bootstrap, que são retiradas dos dados originais com reposição. Esse processo é conhecido como amostragem de linhas.</li>
  <li><b>Bootstrapping:</b> A etapa de amostragem de linhas com reposição é chamada de bootstrapping.</li>
  <li><b>Treinamento Independente do Modelo:</b> Cada modelo é treinado independentemente em sua correspondente Amostra Bootstrap. Esse processo de treinamento gera resultados para cada modelo.</li>
  <li><b>Votação Majoritária:</b> A saída final é determinada combinando os resultados de todos os modelos por meio da votação majoritária. A previsão mais comum entre os modelos é selecionada.</li>
  <li><b>Agregação:</b> Esta etapa, que envolve a combinação de todos os resultados e a geração da saída final com base na votação majoritária, é conhecida como agregação</li>
</ul>
<img src="r3.png">
<p>Agora, vamos analisar um exemplo, quebrando-o com a ajuda da seguinte figura. Aqui, a amostra bootstrap é retirada dos dados reais (Amostra Bootstrap 01, Amostra Bootstrap 02 e Amostra Bootstrap 03) com reposição, o que significa que há uma alta probabilidade de que cada amostra não contenha dados exclusivos. O modelo (Modelo 01, Modelo 02 e Modelo 03) obtido dessa amostra bootstrap é treinado de forma independente. Cada modelo gera resultados conforme mostrado. Agora, o emoji Feliz tem maioria em comparação com o emoji Triste. Assim, com base na votação majoritária, a saída final é obtida como o emoji Feliz.</p>
<img src="r4.png">
<h3 align="center">Boosting</h3>
<p>Boosting é uma das técnicas que utiliza o conceito de aprendizado em conjunto. Um algoritmo de boosting combina vários modelos simples (também conhecidos como aprendizes fracos ou estimadores base) para gerar a saída final. Isso é feito construindo um modelo usando modelos fracos em série.</p>
<p>Existem vários algoritmos de boosting; o AdaBoost foi o primeiro algoritmo de boosting realmente bem-sucedido desenvolvido para fins de classificação binária. AdaBoost é uma abreviação de Adaptive Boosting e é uma técnica de boosting prevalente que combina múltiplos "classificadores fracos" em um único "classificador forte". Existem outras técnicas de boosting que você pode procurar saber mais sobre.</p>
<h3 align="center">Passos Envolvidos no Algoritmo Random Forest</h3>
<ul>
  <li><b>Passo 1:</b> No modelo de Random Forest, um subconjunto de pontos de dados e um subconjunto de características são selecionados para construir cada árvore de decisão. Em termos simples, n registros aleatórios e m características são retirados do conjunto de dados que possui k registros.</li>
  <li><b>Passo 2:</b> Árvores de decisão individuais são construídas para cada amostra.</li>
  <li><b>Passo 3:</b> Cada árvore de decisão gera uma saída.</li>
  <li><b>Passo 4:</b> A saída final é considerada com base na Votação Majoritária ou na Média, para Classificação e regressão, respectivamente.</li>
</ul>
<p><b>Por exemplo:</b></p>
<p>Considere a cesta de frutas como os dados, conforme mostrado na figura abaixo. Agora, n amostras são retiradas da cesta de frutas, e uma árvore de decisão individual é construída para cada amostra. Cada árvore de decisão gera uma saída, conforme mostrado na figura. A saída final é considerada com base na votação majoritária. Na figura abaixo, você pode ver que a maioria das árvores de decisão dá como saída uma maçã em comparação com uma banana, então a saída final é considerada como uma maçã.</p>
<img src="r5.png">
<h2 align="center">Características Importantes do Random Forest</h2>
<ul>
  <li><b>Diversidade:</b> Nem todos os atributos/variáveis/características são considerados ao criar uma árvore individual; cada árvore é diferente.</li>
  <li><b>Imune à Maldição da Dimensionalidade:</b> Como cada árvore não considera todas as características, o espaço de características é reduzido.</li>
  <li><b>Paralelização:</b> Cada árvore é criada independentemente a partir de dados e atributos diferentes. Isso significa que podemos utilizar totalmente a CPU para construir florestas aleatórias.</li>
  <li><b>Divisão de Treino-Teste:</b> Em uma floresta aleatória, não precisamos segregar os dados para treino e teste, pois sempre haverá 30% dos dados que não são vistos pela árvore de decisão.</li>
  <li><b>Estabilidade:</b> A estabilidade surge porque o resultado é baseado em votação majoritária/média.</li>
</ul>
<h2 align="center">Diferença Entre Árvore de Decisão e Random Forest</h2>
<p>Random Forest é uma coleção de árvores de decisão; ainda assim, há muitas diferenças em seu comportamento.</p>
<table>
    <tr>
        <th>Árvores de Decisão</th>
        <th>Random Forest</th>
    </tr>
    <tr>
        <td>1. Árvores de decisão normalmente sofrem com o problema de overfitting se forem permitidas a crescer sem controle.</td>
        <td>1. As florestas aleatórias são criadas a partir de subconjuntos de dados, e a saída final é baseada na média ou na classificação da maioria; portanto, o problema de overfitting é tratado.</td>
    </tr>
    <tr>
        <td>2. Uma única árvore de decisão é mais rápida em termos de computação.</td>
        <td>2. É comparativamente mais lenta.</td>
    </tr>
    <tr>
        <td>3. Quando um conjunto de dados com características é usado como entrada por uma árvore de decisão, ela formulará algumas regras para fazer previsões.</td>
        <td>3. A floresta aleatória seleciona aleatoriamente observações, constrói uma árvore de decisão e obtém o resultado médio. Não utiliza nenhum conjunto de fórmulas.</td>
    </tr>
</table>
<p>Assim, as florestas aleatórias são muito mais bem-sucedidas do que árvores de decisão apenas se as árvores forem diversas e aceitáveis.</p>
<h2 align="center">Hiperparâmetros Importantes em Random Forest</h2>
<p>Hiperparâmetros são usados em florestas aleatórias para melhorar o desempenho e o poder preditivo dos modelos ou para tornar o modelo mais rápido.</p>
<h3 align="center">Hiperparâmetros para Aumentar o Poder Preditivo</h3>
<ul>
  <li><b>n_estimators:</b> Número de árvores que o algoritmo constrói antes de fazer a média das previsões.</li>
  <li><b>max_features:</b> Número máximo de características que a floresta aleatória considera ao dividir um nó.</li>
  <li><b>min_samples_leaf:</b> Determina o número mínimo de folhas necessárias para dividir um nó interno.</li>
  <li><b>criterion:</b> Como dividir o nó em cada árvore? (Impureza de Entropia/Gini/Perda Logarítmica)</li>
  <li><b>max_leaf_nodes:</b> Número máximo de folhas em cada árvore.</li>
</ul>
<h3 align="center">Hiperparâmetros para Aumentar a Velocidade</h3>
<ul>
  <li><b>n_jobs:</b> Indica ao mecanismo quantos processadores ele pode usar. Se o valor for 1, ele usará apenas um processador, mas se o valor for -1, não há limite.</li>
  <li><b>random_state:</b> Controla a aleatoriedade da amostra. O modelo sempre produzirá os mesmos resultados se tiver um valor definido para o estado aleatório e receber os mesmos hiperparâmetros e dados de treinamento.</li>
  <li><b>oob_score:</b> OOB significa out of bag. É um método de validação cruzada para florestas aleatórias. Neste método, um terço da amostra não é usado para treinar os dados; em vez disso, é usado para avaliar o desempenho. Essas amostras são chamadas de amostras out-of-bag.</li>
</ul>
<h2 align="center">Hiperparâmetros Importantes em Random Forest</h2>
<p>Agora vamos implementar a Random Forest no scikit-learn.</p>
<h3 align="center">1. Importando as Bibliotecas</h3>
<pre>
# Importando as Bibliotecas Necessárias
import pandas as pd, numpy as np
import matplotlib.pyplot as plt, seaborn as sns
%matplotlib inline
</pre>
<h3 align="center">2. Importando o Dataset</h3>
<pre>
df = pd.read_csv('heart_v2.csv')
print(df.head())
</pre>
<img src="r6.png">
<h3 align="center">3. Colocando a Variável de Característica em X e a Variável-Alvo em Y.</h3>
<pre>
#Colocando a variável de característica em X
X = df.drop('heart disease', axis=1)
# Colocando a variável de resposta em y
y = df['heart disease']
</pre>
<h3 align="center">4. Realizando a Divisão Treino-Teste</h3>
<pre>
#Agora vamos dividir os dados em treino e teste
from sklearn.model_selection import train_test_split

#Dividindo os dados em treino e teste
X_train, X_test, y_train, y_test = train_test_split(X, y, train_size=0.7, random_state=42)
X_train.shape, X_test.shape
</pre>
<pre>
((189, 4), (81, 4))
</pre>
<h3 align="center">5. Importando RandomForestClassifier e ajustando os dados.</h3>
<pre>
from sklearn.ensemble import RandomForestClassifier

classifier_rf = RandomForestClassifier(random_state=42, n_jobs=-1, max_depth=5,
                                       n_estimators=100, oob_score=True)

%%time
classifier_rf.fit(X_train, y_train)
</pre>
<pre>
Wall Time: 241 ms
RandomForestClassifier(max_depth=5, n_jobs=-1, oob_score=True, random_state=42)
</pre>
<pre>
#Verificando o oob score
classifier_rf.oob_score_
</pre>
<pre>
0.656084656084656
</pre>
<h3 align="center">6. Ajustando os hiperparâmetros para Random Forest usando GridSearchCV e ajustando os dados.</h3>
<pre>
rf = RandomForestClassifier(random_state=42, n_jobs=-1)

params = {
    'max_depth': [2,3,5,10,20],
    'min_samples_leaf': [5,10,20,50,100,200],
    'n_estimators': [10,25,30,50,100,200]
}

from sklearn.model_selection import GridSearchCV

#Instanciando o modelo de grid search
grid_search = GridSearchCV(estimator=rf,
                           param_grid=params,
                           cv = 4,
                           n_jobs=-1, verbose=1, scoring="accuracy")

%%time
grid_search.fit(X_train, y_train)
</pre>
<img src="r7.png">
<pre>
grid_search.best_score_
</pre>
<pre>
0.698582602836879
</pre>
<pre>
rf_best = grid_search.best_estimator_
rf_best
</pre>
<pre>
RandomForestClassifier(max_depth=5, min_samples_leaf=10, n_estimators=10, n_jobs=-1, random_state=42)
</pre>
<p>A partir da sintonização de hiperparâmetros, podemos obter o melhor estimador, conforme mostrado. O melhor conjunto de parâmetros identificado foi max_depth=5, min_samples_leaf=10, n_estimators=10.</p>
<h3 align="center">7. Agora, Vamos Visualizar.</h3>
<pre>
from sklearn.tree import plot_tree
plt.figure(figsize=(80,40))
plot_tree(rf_best.estimators_[5], feature_names = X.columns,class_names=['Disease', "No Disease"],filled=True);
</pre>
<img src="r8.png">
<pre>
from sklearn.tree import plot_tree
plt.figure(figsize=(80,40))
plot_tree(rf_best.estimators_[7], feature_names = X.columns,class_names=['Disease', "No Disease"],filled=True);
</pre>
<img src="r9.png">
<p>As árvores criadas pelos estimadores_[5] e estimadores_[7] são diferentes. Assim, podemos dizer que cada árvore é independente da outra.</p>
<h3 align="center">8. Agora, vamos ordenar os dados com a ajuda da importância das características.</h3>
<pre>
rf_best.feature_importances_
</pre>
<pre>
array([0.46128487, 0.2180848 , 0.13174619 , 0.18888413])
</pre>
<pre>
imp_df = pd.DataFrame({
    "Varname": X_train.columns,
    "Imp": rf_best.feature_importances_
})

imp_df.sort_values(by="Imp", ascending=False)
</pre>
<img src="r10.png">
<h2 align="center">Vantagens e Desvantagens do Algoritmo Random Forest</h2>
<h3 align="center">Vantagens:</h3>
<ul>
  <li>Pode ser usado em problemas de classificação e regressão.</li>
  <li>Resolve o problema de overfitting, pois a saída é baseada em votação majoritária ou média.</li>
  <li>Desempenha bem mesmo se os dados contiverem valores nulos/ausentes.</li>
  <li>Cada árvore de decisão criada é independente das outras; assim, exibe a propriedade de paralelização.</li>
  <li>É altamente estável, pois as respostas médias dadas por um grande número de árvores são consideradas.</li>
  <li>Mantém a diversidade, pois nem todos os atributos são considerados ao criar cada árvore de decisão, embora isso não seja verdade em todos os casos.</li>
  <li>É imune à maldição da dimensionalidade. Como cada árvore não considera todos os atributos, o espaço de características é reduzido.</li>
  <li>Não é necessário segregar dados em treino e teste, pois sempre haverá 30% dos dados, que não são vistos pela árvore de decisão feita a partir do bootstrap.</li>
</ul>
<h3 align="center">Desvantagens:</h3>
<ul>
  <li>A floresta aleatória é altamente complexa em comparação com árvores de decisão, onde as decisões podem ser tomadas seguindo o caminho da árvore.</li>
  <li>O tempo de treinamento é maior do que outros modelos devido à sua complexidade. Sempre que precisa fazer uma previsão, cada árvore de decisão precisa gerar a saída para os dados de entrada fornecidos.</li>
</ul>
<h2 align="center">Conclusão</h2>
<p>Random Forest é uma ótima escolha se alguém quiser construir o modelo de maneira rápida e eficiente, pois uma das melhores características da Random Forest é que ela pode lidar com valores ausentes. É uma das melhores técnicas com alto desempenho, amplamente utilizada em várias indústrias por sua eficiência. Pode lidar com dados binários, contínuos e categóricos. No geral, Random Forest é um modelo rápido, simples, flexível e robusto, com algumas limitações.</p>
<h3 align="center">Principais Conclusões</h3>
<ul>
  <li>O algoritmo Random Forest é uma técnica de aprendizado em conjunto que combina inúmeros classificadores para aprimorar o desempenho de um modelo.</li>
  <li>Random Forest é um algoritmo de aprendizado de máquina supervisionado composto por árvores de decisão.</li>
  <li>Random Forest é utilizado tanto para problemas de classificação quanto de regressão</li>
</ul>
<h2 align="center">Referências:</h2>
<p>https://www.analyticsvidhya.com/blog/2021/06/understanding-random-forest/</p>
