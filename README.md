# Rossmann Sales Predict



![SALES](/sales_analysis.jpg)
## 1. Problema de Negócio

<p> A empresa Rossmann é uma das maiores redes de drogaria da Europa, com cerca de mais de 56.200 funcionários e mais de 4000 lojas espalhadas pelo continente.</p>

<p> Em uma reunião mensal com todos os gerentes da rede, o CFO solicitou uma previsão do faturamento de cada loja para as próximas 6 semanas a fim de que ele possa decidir qual loja terá budget suficiente para realizar reformas em sua estrutura. </p>

<p> As vendas das lojas são influenciadas por muitos fatores, incluindo promoções, competição entre as lojas, feriados escolares e estaduais, sazonalidade e localidade. Com milhares de gerentes individuais prevendo vendas com base em suas circunstâncias únicas, a precisão dos resultados pode ser bastante variada o que preujudica na tomada de decisão do CFO. </p>

<p> Portanto, desenvolvi um modelo de Machine Learning que é capaz de realizar previsões do faturamento de cada loja com maior precisão. Além disso, desenvolvi uma aplicação para que o CFO possa consultar as previsões de faturamento diretamente do seu celular a qualquer momento, auxiliando na tomada de decisão. </p>

## 2. Suposições de Negócio.

***The assumptions about the business problem is as follows:*** 

## Lista de Atributos

Para o processo de análise foi utilizado um dataset que possui os seguintes dados:

| Atributos  |  Descrição |
| ------------------- | ------------------- |
|  Id |  Um id que representa uma (loja, data) dupla dentro do conjunto de teste |
|  Store |  Um id único para cada loja |
|  Sales |  O volume de vendas feitas |
|  Customers |  O número de clientes em um determinado dia |
|  Open |  Um indicador para saber se a loja estava aberta: 0 = fechada, 1 = aberta |
|  Stateholiday |  Indica um feriado estadual. Normalmente todas as lojas, com poucas exceções, fecham nos feriados estaduais. Observe que todas as escolas fecham nos feriados e finais de semana. A = feriado, b = feriado da páscoa, c = natal, 0 = nenhum |
|  Schoolholiday |  Indica se (loja, data) foi afetado pelo fechamento de escolas públicas |
|  Storetype |  	Diferencia entre 4 modelos de loja diferentes: a, b, c, d |
|  Assortment |  Descreve um nível de sortimento de produtos: a = básico, b = extra, c = estendido |
|  Competitiondistance |  Distância em metros até a loja concorrente mais próxima |
|  Competitionopensince[month/year] |  Dá o ano e mês aproximados em que o concorrente mais próximo foi aberto |
|  Promo |  Indica se uma loja está fazendo uma promoção naquele dia |
|  Promo2 |  Promo2 é uma promoção contínua e consecutiva para algumas lojas: 0 = a loja não está participando, 1 = a loja está participando |
|  Promo2since[year/week] |  Descreve o ano e a semana do calendário em que a loja começou a participar da promo2 |
|  Promointerval |  Descreve os intervalos consecutivos em que a promoção2 é iniciada, nomeando os meses em que a promoção é iniciada novamente. EG "fevereiro, maio, agosto, novembro" significa que cada rodada começa em fevereiro, maio, agosto, novembro de qualquer ano para aquela loja |


## 3. Estratégia de Solução

![CRISP](/crisp_metodo.png)

***Minha estratégia para resolver esse desafio foi:***

**Step 01. Data Description:**  O objetivo é utilizar métricas estatísticas para identificar outliers no escopo do negócio.

**Step 02. Feature Engineering:** Derivar novos atributos com base nas variáveis originais para descrever melhor o fenômeno a ser modelado.

**Step 03. Data Filtering:** Filtrar as linhas e selecionar as colunas que não contenham informações para modelagem ou não correspondam ao escopo do negócio.

**Step 04. Exploratory Data Analysis:** Explorar os dados para encontrar insights e entender melhor o impacto das variáveis no aprendizado do modelo.

**Step 05. Data Preparation:** Preparar os dados para que os modelos de aprendizado de máquina possam aprender um comportamento específico.

**Step 06. Feature Selection:** Seleção dos atributos mais significativos para treinar o modelo.

**Step 07. Machine Learning Modelling:** Treinamento do modelo de aprendizado de máquina.

**Step 08. Hyperparameter Fine Tunning:** Escolher os melhores valores para cada um dos parâmetros do modelo selecionado na etapa anterior.

**Step 09. Convert Model Performance to Business Values:** Converter o desempenho do modelo em um resultado de negócios.

**Step 10. Deploy Modelo to Production:** Publicar o modelo em um ambiente web para que outras pessoas ou serviços possam usar os resultados para melhorar a decisão de negócios.

