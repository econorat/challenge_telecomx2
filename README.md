Análise Preditiva de Churn de Clientes Telecom


🚀 Resumo do Projeto

Este projeto tem como objetivo principal desenvolver modelos de machine learning capazes de prever a evasão de clientes (Churn) em uma empresa de telecomunicações. Utilizando um conjunto de dados abrangente, a análise foca na identificação dos principais fatores que levam um cliente a cancelar seu serviço e na construção de um modelo preditivo robusto que possa auxiliar na tomada de decisões estratégicas para a retenção de clientes.

⚙️ Metodologia

O fluxo de trabalho deste projeto seguiu as seguintes etapas: 

1. Extração e Pré-processamento dos Dados: Os dados foram carregados a partir de um arquivo CSV, e foi realizada uma limpeza inicial, removendo colunas irrelevantes como customerID e DailyCharges. A proporção de evasão foi analisada, mostrando um desequilíbrio de classes (aproximadamente 26% de clientes que evadiram e 74% que permaneceram).

2. Análise e Seleção de Variáveis: Variáveis categóricas foram convertidas para um formato numérico através da técnica de One-Hot Encoding. Para lidar com a discrepância de escala entre as variáveis numéricas, a padronização (StandardScaler) foi aplicada para o modelo de Regressão Logística, uma vez que ele é sensível a essa característica dos dados.

3. Balanceamento dos Dados: Para mitigar o problema do desequilíbrio de classes, a técnica de superamostragem, SMOTE (Synthetic Minority Over-sampling Technique), foi utilizada para criar novas amostras da classe minoritária (evasão) no conjunto de treino.

4. Modelagem Preditiva: Foram desenvolvidos e comparados dois modelos de classificação:
* Regressão Logística: Um modelo linear que exige a padronização dos dados para um melhor desempenho.
* Random Forest: Um modelo baseado em árvores que não é sensível à escala dos dados, portanto, não necessita de padronização.

5. Avaliação e Comparação: O desempenho de ambos os modelos foi avaliado usando métricas como Acurácia, Precisão, Recall e F1-score, além da análise da matriz de confusão para entender o tipo de erro cometido por cada modelo. A validação foi feita em um conjunto de teste separado (20% dos dados).

📊 Principais Fatores de Evasão

A análise de correlação e a visualização dos dados revelaram que o tempo de contrato e o tipo de serviço são os fatores mais importantes na previsão de evasão. Os principais insights são:
* Tempo de Contrato (Tenure): Esta é a variável com a maior correlação negativa com a evasão. Clientes que estão na empresa há menos tempo têm uma probabilidade significativamente maior de evadir.
* Tipo de Contrato (Contract): Clientes com contratos "Month-to-month" (mês a mês) têm uma probabilidade muito maior de evasão do que aqueles com contratos de dois anos.
* Serviço de Internet (InternetService_Fiber optic): Clientes que utilizam o serviço de fibra óptica apresentaram uma correlação positiva com a evasão, o que sugere que problemas de qualidade ou custo associados a este serviço podem ser um fator de risco.
* Serviços Adicionais: A ausência de serviços de segurança (OnlineSecurity) e suporte técnico (TechSupport) também são indicadores importantes de maior propensão à evasão.

📈 Desempenho dos Modelos
A tabela abaixo resume o desempenho dos modelos no conjunto de teste.

| Métrica            |	Regressão Logística |	Random Forest |
|--------------------|----------------------|---------------|
| Acurácia           | 0.8115               |	0.8253        |
| Precisão (Churn=1) | 0.68	                | 0.60          |
| Recall (Churn=1)   | 0.54	                | 0.67          |
| F1-Score (Churn=1) | 0.60	                | 0.63          |


* Análise: O modelo Random Forest foi o que apresentou o melhor desempenho geral, com uma acurácia ligeiramente superior e um recall significativamente maior para a classe de evasão (1). Um recall de 67% significa que o modelo é capaz de identificar corretamente 67% dos clientes que realmente evadirão. Isso é fundamental para a estratégia de retenção.

* Observação de Overfitting: O Random Forest demonstrou uma acurácia quase perfeita no conjunto de treino (~1.0), em contraste com a acurácia de teste de 0.8253. Isso sugere um certo grau de overfitting, mas o desempenho no conjunto de teste ainda é superior ao da Regressão Logística, indicando que a capacidade de generalização do modelo é satisfatória.

🎯 Estratégias de Retenção Sugeridas

Com base nos resultados, as seguintes estratégias de retenção de clientes são propostas:

1. Focar em Clientes Recém-Chegados: Priorizar a comunicação e o suporte para clientes nos primeiros meses de contrato, pois eles representam o maior risco de evasão.

2. Oferecer Benefícios para Contratos de Longo Prazo: Criar incentivos e promoções para que clientes com contratos "mês a mês" migrem para contratos de um ou dois anos, reduzindo a flexibilidade de cancelamento.

3. Investigar a Qualidade do Serviço de Fibra Óptica: Analisar as reclamações e o desempenho do serviço de internet de fibra óptica. Melhorar a qualidade pode impactar diretamente a taxa de evasão desse segmento.

4. Promover Serviços de Valor Adicionado: Incentivar a adesão a serviços de segurança e suporte técnico, destacando o valor e a tranquilidade que eles proporcionam, o que demonstrou ter uma correlação negativa com a evasão.
