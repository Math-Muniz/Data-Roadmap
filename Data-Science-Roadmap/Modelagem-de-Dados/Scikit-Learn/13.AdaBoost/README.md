<h1 align="center">AdaBoost</h1>
<p>A seguir apresentaremos uma explicação intuitiva do algoritmo AdaBoost! AdaBoost é um algoritmo de impulsionamento (Boosting) baseado em Florestas Aleatórias (Random Forests).</p>
<h2 align="center">Desmatamento! Oh não!</h2>
<p>Se você já está familiarizado com Florestas Aleatórias(Random Forests), lembrará que uma Floresta Aleatória (Random Forests) é composta por muitas Árvores de Decisão diferentes. AdaBoost é construído usando um conceito semelhante, mas em vez de árvores, o algoritmo usa stumps (tocos).</p>
<img src="stumps.webp">
<p>Visualização de stumps (tocos) (imagem cortesia do Google)</p>
<p>Um toco (stump) é uma árvore de decisão composta por um nó raiz + nós folha. E é isso!</p>
<p>À primeira vista, uma floresta de tocos não parece ser uma metodologia de classificação precisa. E é totalmente correto que um único toco não faz um ótimo trabalho de classificação de amostras. Também é verdade que muitos tocos independentes combinados provavelmente não fariam um ótimo trabalho de classificação de uma amostra. É por isso que o AdaBoost combina estruturas de toco com um conceito chamado Impulsionamento.</p>
<h2 align="center">O Impulso no AdaBoost!</h2>
<p>Este artigo pressupõe que você já está familiarizado com o conceito de Impulsionamento. Como lembrete rápido, o Impulsionamento é uma técnica de aprendizado em conjunto em que cada modelo é construído sequencialmente iterando sobre o modelo anterior.</p>
<p>Na floresta de tocos que compõe o AdaBoost, cada toco tem uma quantidade diferente de influência na decisão final de classificação para cada amostra. Isso é diferente do algoritmo de Floresta Aleatória, onde cada árvore tem um voto igual.</p>
<p>No AdaBoost, a ordem é importante. Os erros que o primeiro toco comete influenciam como o segundo toco é feito, e assim por diante, até que o máximo possível de erros seja levado em consideração.</p>
<p>Vamos começar a construir o primeiro toco de um problema de classificação simplificado e inventado para entender melhor como isso funciona.</p>
<h2 align="center">Construindo Nosso Primeiro Stump (Toco)</h2>
<p>Usaremos nossos próprios dados meteorológicos para simular o algoritmo AdaBoost. Neste conjunto de dados fictício, a variável-alvo é RainTomorrow, e possui dois valores possíveis, "Sim" e "Não". O objetivo do nosso problema de classificação é descobrir se choverá no próximo dia com base na temperatura, umidade e se choveu ou não no dia em questão.</p>
<p>O primeiro passo do algoritmo é atribuir a cada amostra um peso igual. Como há quatro amostras em nosso exemplo simplificado, cada amostra receberá o peso 1/4. Após a criação do primeiro toco, os pesos serão alterados para orientar como o próximo toco é criado.</p>
<img src="table-01.webp">
<p>Em seguida, encontramos a variável que faz o melhor trabalho na classificação das amostras usando o Índice GINI. Neste passo, podemos ignorar os pesos, pois atualmente todos são iguais.</p>
<p>Vamos supor que a Umidade teve o maior Índice GINI e escolhê-la para o nó raiz da nossa primeira amostra. Digamos que ela classificou corretamente todas as amostras, exceto a destacada abaixo.</p>
<img src="table-02.webp">
<p>Para determinar quanto peso este toco tem em nossa classificação final, precisaremos calcular o Erro Total e a Quantidade de Influência.</p>
<p>Vamos começar com o erro total. O Erro Total para um toco é a soma dos pesos associados às amostras incorretamente classificadas. Aqui, o erro total é 1/4.</p>
<p>É importante observar que, como todos os Pesos das Amostras somam 1, o Erro Total sempre estará entre 0 (para um toco perfeito) e 1 (para um toco horrível).</p>
<p>Em seguida, usamos o Erro Total para calcular a Quantidade de Influência que um toco tem na classificação final. Isso é calculado usando a equação abaixo.</p>
<img src="formula-01.webp">
<p>Para entender melhor como esta equação determina a quantidade de influência, vamos visualizá-la.</p>
<img src="grafico-01.webp">
<p>Após analisar a visualização acima, podemos ver que quando um toco faz um bom trabalho e o erro total é pequeno, a Quantidade de Influência é um valor relativamente grande e positivo. E quando um toco faz um trabalho terrível e o Erro Total está próximo de 1 (o que significa que o toco consistentemente fornece a resposta oposta para a classificação), então a Quantidade de Influência será um valor grande e negativo.</p>
<p>Além disso, quando um toco não é melhor na classificação do que um palpite aleatório, como jogar uma moeda, então a Quantidade de Influência será 0. Observação: se o Erro Total for 1 ou 0, então a equação da Quantidade de Influência é indefinida.</p>
<p>Podemos calcular nossa Quantidade de Influência usando nosso Erro Total de 1/4. Isso resulta em:</p>
<img src="formula-02.webp">
<p>Agora temos nosso Erro Total e nossa Quantidade de Influência, mas precisamos incorporá-los ao nosso algoritmo para que nosso próximo toco leve em consideração os erros do toco atual. Faremos isso usando o Erro Total e a Quantidade de Influência para calcular novos pesos de amostra.</p>
<h2 align="center">Calculando Novos Pesos de Amostra</h2>
<p>A ideia principal por trás do cálculo de novos pesos de amostra é que as amostras que o primeiro toco classifica erroneamente recebem um peso aumentado antes que o próximo toco seja construído. Isso significa que quando o algoritmo for construir a segunda árvore, ele saberá quais amostras são mais importantes para acertar desta vez.</p>
<p>Vamos calcular nossos novos pesos. Para calcular novos pesos de amostra, precisaremos de duas equações separadas. Primeiro, a fórmula para aumentar o peso da amostra que foi classificada incorretamente.</p>
<img src="formula-03.webp">
<p>Podemos mais uma vez visualizar isso para nos ajudar a entender melhor como nossa equação funciona.</p>
<img src="grafico-02.webp">
<p>Como você pode ver, quando a Quantidade de Influência é relativamente grande (ou seja, o último toco fez um bom trabalho na classificação das amostras), escalamos o peso anterior da amostra com um número grande. Isso faz com que o novo peso da amostra seja muito maior que o anterior.</p>
<p>E quando a quantidade de influência é relativamente baixa, o peso anterior da amostra é escalado por um número relativamente pequeno. Isso significa que o novo peso da amostra será apenas ligeiramente maior que o anterior.</p>
<p>Vamos calcular nosso novo peso de amostra para nossa amostra classificada incorretamente.</p>
<img src="formula-04.webp">
<p>Nossa segunda fórmula é para diminuir os pesos das amostras que foram classificadas corretamente. A fórmula é fornecida abaixo.</p>
<img src="formula-05.webp">
<p>Vamos visualizar essa equação.</p>
<img src="grafico-03.webp">
<p>Quando a quantidade de influência é relativamente grande, escalamos o peso da amostra por um valor muito próximo de zero. Isso faz com que o novo peso da amostra seja muito pequeno.</p>
<p>Se a quantidade de influência do último toco for relativamente pequena, então escalamos o peso da amostra por um valor próximo a 1. Isso faz com que o novo peso da amostra seja apenas um pouco menor que o anterior.</p>
<p>Vamos calcular nossos novos pesos de amostra para nossas três amostras classificadas corretamente. Observe que esse valor é menor que 0,25, que foi o valor do primeiro peso da amostra para essas amostras.</p>
<img src="formula-06.webp">
<p>Agora que temos nossos novos pesos de amostra, podemos colocá-los em nosso quadro de dados.</p>
<img src="table-03.webp">
<p>Há mais um passo que precisamos concluir antes de prosseguir. Precisamos normalizar os novos pesos das amostras. Como lembrete, isso significa ajustar cada peso da amostra para que todos os quatro pesos das amostras somem 1. Isso pode ser feito dividindo cada peso da amostra pela soma de todos os novos pesos das amostras.</p>
<img src="table-04.webp">
<p>E finalmente, não precisamos mais dos nossos primeiros pesos das amostras. Portanto, nossos novos pesos das amostras tornam-se nossos pesos atuais das amostras!</p>
<img src="table-05.webp">
<p>Agora que temos nossos dados meteorológicos de amostra com pesos baseados no primeiro toco, podemos construir nosso próximo toco. (E assim por diante! Isso é AdaBoost!).</p>
<h2 align="center">Configurando Nosso Segundo Stump (Toco)</h2>
<p>Para construir nosso segundo toco, temos duas opções.</p>
<ul>
  <li>Podemos calcular um Índice Gini ponderado para que a variável que faz um bom trabalho na classificação de amostras previamente classificadas incorretamente seja escolhida como a raiz do segundo toco.</li>
  <li>Podemos criar uma nova coleção de amostras que contenha cópias duplicadas das amostras com os maiores pesos das amostras. Isso é feito criando um novo conjunto de dados vazio. Em seguida, para cada linha no novo conjunto de dados vazio, escolheríamos um número aleatório entre 0 e 1 e veríamos onde esse número se encaixa quando usamos os pesos das amostras como uma distribuição. Em seguida, preencheríamos a linha de acordo. Continuaríamos esse processo até que todas as linhas na nova coleção de amostras sejam preenchidas.</li>
