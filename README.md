# LabMetrics
### Análise de dados aplicada à rotina de laboratórios clínicos

![Power BI](https://img.shields.io/badge/Power_BI-Analytics-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![Power Query](https://img.shields.io/badge/Power_Query-ETL-217346?style=for-the-badge&logo=microsoft&logoColor=white)
![DAX](https://img.shields.io/badge/DAX-Measures-0078D4?style=for-the-badge&logo=microsoft&logoColor=white)
![GitHub](https://img.shields.io/badge/GitHub-Versionamento-181717?style=for-the-badge&logo=github&logoColor=white)
![Status](https://img.shields.io/badge/Status-Em_desenvolvimento-orange?style=for-the-badge)

O projeto tem como objetivo principal entender como os dados gerados na rotina de um laboratório podem ser utilizados para analisar o desempenho operacional. A proposta é explorar dados laboratoriais, construir indicadores e investigar situações que podem passar despercebidas na operação diária.

## Sobre o projeto
O projeto foi desenvolvido no Power BI, utilizando uma base de dados referente a janeiro de 2025, com 22.805 registros de exames.
O foco inicial foi analisar o cumprimento dos prazos de liberação dos exames (SLA), observando o comportamento dos resultados por origem, área técnica e período.
Durante o desenvolvimento, também trabalhei na preparação dos dados, identificação de registros sem informações temporais válidas e definição das regras necessárias para calcular os indicadores corretamente.

## Resultados obtidos

Dos 22.805 registros analisados, 19.781 foram considerados elegíveis para avaliação do SLA, conforme as regras de negócio definidas.
Os resultados desse grupo foram:

| Indicador | Resultado |
|---|---:|
| Exames dentro do SLA | 18.193 |
| Exames fora do SLA | 1.588 |
| Cumprimento do SLA | 92,0% |
| Fora do SLA | 8,0% |

Os demais registros foram tratados separadamente:

- 1.499 exames pertenciam à unidade LabApoio e não se aplicavam ao SLA hospitalar utilizado na análise.
- 1.525 registros não apresentavam TAT válido.

Essa separação foi importante para evitar que registros sem critérios de avaliação fossem incorporados indevidamente aos indicadores.
