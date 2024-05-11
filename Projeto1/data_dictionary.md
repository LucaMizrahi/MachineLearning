# Data dictionary

| column name | description |
|-------------|-------------|
| school      | student's school (binary: "GP" - Gabriel Pereira or "MS" - Mousinho da Silveira) |
| sex         | student's sex (binary: "F" - female or "M" - male) |
| age         | student's age (numeric: from 15 to 22) |
| address     | student's home address type (binary: "U" - urban or "R" - rural) |
| famsize     | family size (binary: "LE3" - less or equal to 3 or "GT3" - greater than 3) |
| Pstatus     | parent's cohabitation status (binary: "T" - living together or "A" - apart) |
| Medu        | mother's education (numeric: 0 - none,  1 - primary education (4th grade), 2 – 5th to 9th grade, 3 – secondary education or 4 – higher education) |
| Fedu        | father's education (numeric: 0 - none,  1 - primary education (4th grade), 2 – 5th to 9th grade, 3 – secondary education or 4 – higher education) |
| Mjob        | mother's job (nominal: "teacher", "health" care related, civil "services" (e.g. administrative or police), "at_home" or "other") |
| Fjob        | father's job (nominal: "teacher", "health" care related, civil "services" (e.g. administrative or police), "at_home" or "other") |
| reason      | reason to choose this school (nominal: close to "home", school "reputation", "course" preference or "other") |
| guardian    | student's guardian (nominal: "mother", "father" or "other") |
| traveltime  | home to school travel time (numeric: 1 - <15 min., 2 - 15 to 30 min., 3 - 30 min. to 1 hour, or 4 - >1 hour) |
| studytime   | weekly study time (numeric: 1 - <2 hours, 2 - 2 to 5 hours, 3 - 5 to 10 hours, or 4 - >10 hours) |
| failures    | number of past class failures (numeric: n if 1<=n<3, else 4) |
| schoolsup   | extra educational support (binary: yes or no) |
| famsup      | family educational support (binary: yes or no) |
| paid        | extra paid classes within the course subject (Math or Portuguese) (binary: yes or no) |
| activities  | extra-curricular activities (binary: yes or no) |
| nursery     | attended nursery school (binary: yes or no) |
| higher      | wants to take higher education (binary: yes or no) |
| internet    | Internet access at home (binary: yes or no) |
| romantic    | with a romantic relationship (binary: yes or no) |
| famrel      | quality of family relationships (numeric: from 1 - very bad to 5 - excellent) |
| freetime    | free time after school (numeric: from 1 - very low to 5 - very high) |
| goout       | going out with friends (numeric: from 1 - very low to 5 - very high) |
| Dalc        | workday alcohol consumption (numeric: from 1 - very low to 5 - very high) |
| Walc        | weekend alcohol consumption (numeric: from 1 - very low to 5 - very high) |
| health      | current health status (numeric: from 1 - very bad to 5 - very good) |
| absences    | number of school absences (numeric: from 0 to 93) |
| grade       | final grade on Mathematics (numeric: from 0 to 20, output target) |


## Descrição do projeto

O projeto tem duas partes: modelagem inicial, e modelo com filtragem dos dados.

### Fase 1 

Na parte inicial, você deverá:

- Realizar *feature engineering* conforme necessário
    - Por exemplo: codificar as variáveis categóricas com `OneHotEncoding`
    - Não remova *outliers* aqui: faremos isso na seção seguinte
- Construir três modelos de regressão:
    - Um modelo usando o regressor `DummyRegressor` do scikit-learn (https://scikit-learn.org/stable/modules/generated/sklearn.dummy.DummyRegressor.html) que vai servir de "regressor trivial" para nós.
    - Um modelo `Ridge`.
    - Um outro modelo qualquer à sua escolha.
    Como o professor é santo, os dois primeiros já estão implementados para você! Então só falta escolher o terceiro.
- Fazer o ajuste de hiperparâmetros dos modelos. O código de exemplo já mostra como fazer o ajuste dos modelos iniciais, você especifica o grid de parâmetros de teste para o seu terceiro modelo.
- Comparar os desempenhos de modelos de modo adequado. Estude o material em https://scikit-learn.org/stable/auto_examples/model_selection/plot_grid_search_stats.html para saber como fazer o teste t com compensação de correlação dos desempenhos dos modelos em um cenário de validação cruzada.
- Escolhido o melhor modelo, treiná-lo no conjunto de treinamento e medir o desempenho no
conjunto de teste, para estimar o desempenho de generalização do modelo.
- Escrever suas conclusões à respeito do que foi aprendido acerta do modelo, por exemplo:
    - Quais as consequências do desempenho do modelo final para a estimação das notas finais?
    - Quais features são mais importantes na determinação da estimativa da nota final? Note que essa pergunta pode ou não ter resposta, dependendo das capacidades dos modelos de regressão que você escolher.

### Fase 2

Agora execute uma filtragem dos dados de treinamento para remover valores anormais. Por exemplo:

- Remova os alunos que tiveram nota final zero
- Remova os alunos que faltaram muito - defina você mesmo o que é "faltar muito"

Refaça o processo da fase 1 para esses dados filtrados.

### Rubrica

Os itens a serem avaliados no projeto são:

FEAT – Fazer feature engineering adequadamente

HYPER – Para cada modelo, fez ajuste de hiperparâmetros adequadamente

MODEL – Treinou e comparou adequadamente os modelos para selecionar o melhor modelo

PERF – Análise de desempenho do modelo. NÃO SERÁ EXIGIDA NENHUMA PERFORMANCE ESPECÍFICA, ISTO NÃO É UMA COMPETIÇÃO DE DESEMPENHO.

FILT - Executar a fase 2: filtragem de dados adequada e repetição do experimento.

- I – Insuficiente

    - Não entregou, ou entregou abobrinha

- D – Em desenvolvimento

    - Faltou um de FEAT, MODEL, PERF

- C – Minimo aceitável

    - Fez FEAT, MODEL, PERF

- B – Esperado

    - Fez FEAT, HYPER, MODEL, PERF

- A – Excepcional

    - Fez FEAT, HYPER, MODEL, PERF, FILT