</ul>
<p>Uma vez escolhido o método para configurar o segundo toco, essa metodologia será usada para todos os tocos restantes.</p>
<h2 align="center">Decidindo a Classificação Final</h2>
<p>Você pode estar se perguntando — uma vez que todos os tocos realizaram a classificação, como esta floresta de tocos decide a classificação final para cada amostra? Aqui está como funciona para uma amostra. Vamos assumir que a variável-alvo tinha duas respostas possíveis, assim como nossos dados de exemplo — 'Sim' e 'Não'.</p>
<p>Primeiro, somamos a quantidade de influência para todos os tocos que classificaram como 'Sim'. Em seguida, fazemos o mesmo para todos os tocos que classificaram como 'Não'. A soma que for maior vence como a classificação final da amostra.</p>
<p>Esse processo é realizado para todas as amostras no conjunto de dados de teste. Uma vez concluído esse processo, a classificação do AdaBoost também está concluída."</p>
<h2 align="center">Conceitos Fundamentais</h2>
<ul>
  <li>Aprendizados Fracos (Weak Learners): O AdaBoost opera principalmente com uma classe de algoritmos chamada 'learners fracos'. Learners fracos são modelos que têm um desempenho ligeiramente melhor do que o palpite aleatório, mas ainda estão longe de ser classificadores precisos. Estes podem ser tocos de decisão (árvores de decisão simples com uma única divisão), modelos lineares ou outros algoritmos simples.</li>
  <li>Aprendizado de Conjunto (Ensemble Learning): O AdaBoost pertence à categoria de aprendizado de conjunto. Métodos de conjunto combinam vários modelos de aprendizado de máquina para criar um modelo mais forte e preciso do que qualquer um de seus componentes individuais. O AdaBoost alcança isso treinando iterativamente learners fracos e atribuindo pesos com base em seu desempenho.</li>
