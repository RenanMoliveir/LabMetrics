# LabMetrics
### Análise de dados aplicada à rotina de laboratórios clínicos

O LabMetrics surgiu da minha experiência na área laboratorial e do interesse em entender como os dados gerados na rotina de um laboratório podem ser utilizados para analisar o desempenho operacional.

A proposta é explorar dados laboratoriais, construir indicadores e investigar situações que podem passar despercebidas na operação diária.

Este projeto também faz parte da minha transição profissional para a área de Ciência de Dados, unindo minha experiência em laboratório clínico ao desenvolvimento de habilidades em análise de dados e Business Intelligence.

## Sobre o projeto

A primeira etapa do LabMetrics foi desenvolvida no Power BI, utilizando uma base de dados referente a janeiro de 2025, com 22.805 registros de exames.

O foco inicial foi analisar o cumprimento dos prazos de liberação dos exames (SLA), observando o comportamento dos resultados por origem, área técnica e período.

Durante o desenvolvimento, também trabalhei na preparação dos dados, identificação de registros sem informações temporais válidas e definição das regras necessárias para calcular os indicadores corretamente.

## Primeiros resultados

Dos 22.805 registros analisados, 19.781 foram considerados elegíveis para avaliação do SLA.

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

## O que estou investigando?

Ao aprofundar a análise, alguns resultados chamaram minha atenção:

- **UTI:** concentra o maior número absoluto de exames fora do SLA.
- **Pronto Atendimento:** apresenta uma taxa de não cumprimento de aproximadamente 1,1%.
- **INTER III:** apresenta uma taxa de 17,7%.
- **BIOQ:** concentra o maior volume de atrasos entre as áreas técnicas.
- **HEM:** apresenta 18,2% de exames fora do SLA.
- **IMU:** apresenta uma taxa de 86,9%, resultado que merece investigação mais aprofundada.

Esses números mostram por que olhar apenas para o volume de atrasos não é suficiente. É necessário considerar também a proporção de exames fora do prazo e o contexto de cada área.

O próximo passo é investigar quais exames estão concentrando esses atrasos e compreender melhor os resultados encontrados.

## Ferramentas utilizadas

- **Power BI:** construção das análises e visualizações.
- **Power Query:** preparação e transformação dos dados.
- **DAX:** desenvolvimento de medidas e indicadores.
- **GitHub:** organização e documentação do projeto.

## Organização do projeto

```text
LabMetrics/
│
├── README.md
├── LICENSE
├── .gitignore
│
├── dashboard/
│   ├── README.md
│   └── screenshots/
│
├── docs/
│   ├── 01_contexto_e_objetivos.md
│   ├── 02_regras_de_negocio.md
│   ├── 03_modelagem_de_dados.md
│   ├── 04_indicadores_e_medidas.md
│   ├── 05_insights_e_storytelling.md
│   └── 06_evolucao_do_projeto.md
│
├── data/
│   └── README.md
│
└── assets/
    └── README.md
```

## Documentação

- [Contexto e objetivos](docs/01_contexto_e_objetivos.md)
- [Regras de negócio](docs/02_regras_de_negocio.md)
- [Modelagem de dados](docs/03_modelagem_de_dados.md)
- [Indicadores e medidas](docs/04_indicadores_e_medidas.md)
- [Insights e storytelling](docs/05_insights_e_storytelling.md)
- [Evolução do projeto](docs/06_evolucao_do_projeto.md)

## Status

O LabMetrics continua em desenvolvimento.

Ainda existem análises a aprofundar, hipóteses a investigar e melhorias a implementar. A ideia é documentar essa evolução à medida que o projeto avança.

---

*LabMetrics — Dados laboratoriais além dos resultados.*
