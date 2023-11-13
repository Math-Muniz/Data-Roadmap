<h1 align="center">K-Nearest Neighbors</h1>
<h2 align="center">O que é o K-Nearest Neighbors?</h2>
<p>K-Nearest Neighbors (KNN) é um algoritmo de aprendizado de máquina que se baseia no princípio de que pontos de dados semelhantes tendem a estar próximos no espaço de características. Ele é usado para classificação e regressão, onde a ideia-chave é que objetos com características semelhantes compartilham a mesma classe ou categoria. Mas o que é isso?</p>
<p>Imagine que você quer prever qual será o meu voto na próxima eleição presidencial se eu morasse no Texas, nos Estados Unidos. Se não souber mais nada sobre mim (e se tiver os dados), uma abordagem sensata seria analisar o voto dos meus vizinhos. Morando no Texas, como eu, meus vizinhos invariavelmente planejam votar em um candidato republicano, logo, “candidato republicano” também é um bom palpite para o meu voto.</p>
<p>Agora, imagine que você sabe mais do que minha localização geográfica (talvez saiba minha idade, minha renda, quantos filhos tenho e assim por diante.). Na medida em que meu comportamento é influenciado (ou caracterizado) por esses fatos, uma análise dos vizinhos mais próximos de mim em todas essas dimensões parece ser um indicador melhor do que uma análise de todos os meus vizinhos. Essa é a ideia central da classificação baseada nos vizinhos mais próximos.</p>
<h2 align="center">O KNN é usado em diversas aplicações em Ciência de Dados, incluindo:</h2>
<ul>
  <li>1. Classificação de Documentos: Pode ser usado para classificar documentos com base em seu conteúdo ou tema.</li>
  <li>2. Recomendação de Produtos: Usado em sistemas de recomendação para encontrar produtos ou conteúdo semelhante aos gostos do usuário.</li>
  <li>3. Detecção de Anomalias: Pode ajudar a identificar anomalias em conjuntos de dados.</li>
  <li>4. Previsão de Preços e Valores: Pode ser usado para prever preços de ações, valores imobiliários, entre outros.</li>
  <li>5. Diagnóstico Médico: Auxilia na classificação de pacientes com base em sintomas e histórico médico.</li>
</ul>
<h2 align="center">Características:</h2>
<ul>
  <li><b>Não Paramétrico</b>: O KNN é um algoritmo não paramétrico, o que significa que não faz suposições rígidas sobre a distribuição dos dados. Ele se adapta aos dados disponíveis, tornando-o flexível.</li>
  <li><b>Sensibilidade ao Tamanho do Conjunto de Dados</b>: A eficiência do KNN pode variar dependendo do tamanho do conjunto de dados. A complexidade computacional do KNN aumenta à medida que o conjunto de dados cresce, tornando-o mais lento em grandes conjuntos de dados.</li>
  <li><b>Velocidade Ajustável</b>: A velocidade de cálculo do KNN é ajustável e depende de fatores como o tamanho do conjunto de treinamento e o valor escolhido para K. Um valor menor de K (mais vizinhos) geralmente requer mais cálculos, tornando-o mais lento, enquanto um valor maior de K (menos vizinhos) pode tornar o algoritmo mais rápido, mas potencialmente menos preciso.</li>
  <li><b>Simplicidade</b>: O KNN é um algoritmo relativamente simples de entender e implementar. Sua lógica é direta, tornando-o uma excelente escolha para iniciantes em aprendizado de máquina.</li>
  <li><b>Aplicação Versátil</b>: O KNN pode ser usado tanto para tarefas de classificação quanto de regressão. Na classificação, ele atribui uma classe com base na maioria dos K vizinhos mais próximos, enquanto na regressão, ele calcula a média dos valores de destino dos K vizinhos mais próximos para fazer uma previsão numérica.</li>
  <li><b>Amplamente Conhecido e Estudado</b>: O KNN é um dos algoritmos mais antigos e bem estudados em aprendizado de máquina. Isso significa que há uma riqueza de recursos, tutoriais e informações disponíveis para aprender e aprimorar seu uso.</li>
</ul>
<h2 align="center">Fórmula do Algoritmo K-Nearest Neighbors (KNN):</h2>
<p>A fórmula matemática para o algoritmo KNN envolve o cálculo da distância entre pontos no espaço de características para determinar a classe de um novo ponto. Uma das métricas de distância mais comuns usadas é a Distância Euclidiana.</p>
<p>A Distância Euclidiana entre dois pontos, x e y, com coordenadas xi e yi em n dimensões, é calculada da seguinte maneira:</p>
<pre>d(x, y) = √((x₁ — y₁)² + (x₂ — y₂)² + … + (xn — yn)²)</pre>
<p>Nesta fórmula:</p>
<ul>
  <li>d(x, y) é a distância entre os pontos x e y.</li>
  <li>n é o número de dimensões (ou características) do espaço.</li>
  <li>xn e yn são as coordenadas do ponto x e y na dimensão i.</li>
