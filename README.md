# LabMetrics
### Business Intelligence e Análise de Dados aplicados a Laboratórios Clínicos

O **LabMetrics** é um projeto de Business Intelligence desenvolvido em Power BI com o objetivo de transformar dados operacionais laboratoriais em informações estratégicas para análise de desempenho, acompanhamento de indicadores e apoio à tomada de decisão.

O projeto utiliza dados de uma operação laboratorial para investigar o cumprimento de prazos de liberação de exames (SLA), identificar pontos de atenção e compreender como o desempenho varia entre origens e áreas técnicas.

---

## Objetivo do projeto

Investigar o desempenho operacional de um laboratório clínico por meio da análise de dados, buscando responder questões como:

- Qual é o percentual de exames liberados dentro do SLA?
- Quais origens apresentam maior concentração de atrasos?
- Quais áreas técnicas possuem maior percentual de exames fora do prazo?
- Como o desempenho varia ao longo do tempo?
- Quais pontos merecem investigação mais aprofundada?

Mais do que apresentar indicadores, o objetivo é transformar resultados em informações que possam orientar decisões e melhorias nos processos laboratoriais.

---

## Contexto da análise

A análise inicial considera dados referentes a **janeiro de 2025**, totalizando 22.805 registros de exames.

Durante a preparação e exploração dos dados, foram identificados três grupos importantes:

| Classificação | Registros | Percentual |
|---|---:|---:|
| Exames elegíveis para SLA | 19.781 | 86,74% |
| Exames LabApoio — não aplicáveis ao SLA hospitalar | 1.499 | 6,57% |
| Registros sem TAT válido | 1.525 | 6,69% |
| **Total** | **22.805** | **100%** |

A partir dos 19.781 exames elegíveis, foram obtidos os seguintes resultados:

| Indicador | Resultado |
|---|---:|
| Exames dentro do SLA | 18.193 |
| Exames fora do SLA | 1.588 |
| Cumprimento do SLA | 92,0% |
| Não cumprimento do SLA | 8,0% |

Os percentuais de cumprimento e não cumprimento consideram exclusivamente os exames elegíveis para avaliação do SLA.

---

## Análises desenvolvidas

### 1. Desempenho geral do SLA
Avaliação do cumprimento dos prazos de liberação dos exames, considerando os registros elegíveis e a classificação dentro ou fora do SLA.

### 2. Análise por origem
Investigação das diferenças de desempenho entre as origens dos exames, identificando setores com maior volume de atrasos e maiores taxas de não cumprimento.

### 3. Análise por área técnica
Comparação do desempenho entre as áreas técnicas do laboratório, permitindo identificar concentrações de atrasos e possíveis prioridades de investigação.

### 4. Análise temporal
Acompanhamento da evolução diária do percentual de exames fora do SLA, buscando identificar oscilações e possíveis padrões operacionais.

---

## Principais descobertas até o momento

A exploração inicial dos dados revelou alguns pontos relevantes:

- **UTI:** apresenta o maior volume absoluto de exames fora do SLA, com 972 registros.
- **Pronto Atendimento:** apresenta percentual de exames fora do SLA de aproximadamente 1,1%.
- **INTER III:** apresenta percentual de não cumprimento de 17,7%.
- **BIOQ:** concentra o maior volume absoluto de atrasos entre as áreas técnicas, com 787 registros.
- **HEM:** apresenta 18,2% de exames fora do SLA.
- **IMU:** apresenta percentual de 86,9%, sendo um ponto prioritário para investigação adicional.

Esses resultados demonstram a importância de analisar os indicadores sob diferentes perspectivas. Um setor pode concentrar o maior volume de atrasos sem necessariamente apresentar a maior proporção de não cumprimento.

Os resultados identificados são pontos de partida para investigações mais aprofundadas, não conclusões definitivas sobre as causas dos atrasos.

---

## Tecnologias e ferramentas

- **Power BI:** desenvolvimento das visualizações e análise dos indicadores.
- **Power Query:** extração, transformação e preparação dos dados (ETL).
- **DAX:** criação de medidas, indicadores e cálculos analíticos.
- **GitHub:** versionamento, organização e documentação do projeto.

---

## Estrutura do repositório

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

---

## Documentação

A documentação técnica e analítica do projeto está organizada em:

- [Contexto e objetivos](docs/01_contexto_e_objetivos.md)
- [Regras de negócio](docs/02_regras_de_negocio.md)
- [Modelagem de dados](docs/03_modelagem_de_dados.md)
- [Indicadores e medidas DAX](docs/04_indicadores_e_medidas.md)
- [Insights e storytelling](docs/05_insights_e_storytelling.md)
- [Evolução do projeto](docs/06_evolucao_do_projeto.md)

---

## Status do projeto

**Em desenvolvimento.**

O projeto está em evolução contínua, com foco no aprofundamento das análises, validação dos indicadores, documentação das regras de negócio e aprimoramento da capacidade de gerar insights a partir dos dados.

### Próximas etapas

- Investigar os exames responsáveis pela concentração de atrasos nas áreas HEM e IMU.
- Aprofundar a análise por tipo de exame.
- Investigar possíveis inconsistências e limitações na qualidade dos dados.
- Consolidar a documentação das medidas e regras de negócio.
- Aprimorar as análises e o storytelling dos resultados.

---

## Considerações sobre os dados

Por envolver informações de uma operação laboratorial, a base original não é disponibilizada neste repositório.

O projeto tem finalidade educacional e de demonstração de competências em análise de dados e Business Intelligence. Nenhuma informação confidencial ou identificável de pacientes deve ser publicada.

