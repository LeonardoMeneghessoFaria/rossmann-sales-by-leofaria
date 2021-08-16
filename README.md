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
| Id                               | |
| Store                            | |
| Sales                            | |
| Customers                        | |
| Open                             | |
| Stateholiday                     | |
| Schoolholiday                    | |
| Storetype                        | |
| Assortment                       | |
| Competitiondistance              | |
| Competitionopensince[month/year] | |
| Promo                            | |
| Promo2                           | |
| Promo2since[year/week]           | |
| Promointerval                    | |
