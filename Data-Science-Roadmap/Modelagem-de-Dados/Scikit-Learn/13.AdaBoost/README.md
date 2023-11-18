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
<h2 align="center">Construindo Nosso Primeiro Stump</h2>
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
<p></p>
<p></p>
<p></p>
<img src="formula-02.webp">
