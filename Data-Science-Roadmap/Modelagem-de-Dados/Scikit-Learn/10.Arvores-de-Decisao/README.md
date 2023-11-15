<h1 align="center">Árvores de Decisão</h1>
<h2 align="center">O que são?</h2>
<p>Árvores de decisão são métodos de aprendizado de máquinas supervisionado não-paramétricos, muito utilizados em tarefas de classificação e regressão.</p>
<p>Antes de explicarmos melhor o significado dessa definição, vamos entender o que é uma árvore de decisão a partir de uma perspectiva mais geral.</p>
<p>Provavelmente, você já deve ter visto ou utilizado uma árvore de decisão em sua vida. Por exemplo, você já deve ter utilizado ou visto um fluxograma, não é mesmo? Espero que sim (senão dê uma olhada na figura abaixo). Isso mesmo! Um fluxograma pode ser considerado uma árvore de decisão (caso não contenha loop).</p>
<img src="grafico-01.webp">
<p>Árvores, de um modo geral em computação, são estruturas de dados formadas por um conjunto de elementos que armazenam informações chamadas nós. Na figura acima, os nós são representados pelos quadradinhos com as perguntas e as informações podem ser consideradas as perguntas e suas possíveis respostas. Além disso, toda árvore possui um nó chamado raiz, que possui o maior nível hierárquico (o ponto de partida) e ligações para outros elementos, denominados filhos. Esses filhos podem possuir seus próprios filhos que por sua vez também possuem os seus. O nó que não possui filho é conhecido como nó folha ou terminal (representado pelo símbolo arredondado na figura). Tendo essas definições esclarecidas, uma árvore de decisão nada mais é que uma árvore que armazena regras em seus nós, e os nós folhas representam a decisão a ser tomada (no caso do exemplo, qual jogo escolher).</p>
<p>Em uma árvore de decisão, uma decisão é tomada através do caminhamento a partir do nó raiz até o nó folha. Para elucidar melhor, suponha que tenhamos essa situação: você vai fazer uma reunião com seus amigos em sua casa, e vai rolar comidas e bebidas. Você quer jogar um jogo de tabuleiro, mas não sabe qual o melhor para essa situação, portanto, você vai recorrer a árvore de decisão para tomar sua decisão de forma mais correta. Para isso vamos caminhar por ela a partir do nó raiz, que contém a pergunta: Está jogando com crianças? Não, então iremos para nó filho da esquerda. Vamos jogar por mais de duas horas? Acho que sim! Assim, o próximo é: Regras difíceis? Vou tomar uma, logo não vou querer pensar muito rsrs. Reposta é não. Todos os jogadores vão ficar até o final? Vamos supor que sim! Desse modo, chegamos ao nó folha, com jogo <a href="https://boardgamegeek.com/boardgame/35677/le-havre">Le Havre</a>.</p>
<p>Simples assim! Mas o que isso tem a ver com aprendizado de máquina? De fato, uma árvore de decisão por si só não é aprendizado de máquina já que eu posso criar uma sem auxílio de um computador e utilizá-la para organizar melhor minhas ideias e tomada de decisão (como alguém fez com o problema de escolher jogos de tabuleiro). Todavia, seu processo de construção automático, a partir de um conjunto de dados, é. No geral, os algoritmos para isso o fazem de forma não-paramétrica (termo estatístico que significa, em termos gerais: não assumir nada sobre os dados de antemão) e supervisionada (os dados devem conter as respostas/rótulos, mais detalhes <a href="https://medium.com/opensanca/aprendizagem-de-maquina-supervisionada-ou-n%C3%A3o-supervisionada-7d01f78cd80a">aqui</a>).</p>
<p>Tendo tudo isso em vista, na próxima seção veremos como aprender a estrutura da árvore de decisão de forma automática a partir dos dados.</p>
<h2 align="center">Como construir uma Árvore de Decisão?</h2>
<p>A ideia geral de métodos baseados em árvores é particionar o espaço recursivamente em retângulos (sub-regiões), nos quais um modelo simples é aprendido.</p>
<p>Para elucidar melhor como a árvore de decisão particiona o espaço em sub-regiões, vamos introduzir o conjunto de dados de <a href="https://archive.ics.uci.edu/dataset/53/iris">flores de íris</a>.</p>
<img src="flor.png">
<p>Esse conjunto de dados contém exemplos de três espécies de flor de Íris. Cada um dos quais possui 4 atributos, que são a largura e comprimento da pétala e da sépala da flor.
Nós iremos utilizar apenas 2 atributos em nosso exemplo (comprimento e largura da pétala), já que é mais fácil para visualização no plano 2d. Além disso, conseguimos dividir o espaço satisfatoriamente apenas com esses dois atributos, ou seja, são dois atributos bem discriminativos para esse problema.</p>
<img src="grafico-02.png">
<p>O espaço é representado pelo gráfico ao lado, onde cada uma das três cores representa uma espécie da flor de íris, são elas: setosa (amarela), versicolor (verde) e viriginica (roxa). Tendo isso em vista, nos queremos construir uma árvore de decisão para determinar a qual espécie uma nova flor de íris pertence dada suas características (nesse caso, comprimento e largura da pétala). Para isso, vamos particionar o espaço recursivamente, fazendo cortes ortogonais, levando em consideração uma variável por vez, que maximiza a pureza das sub-regiões resultantes (pureza = homogeneidade no que diz respeito às espécies/rótulos). Cada divisão do espaço é representada por um nó na árvore de decisão. A primeira divisão (nós raiz da árvore) leva em consideração todos os exemplos (pontos) do espaço ao encontrar o ponto de corte que maximiza a pureza, de acordo com algum critério de impureza (veremos adiante), das sub-regiões resultantes. Vamos supor que o comprimento da pétala de valor 2,45 cm é o ponto de corte que melhor divide o espaço. Portanto, essa será o nó raiz de nossa árvore de decisão.</p>
<img src="grafico-03.webp">
<p>A figura acima mostra como fica essa divisão (esquerda) e nosso nó raiz (direita). De fato, esse corte nos deu uma região totalmente pura (conseguimos separa as setosas do restante) e uma outra heterogênea. Agora, vamos recursivamente particionar as duas sub-regiões do espaço (da esquerda e da direita). Na esquerda, temos uma região completamente pura e isso significa que qualquer corte que fizermos nessa região teremos como resultados regiões puras. Portanto, podemos parar o particionamento, ou seja, essa região será considerada um nó folha em nossa árvore. Já a região da direita não é pura, assim devemos continuar o particionamento por ela até que cheguemos em sub-regiões puras. Figura a seguir mostra a próxima partição.</p>
<img src="grafico-04.webp">
<p>A partição na sub-região da direita, foi feita no eixo da largura da pétala no valor 1,75 cm. Como pode-se notar, foram gerados mais duas novas sub-regiões disjuntas, que, por sua vez, não estão completamente puras. Esse processo é repetido recursivamente até que um critério de parada seja alcançado (i.e., profundidade, número de folhas) ou que todas as folhas sejam puras, que implica na costrução até sua profundidade máxima . A figura a seguir mostra como ficaria nossa árvore e as partições (quase) puras do espaço.</p>
<img src="grafico-05.webp">
<p>Essa é a intuição do algoritmo de construção de uma árvore de decisão. Há vários algoritmos para aprender sua estrutura, são eles CART, ID3 e C4.5, todos seguem mais ou menos essa lógica. Nesse artigo, vamos focar no algoritmo CART, pois é um dos mais intuitivos e simples de implementar, além de sua implementação estar disponível em várias bibliotecas de aprendizado de máquinas, tal como scikit-learn. O código a seguir sintetiza o algoritmo.</p>
<pre>
def build_tree(data, labels, tree, depth = 1):
    classes, counts = np.unique(labels, return_counts=True)
    n_classes = classes.shape[0]

    # criétio de parada
    if not stopping_criterion(n_classes, depth, tree.max_depth):
        node = Node()

        # encontra melhor ponto de corte dado a região atual do espaço
        # de acordo com critério de impureza escolhido
        feature, threshold = find_cut_point(data, labels, 
                                            tree.impurity_criterion)
        
        # aplicando o limiar para particionar o espaço
        mask = data[:, feature] <= threshold
        
        # contruindo árvore recursivamente para
        # os sub-espaço da direita e da esquerda.
        left = build_tree(data[mask], labels[mask], tree, depth + 1)
        right = build_tree(data[~mask], labels[~mask], tree, depth + 1)
     
        return Node(feature=feature, threshold=threshold, left=left, right=right)

    # calcula a quantidade de exemplos por classe nesse nó folha
    # e instancia um nó folha com essas quantidades, lembre-se que isso
    # será usado para predição. 
    values = np.zeros(tree.n_classes)
    values[classes] = counts
    return Node(is_leaf=True, counts=values)
</pre>
