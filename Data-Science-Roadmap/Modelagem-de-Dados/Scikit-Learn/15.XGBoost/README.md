<h1 align="center">XGBoost</h1>
<p>A Inteligência Artificial enfrenta desafios quando precisa lidar com dados não estruturados, como sequenciamento de DNA, transações com cartão de crédito e até mesmo em cibersegurança, que é a base para manter nossa presença online segura. Curioso? Não se preocupe! Nós cuidamos disso para você. Na era cibernética, a Aprendizado de Máquina (ML), como um campo da Inteligência Artificial, nos proporcionou soluções para muitos problemas considerados insolúveis, incluindo os mencionados acima, com a implementação de Máquinas de Impulso Gradiente (GBM, na sigla em inglês). Existem muitos algoritmos prontamente disponíveis para realizar o impulso gradiente; no entanto, ainda podemos enfrentar diferentes problemas, como baixa precisão, perda elevada, grande variação no resultado, dependendo da aplicação. Portanto, vamos apresentar a você um algoritmo de aprendizado de máquina de última geração chamado XGBoost, desenvolvido por Tianqi Chen, que não apenas superará esses problemas, mas também se sairá excepcionalmente bem para problemas de regressão e classificação. Este blog ajudará você a descobrir a lógica, técnicas e habilidades com o XGBoost que você pode aplicar em seus projetos de aprendizado de máquina.</p>
<h2 align="center">XGBoost, em uma visão geral!</h2>
<p>eXtreme Gradient Boosting (XGBoost) é uma versão escalável e aprimorada do algoritmo de impulso gradiente (atenção à terminologia) projetada para eficácia, velocidade computacional e desempenho do modelo. É uma biblioteca de código aberto e faz parte da Comunidade de Aprendizado de Máquina Distribuído. O XGBoost é uma combinação perfeita de capacidades de software e hardware projetadas para aprimorar as técnicas de impulso existentes com precisão em um curto período de tempo. Dê uma olhada rápida em uma comparação objetiva de benchmark do XGBoost com outros algoritmos de impulso gradiente treinados em uma floresta aleatória com 500 árvores, realizada por Szilard Pafka.</p>
<img src="table-01.webp">
<p>Muito complexo para compreender? Não se preocupe! Vamos primeiro entender os rudimentos dos métodos de aprendizado de máquina que nos levam ao XGBoost e à vitalidade de seu desempenho.</p>
<h2 align="center">Um breve retrospecto sobre Boosting:</h2>
<p>Boosting geralmente significa aumentar o desempenho. Em ML, Boosting é uma técnica sequencial de aprendizado de conjunto (outra atenção à terminologia, não se preocupe! vamos explicar isso também) para converter uma hipótese fraca ou aprendizes fracos em aprendizes fortes para aumentar a precisão do modelo.
Podemos entender a necessidade de boosting por meio de um exemplo simples de classificação: Classificar uma conta no Twitter como Bot ou Humana com a ajuda de regras subjacentes (limitadas em extensão):</p>
<ul>
  <li>Nenhuma informação da conta e foto de perfil → Bot</li>
  <li>Nome de usuário é um absurdo → Bot</li>
  <li>Tweetando em mais de um idioma → Bot</li>
  <li>Tem uma quantidade adequada de atividade e uma foto → Humana</li>
  <li>Uma quantidade enorme de tweets por dia → Bot</li>
  <li>Outras contas de mídia social vinculadas → Humana</li>
</ul>
<p>Agora que estamos cientes das regras, vamos aplicá-las no exemplo abaixo: <b>Cenário</b> — Uma conta postando tweets em inglês e francês.</p>
<p>A terceira regra classificará como um bot, mas isso será uma previsão incorreta, pois uma pessoa pode conhecer e tweetar em vários idiomas. Consequentemente, com base em uma única regra, nossa previsão pode ser falha. Uma vez que essas regras individuais não são fortes o suficiente para fazer uma previsão precisa, são chamadas de aprendizes fracos. Tecnicamente, um aprendiz fraco é um classificador que tem uma correlação fraca com o valor real. Portanto, para tornar nossas previsões mais precisas, criamos um modelo que combina as previsões dos aprendizes fracos para criar um aprendiz forte, e isso é feito usando a técnica de boosting.</p>
<p>Regras fracas são geradas em cada iteração por algoritmos de aprendizado base, que em nosso caso podem ser de dois tipos:</p>
<ul>
  <li>Árvore como aprendiz base</li>
  <li>Aprendiz base linear</li>
