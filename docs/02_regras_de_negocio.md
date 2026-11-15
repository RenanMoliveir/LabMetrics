# Regras de Negócio
![Regras de Negócio](https://img.shields.io/badge/Documentação-Regras_de_Negócio-00897B?style=for-the-badge)

## Definição do TAT

O **Turnaround Time (TAT)** representa o tempo decorrido entre duas etapas do processo laboratorial.<br>
No LabMetrics, foi considerado o **TAT operacional**, definido como o intervalo entre a triagem da amostra no laboratório e a liberação do resultado do exame.

**TAT (minutos) = Data/Hora da Liberação − Data/Hora da Triagem**

**Esse intervalo é utilizado para avaliar o tempo de processamento dos exames e verificar o cumprimento dos prazos estabelecidos.**

## Definição do SLA

O **Service Level Agreement (SLA)** representa o prazo estabelecido para a liberação dos exames.
No projeto, as metas de SLA foram definidas considerando a origem da solicitação e as particularidades de determinados exames.
O cumprimento do SLA é determinado pela comparação entre o TAT operacional e a meta estabelecida.

| Condição | Classificação |
|---|---|
| TAT ≤ Meta SLA | Dentro do SLA |
| TAT > Meta SLA | Fora do SLA |
| Sem condições válidas para avaliação | Não avaliado |

## Metas de SLA

As metas utilizadas nesta análise seguem as regras de negócio definidas para o projeto.

| Origem | Meta SLA |
|---|---:|
| Pronto Atendimento (PA) | 90 minutos |
| Demais origens hospitalares | 180 minutos |
| LabApoio | Não aplicável |

Alguns exames possuem prazos específicos, independentemente da origem da solicitação.

| Exame | Meta SLA |
|---|---:|
| Gasometria | 30 minutos |
| Hemoglobina/Hematócrito (HB/HT) | 30 minutos |
| Troponina | 30 minutos |
| Lactato arterial | 30 minutos |

**As metas específicas dos exames prevalecem sobre as regras gerais definidas pela origem.**

Por exemplo, uma gasometria solicitada pelo Pronto Atendimento possui meta de 30 minutos, e não de 90 minutos.

## Critérios de elegibilidade

Nem todos os registros disponíveis na base possuem condições de serem avaliados pelos critérios de SLA estabelecidos.
Para que um exame seja considerado elegível, é necessário:

- Possuir informações temporais válidas para o cálculo do TAT.
- Pertencer a uma origem contemplada pelas regras de SLA hospitalar.
- Possuir uma meta de SLA aplicável.
- Permitir a comparação entre o TAT calculado e o prazo estabelecido.

Os registros que não atendem a esses critérios são tratados separadamente, evitando interferências nos indicadores de desempenho.

## Classificação dos registros

A base utilizada contém **22.805 registros de exames**, referentes a janeiro de 2025.
Após a aplicação das regras de negócio, os registros foram classificados da seguinte forma:

| Classificação | Registros | Percentual |
|---|---:|---:|
| Exames elegíveis para SLA | 19.781 | 86,74% |
| LabApoio — SLA não aplicável | 1.499 | 6,57% |
| Registros sem TAT válido | 1.525 | 6,69% |
| **Total** | **22.805** | **100%** |

Os exames elegíveis representam o conjunto utilizado no cálculo dos indicadores de cumprimento do SLA.
Os registros da unidade LabApoio foram separados por não estarem contemplados nas metas hospitalares utilizadas nesta análise.
Já os registros sem TAT válido não apresentam informações temporais suficientes para avaliação.
**Essa separação permite que os indicadores considerem exclusivamente os exames sujeitos às regras de SLA estabelecidas.**

## Indicadores de SLA

Os indicadores foram calculados considerando exclusivamente os **19.781 exames elegíveis**.

| Indicador | Resultado |
|---|---:|
| 🟢 Exames dentro do SLA | **18.193** |
| 🔴 Exames fora do SLA | **1.588** |
| 🟢 Cumprimento do SLA | **92,0%** |
| 🔴 Não cumprimento do SLA | **8,0%** |

O percentual de cumprimento é calculado pela relação entre os exames liberados dentro do prazo e o total de exames elegíveis.

**Cumprimento do SLA (%) = (Exames dentro do SLA / Exames elegíveis) × 100**
Da mesma forma, o percentual de não cumprimento considera os exames que ultrapassaram o prazo estabelecido.
**Fora do SLA (%) = (Exames fora do SLA / Exames elegíveis) × 100**

## Tratamento de registros sem TAT válido

Durante a preparação dos dados, foram identificados registros com informações temporais ausentes ou insuficientes para o cálculo do TAT.
Esses registros não foram classificados automaticamente como exames atrasados.
A ausência de informações temporais pode estar relacionada a diferentes situações operacionais, como ocorrências durante o processamento das amostras, ou a limitações na extração dos dados.
Entretanto, essas possibilidades não foram consideradas causas confirmadas.
Por esse motivo, os registros sem TAT válido foram mantidos em uma classificação separada, permitindo investigações posteriores sem comprometer os indicadores de SLA.

## Limitações

O TAT operacional utilizado no projeto considera apenas o intervalo entre a triagem da amostra e a liberação do resultado.
Dessa forma, não representa necessariamente todo o tempo decorrido desde a solicitação médica até a disponibilização do exame.
Além disso, o descumprimento de uma meta de SLA não permite identificar automaticamente a causa do atraso.
Os indicadores permitem localizar situações que merecem investigação, mas sua interpretação deve considerar as características dos exames, as etapas do processo e as limitações dos dados disponíveis.
