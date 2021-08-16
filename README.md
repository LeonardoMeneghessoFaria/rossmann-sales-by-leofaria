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

# Três principais insights
