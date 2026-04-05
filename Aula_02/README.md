# Aula 02 — Titanic Pipeline

## 5 pontos obrigatórios

1. **Baseline escolhido:** Logistic Regression, por ser um modelo
   linear simples, interpretável e um bom ponto de partida para
   classificação binária.

2. **Tratamento de missing values:**
   - Numéricas: preenchidas com a **mediana** via SimpleImputer
   - Categóricas: preenchidas com a **moda** (most_frequent)
     via SimpleImputer, seguido de OneHotEncoder

3. **Melhoria aplicada:** Troca do classificador para
   **RandomForestClassifier**, que captura relações não-lineares
   e interações entre variáveis sem precisar de ajuste de
   `class_weight`.

4. **Comparação FP e FN:**
   - O Random Forest **reduziu o FP** (menos falsos positivos)
     em relação ao baseline
   - Porém **aumentou o FN** (mais sobreviventes perdidos)
   - Esse é o trade-off esperado entre precisão e recall

5. **Limitação do dataset:** A coluna `deck` tem ~77% de valores
   ausentes, tornando-a pouco confiável. Além disso, o viés
   histórico de gênero ("mulheres e crianças primeiro") domina
   as previsões, o que não necessariamente reflete outros
   contextos reais de emergência.