</ul>
<p>Geralmente, árvores de decisão são aprendizes base padrão para boosting.</p>
<p>Interessado em saber mais sobre aprendizes? Fique tranquilo, demonstraremos como usar ambos os aprendizes base para treinar modelos XGBoost em uma seção posterior.</p>
<p>Primeiro, vamos entender a técnica de aprendizado de conjunto mencionada acima.</p>
<h2 align="center">Aprendizado de Conjunto (Ensemble Learning):</h2>
<p>O aprendizado de conjunto é um processo no qual decisões de vários modelos de aprendizado de máquina são combinadas para reduzir erros e melhorar as previsões quando comparadas a um único modelo de aprendizado de máquina. Em seguida, a técnica de votação máxima é usada nas decisões agregadas (ou previsões na linguagem de aprendizado de máquina) para deduzir a previsão final. Está confuso?</p>
<p>Pense nisso como organizar rotas eficientes para o trabalho, faculdade ou supermercados. Assim como você pode usar várias rotas para chegar ao seu destino, tende a aprender sobre o tráfego e o atraso que pode causar em diferentes momentos do dia, permitindo que você planeje uma rota perfeita, o aprendizado de conjunto é semelhante!</p>
<p>Esta imagem mostra uma clara distinção entre um único modelo de aprendizado de máquina em relação a um aprendiz de conjunto:</p>
<img src="grafico-01.webp">
<h3 align="center">Tipos de Aprendizado de Conjunto (Ensemble Learning):</h3>
<p>Os métodos de aprendizado de conjunto podem ser realizados de duas maneiras:</p>
<ul>
  <li>Bagging (conjunto paralelo)</li>
  <li>Boosting (conjunto sequencial)</li>
