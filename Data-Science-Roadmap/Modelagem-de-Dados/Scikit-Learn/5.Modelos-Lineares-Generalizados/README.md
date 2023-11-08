<h1 align="center">Modelos Lineares Generalizados (GLM)</h1>
<p>O Modelo Linear Generalizado (GLM) é um dos muitos modelos para formar a relação linear entre a variável dependente e seus preditores. Os GLMs possuem três componentes: aleatório, sistemático e função de ligação. Existem muitos tipos de GLM: binomial, Poisson, gama, quasi, gaussiano, tweedie, etc. Os GLMs são recentemente um ótimo e fácil ponto de partida para metodologias estatísticas avançadas. Podemos usar GLMs, por exemplo, para extrapolação, onde o aumento de gradiente ou florestas aleatórias não funcionam bem. Podemos usar GLMs no setor financeiro para avaliar empréstimos ou ações, no setor de saúde ou em quaisquer outros casos com várias variáveis independentes. O conceito de GLM é direto em comparação com metodologias de ML e geralmente são necessárias mais transformações e compreensão antes de fazer uma conclusão.</p>
<p>O objetivo deste código Python é criar um GLM binomial (ou tweedie) simples e prever/prever valores de inadimplência para um departamento de crédito em um banco. O inadimplência é a variável de resposta/dependente, falhas no cumprimento de uma obrigação de empréstimo. Quanto maior o inadimplência, maior a chance de o empréstimo não ser reembolsado. As variáveis independentes são: RiskLevel, YOB (Years On Book), LGD (Loss Given Default), EAD (exposição em caso de inadimplência), ID (Chave Primária), Ano, Retorno DJX (Índice Dow Jones), PIB (Produto Interno Bruto).</p>
<p>Os conjuntos de dados estão localizados aqui:</p>
<ul>
  <li>Empréstimos Pendentes (Outstanding Loans) - Colunas: RiskLevel, YOB, LGD, EAD</li>
  <li>Empréstimos Antigos (Old Loans) - Colunas: ID, RiskLevel, YOB, Ano, Inadimplência</li>
  <li>Histórico Simplificado do Fed (Simplified Fed History) (anos 2000 – 2017) - Colunas: Ano, Retorno DJX, PIB</li>
  <li>Adverso Simplificado (Simplified Adverse) (anos 2018, 2019, 2020) - Colunas: Ano, DJX, PIB</li>
</ul>
<h2 align="center">1. Código Python</h2>
<p>O código Python completo está disponível nas refêrencias. Instale e importe bibliotecas no Google Colaboratory.</p>
<pre>
%matplotlib inline
import numpy as np
import pandas as pd
import statsmodels.api as sm
import matplotlib.pyplot as plt
import statsmodels.formula.api as smf
</pre>
<p>Prepare os dados para o trabalho.</p>
<pre>
# Leia o portfólio de crédito. Portfólio de empréstimos para teste
myPortfolio = pd.read_excel("OutstandingLoans.xlsx")
# Leia empréstimos antigos
myLoanHistory = pd.read_excel("OldLoans.xlsx")
# Leia os dados econômicos e financeiros do Fed
FedHistory = pd.read_csv("Simplified_FedHistory.csv")
</pre>
<p>Combine os dois conjuntos de dados, crie o modelo GLM e exiba os resultados. Você pode escolher entre as famílias GLM da biblioteca Statsmodels, Binomial, Tweedie ou Poisson, estas 3 fornecerão um ajuste muito bom. A diferença não é crítica, no entanto, Tweedie é recentemente considerado o mais projetado para questões de risco coletivo. A função de link do Tweedie não é logit, mas log.</p>
<pre>
# Combine os dois conjuntos de dados para obter as variáveis para os valores históricos em 1 quadro de dados
combinedHistory = pd.merge(myLoanHistory, FedHistory, on = "Year")
# Criar MODELO LINEAR GENERALIZADO
# fórmula: Default representa o intercepto (variável dependente)
# O intercepto é o valor previsto das variáveis dependentes, quando todas as variáveis independentes / Nível de risco, YOB, DJX, PIB / são 0.
# Você também pode tentar a família Tweedie com sua função de link neste caso

model = smf.glm(formula = "Default ~ RiskLevel + YOB + DJX_Return + GDP", data = combinedHistory, family = sm.families.Binomial())

#De um Fit no modelo
result = model.fit()

#Exibir e interpretar os resultados
print(result.summary())

