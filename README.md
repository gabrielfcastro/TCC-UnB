# Otimização e Combinação de Modelos EFC para Detecção de Intrusão em IoT

Este repositório contém o código-fonte, os dados e os artefatos de pesquisa do meu
Trabalho de Conclusão de Curso (Engenharia da Computação — UnB, 2026).

O trabalho investiga o desempenho do classificador **Energy-based Flow Classifier
(EFC)** em sistemas de detecção de intrusão para ambientes de Internet das Coisas
(IoT), avaliando o impacto de estratégias de **otimização de hiperparâmetros**
(TPE e NSGA-II) e de **arquiteturas de combinação de modelos** (Ensemble e Stacking)
em um cenário de classificação multiclasse. Como referência, o EFC e suas variantes
são comparados ao **Random Forest** e ao **LightGBM** sob um protocolo estatístico de
30 execuções independentes.

📄 Monografia completa: ⚠️ [link para o PDF, se for disponibilizar]

---

## 📊 Dataset

Os experimentos utilizam o **⚠️ [CIC17]**, cujos fluxos
foram agrupados em seis categorias: `Benign`, `DoS`, `DDoS`, `MQTT`, `Reconnaissance`
e `Spoofing`.

Devido ao severo desbalanceamento do conjunto original (~7 milhões de amostras),
aplicou-se **subamostragem aleatória** limitada a 8.000 amostras por classe
(48.000 no total). Os detalhes estão em `1_preprocessamento.ipynb`.

## 📂 Estrutura do Repositório

- **`data/`** — dados brutos e/ou já processados usados nos experimentos.
- **`notebooks/`** — notebooks Jupyter na ordem de execução (ver abaixo).
- **`tests/`** — bases geradas para validação (partições balanceadas e desbalanceadas).
- **`docs/`** — diagramas (`.drawio`), esboços e slides da defesa.

---

## 📓 Fluxo de Execução

Para reproduzir os resultados, execute os notebooks nesta ordem:

**1. Pré-processamento** — ingestão dos dados, tratamento de valores inválidos,
subamostragem, particionamento estratificado (80/20) e codificação dos rótulos.

**2. Otimização de Hiperparâmetros** — busca das configurações ótimas do EFC via
**TPE** e **NSGA-II**, usando o framework Optuna.

**3. Random Forest vs Floresta de EFCs** — implementação da arquitetura de comitê
(*Ensemble*), confrontando o Random Forest tradicional com a **Floresta de EFCs
(Ensemble EFC)** proposta neste trabalho.

**4. K-Fold e Stacking** — validação cruzada e a arquitetura de **Stacking**
(EFC + LightGBM com metaclassificador de Regressão Logística).

**5. Comparação Global** — análise comparativa de todos os modelos ao longo de
**30 execuções independentes** com sementes aleatórias distintas, reportando a
distribuição do **Macro F1-Score**.

---

## 🚀 Requisitos e Execução

**Recomendação principal:** Para maior praticidade e para evitar problemas de configuração de ambiente ou limitações de hardware, recomenda-se fortemente a execução dos *notebooks* diretamente no **Google Colab**. Basta fazer o upload dos arquivos `.ipynb` e da pasta de datasets para o seu Google Drive e abri-los na plataforma.

---

## �「」Citação

Se este trabalho for útil, cite:

> CASTRO, Gabriel Francisco de Oliveira. *EFC para detecção multiclasse de ataques
> em IoT: otimização, novas arquiteturas e análise comparativa.* Monografia
> (Engenharia da Computação) — Universidade de Brasília, Brasília, 2026.
