# Rossmann Store Sales Prediction

Predição de vendas usando Machine Learning

![machine-learning](https://user-images.githubusercontent.com/87080266/129563112-146c946e-dfdb-4f6d-8721-246ebf7a5458.jpg)

# Problema da Loja

O CFO solicita a previsão de cada loja em uma reunião mensal, pois era difícil saber o melhor valor de investimento para as reformas de cada loja, devido à previsão fornecida pelos diretores não ser assertiva, havia muitos erros no valor necessitado. Então, para resolver esse problema, usei algoritmos de Machine Learning para prever precisamente como seria a previsão da loja nas próximas seis semanas.

# Suposições

- Os dias em que as lojas estavam fechadas foram descartados.
- Apenas lojas com vendas maiores que 0 foram consideradas para a predição.
- Para lojas que não tinham informações sobre a distância das competições, foi assumido que a distância seria duas vezes maior do que a maior distância de um concorrente mais próximo.

# Lista de Atributos

| Atributos                        | Descrições                                                     |
| -------------------------------- | ------------------------------------------------------------ |
| Id                               | Um id que representa uma (loja, data) dupla dentro do conjunto de teste|
| Store                            | Um id único para cada loja|
| Sales                            | O volume de venda da loja|
| Customers                        | O número de clientes em um determinado dia|
| Open                             | Um indicador para saber se a loja estava aberta: 0 = fechada, 1 = aberta|
| Stateholiday                     | Indica um feriado estadual. A grande maioria das lojas fecham nos feriados estaduais. Observe que todas as escolas fecham nos feriados e finais de semana. A = feriado, b = feriado da páscoa, c = natal, 0 = nenhum|
| Schoolholiday                    | Indica se a (loja, data) foi afetada pelo fechamento de escolas públicas|
| Storetype                        | Diferencia entre 4 tipos des lojas diferentes: a, b, c, d|
| Assortment                       | Descreve um nível de sortimento: a = básico, b = extra, c = estendido|
| Competitiondistance              | Distância em metros até a loja concorrente mais próxima|
| Competitionopensince[month/year] | Mostra o ano e mês aproximados em que o concorrente mais próximo foi aberto|
| Promo                            | Indica se a loja está fazendo uma promoção naquele dia|
| Promo2                           | Promo2 é uma promoção contínua e consecutiva para algumas lojas: 0 = a loja não está participando, 1 = a loja está participando|
| Promo2since[year/week]           | Descreve o ano e a semana do calendário em que a loja começou a participar da promo2|
| Promointerval                    | Descreve os intervalos consecutivos em que a promoção2 é iniciada, nomeando os meses em que a promoção é iniciada novamente|

# Estratégia de Solução

O método que apliquei no projeto foi o CRISP-DM:
- Step 01. O objetivo é usar métricas estatísticas para identificar outliers no escopo do negócio.

- Step 02. Derive novos atributos com base nas variáveis originais para descrever melhor o fenômeno a ser modelado.

- Step 03. Filtre as linhas e selecione as colunas que não contêm informações para modelagem ou não correspondem ao escopo do negócio.

- Step 04. Explore os dados para encontrar insights e entender melhor o impacto das variáveis no aprendizado do modelo.

- Step 05. Prepare os dados para que os modelos de machine learning possam aprender um comportamento específico.

- Step 06. Seleção dos atributos mais significativos para treinar o modelo.

- Step 07. Treinamento de modelo de machine learning.

- Step 08. Escolha os melhores valores para cada um dos parâmetros do modelo selecionado na etapa anterior.

- Step 09. Converta o desempenho do modelo em um resultado de negócios.

- Step 10. Publique o modelo em um ambiente de nuvem para que outras pessoas ou serviços possam usar os resultados para melhorar a decisão de negócios.

- Step 11. Criação de um bot no app do telegrama, para consultar a previsão a qualquer momento e em qualquer lugar.

# Três principais Insights para o time de negócio

- Hipótese 2 - As lojas com concorrentes mais próximos deveriam vender menos.

FALSE: As lojas com concorrentes mais próximos vendem mais.

![image](https://user-images.githubusercontent.com/87080266/129576697-4a011cde-da5f-40b7-ac7c-b93f1f6c2efc.png)

- Hipótese 9. As lojas da loja vendem mais com o passar dos anos.

FALSE: As lojas vendem menos ao longo dos anos

![image](https://user-images.githubusercontent.com/87080266/129579189-b08148ee-cd51-4955-b372-79fa151a293c.png)

- Hipótese 11. - As lojas devem vender mais a partir do dia 10 de cada mês.

TRUE: As lojas vendem mais a partir do dia 10 de cada mês.

![image](https://user-images.githubusercontent.com/87080266/129579448-5957f4ff-c678-439e-ada4-f7bb118b1a55.png)

# Machine Learning aplicados

Os testes foram realizados usando os seguintes algoritmos:

Linear Regression Model

Linear Regression Regularized Model - Lasso

Random Forest Regressor

XGBoost Regressor

# Machine Learning Model Performance

- Single Performance

|Model Name               |	MAE        |MAPE      |	RMSE|
| ------------------------|------------|----------|-----|
|Random Forest Regressor  |	678.296634 |0.099816	|1008.248950|
|XGBoost Regressor	      |843.112293	 |0.122609	|1250.952637|
|Average Model	          |1354.800353 |0.455051	|1835.135542|
|Linear Regression	      |1867.089774 |0.292694	|2671.049215|
|Linear Regression - Lasso|1869.571858 |0.288111	|2694.005137|

- Real Performance - Cross Validation

|Model Name               |	MAE CV           |MAPE CV        |	RMSE CV          |
| ------------------------|------------------|---------------|-------------------|
|Random Forest Regressor  |838.18 +/- 218.74 |0.12 +/- 0.02	|1256.87 +/- 319.67|
|XGBoost Regressor	      |1030.28 +/- 167.19|0.14 +/- 0.02	|1478.26 +/- 229.79|
|Linear Regression	      |2081.73 +/- 295.63|0.3 +/- 0.02  |2952.52 +/- 468.37|
|Linear Regression - Lasso|2088.88 +/- 327.01|0.3 +/- 0.01  |2988.6 +/- 499.57 |

Embora o modelo Random Forest tenha se mostrado superior aos demais, em alguns casos esse modelo acaba exigindo muito espaço para ser publicado, resultando em um custo extra para a empresa mantê-lo funcionando. Portanto, o algoritmo escolhido foi o XGBoost Regressor que em sequência passou para a etapa de Fine Tunning de Hiperparâmetros.

- Final Performance - Hyperparameter Fine Tunning Cross Validation

Depois de encontrar os melhores parâmetros para o modelo por meio do método de pesquisa aleatória, as métricas finais para o modelo foram as seguintes:

|Model Name               |	MAE CV           |MAPE CV        |	RMSE CV          |
| ------------------------|------------------|---------------|-------------------|
|XGBoost Regressor        |1030.28 +/- 167.19|0.14 +/- 0.02	 |1478.26 +/- 229.79 |

# Desempenho do modelo em valores de receita

Agora é possível analisar as métricas e comparar a diferença de desempenho entre o modelo atual utilizado pela empresa (Média das vendas) e o modelo proposto pelo cientista de dados (XGBoost Regressor).

- Modelo atual baseado em vendas médias

|Scenery           |	Values         |
| -----------------|-----------------|
|Predictions       |R$ 280,754,389.45|

- Model with XGBoost Regression

|Scenery           |	Values        |
| -----------------|----------------|
|Predictions       |R$285,860,497.84|
|Worst Scenario	   |R$285.115,015.78|
|Best Scenery      |R$286.605,979.91|

# Como ver o modelo em produção executando a predição de vendas

- Fazer download do telegram no celular, no computador ou utilizar o telegram web; 
- Criar uma conta no telegram;
- Fazer login no telegram; 

# Telegram Bot

Para acessar o bot do telegram clique abaixo:

[<img alt="Telegram" src="https://img.shields.io/badge/Telegram-2CA5E0?style=for-the-badge&logo=telegram&logoColor=white"/>](https://t.me/rossmann_by_leofaria_bot)

# Predição em tempo real

Envie um número por vez para receber a predição da loja com base nas próximas seis semanas.

![image](https://user-images.githubusercontent.com/87080266/129598095-9bb8c6e4-83ef-4cf8-8ea2-4ed0695493f1.png)

Se o bot Rossmann receber algo diferente de números, ele responderá Store ID is Wrong. No banco de dados utilizado pode ocorrer que tenha algumas lojas indisponíveis para predição, então ele responderá Store Not Available. Se isso acontecer, você pode requisitar a predição de uma outra loja e seguir em frente.

![image](https://user-images.githubusercontent.com/87080266/129598871-ea72a747-e26c-48cb-a182-ef6f7857d49a.png)

#  Next steps

Iniciar um segundo ciclo de análise do problema, buscando diferentes abordagens, principalmente considerando lojas com comportamento difícil de prever. Nessas lojas, o cientista de dados deve ganhar bastante experiência.

Possíveis pontos a serem abordados no segundo ciclo:

-**Trabalhe com os dados de NA de maneira diferente**

-**Reescalonamento e codificação de dados com diferentes metodologias**

-**Trabalhe com novos recursos de previsão**

-**Trabalhe com um método mais robusto para encontrar os melhores parâmetros Hyper para o modelo**

# Conclusão

Por fim, é possível compreender que embora o modelo baseado em médias seja simples, ele ainda é coerente, porém não é o suficiente para compreender a oscilação das vendas das lojas, já os modelos de machine learning possuem uma precisão mais perto do real, informando assim o melhor e o pior cenário.

O Modelo XGBoost para o primeiro ciclo (Metodologia CRISP-DM) apresentou um resultado dentro da faixa aceitável, embora algumas lojas tenham sido difíceis de ter o comportamento esperado apresentando o MAPE (Mean Absolute Percenage Error) entre 0,30 a 0,56, este primeiro resultado irá ser apresentado à empresa, para informar o andamento do projeto e o que já está disponível como solução.

# Tecnologias Utilizadas

- Python;
- Jupyter.
 
# Author

Leonardo Meneghesso Faria

[<img alt="LinkedIn" src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white"/>](https://www.linkedin.com/in/leonardo-meneghesso-faria-92553b155/)





