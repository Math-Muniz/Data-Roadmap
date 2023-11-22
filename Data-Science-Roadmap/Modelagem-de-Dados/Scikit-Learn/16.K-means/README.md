<h1 align="center">K-means</h1>
<h2 align="center">O que é K-means?</h2>
<p>O K-Means divide o conjunto de dados em k (um hiperparâmetro) clusters usando uma estratégia de otimização iterativa. Cada cluster é representado por um centro. Um ponto pertence a um cluster cujo centro está mais próximo dele. Para simplificar, assume-se que os centros são inicializados aleatoriamente.</p>
<p>O objetivo do modelo é encontrar clusters que minimizem a soma de SSE (Erro Quadrático Médio) sobre k clusters, movendo seus centros. SSE, ou Soma dos Erros Quadráticos, de um cluster é a soma das distâncias quadráticas entre o seu centro e seus pontos.</p>
<p>Usando cálculo, pode-se provar que a melhor maneira de minimizar o SSE é mover o centro do cluster para o centróide (=média) de todos os pontos no cluster. Reatribuímos os pontos aos clusters com base na mesma estratégia de centro mais próximo com os centros atualizados.</p>
<p>Repita o processo até que os centros não se movam muito e converjam.</p>
<pre>
K-Means Resumo
------------------------------
X -> dataset com N pontos e M características ((N,M) matriz)
k -> Número de centros escolhidos (hiperparâmetro)
centers -> centros k inicializados aleatoriamente (matriz (k, M))
for i in n_steps:
    - atribuir cada ponto a um cluster com base no centro mais próximo. Pontos no j-ésimo cluster são denotados por X_j
    - updated_centers -> centros k inicializados aleatoriamente ((k,M) matriz)
    - for j in [1, 2, .. k]
          - updated_center[j] = mean(X_j)

    - if distance(updated_centers, centers) is small
          - exit
    - else
          - centers = updated_centers
          - continue 
</pre>
<h2 align="center">Código Python</h2>
<pre>
import numpy as np

class CustomKMeans:
    def __init__(self, k, centroids, X):
        '''
        k: número de clusters
        centroids:  valor inicial dos centros.
                    np.array de forma (k, n_features)
        X:  conjunto de dados de m pontos e n_features.
            array de forma (m, n_features)
        '''
        self.k = k
        self.centroids = centroids
        self.X = X
        self.dim = X.shape[1]
        self.index = {i:[] for i in range(len(self.centroids))}


    def get_squared_distance_from_centroid(self, centroid):
        '''
        calcula a distância quadrada de um
        centróide de cada ponto em X
        '''
        return np.sum(np.square(self.X-centroid), axis=1)


    def get_cluster_variances(self):
        '''
        Para cada centróide,
        obtém get_squared_distance_from_centroid
        '''
        intra_cluster_variances = []
        for i in range(self.k):
            centroid = self.centroids[i]
            distance = self.get_squared_distance_from_centroid(centroid)
            intra_cluster_variances.append(
                                    distance.reshape(-1,1)
                                )
        return np.hstack(intra_cluster_variances)


    def update_centroids(self, min_variance_clusters):
        '''
        Atualiza o índice com base no centróide mais próximo
        para um ponto e, em seguida, atualiza o centróide
        com base neste índice atualizado
        '''
        for i in range(self.k):
            self.index[i] = np.where(min_variance_clusters==i)[0]
            self.centroids[i] = np.mean(
                                    self.X[self.index[i]], 
                                    axis=0
                                )

    
    def update(self):
        '''
        Etapa de atualização no algoritmo KMeans.
        '''
        intra_cluster_variances = self.get_cluster_variances()
        min_variance_clusters = np.argmin(
                                    intra_cluster_variances, 
                                    axis=1
                                )
        self.update_centroids(min_variance_clusters)
        

    
centroids = np.array([
    [0, 0.5],
    [1, 0]
])
k = 2
X = np.random.randn(1000, 2)

model = CustomKMeans(k, centroids, X)
</pre>
