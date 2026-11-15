# Modelagem de Dados

## Contexto
Após a exploração inicial da base, foi necessário organizar os dados para facilitar a construção dos indicadores e permitir análises por diferentes perspectivas.
Para isso, foi utilizada uma abordagem de **modelagem dimensional**, seguindo o conceito de **modelo estrela (Star Schema)**.
Nesse modelo, os registros dos exames ficam concentrados em uma tabela fato, enquanto as informações utilizadas para segmentar as análises são organizadas em tabelas dimensão.

## Preparação dos dados
A preparação dos dados foi realizada no **Power Query**, antes da construção dos relacionamentos e das medidas DAX.
Entre as principais etapas desenvolvidas estão:
- Análise inicial da estrutura da base e dos tipos de dados.
- Identificação de valores nulos e informações temporais ausentes.
- Conversão das colunas de data e hora para os tipos adequados.
- Organização das informações utilizadas nos cálculos de TAT e SLA.
- Criação de consultas auxiliares para investigação dos registros.
- Separação das informações necessárias para compor as tabelas fato e dimensão.

Durante essa etapa, também foram identificados registros sem informações suficientes para calcular o TAT operacional. Esses registros foram tratados separadamente, conforme os critérios definidos nas [Regras de Negócio](02_regras_de_negocio.md).

## Estrutura do modelo
O modelo foi organizado em **uma tabela fato e cinco tabelas dimensão**, permitindo analisar os registros por data, área técnica, exame, origem e ocorrência.

| Tabela | Tipo | Finalidade |
|---|---|---|
| `fato_exames` | Fato | Armazenar os registros dos exames e as informações utilizadas nos indicadores. |
| `dim_calendario` | Dimensão | Permitir análises por data e período. |
| `dim_setor` | Dimensão | Organizar os exames por área técnica. |
| `dim_exame` | Dimensão | Identificar e classificar os exames laboratoriais. |
| `dim_origem` | Dimensão | Permitir análises por origem da solicitação. |
| `dim_ocorrencia` | Dimensão | Organizar informações relacionadas às ocorrências laboratoriais. |

## Tabela fato
A tabela `fato_exames` representa a estrutura central do modelo analítico.
Ela reúne os registros utilizados para calcular os indicadores de desempenho, incluindo informações relacionadas à identificação dos exames, origem, área técnica e etapas do processamento.
Entre os principais campos utilizados estão:
- `Amostra`: identificação da amostra.
- `Area`: área técnica relacionada ao exame.
- `CodigoExame`: código de identificação do exame.
- `CodigoMPP`: código relacionado às ocorrências laboratoriais.
- Campos de data e hora relacionados às etapas do processo.
- Informações utilizadas no cálculo do TAT e na classificação do SLA.

A partir dessas informações, foram desenvolvidas medidas DAX para calcular os indicadores de desempenho operacional.

## Tabelas dimensão

### dim_calendario
A dimensão calendário foi criada para organizar as análises temporais.
Contém informações como data, dia, mês, dia da semana e semana do mês, permitindo acompanhar a evolução dos indicadores durante o período analisado.

### dim_setor
Organiza as informações relacionadas às áreas técnicas do laboratório.
Seus principais campos são `Area` e `NomeArea`, permitindo segmentar os indicadores por setor técnico.

### dim_exame
Organiza as informações relacionadas aos exames laboratoriais.
Contém os campos `CodigoExame`, `NomeExame`, `Material` e `Volume`, permitindo identificar os exames e aprofundar as análises por tipo de procedimento.

### dim_origem
Organiza as informações relacionadas às origens das solicitações.
Contém os campos `NomeOrigem` e `Origem`, permitindo analisar a distribuição dos exames e comparar o desempenho entre diferentes setores hospitalares.

### dim_ocorrencia
Organiza as informações relacionadas às ocorrências registradas no sistema laboratorial.
Contém os campos `CodigoMPP`, `DescricaoMPP` e `CategoriaOcorrencia`.
Essa dimensão foi utilizada para apoiar a investigação de registros com informações temporais ausentes e compreender possíveis relações com ocorrências operacionais.
A presença de uma ocorrência não significa, necessariamente, que ela seja a causa da ausência do TAT.

## Relacionamentos
As tabelas dimensão estão relacionadas à tabela `fato_exames`, seguindo a estrutura de um modelo estrela.
Na imagem do modelo, os relacionamentos apresentam cardinalidade **um para muitos (1:*)**, com as dimensões no lado 1 e a tabela fato no lado muitos.
A direção de filtragem apresentada é das dimensões para a tabela fato, permitindo que os filtros aplicados nas dimensões sejam utilizados nos cálculos e nas visualizações.
Essa organização facilita a construção de medidas DAX e permite analisar os mesmos indicadores por diferentes perspectivas.

## Medidas e indicadores
Com os dados organizados, foram desenvolvidas medidas DAX para calcular os indicadores utilizados nas análises.
Entre os principais indicadores estão:
- Quantidade total de exames.
- Quantidade de exames elegíveis para SLA.
- Quantidade de exames dentro do SLA.
- Quantidade de exames fora do SLA.
- Percentual de cumprimento do SLA.
- Percentual de não cumprimento do SLA.

As medidas respondem aos filtros aplicados no relatório, permitindo analisar os resultados por origem, área técnica e período.
A documentação dos cálculos está disponível em [Indicadores e Medidas](04_indicadores_e_medidas.md).

## Considerações
A modelagem dimensional foi utilizada para organizar os dados e facilitar a construção das análises no Power BI.
A separação entre a tabela fato e as dimensões contribui para manter o modelo mais compreensível, facilitar a manutenção das medidas e permitir novas análises conforme o projeto evolui.