</ul>
<h2 align="center">Conclusões sobre como o AdaBoost Funciona</h2>
<p>O AdaBoost opera em uma série de iterações, ou rounds, para construir um classificador forte. Aqui está uma visão geral passo a passo de como o AdaBoost funciona:</p>
<ul>
  <li>Inicializar Pesos (Initialize Weights): Na primeira rodada, todos os exemplos de treinamento recebem pesos iguais. O objetivo é classificar esses exemplos corretamente.</li>
  <li>Treinar um Learner Fraco (Train a Weak Learner): O AdaBoost seleciona um learner fraco e o treina nos dados de treinamento, dando mais peso aos exemplos classificados incorretamente na rodada anterior.</li>
  <li>Calcular Erro (Calculate Error): Após o treinamento, o AdaBoost calcula o erro do learner fraco. O erro é a soma dos pesos dos exemplos classificados incorretamente dividida pelo peso total.</li>
  <li>Atualizar Pesos (Update Weights): O AdaBoost aumenta os pesos dos exemplos classificados incorretamente, tornando-os mais importantes na próxima rodada. Isso coloca maior ênfase nos pontos de dados que foram desafiadores anteriormente.</li>
  <li>Iterar (Iterate): Os passos 2 a 4 são repetidos por um número predefinido de rodadas ou até atingir um certo nível de precisão.</li>
  <li>Combinação de Learners Fracos (Combine Weak Learners): Finalmente, o AdaBoost combina as previsões dos learners fracos atribuindo pesos a cada learner com base em seu desempenho. Learners mais fortes recebem pesos mais altos, contribuindo mais para a previsão final.</li>
  <li>Fazer Previsões (Make Predictions): Para fazer previsões em novos dados, o AdaBoost calcula a soma ponderada das previsões dos learners fracos, sendo que cada learner tem seu peso determinado pelo seu desempenho durante o treinamento.</li>