</ul>
<h2 align="center">Explicação:</h2>
<p>O algoritmo KNN é um algoritmo de classificação e regressão baseado na ideia de que os pontos em um espaço de características semelhantes devem ter rótulos semelhantes. Para classificar um novo ponto, o KNN calcula a distância entre esse ponto e todos os pontos de treinamento conhecidos. Em seguida, ele seleciona os k pontos mais próximos (os “vizinhos mais próximos”) com base na métrica de distância, que é frequentemente a Distância Euclidiana.</p>
<p>Após encontrar os k vizinhos mais próximos, o KNN determina a classe do novo ponto (ou seu valor, no caso de regressão) com base na classe predominante dos vizinhos.</p>
<p>Esta fórmula matemática ajuda a calcular as distâncias entre os pontos, permitindo que o KNN identifique os vizinhos mais próximos e tome decisões de classificação ou regressão com base em sua proximidade.</p>
<p>Lembre-se de que o KNN é um algoritmo simples e eficaz, amplamente utilizado em aprendizado de máquina para tarefas de classificação e regressão.</p>
<h2 align="center">Escolha de K:</h2>
<p>Uma decisão crítica ao usar o KNN é a escolha do valor de K. O valor de K representa o número de vizinhos próximos que o algoritmo considera ao fazer uma previsão. Escolher um valor apropriado de K é fundamental, pois ele afeta o viés e a variância do modelo. Um valor pequeno de K pode levar a previsões instáveis e sensíveis ao ruído nos dados, enquanto um valor grande de K pode resultar em previsões mais suaves, mas potencialmente enviesadas.</p>
<p>Determinar o valor de K ideal geralmente envolve técnicas de validação cruzada, como a validação cruzada k-fold, que ajuda a avaliar o desempenho do modelo com diferentes valores de K e escolher aquele que oferece o melhor equilíbrio entre viés e variância.</p>
<h2 align="center">Métricas de Distância:</h2>
<p>O K-Nearest Neighbors (KNN) pode usar várias métricas de distância, dependendo do problema e das necessidades específicas. A métrica de distância mais comum e padrão usada pelo KNN é a Distância Euclidiana. No entanto, o KNN é altamente flexível e permite a escolha de diferentes métricas de distância, como:</p>
<ul>
  <li><b>1. Distância Euclidiana</b>b>: Essa é a métrica de distância padrão, como discutida anteriormente, e é a mais comumente usada.</li>
  <li><b>2. Distância de Manhattan</b>: Também conhecida como norma L1, é a soma dos valores absolutos das diferenças entre as coordenadas.</li>
  <li><b>3. Distância de Minkowski</b>: É uma métrica de distância generalizada que engloba tanto a Distância Euclidiana quanto a Distância de Manhattan. A Distância de Minkowski inclui um parâmetro “p” que permite ajustar a métrica de acordo com a necessidade, onde “p” é um valor real positivo.</li>
  <li><b>4. Distância Ponderada</b>: Além das métricas mencionadas acima, é possível aplicar pesos diferentes às diferentes características ao calcular a distância. Isso é conhecido como Distância Ponderada e pode ser útil quando algumas características são mais importantes que outras.</li>
</ul>
<p>A escolha da métrica de distância depende da natureza do problema e dos dados. Por exemplo, a Distância de Manhattan é mais apropriada quando as características têm unidades diferentes, enquanto a Distância Euclidiana é eficaz quando as unidades são semelhantes. A seleção da métrica e a escolha do valor de “p” (para Distância de Minkowski) são etapas importantes ao aplicar o KNN a um problema específico.</p>
<h2 align="center">Algoritmo:</h2>
<p>1. Definir um valor para K: Isso envolve escolher o número de vizinhos próximos que serão considerados ao tomar uma decisão de classificação ou regressão.</p>
<p>2. Encontrar os K vizinhos mais próximos: Isso envolve calcular as distâncias entre o ponto a ser classificado e todos os pontos de dados no conjunto de treinamento e, em seguida, selecionar os K pontos mais próximos.</p>
<p>3. Tomar uma decisão com base nos K vizinhos:</p>
<ul>
  <li>Se for um problema de Regressão: Calcular a média dos valores dos K vizinhos e atribuir esse valor ao ponto de interesse.</li>
  <li>Se for um problema de Classificação: Calcular a moda (classe mais comum) dos K vizinhos e atribuir essa classe ao ponto de interesse.</li>
</ul>
<p>4. Atribuir o valor/classe ao ponto de interesse conforme o cálculo do Terceiro Passo.</p>
<h2 align="center">Vantagens do K-Nearest Neighbors (KNN):</h2>
<p>O algoritmo K-Nearest Neighbors (KNN) apresenta várias vantagens notáveis. Primeiramente, ele é amplamente elogiado por sua simplicidade. Sua lógica é direta e fácil de entender, tornando-o uma excelente escolha para introdução a algoritmos de aprendizado de máquina. Além disso, o KNN é não paramétrico, o que significa que ele não faz suposições rígidas sobre a distribuição dos dados. Isso torna o KNN altamente flexível e adequado para uma ampla gama de aplicações.</p>
<p>Outra vantagem importante do KNN é sua capacidade de se adaptar a dados com estruturas de cluster visíveis. Quando os pontos de dados compartilham características semelhantes, eles tendem a estar próximos uns dos outros no espaço de características. O KNN aproveita essa proximidade para fazer previsões precisas. Portanto, se os seus dados possuem agrupamentos bem definidos, o KNN pode ser uma escolha particularmente eficaz.</p>
<h2 align="center">Desvantagens do K-Nearest Neighbors (KNN):</h2>
<p>Apesar das vantagens, o KNN não é isento de limitações. Uma desvantagem notável é sua sensibilidade a valores atípicos (outliers). Pontos de dados extremos podem afetar adversamente as previsões do KNN, tornando-o menos adequado para dados com valores discrepantes. Além disso, o KNN requer armazenamento dos dados de treinamento para realizar previsões, o que pode ser desafiador quando o conjunto de treinamento é extenso.</p>
<p>KNN também sofre da chamada “maldição da dimensionalidade.” À medida que a dimensionalidade dos dados aumenta, o espaço de características se torna cada vez mais esparsamente povoado, o que pode levar a previsões menos precisas. Essa é uma desvantagem particularmente relevante ao lidar com dados de alta dimensionalidade.</p>
