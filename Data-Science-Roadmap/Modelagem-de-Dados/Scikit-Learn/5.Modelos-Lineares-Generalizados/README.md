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

# de um Fit no modelo
result = model.fit()
# Exibir e interpretar os resultados
print(result.summary())
# Probabilidades estimadas de inadimplência
predictions = result.predict()
</pre>
