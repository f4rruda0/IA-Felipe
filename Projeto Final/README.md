# Detecção de Ataques DDoS com Machine Learning

## Descrição

Este projeto aplica técnicas de Machine Learning para detectar ataques DDoS (Distributed Denial of Service) em tráfego de rede real. Utilizando o arquivo `DrDoS_NTP.csv` do CICDDoS2019 — o mais balanceado da coleção com ~25% de tráfego benigno — modelos de classificação são treinados para distinguir tráfego normal de ataques de amplificação via NTP — sem necessidade de inspecionar o conteúdo dos pacotes (abordagem baseada em metadados de fluxo). O pipeline cobre desde a análise exploratória até a serialização do modelo para uso em produção.

## Dataset

- **Fonte:** Canadian Institute for Cybersecurity — [CICDDoS2019](https://www.unb.ca/cic/datasets/ddos-2019.html)
- **Arquivo utilizado:** `DrDoS_NTP.csv` (630 MB) — arquivo mais balanceado do CICDDoS2019 (~25% BENIGN)
- **Amostras carregadas:** 100.000 linhas (de ~500.000 disponíveis)
- **Features:** 79 features numéricas de fluxo de rede (duração, bytes, pacotes, flags TCP, janelas, etc.)
- **Classes:** `BENIGN` (tráfego normal) e `DrDoS NTP` (ataque de amplificação via NTP)
- **Referência:** Sharafaldin et al. (2019) — *Developing Realistic DDoS Attack Dataset and Taxonomy*, IEEE Carnahan Conference on Security Technology

## Tipo de Problema

```
Tipo:             Classificação binária (BENIGN vs. ATAQUE)
Métrica principal: Recall (minimizar ataques não detectados)
Abordagem:         Supervisionada com Pipeline scikit-learn
```

## Tecnologias Utilizadas

```
Python 3.10+
Pandas 2.x
NumPy 1.x
Scikit-learn 1.3+
Imbalanced-learn 0.11+
Matplotlib 3.7+
Seaborn 0.12+
Joblib (serialização do modelo)
Google Colab (ambiente de execução)
```

## Instalação

1. Clone o repositório:
```bash
git clone https://github.com/seu-usuario/projeto-final-ia-felipe.git
cd projeto-final-ia-felipe
```

2. Instale as dependências:
```bash
pip install -r requirements.txt
```

3. Faça o download do dataset:
   - Acesse: https://www.unb.ca/cic/datasets/ddos-2019.html
   - Baixe o arquivo `DrDoS_NTP.csv` da pasta `CSV-03-11`
   - Coloque o arquivo em `dados/DrDoS_NTP.csv`

4. Execute o notebook:
```bash
jupyter notebook Trabalho_Final_DDOS (1).ipynb
```

> **No Google Colab:** Faça upload do `DrDoS_NTP.csv` para o Google Drive e ajuste o caminho `CAMINHO_NTP` na Célula de carregamento.

## Resultados Principais

Melhor modelo: **Random Forest**

| Modelo | Acurácia | Recall | F1-Score |
|--------|----------|--------|----------|
| Regressão Logística | ~99% | variável | menor |
| Árvore de Decisão | ~99% | alto | bom |
| **Random Forest** | **~99%** | **alto** | **melhor** |
| KNN | ~99% | alto | bom |
| Gradient Boosting | ~99% | alto | bom |

> **Nota:** A acurácia de 99% deve ser interpretada com cautela — o dataset é extremamente desbalanceado (99,99% ataques). A métrica mais relevante é o **Recall**, que mede a capacidade de detectar ataques reais sem deixá-los passar.

## Estrutura do Repositório

```
IA-Felipe/Projeto Final
├── README.md
├── Trabalho_Final_DDOS.ipynb
├── dados/
│   └── DrDoS_NTP.csv         # baixar manualmente (630 MB)
```

## Referências

- Sharafaldin, I., Lashkari, A. H., Hakak, S., & Ghorbani, A. A. (2019). Developing Realistic Distributed Denial of Service (DDoS) Attack Dataset and Taxonomy. *IEEE 53rd International Carnahan Conference on Security Technology*.
- Canadian Institute for Cybersecurity: https://www.unb.ca/cic/
- Scikit-learn: https://scikit-learn.org/
- Imbalanced-learn: https://imbalanced-learn.org/