</ul>
<p>Embora ambos tenham alguma matemática fascinante por baixo, não precisamos conhecê-la para poder usá-los como ferramentas. Nosso foco será mais na compreensão do Boosting devido à sua relevância para o XGBoost.</p>
<h3 align="center">Funcionamento do algoritmo de boosting:</h3>
<p>O algoritmo de boosting cria novos aprendizes fracos (modelos) e combina sequencialmente suas previsões para melhorar o desempenho geral do modelo. Para qualquer previsão incorreta, são atribuídos pesos maiores às amostras classificadas incorretamente e menores às amostras classificadas corretamente. Modelos de aprendizes fracos que se saem melhor têm pesos mais altos no modelo de conjunto final. O boosting nunca altera o preditor anterior e apenas corrige o próximo preditor aprendendo com os erros. Como o boosting é ganancioso, é recomendável definir um critério de parada, como o desempenho do modelo (parada precoce) ou várias etapas (por exemplo, profundidade da árvore em aprendizes baseados em árvore) para evitar o overfitting dos dados de treinamento. A primeira implementação do boosting foi chamada de AdaBoost (Adaptive Boosting) que já vimos nos estudos passados.</p>
<img src="formula-01.webp">
<pre>
Capital F(i) is current model, F(i-1) is previous model and small f(i) represents a weak model
</pre>
<img src="grafico-02.webp">
<p>Se sentindo confiante? Dê uma olhada em mais dois algoritmos (CART e Gradient Boosting) para entender a mecânica do XGBoost antes de aprofundarmos mais no tópico.</p>
<h3 align="center">Árvores de Classificação e Regressão (CART):</h3>
<p>Uma árvore de decisão é um algoritmo de aprendizado de máquina supervisionado usado para modelagem preditiva de uma variável dependente (alvo) com base na entrada de várias variáveis independentes. Ela tem uma estrutura em forma de árvore com a raiz no topo. CART, que significa Classificação e Regressão de Árvores, é usado como um termo genérico para se referir aos seguintes tipos de árvores de decisão:</p>
<p><b>Árvores de Classificação</b>: onde a variável de destino é fixa ou categórica, esse algoritmo é usado para identificar a classe/categoria na qual o alvo mais provavelmente se encaixaria.</p>
<p><b>Árvores de Regressão</b>: onde a variável de destino é contínua e a árvore/algoritmo é usado para prever seu valor, por exemplo, prever o tempo.</p>
<h3 align="center">Gradient Boosting:</h3>
<p>O gradient boosting é um caso especial de algoritmo de boosting, onde os erros são minimizados por um algoritmo de descida de gradiente e produzem um modelo na forma de modelos de previsão fracos, como árvores de decisão.</p>
<p>A principal diferença entre boosting e gradient boosting está em como ambos os algoritmos atualizam o modelo (aprendizes fracos) a partir de previsões incorretas. O gradient boosting ajusta os pesos pelo uso do gradiente (uma direção na função de perda) usando um algoritmo chamado Descida de Gradiente, que otimiza iterativamente a perda do modelo atualizando os pesos. Perda normalmente significa a diferença entre o valor previsto e o valor real. Para algoritmos de regressão, usamos a perda de MSE (Erro Quadrático Médio) como métrica de avaliação, enquanto para problemas de classificação, usamos a perda logarítmica.</p>
<img src="formula-02.webp">
<pre>
w representa o vetor de pesos, η é a taxa de aprendizado.
</pre>
<h3 align="center">Processo de Gradient Boosting:</h3>
<img src="grafico-03.webp">
<p>O gradient boosting utiliza Modelagem Aditiva, na qual uma nova árvore de decisão é adicionada uma de cada vez a um modelo que minimiza a perda usando descida de gradiente. As árvores existentes no modelo permanecem intocadas, diminuindo assim a taxa de overfitting. A saída da nova árvore é combinada com a saída das árvores existentes até que a perda seja minimizada abaixo de um limiar ou o número especificado de árvores seja atingido.</p>
<p>A Modelagem Aditiva na matemática é uma decomposição de uma função na adição de N subfunções. Em termos estatísticos, pode ser considerada como um modelo de regressão no qual a resposta y é a soma aritmética dos efeitos individuais das variáveis preditoras x.</p>
<h2 align="center">XGBOOST em ação</h2>
<p>O que torna o XGBoost um algoritmo essencial para ganhar em Machine Learning e competições Kaggle?</p>
<img src="grafico-04.webp">
<h3 align="center">Recursos do XGBOOST</h3>v
<p>Não é interessante ver uma única ferramenta para lidar com todos os nossos problemas de impulso! Aqui estão os recursos com detalhes e como eles são incorporados no XGBoost para torná-lo robusto.</p>
<h3 align="center">Processo de Gradient Boosting:</h3>
<ul>
  <li><b>Poda de Árvores (Tree Pruning)</b> — A poda é uma técnica de aprendizado de máquina para reduzir o tamanho de árvores de regressão, substituindo nós que não contribuem para melhorar a classificação nas folhas. A ideia da poda de uma árvore de regressão é evitar o overfitting dos dados de treinamento. O método mais eficiente para poda é o de Poda de Complexidade de Custo ou Poda do Elo Mais Fraco, que internamente utiliza erro médio quadrático, validação cruzada k-fold e taxa de aprendizado. O XGBoost cria nós (também chamados de divisões) até a max_depth especificada e inicia a poda de trás para frente até que a perda esteja abaixo de um limiar. Considere uma divisão que tem uma perda de -3 e o nó subsequente tem uma perda de +7, o XGBoost não removerá a divisão apenas olhando uma das perdas negativas. Ele calculará a perda total (-3 + 7 = +4) e, se for positiva, manterá ambas.</li>
  <li><b>Encontrar Divisões Conscientes de Esparsidade (Sparsity Aware Split Finding)</b> — É bastante comum que os dados que coletamos tenham esparsidade (muitos valores ausentes ou vazios) ou se tornem esparsos após a realização de engenharia de dados (codificação de características). Para estar ciente dos padrões de esparsidade nos dados, uma direção padrão é atribuída a cada árvore. O XGBoost lida com dados ausentes atribuindo-os à direção padrão e encontrando o melhor valor de imputação para minimizar a perda de treinamento. A otimização aqui é visitar apenas os valores ausentes, o que faz com que o algoritmo execute 50 vezes mais rápido do que o método ingênuo.</li>