**Step 11. Telegram Bot:** Criação de um bot no app do telegram, para consultar a previsão a qualquer momento

## 4. Top 3 Insights de Negócio
No processo das análises exploratórias dos dados, foram levantadas algumas hipóteses de negócio que deveriam ser validadas (ou invalidadas) a fim de trazer insights de negócio. Destaco aqui 3 Insights identificados nos dados.

**Hipótese**: Lojas com competidores mais próximos deveriam vender menos.

![DISTANCE](/in_distance.png)

Com este gráfico podemos comprovar que esta hipótese é falsa, pois podemos notar que lojas que possuem competidores mais próximos vendem mais.


**Hipótese**: Lojas com maior sortimentos de produtos deveriam vender mais.

![ASSORTMENT](/in_assortment.png)

Este Insight nos mostra que lojas com maior sortimento de produtos vendem menos.

**Hipótese**: As lojas deveriam vender mais ao longo dos anos

![SALES](/in_sales.png)

Este Insight nos mostra que as lojas estão vendendo menos ao longo dos anos.

## 5. Modelos de Machine Learning Aplicados
Os testes foram realizados usando os seguintes algoritmos:

  -> Modelo de Regressão Linear

  -> Modelo Regularizado de Regressão Linear - Lasso

  -> Random Forest Regressor

  -> Regressor XGBoost

  -> Light GBM


## 6. Performance do Modelo de Machine Learning
**Performance Individual**
| Modelo  |  MAE  | MAPE  |  RMSE  |
| ------------------- | ------------------- | ------------------- | ------------------- |
|  Random Forest Regressor |  679.598831	 |  0.099913 |  	1011.119437 |
|  LGBM Regressor |  1325.406431 |  0.196505 |  1896.403553 |
|  Linear Regression |  1867.089774	 |  0.292694	 |  2671.049215 |
|  Linear Regression - Lasso |  1891.704881 |  0.289106 |  2744.451737 |
|  XGBoost Regressor |  6683.606400 |  0.949503	 |  7330.742181 |

**Desempenho Real: Aplicando Cross Validation**
| Modelo  |  MAE  | MAPE  |  RMSE  |
| ------------------- | ------------------- | ------------------- | ------------------- |
|  Random Forest Regressor |  836.61 +/- 217.1	 |  0.12 +/- 0.02 |  	1254.3 +/- 316.17 |
|  LGBM Regressor |  1449.09 +/- 183.35 |  0.2 +/- 0.01 |  2080.81 +/- 249.66 |
|  Linear Regression |  2081.73 +/- 295.63	 |  0.3 +/- 0.02	 |  2952.52 +/- 468.37 |
|  Linear Regression - Lasso |  2116.38 +/- 341.5 |  0.29 +/- 0.01 |  3057.75 +/- 504.26 |
|  XGBoost Regressor |  7047.97 +/- 587.65 |  0.95 +/- 0.0	 |  7714.03 +/- 688.72 |

Apesar do modelo resultante do algoritmo **Random Forest** apresentar resultados superiores aos demais algoritmos, o mesmo toma muito espaço de armazenamento para fazer o deploy em produção, resultando em um custo maior para a empresa mantê-lo no ar. Portanto, decidi escolher o algoritmo **LGBM Regressor** que apresentou um desempenho levemente inferior que tenha um menor custo para publicação. **Posteriormente foi realizado o processo de Ajuste de Hiperparâmetros do modelo e tivemos o seguinte resultado:**

| Modelo  |  MAE  | MAPE  |  RMSE  |
| ------------------- | ------------------- | ------------------- | ------------------- |
|  LGBM Regressor |  630.352479		 |  0.091133|  	922.178829 |


![PRED](/pred_erro.png)


## 7. Resultados de Negócio

Por meio do modelo é possível reportar para o CFO da empresa a previsão de faturamento total de todas as lojas, com melhor cenário e pior cenário (baseado no erro do modelo). Desse modo ele pode ter uma visão do total de recursos disponíveis para o investimento nas reformas.

| Cenários  |  Faturamento |
| ------------------- | ------------------- |
| Predição |	R$ 283.225.608,85 |
| Pior Cenário |	R$ 282.518.502,12 |
| Melhor Cenário |	R$ 283.932.715,58 |


## 8. Produto de Dados
Para que o CFO tenha acesso às **predições em tempo real**, desenvolvi um bot no telegram que acessa o modelo desenvolvido, que está na web, e possa ter em poucos segundos a **previsão de faturamento das próximas 6 semanas** para todas as lojas que ele desejar.

![BOT](/bot_tel.png)

## 9. Conclusões


## 10. Lições Aprendidas


## 11. Próximos Passos


