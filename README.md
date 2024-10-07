# Washington Bike Rental Business Case

![roman-koester-bike.jpg](assets\roman-koester-bike.jpg)

## Background do Projeto

Este projeto tem como objetivo **realizar a análise de um conjunto de dados com informações que representam o aluguel de bicicletas na cidade de Washington/EUA**.

Os insights são disponibilizados nas seguintes áreas:

* **Comportamento de Usuário**
* **Clima**
* **Tempo**

![tools](assets\tools.png)

Para o desenvolvimento do projeto, utilizarei **`Python`** para a preparação e exploração dos dados devido à sua flexibilidade e eficiência. Após estas etapas, os dados serão exportados no formato **`csv`** e importados ao Google Sheets para análisar as hipóteses geradas.

O código em Python utilizado para inspecionar, limpar os dados e correlacionar as variáveis pode ser encontrado [neste link](https://github.com/hyrtx/bike-rental-business-case/blob/main/washington_bikes_analysis.ipynb).

O dashboard interativo utilizado para reportar e explorar a relação das variáveis no número do aluguel de bicicletas pode ser acessado [neste link](https://lookerstudio.google.com/reporting/3b0572a1-d24b-45a4-a23c-d5569bbab053)

## Estrutura de Dados

Os dados foram disponibilizados em um único arquivo Excel (xlsx), com uma quantidade total de 10.886 linhas. A descrição de cada variável é a seguinte:

| **Nome da Variável** | **Descrição**                                                                  |
|----------------------|--------------------------------------------------------------------------------|
| Datetime             | Data e Hora                                                                    |
| Season               | Estações do ano: 1 = inverno, 2 = primavera, 3 = verão, 4 = outono             |
| Holiday              | Feriado                                                                        |
| Workingday           | Dia de trabalho                                                                |
| Weather              | Condição climática: 1 = ensolarado, 2 = nublado, 3 = chovendo, 4 = nevasca     |
| Temp                 | Temperatura no dia                                                             |
| Humidity             | Umidade no dia                                                                 |
| Windspeed            | Velocidade do vento. A unidade de medida é km/h.                               |
| Casual               | Aluguel não mensalista                                                         |
| Registered           | Aluguel mensalista                                                             |
| Count                | Quantidade total de aluguel (casual + registered)                              |
| temp                 | Temperatura em Celsius                                                         |
| atemp                | Temperatura normalizada em Celsius, sensação térmica                           |
| hum                  | Umidade normalizada (os valores são divididos por 100, valor máximo)           |
| windspeed            | Velocidade do vento normalizada (os valores são divididos por 67, valor máximo)|

## Resumo Executivo

### Insights

#### Comportamento de Uso e Tendência de Aluguéis:

* Observa-se um **crescimento no número total de aluguéis no ano de 2012, com crescimento de 66.7% em relação ao mês anterior**.
* Os usuários registrados no serviço correspondem a **81% dos aluguéis de bicicletas**.

![comportamento_uso_tendencias](assets\comportamento_uso_tendencias.png)

#### Influência de Fatores Climáticos:

* Há um aumento consistente no número total de aluguéis **durante os meses mais quentes (de abril a setembro)**, indicando que o clima agradável do verão e primavera impulsiona o uso de bicicletas.
* Nos meses mais frios (de novembro a março), observa-se uma diminuição significativa no número de aluguéis, sugerindo que temperaturas mais baixas desencorajam o uso de bicicletas.
* A temperatura influencia consideravelmente o número de aluguéis. Dias com temperaturas acima de 30 graus tem média de  344 bicicletas alugadas, 93% maior em relação aos dias com temperatura abaixo de 30º.
* Usuários tendem a alugar mais bicicletas em dias com menor umidade do ar. Dias com a umidade relativa do ar abaixo de 40% tem média de 290 aluguéis, 62% maior em relação aos dias mais umidos.

![influencia_clima](assets\influencia_clima.png)

#### Influência de Fatores Temporáis:

* O uso de bicicleta está mais concentrado nos períodos de 8AM e 5PM-6PM. Isso implica que o uso mais frequente é em horários de ida e retorno do trabalho.
* Nos finais de semana o comportamento é mais distribuido durante o dia, concentrando mais aluguéis entre fim da manhã e o fim de tarde.

![influencia_tempo](assets\influencia_tempo.png)

## Premissas

1. O dicionário de dados não informou as unidades de medidas das variáveis `windspeed` e `humidity`. Em contato com a pessoa responsável por disponibilizar o dataset, foi informado que podemos considerar km/h para `windspeed` e unidade relativa do ar (%rh).
2. A variável `windspeed` apresenta valores incoerentes, com média de 116796,5 km/h, muito superior ao recorde mundial de velocidade do vento. Acreditamos que houve um erro de digitação ou conversão de unidade. Para corrigir, vamos **normalizar a variável**, dividindo os valores pelo valor máximo e analisar a distribuição dos dados. A explicação mais detalhada sobre essa premissa está na etapa de **Carregamento e Inspeção dos Dados**.