# Projeto A3 - Comite de Classificadores

Universidade Sao Judas Tadeu  
Disciplina: Inteligencia Artificial

## Base de dados

Este projeto utiliza a base `synthetic_fraud_dataset.csv`, uma base sintetica de transacoes financeiras para deteccao de fraude.

A base possui 10.000 registros e 10 colunas. Cada linha representa uma transacao, com informacoes sobre valor, tipo da transacao, categoria do comerciante, pais, horario e escores de risco do dispositivo e do IP.

## Problema de classificacao

O objetivo e prever se uma transacao e fraudulenta.

- Target: `is_fraud`
- Classe 0: transacao nao fraudulenta
- Classe 1: transacao fraudulenta

A base e desbalanceada: aproximadamente 95% das transacoes sao legitimas e 5% sao fraudes. Por isso, alem da acuracia, tambem sao avaliadas metricas como precisao, recall e F1-score.

## Features utilizadas

As colunas `transaction_id` e `user_id` foram removidas por serem identificadores. As features utilizadas no modelo sao:

- `amount`
- `transaction_type`
- `merchant_category`
- `country`
- `hour`
- `device_risk_score`
- `ip_risk_score`

## Pre-processamento

O notebook realiza:

- verificacao de dimensoes, tipos de dados e valores ausentes;
- analise exploratoria inicial;
- separacao entre features e target;
- divisao estratificada em treino e teste;
- imputacao de valores ausentes, mesmo que a base atual nao tenha nulos;
- padronizacao das variaveis numericas;
- codificacao one-hot das variaveis categoricas;
- balanceamento do conjunto de treino por oversampling simples da classe minoritaria.

## Modelo de rede neural

A rede neural foi implementada com `MLPClassifier`, da biblioteca Scikit-learn.

Configuracao inicial:

- camadas ocultas: 64 e 32 neuronios;
- funcao de ativacao: ReLU;
- otimizador: Adam;
- parada antecipada: ativada;
- maximo de iteracoes: 300.

O modelo e avaliado com:

- acuracia;
- precisao;
- recall;
- F1-score;
- matriz de confusao;
- relatorio de classificacao.

## Proximas etapas

O notebook ja possui secoes `TODO` para completar o restante do trabalho:

- treinar pelo menos 3 classificadores individuais;
- construir o comite por votacao;
- comparar os resultados dos modelos;
- finalizar discussao e conclusao.

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
