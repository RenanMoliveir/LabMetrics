# Contexto e Objetivos
![Contexto](https://img.shields.io/badge/Documentação-Contexto_e_Objetivos-607D8B?style=for-the-badge)

## Contexto
A rotina de um laboratório de análises clínicas envolve diferentes etapas, desde a solicitação e coleta das amostras até o processamento e a liberação dos resultados.
Durante esse processo, são gerados dados que permitem acompanhar não apenas os exames realizados, mas também o desempenho operacional do laboratório.
Entre os indicadores utilizados nesse acompanhamento está o **Turnaround Time (TAT)**, que representa o tempo decorrido entre duas etapas definidas do processo laboratorial.<br>
Neste projeto, o TAT operacional foi definido como o **intervalo entre a triagem da amostra no laboratório e a liberação do resultado**.
A partir desse indicador, é possível avaliar o cumprimento dos prazos estabelecidos para a liberação dos exames, considerando as regras de negócio aplicáveis a cada situação.

## Problema analisado

Na rotina laboratorial, atrasos na liberação dos exames podem ocorrer por diferentes motivos. Entretanto, observar apenas casos isolados não permite compreender o comportamento geral da operação.

Algumas questões motivaram o desenvolvimento desta análise:

- Qual é o percentual de exames liberados dentro do prazo estabelecido?
- Quais setores de origem concentram o maior número de atrasos?
- Quais áreas técnicas apresentam maiores percentuais de exames fora do prazo?
- Existem variações no desempenho ao longo dos dias?
- Quais exames merecem uma investigação mais detalhada?

**A proposta é utilizar os dados disponíveis para responder a essas perguntas e identificar pontos que possam orientar análises futuras.**

## Objetivo geral

Analisar o desempenho operacional de um laboratório clínico por meio dos dados de liberação de exames, utilizando indicadores de TAT e SLA para avaliar o cumprimento dos prazos e identificar possíveis pontos de atenção na operação.

## Objetivos específicos

- Preparar e organizar os dados para análise.
- Identificar registros com informações temporais ausentes ou inválidas.
- Definir critérios de elegibilidade para avaliação do SLA.
- Calcular o TAT operacional dos exames.
- Desenvolver indicadores de cumprimento e não cumprimento do SLA.
- Analisar o desempenho por origem e área técnica.
- Investigar a distribuição dos atrasos ao longo do período.
- Identificar exames e setores que merecem análises mais aprofundadas.

## Escopo da análise

A primeira etapa do projeto utiliza uma base referente a **janeiro de 2025**, contendo **22.805 registros de exames**.
A análise está concentrada no cumprimento dos prazos de liberação, considerando o TAT operacional e as metas de SLA definidas pelas regras de negócio.
Nem todos os registros da base possuem condições de serem avaliados por esses critérios.
Por esse motivo, foi necessário separar os exames elegíveis daqueles que não se enquadram nas regras de SLA hospitalar ou não apresentam informações temporais válidas.
A definição desses critérios e o tratamento dos registros são apresentados no documento [Regras de Negócio](02_regras_de_negocio.md).

## Limitações

Os resultados apresentados representam o comportamento dos registros analisados no período e não devem ser interpretados, isoladamente, como uma avaliação completa da eficiência do laboratório.
O cumprimento do SLA é apenas uma das dimensões do desempenho operacional.
Além disso, a identificação de atrasos não permite determinar automaticamente suas causas. Para isso, são necessárias investigações adicionais, considerando os processos envolvidos e as características dos exames.
O projeto busca identificar padrões e levantar hipóteses com base nos dados disponíveis, evitando conclusões que não possam ser sustentadas pelas análises.
