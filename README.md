# Projeto A3 - Comitê de Classificadores

Universidade São Judas Tadeu  
Disciplina: Inteligência Artificial

## Base de dados

Este projeto utiliza a base `synthetic_fraud_dataset.csv`, uma base sintética de transações financeiras para detecção de fraude.

A base possui 10.000 registros e 10 colunas. Cada linha representa uma transação, com informações sobre valor, tipo da transação, categoria do comerciante, país, horário e escores de risco do dispositivo e do IP.

## Problema de classificação

O objetivo é prever se uma transação é fraudulenta.

- Target: `is_fraud`
- Classe 0: transação não fraudulenta
- Classe 1: transação fraudulenta

A base é desbalanceada: aproximadamente 95% das transações são legítimas e 5% são fraudes. Por isso, além da acurácia, também são avaliadas métricas como precisão, recall e F1-score.

## Features utilizadas

As colunas `transaction_id` e `user_id` foram removidas por serem identificadores. As features utilizadas no modelo são:

- `amount`
- `transaction_type`
- `merchant_category`
- `country`
- `hour`
- `device_risk_score`
- `ip_risk_score`

## Pré-processamento

O notebook realiza:

- verificação de dimensões, tipos de dados e valores ausentes;
- análise exploratória inicial;
- separação entre features e target;
- divisão estratificada em treino e teste, usando 80% para treino e 20% para teste;
- imputação de valores ausentes;
- padronização das variáveis numéricas;
- codificação one-hot das variáveis categóricas;
- balanceamento do conjunto de treino por oversampling simples da classe minoritária.

## Modelos individuais

Foram implementados e avaliados três classificadores:

- Rede Neural (`MLPClassifier`)
- Árvore de Decisão (`DecisionTreeClassifier`)
- Regressão Logística (`LogisticRegression`)

Cada modelo foi treinado individualmente e avaliado com acurácia, precisão, recall, F1-score, relatório de classificação e matriz de confusão.

## Comitê de classificadores

O comitê foi construído com `VotingClassifier` usando votação majoritária. A estratégia combina modelos com características diferentes para produzir uma decisão final mais robusta.

## Resultados

O notebook gera uma tabela comparativa entre os três modelos individuais e o comitê. Nesta base sintética, os modelos apresentaram desempenho perfeito nas métricas avaliadas, o que indica que as variáveis de risco separam muito bem as classes.

## Como executar

No PowerShell, dentro desta pasta:

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install -r requirements.txt
python -m notebook
```

Depois, abra:

```text
A3_classifier_committee.ipynb
```
