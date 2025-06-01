
# 📊 Classificador de Sentimento de Reviews da Microsoft

Este projeto tem como objetivo construir um modelo de machine learning capaz de classificar automaticamente **avaliações da Microsoft** como **positivas ou negativas** com base no **texto escrito pelos colaboradores**.

## 🧠 Objetivo

Classificar reviews da Microsoft (ex: opiniões de funcionários) em:

- **Positivas**: avaliações com nota ≥ 4
- **Negativas**: avaliações com nota ≤ 2

A classificação é feita com base no conteúdo textual (pros, cons, etc), utilizando técnicas de **NLP (Processamento de Linguagem Natural)** e **modelos supervisionados**.

---

## 🛠️ Tecnologias Utilizadas

- Python
- Jupyter Notebook
- `scikit-learn`
- `pandas`, `numpy`
- `nltk` (para pré-processamento de texto)
- `imbalanced-learn` (para balancear as classes)
- `TfidfVectorizer` (vetorização de texto)
- Modelos testados:
  - `RandomForestClassifier`
  - ✅ `LogisticRegression` (modelo final escolhido)

---

## ⚙️ Como funciona

1. **Pré-processamento de Texto**
   - Conversão para minúsculas
   - Remoção de pontuação
   - Stopwords removidas (em inglês)
   - Vetorização com TF-IDF

2. **Criação dos Rótulos**
   - Reviews com nota 4 ou 5 → `1` (positivo)
   - Reviews com nota 1 ou 2 → `0` (negativo)

3. **Balanceamento das classes**
   - Uso de `RandomOverSampler` para lidar com o desbalanceamento dos dados (muito mais avaliações positivas que negativas)

4. **Treinamento**
   - O modelo final é um `LogisticRegression` com `class_weight='balanced'` e threshold ajustado com `predict_proba`

5. **Predição**
   - O modelo recebe um novo texto e retorna se a review é **positiva ou negativa**

---

## 📈 Resultados

Com o modelo balanceado, obtivemos os seguintes resultados (exemplo):

| Classe       | Precision | Recall | F1-Score |
|--------------|-----------|--------|----------|
| Negativa (0) | 0.72      | 0.78   | 0.75     |
| Positiva (1) | 0.91      | 0.87   | 0.89     |

> Accuracy final: **0.86**

---

## 🧪 Exemplo de uso

```python
predict_review("The team is very collaborative and the benefits are great.")
# Saída: "Positivo"

predict_review("Management is poor and there's no growth opportunity.")
# Saída: "Negativo"
```

---

## 📄 DataSet:

[Employee Reviews](https://www.kaggle.com/datasets/kunalpatil2181/employee-reviews)