#Probabilidades estimadas de inadimplência
predictions = result.predict()
</pre>
<p>Vamos agorta interpretar os resultados.</p>
<img src="resultado.webp">
<p><b>Variáveis</b> — as variáveis independentes são aquelas que selecionamos na Fórmula acima: RiskLevel, YOB, DJX_Return e GDP. A variável dependente é o Default, está na primeira linha chamada como Intercept, a que predizemos.</p>
<p><b>Coeficientes</b> — a partir da saída da regressão, podemos ver que o coeficiente de regressão para RiskLevel é 0.6735. Isso significa que, em média, cada nível de risco adicional está associado a um aumento de 0.6735 pontos no inadimplência final, assumindo que as outras variáveis preditoras YOB, DJX e PIB sejam mantidas constantes.</p>
<p><b>Deviance</b> - é a variância não explicada pelo modelo. O deviance é uma métrica de qualidade do ajuste para modelos estatísticos, usada para GLMs. É a diferença entre o modelo saturado (perfeito) e o modelo proposto, o quanto de variação existe no modelo de dados proposto. Quanto menor o deviance, melhor o modelo.</p>
<p><b>Df Model</b> - o Df Model é o número das nossas 4 variáveis ​​preditoras. Temos 4 preditores aqui: RiskLevel, YOB, DJX, GDP.</p>
<p><b>Df Residuals</b> - é o tamanho da amostra menos o número de parâmetros sendo estimados, df(Residual) = n - (k+1) = n - k - 1. O Df Residuals é outro nome para nossos graus de liberdade no nosso modelo.</p>
<p><b>Função de ligação (função canônica)</b> - ela liga o seu preditor linear. A distribuição normal tem função de ligação identidade, a distribuição Poisson tem função de ligação log e a distribuição Binomial tem função de ligação logit. A melhor descrição é fornecida na biblioteca statsmodels.</p>
<p><b>Escala (escala real)</b>- na Binomial e Poisson, a escala é 1 sob a hipótese de especificação correta. Em gaussian e outros, temos um parâmetro de escala adicional não fixo em um. Em Poisson ou Binomial dispersos, também temos um parâmetro de escala adicional.</p>
<p><b>[0.025 e 0.975]</b> - estes são intervalos de confiança simétricos. Para amostras menores, 0.025 é melhor/mais preciso do que 0.5, claro. 0.025 e 0.975 são medidas dos valores dos nossos coeficientes dentro de 97.5% dos nossos dados. Fora desses valores, geralmente podem ser considerados outliers. 97.5% da área de uma distribuição normal do coeficiente RiskLevel está entre os valores 0.637 e 0.710. Ou seja, há uma chance de 97.5% de que o coeficiente de YOB tenha um valor entre -0.327 e -0.303.</p>
<p><b>Std err</b> - o std err é o erro padrão / desvio padrão da estimativa do ponto do coeficiente no GLM. É uma medida de incerteza sobre esta estimativa. Um erro muito grande significa que uma estimativa do coeficiente é calculada com muita imprecisão. Por exemplo, o coeficiente do DJX é estimado com mais precisão do que o coeficiente do PIB.</p>
<p><b>P>|z|</b> - um dos dados estatísticos mais importantes no resumo do GLM. Ele usa as estatísticas z para gerar o valor p, uma medida de quão provável é que sua estimativa do ponto do coeficiente seja medida por meio do modelo GLM por acaso. O valor p de 0% para RiskLevel está dizendo que não há chance de que o RiskLevel não tenha efeito na variável dependente Default, portanto, os resultados não são produzidos por acaso. O valor p de, por exemplo, 0,256 para RiskLevel estaria dizendo que há uma chance de 25,6% de que a variável RiskLevel não tenha efeito na variável dependente, Default, e os resultados sejam produzidos por acaso. O P>|z| informa se nossa estimativa do ponto foi calculada "bem" para distingui-la de zero. Definimos "bem" usando o p < 0,05, porque uma alfa comum é 0,05. O P>|z| irá comparar o valor p a um valor alfa previamente estabelecido ou a um limiar z com o qual você aplica significância ao seu coeficiente.</p>
<p><b>Pearson Chi2</b> - quanto maior o valor do Qui-quadrado, maior a probabilidade de que haja uma diferença significativa. O Chi2 é uma função dos graus de liberdade e da escala real. É um teste de independência e faz sentido comparar, por exemplo, 2 modelos GLM (escolha o modelo com o menor Chi2) ou comparar as contagens observadas com seus valores esperados sob a configuração multinomial. Quanto maior o valor do Qui-quadrado, maior a probabilidade de que realmente exista uma diferença significativa.</p>
<p><b>Iterations</b> - quanto tempo levou para você ajustar a verossimilhança do log no modelo. Normalmente, o IRLS não leva mais do que 25 iterações e você deseja minimizar o tempo de computação. Com cada nova iteração, a verossimilhança do log é ligeiramente mais alta/melhor. Muitas outras metodologias iterativas estão tentando remover cálculos redundantes, lidar melhor com cálculos de matrizes tabuladas, incluir mais funções para validações cruzadas automatizadas, etc.</p>
<p><b>Log likelihood</b> - é o logaritmo natural da probabilidade. A log-likelihood é uma indicação numérica da probabilidade de que seu modelo produzido produziu. Ele compara os valores dos coeficientes para cada variável no processo de criação do modelo. A probabilidade é o produto da densidade avaliada nas observações. Normalmente, a densidade assume valores menores que um, portanto, seu logaritmo será negativo como neste caso: -27334. Valores mais altos (valores menos negativos) correspondem a um melhor ajuste, porque você deseja maximizar a verossimilhança do intercepto. Por exemplo, um valor de log-likelihood de -3 é melhor do que -7. O logaritmo é uma função monotônica crescente de seu argumento, a maximização do log de uma função está correlacionada com a maximização da função em si.</p>
<p><b>Z-score</b> - é uma medida numérica que descreve uma relação entre um valor e a média de um grupo de valores. É o desvio padrão da média. Se uma pontuação Z é 0, a pontuação do ponto de dados é idêntica à pontuação média.</p>
<p>Revisar AIC e BIC. O AIC (critério de informação de Akaike) tem valor menor quanto melhor ajustamos o modelo. Da mesma forma que BIC ou MDL, o AIC fornece a pontuação básica para escolher o melhor modelo. O BIC (critério de informação bayesiana) tem um valor menor, melhor o ajuste do modelo. O cálculo é semelhante ao MDL. Geralmente, há uma alta correlação entre AIC e BIC. MDL (descrição mínima) é outro critério para pontuar um modelo, valor menor, melhor o ajuste do modelo.</p>
