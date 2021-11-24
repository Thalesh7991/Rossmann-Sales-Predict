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

## 5. Modelos de Machine Learning Aplicados


## 6. Performance do Modelo de Machine Learning

## 7. Resultados de Negócio

## 8. Conclusões


## 9. Lições Aprendidas


## 10. Próximos Passos