</ul>
<h2 align="center">Aplicações do AdaBoost</h2>
<p>O AdaBoost encontrou aplicações em uma ampla gama de campos, incluindo:</p>
<ul>
  <li>Detecção de Rosto: O AdaBoost é amplamente utilizado em visão computacional para detecção de rostos, onde ajuda a identificar rostos em imagens e vídeos com precisão.</li>
  <li>Classificação de Texto: Em processamento de linguagem natural, o AdaBoost é usado em tarefas de classificação de texto, como detecção de e-mails de spam e análise de sentimentos.</li>
  <li>Bioinformática: O AdaBoost foi aplicado à análise de dados biológicos, incluindo perfil de expressão gênica e previsão de função proteica.</li>
  <li>Diagnóstico Médico: Na indústria de saúde, o AdaBoost auxilia em tarefas de diagnóstico médico, como detecção de doenças com base em dados do paciente.</li>
  <li>Detecção de Anomalias: O AdaBoost é empregado na detecção de anomalias em vários domínios, incluindo segurança de rede e detecção de fraudes.</li>
</ul>
<h2 align="center">Código em Python</h2>
<p>Aqui está um exemplo completo de código em Python do AdaBoost com um conjunto de dados e gráficos. Utilizaremos o famoso conjunto de dados Iris para este exemplo, que é um problema de classificação multiclasse.</p>
<pre>
#Importamos as bibliotecas necessárias
import numpy as np
import matplotlib.pyplot as plt
from sklearn.datasets import load_iris
from sklearn.ensemble import AdaBoostClassifier
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score

#Carregamos o conjunto de dados Iris
iris = load_iris()
X = iris.data
y = iris.target

#dividimos em conjuntos de treinamento e teste
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, random_state=42)

#Criamos um AdaBoostClassifier com 50 estimadores
clf = AdaBoostClassifier(n_estimators=50, random_state=42)

#Ajustamos (Fit) o classificador aos dados de treinamento
clf.fit(X_train, y_train)

#fazemos previsões nos dados de teste.
y_pred = clf.predict(X_test)

#Plotar a fronteira de decisão usando as duas primeiras características
feature1 = 0  #Escolha os índices das características que você deseja plotar
feature2 = 1

#Extrair as características selecionadas do conjunto de dados
X_subset = X[:, [feature1, feature2]]

#Criamos um AdaBoostClassifier com 50 estimadores
clf = AdaBoostClassifier(n_estimators=50, random_state=42)

#Ajustamos (Fit) o classificador aos dados de treinamento
clf.fit(X_train[:, [feature1, feature2]], y_train)

#fazemos previsões nos dados de teste.
y_pred = clf.predict(X_test[:, [feature1, feature2]])

#Calcular a precisão (accuracy)
accuracy = accuracy_score(y_test, y_pred)
print(f"Accuracy: {accuracy:.2f}")

#Plotar a fronteira de decisão
x_min, x_max = X_subset[:, 0].min() - 1, X_subset[:, 0].max() + 1
y_min, y_max = X_subset[:, 1].min() - 1, X_subset[:, 1].max() + 1
xx, yy = np.meshgrid(np.arange(x_min, x_max, 0.1), np.arange(y_min, y_max, 0.1))

Z = clf.predict(np.c_[xx.ravel(), yy.ravel()])
Z = Z.reshape(xx.shape)

plt.contourf(xx, yy, Z, alpha=0.4)
plt.scatter(X_subset[:, 0], X_subset[:, 1], c=y, marker='o', s=25)
plt.xlabel(f"Feature {feature1 + 1}")
plt.ylabel(f"Feature {feature2 + 1}")
plt.title("AdaBoost Classifier Decision Boundary")
plt.show()
</pre>