</ul>
<h3 align="center">Aprimoramentos no Sistema:</h3>
<ul>
  <li><b>Parallelization (Paralelização)</b> — A aprendizagem da árvore precisa de dados de maneira ordenada. Para reduzir os custos de ordenação, os dados são divididos em blocos comprimidos (cada coluna com o valor de característica correspondente). O XGBoost ordena cada bloco paralelamente usando todos os núcleos/threads disponíveis da CPU. Essa otimização é valiosa, uma vez que um grande número de nós é criado frequentemente em uma árvore. Em resumo, o XGBoost paraleliza o processo sequencial de geração de árvores.</li>
  <li><b>Cache Aware (Consciência de Cache)</b> — Por meio de otimização consciente de cache, armazenamos estatísticas de gradiente (direção e valor) para cada nó de divisão em um buffer interno de cada thread e realizamos a acumulação de maneira por mini-lotes. Isso ajuda a reduzir o tempo de overhead de operações de leitura/gravação imediatas e também evita a falta de cache. A consciência de cache é alcançada escolhendo o tamanho ideal do bloco (geralmente 2¹⁶).</li>
</ul>
<h3 align="center">Flexibilidade no XGBoost:</h3>
<p>1.<b>Função Objetivo Personalizada (Customized Objective Function)</b> — Uma função objetivo tem a intenção de maximizar ou minimizar algo. Em ML, tentamos minimizar a função objetivo, que é uma combinação da função de perda e termo de regularização."</p>
<img src="formula-03.webp">
<pre>
L(Φ) é a função objetiva
</pre>
<p>Otimizar a função de perda incentiva modelos preditivos, enquanto otimizar a regularização leva a uma menor variância e torna as previsões mais estáveis. Diferentes funções objetivas disponíveis no XGBoost são:</p>
<ul>
  <li>reg: linear para regressão</li>
  <li>reg: logistic e binary: logistic para classificação binária</li>
  <li>multi: softmax e multi: softprob para classificação multiclasse</li>
</ul>
<p>2.Métrica de Avaliação Personalizada — Esta é uma métrica usada para monitorar a precisão do modelo nos dados de validação.</p>
<ul>
  <li>rmse — Erro quadrático médio (Regressão)</li>
  <li>mae — Erro médio absoluto (Regressão)</li>
  <li>error — Erro de classificação binária (Classificação)</li>
  <li>logloss — Log-verossimilhança negativa (Classificação)</li>
  <li>auc — Área sob a curva (Classificação)</li>
</ul>
<h3 align="center">Cross-validation (Validação Cruzada):</h3>
<p>1.Validação Cruzada Incorporada — A validação cruzada é um método estatístico para avaliar modelos de aprendizado de máquina em dados não vistos. É útil quando o conjunto de dados é limitado e evita o overfitting, não retirando uma amostra independente (holdout) dos dados de treinamento para validação. Ao reduzir o tamanho dos dados de treinamento, comprometemos as características e padrões ocultos nos dados, o que pode induzir erros em nosso modelo. Isso é semelhante à funcionalidade cross_val_score fornecida pela biblioteca scikit-learn.</p>
<p>O XGBoost usa a função de validação cruzada incorporada cv():</p>
<pre>
xgb.cv()
</pre>
<p><b>Quer experimentar por conta própria?</b></p>
<pre>
import xgboost as xgb
import pandas as pd
from sklearn.datasets import load_boston

#Carrega o conjunto de dados de Boston
X, y = load_boston(return_X_y=True)

#Cria uma matriz DMatrix a partir dos dados
boston_dmatrix = xgb.DMatrix(data=X, label=y)

#Lista de parâmetros de regularização
reg_params = [1, 10, 100]

#Parâmetros do modelo
params = {"objective": "reg:squarederror", "max_depth": 3}

#Cria uma lista vazia para armazenar os valores de RMSE em função da complexidade da regressão ridge
ridge_regression = []

#Itera sobre os parâmetros de regularização
for reg in reg_params:

    #Atualiza a força do termo L2
    params["lambda"] = reg

    #Passa este dicionário de parâmetros atualizado para o cv
    cv_results_rmse = xgb.cv(dtrain=boston_dmatrix, params=params, nfold=5, num_boost_round=5, metrics="rmse", as_pandas=True, seed=123)

    #Adiciona o melhor RMSE (última rodada) à lista
    ridge_regression.append(cv_results_rmse["test-rmse-mean"].tail(1).values[0])

#Exibe o melhor RMSE para cada parâmetro de regularização
print("Best RMSE as a function of ridge regression (L2 regularization):")
print(pd.DataFrame(list(zip(reg_params, ridge_regression)), columns=["l2", "rmse"]))
</pre>
<img src="table-02.webp">
<p></p>
<p>2.</p>
<p></p>
<pre>

</pre>
<h3 align="center">Cross-validation (Validação Cruzada):</h3>
<p></p>
<p>1.</p>
<p>2.</p>
<pre>

</pre>
