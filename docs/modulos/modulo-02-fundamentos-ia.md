# Módulo 2: Fundamentos de Inteligência Artificial

## Informações Gerais

| Item | Descrição |
|------|-----------|
| **Módulo** | 2 |
| **Trilha** | Fundamentos |
| **Disciplina** | Fundamentos de Inteligência Artificial |
| **Carga Horária** | 40 horas |
| **Teoria/Prática** | 16h teóricas (40%) / 24h práticas (60%) |
| **Número de Aulas** | 8 aulas de 5 horas |
| **Pré-requisitos** | Módulo 1 ou conhecimentos equivalentes |

## Ementa

Introdução à Inteligência Artificial: histórico, conceitos e aplicações. Machine Learning: aprendizado supervisionado, não supervisionado e por reforço. Redes neurais e Deep Learning. Processamento de Linguagem Natural (NLP). Large Language Models (LLMs): arquitetura, funcionamento e aplicações. Introdução ao Python para IA. Bibliotecas fundamentais: NumPy, Pandas, Scikit-learn. Frameworks de Deep Learning: TensorFlow, PyTorch. Ética e vieses em IA.

## Objetivos de Aprendizagem

Ao final deste módulo, o aluno será capaz de:

1. Compreender os fundamentos teóricos de IA e Machine Learning
2. Diferenciar tipos de aprendizado de máquina e suas aplicações
3. Implementar modelos básicos de ML em Python usando Scikit-learn
4. Entender a arquitetura e funcionamento de redes neurais e LLMs
5. Utilizar bibliotecas fundamentais de IA (NumPy, Pandas, TensorFlow)
6. Reconhecer questões éticas e vieses em sistemas de IA

## Competências Desenvolvidas

| Competência | Nível | Indicadores |
|-------------|-------|-------------|
| Programação Python | Intermediário | Desenvolve scripts de análise de dados |
| Machine Learning | Básico-Intermediário | Implementa modelos supervisionados |
| Deep Learning | Básico | Compreende arquiteturas de redes neurais |
| NLP/LLMs | Básico | Utiliza modelos de linguagem |
| Ética em IA | Básico | Identifica vieses e problemas éticos |

---

# PLANOS DE AULA DETALHADOS

---

## AULA 1: Introdução à IA - História, Conceitos e Aplicações

### Informações da Aula

| Item | Descrição |
|------|-----------|
| **Aula** | 1 de 8 |
| **Tema** | Introdução à Inteligência Artificial |
| **Carga Horária** | 5 horas |
| **Teoria/Prática** | 3h teoria / 2h prática |

### Objetivos da Aula

**Objetivo Geral:**
Compreender os fundamentos, evolução histórica e aplicações da Inteligência Artificial.

**Objetivos Específicos:**
1. Definir Inteligência Artificial e seus subcampos
2. Conhecer a evolução histórica da IA (invernos e primaveras)
3. Diferenciar IA estreita (ANI), IA geral (AGI) e superinteligência
4. Identificar aplicações de IA em cibersegurança
5. Configurar ambiente de desenvolvimento Python para IA

### Descrição da Aula

Esta aula inaugural apresenta o campo da Inteligência Artificial, desde suas origens na conferência de Dartmouth (1956) até os avanços recentes com LLMs. O aluno será introduzido aos conceitos fundamentais e configurará seu ambiente de desenvolvimento.

### Estrutura da Aula

| Tempo | Atividade | Tipo | Descrição |
|-------|-----------|------|-----------|
| 0:00-0:45 | O que é IA? | Expositiva-dialogada | Definições, tipos, subcampos |
| 0:45-1:30 | História da IA | Expositiva | De Turing aos LLMs |
| 1:30-2:15 | IA em Cibersegurança | Expositiva-dialogada | Aplicações e exemplos |
| 2:15-2:30 | **Intervalo** | - | - |
| 2:30-4:00 | **Lab 1.1** | Prática | Setup do ambiente Python |
| 4:00-4:45 | **Lab 1.2** | Prática | Primeiro contato com IA |
| 4:45-5:00 | Encerramento | Discussão | Síntese e próximos passos |

### Conteúdo Programático Detalhado

#### 1. O que é Inteligência Artificial? (45 min)

**Definições:**
- "Sistemas que pensam como humanos" (abordagem cognitiva)
- "Sistemas que agem como humanos" (Teste de Turing)
- "Sistemas que pensam racionalmente" (lógica)
- "Sistemas que agem racionalmente" (agentes racionais)

**Subcampos da IA:**
- Machine Learning
- Deep Learning
- Natural Language Processing
- Computer Vision
- Robotics
- Expert Systems

**Tipos de IA:**
- **ANI (Artificial Narrow Intelligence):** Especializada em uma tarefa
- **AGI (Artificial General Intelligence):** Inteligência humana
- **ASI (Artificial Super Intelligence):** Além da humana

#### 2. História da IA (45 min)

**Linha do tempo:**
- 1950: Teste de Turing
- 1956: Conferência de Dartmouth (nascimento oficial)
- 1960s: Primeiros sistemas especialistas
- 1970s: Primeiro inverno da IA
- 1980s: Expert systems boom
- 1987-1993: Segundo inverno da IA
- 1997: Deep Blue vence Kasparov
- 2012: AlexNet revoluciona visão computacional
- 2017: Arquitetura Transformer (Attention is All You Need)
- 2020+: Era dos LLMs (GPT-3, ChatGPT, GPT-4)

#### 3. IA em Cibersegurança (45 min)

**Aplicações Defensivas:**
- Detecção de malware
- Análise de tráfego anômalo
- UEBA (User Entity Behavior Analytics)
- Automação de SOC
- Threat Intelligence

**Aplicações Ofensivas (adversários):**
- Geração de phishing com LLMs
- Evasão de detecção
- Deepfakes
- Ataques automatizados

**O Futuro:**
- Machine vs Machine warfare
- Agentes autônomos de segurança
- AI-powered attacks

### Atividades Práticas

#### Laboratório 1.1: Setup do Ambiente (90 min)

**Objetivo:** Configurar ambiente de desenvolvimento Python para IA

**Tarefas:**
1. Instalar Python 3.10+
2. Configurar ambiente virtual (venv)
3. Instalar bibliotecas essenciais:
```bash
pip install numpy pandas matplotlib scikit-learn jupyter
pip install tensorflow torch
pip install openai anthropic  # APIs de LLMs
```
4. Testar instalação com Jupyter Notebook
5. Criar primeiro notebook de teste

**Entregável:** Screenshot do ambiente funcionando

#### Laboratório 1.2: Primeiro Contato com IA (45 min)

**Objetivo:** Experimentar diferentes tipos de IA

**Tarefas:**
1. Usar ChatGPT/Claude para tarefa de segurança
2. Testar classificador de spam simples (demo)
3. Explorar playground de ML (Teachable Machine)

**Entregável:** Relatório de experiências

### Materiais e Recursos

**Leitura Prévia:**
- RUSSELL, Stuart; NORVIG, Peter. Inteligência Artificial, Cap. 1

**Recursos:**
- Google Colab (alternativa ao ambiente local)
- Teachable Machine (https://teachablemachine.withgoogle.com/)

### Abordagem Metodológica

- **Expositiva dialogada:** Conceitos fundamentais
- **Storytelling:** História da IA
- **Hands-on:** Setup de ambiente
- **Exploratória:** Primeiro contato com ferramentas

### Avaliação da Aula

| Instrumento | Peso | Critérios |
|-------------|------|-----------|
| Lab 1.1 | 50% | Ambiente configurado corretamente |
| Lab 1.2 | 30% | Relatório de experiências |
| Participação | 20% | Discussão em aula |

### Referências

1. RUSSELL, Stuart; NORVIG, Peter. **Inteligência Artificial**. 4ª ed. GEN LTC, 2022. Cap. 1.
2. TURING, Alan. "Computing Machinery and Intelligence". Mind, 1950.
3. McCARTHY, John et al. "A Proposal for the Dartmouth Summer Research Project on Artificial Intelligence". 1955.

---

## AULA 2: Python para IA - NumPy, Pandas, Visualização

### Informações da Aula

| Item | Descrição |
|------|-----------|
| **Aula** | 2 de 8 |
| **Tema** | Python para IA: Bibliotecas Fundamentais |
| **Carga Horária** | 5 horas |
| **Teoria/Prática** | 1h teoria / 4h prática |

### Objetivos da Aula

**Objetivo Geral:**
Dominar as bibliotecas Python essenciais para trabalhar com IA e análise de dados.

**Objetivos Específicos:**
1. Manipular arrays multidimensionais com NumPy
2. Processar e analisar dados tabulares com Pandas
3. Criar visualizações com Matplotlib e Seaborn
4. Preparar dados para modelos de ML
5. Analisar datasets de segurança

### Descrição da Aula

Esta aula focada em prática capacita o aluno a trabalhar com as bibliotecas Python mais importantes para IA: NumPy para computação numérica, Pandas para manipulação de dados e Matplotlib/Seaborn para visualização.

### Estrutura da Aula

| Tempo | Atividade | Tipo | Descrição |
|-------|-----------|------|-----------|
| 0:00-0:30 | Revisão | Discussão | Python basics review |
| 0:30-1:00 | NumPy Overview | Expositiva | Arrays e operações |
| 1:00-1:30 | **Lab 2.1** | Prática | Exercícios NumPy |
| 1:30-2:00 | Pandas Overview | Expositiva | DataFrames e operações |
| 2:00-2:15 | **Intervalo** | - | - |
| 2:15-3:15 | **Lab 2.2** | Prática | Análise de dados com Pandas |
| 3:15-3:45 | Visualização | Expositiva | Matplotlib e Seaborn |
| 3:45-4:45 | **Lab 2.3** | Prática | Análise de dataset de segurança |
| 4:45-5:00 | Encerramento | Discussão | Dúvidas e próximos passos |

### Conteúdo Programático

#### 1. NumPy (30 min)

```python
import numpy as np

# Criação de arrays
arr = np.array([1, 2, 3, 4, 5])
matrix = np.array([[1, 2, 3], [4, 5, 6]])
zeros = np.zeros((3, 3))
ones = np.ones((2, 2))
random = np.random.rand(100)

# Operações vetorizadas
arr * 2
arr + arr
np.dot(matrix, matrix.T)

# Estatísticas
np.mean(arr), np.std(arr), np.max(arr)

# Indexação e slicing
arr[0:3]
matrix[:, 1]
```

#### 2. Pandas (30 min)

```python
import pandas as pd

# Criação de DataFrames
df = pd.read_csv('security_logs.csv')

# Exploração
df.head()
df.info()
df.describe()

# Seleção e filtragem
df['column_name']
df[df['severity'] == 'HIGH']
df.loc[0:10, ['source_ip', 'dest_ip']]

# Agregação
df.groupby('attack_type').count()
df.pivot_table(values='count', index='hour', columns='day')

# Limpeza
df.dropna()
df.fillna(0)
df.drop_duplicates()
```

#### 3. Visualização (30 min)

```python
import matplotlib.pyplot as plt
import seaborn as sns

# Matplotlib básico
plt.figure(figsize=(10, 6))
plt.plot(x, y)
plt.xlabel('Time')
plt.ylabel('Events')
plt.title('Security Events Over Time')
plt.show()

# Seaborn
sns.histplot(df['severity'])
sns.heatmap(correlation_matrix, annot=True)
sns.boxplot(x='attack_type', y='duration', data=df)
```

### Atividades Práticas

#### Laboratório 2.1: Exercícios NumPy (30 min)

1. Criar array com 1000 valores aleatórios
2. Calcular estatísticas (média, mediana, desvio padrão)
3. Normalizar dados (min-max scaling)
4. Encontrar outliers (> 2 desvios padrão)

#### Laboratório 2.2: Análise com Pandas (60 min)

**Dataset:** CICIDS2017 (sample)

**Tarefas:**
1. Carregar dataset
2. Explorar estrutura
3. Tratar valores faltantes
4. Filtrar ataques específicos
5. Agregar por tipo de ataque

#### Laboratório 2.3: Análise de Dataset de Segurança (60 min)

**Objetivo:** Análise exploratória completa de logs de segurança

**Tarefas:**
1. Carregar e limpar dados
2. Análise estatística descritiva
3. Visualizar distribuição de ataques
4. Criar heatmap temporal
5. Identificar padrões

**Entregável:** Jupyter Notebook com análise completa

### Avaliação da Aula

| Instrumento | Peso | Critérios |
|-------------|------|-----------|
| Lab 2.1 | 20% | Exercícios NumPy corretos |
| Lab 2.2 | 30% | Análise Pandas completa |
| Lab 2.3 | 50% | Notebook de análise de segurança |

### Referências

1. McKINNEY, Wes. **Python for Data Analysis**. 3rd ed. O'Reilly, 2022.
2. VANDERPLAS, Jake. **Python Data Science Handbook**. O'Reilly, 2016.

---

## AULA 3: Machine Learning Supervisionado

### Informações da Aula

| Item | Descrição |
|------|-----------|
| **Aula** | 3 de 8 |
| **Tema** | Machine Learning Supervisionado |
| **Carga Horária** | 5 horas |
| **Teoria/Prática** | 2h teoria / 3h prática |

### Objetivos da Aula

**Objetivo Geral:**
Compreender e implementar algoritmos de aprendizado supervisionado.

**Objetivos Específicos:**
1. Diferenciar classificação e regressão
2. Implementar algoritmos clássicos (KNN, Decision Tree, Random Forest, SVM)
3. Avaliar modelos com métricas apropriadas
4. Aplicar cross-validation
5. Tratar overfitting e underfitting

### Conteúdo Programático

#### 1. Fundamentos de ML Supervisionado (30 min)

**Conceitos:**
- Features (X) e Target (y)
- Training set vs Test set
- Classificação vs Regressão
- Overfitting vs Underfitting
- Bias-Variance tradeoff

**Pipeline de ML:**
1. Coleta de dados
2. Preparação (limpeza, feature engineering)
3. Divisão (train/test split)
4. Treinamento
5. Avaliação
6. Tuning
7. Deploy

#### 2. Algoritmos de Classificação (45 min)

**K-Nearest Neighbors (KNN):**
```python
from sklearn.neighbors import KNeighborsClassifier
knn = KNeighborsClassifier(n_neighbors=5)
knn.fit(X_train, y_train)
predictions = knn.predict(X_test)
```

**Decision Tree:**
```python
from sklearn.tree import DecisionTreeClassifier
tree = DecisionTreeClassifier(max_depth=5)
tree.fit(X_train, y_train)
```

**Random Forest:**
```python
from sklearn.ensemble import RandomForestClassifier
rf = RandomForestClassifier(n_estimators=100)
rf.fit(X_train, y_train)
```

**Support Vector Machine:**
```python
from sklearn.svm import SVC
svm = SVC(kernel='rbf')
svm.fit(X_train, y_train)
```

#### 3. Métricas de Avaliação (30 min)

**Para Classificação:**
- Accuracy: (TP + TN) / Total
- Precision: TP / (TP + FP)
- Recall: TP / (TP + FN)
- F1-Score: 2 * (Precision * Recall) / (Precision + Recall)
- Confusion Matrix
- ROC-AUC

```python
from sklearn.metrics import classification_report, confusion_matrix
print(classification_report(y_test, predictions))
```

### Atividades Práticas

#### Laboratório 3.1: Classificador de Malware (3h)

**Dataset:** Malware classification dataset (features extraídas)

**Tarefas:**
1. Carregar e explorar dataset
2. Preparar features (scaling, encoding)
3. Dividir dados (80% train, 20% test)
4. Implementar e comparar:
   - KNN
   - Decision Tree
   - Random Forest
   - SVM
5. Avaliar com métricas
6. Comparar resultados

**Entregável:** Notebook com comparativo de modelos

### Avaliação da Aula

| Instrumento | Peso | Critérios |
|-------------|------|-----------|
| Lab 3.1 | 80% | Implementação correta e análise |
| Quiz | 20% | Conceitos de ML supervisionado |

### Referências

1. GÉRON, Aurélien. **Mãos à Obra: Aprendizado de Máquina**. 3ª ed. Alta Books, 2023. Cap. 3-6.
2. Scikit-learn Documentation: https://scikit-learn.org/

---

## AULA 4: Machine Learning Não Supervisionado

### Informações da Aula

| Item | Descrição |
|------|-----------|
| **Aula** | 4 de 8 |
| **Tema** | Machine Learning Não Supervisionado |
| **Carga Horária** | 5 horas |
| **Teoria/Prática** | 2h teoria / 3h prática |

### Objetivos da Aula

**Objetivo Geral:**
Compreender e aplicar algoritmos de aprendizado não supervisionado para detecção de anomalias.

**Objetivos Específicos:**
1. Entender clustering e redução de dimensionalidade
2. Implementar K-Means e DBSCAN
3. Aplicar PCA para redução dimensional
4. Usar Isolation Forest para detecção de anomalias
5. Aplicar em cenários de segurança

### Conteúdo Programático

#### 1. Fundamentos (30 min)

**Diferença para Supervisionado:**
- Sem labels (y)
- Descoberta de padrões
- Aplicações: clustering, detecção de anomalias, redução dimensional

**Aplicações em Segurança:**
- Detecção de anomalias de rede
- Identificação de comportamento anômalo
- Agrupamento de malware
- Redução de features

#### 2. Algoritmos de Clustering (45 min)

**K-Means:**
```python
from sklearn.cluster import KMeans
kmeans = KMeans(n_clusters=3)
clusters = kmeans.fit_predict(X)
```

**DBSCAN:**
```python
from sklearn.cluster import DBSCAN
dbscan = DBSCAN(eps=0.5, min_samples=5)
clusters = dbscan.fit_predict(X)
# -1 indica anomalias
```

#### 3. Detecção de Anomalias (30 min)

**Isolation Forest:**
```python
from sklearn.ensemble import IsolationForest
iso = IsolationForest(contamination=0.1)
predictions = iso.fit_predict(X)
# -1 = anomalia, 1 = normal
```

**One-Class SVM:**
```python
from sklearn.svm import OneClassSVM
ocsvm = OneClassSVM(nu=0.1)
predictions = ocsvm.fit_predict(X)
```

#### 4. Redução de Dimensionalidade (15 min)

**PCA:**
```python
from sklearn.decomposition import PCA
pca = PCA(n_components=2)
X_reduced = pca.fit_transform(X)
```

### Atividades Práticas

#### Laboratório 4.1: Detecção de Anomalias em Tráfego de Rede (3h)

**Dataset:** Network traffic dataset com features numéricas

**Tarefas:**
1. Carregar e preparar dados
2. Aplicar PCA para visualização
3. Implementar K-Means para clustering
4. Implementar Isolation Forest para anomalias
5. Comparar resultados
6. Identificar possíveis ataques

**Entregável:** Notebook com análise de anomalias

### Avaliação da Aula

| Instrumento | Peso | Critérios |
|-------------|------|-----------|
| Lab 4.1 | 80% | Implementação e análise |
| Participação | 20% | Discussão de resultados |

### Referências

1. GÉRON, Aurélien. **Mãos à Obra: Aprendizado de Máquina**. Cap. 8-9.
2. STAMP, Mark. **Introduction to Machine Learning with Applications in Information Security**. Cap. 7.

---

## AULA 5: Redes Neurais e Deep Learning

### Informações da Aula

| Item | Descrição |
|------|-----------|
| **Aula** | 5 de 8 |
| **Tema** | Redes Neurais e Deep Learning |
| **Carga Horária** | 5 horas |
| **Teoria/Prática** | 2h teoria / 3h prática |

### Objetivos da Aula

**Objetivo Geral:**
Compreender os fundamentos de redes neurais e implementar modelos básicos de Deep Learning.

**Objetivos Específicos:**
1. Entender a arquitetura de redes neurais
2. Compreender o processo de treinamento (forward/backpropagation)
3. Implementar redes neurais com TensorFlow/Keras
4. Aplicar regularização e otimização
5. Treinar modelo para classificação de ameaças

### Conteúdo Programático

#### 1. Fundamentos de Redes Neurais (45 min)

**Perceptron:**
- Entradas (x), Pesos (w), Bias (b)
- Função de ativação
- output = activation(w·x + b)

**Multi-Layer Perceptron (MLP):**
- Input layer, Hidden layers, Output layer
- Forward propagation
- Backpropagation
- Gradient descent

**Funções de Ativação:**
- Sigmoid: σ(x) = 1/(1+e^-x)
- ReLU: max(0, x)
- Tanh: (e^x - e^-x)/(e^x + e^-x)
- Softmax (output para classificação)

#### 2. Treinamento (30 min)

**Loss Functions:**
- Binary Cross-Entropy (classificação binária)
- Categorical Cross-Entropy (multi-classe)
- MSE (regressão)

**Otimizadores:**
- SGD (Stochastic Gradient Descent)
- Adam (Adaptive Moment Estimation)
- RMSprop

**Regularização:**
- Dropout
- L1/L2 regularization
- Early stopping

#### 3. TensorFlow/Keras (30 min)

```python
import tensorflow as tf
from tensorflow import keras

# Modelo sequencial
model = keras.Sequential([
    keras.layers.Dense(128, activation='relu', input_shape=(n_features,)),
    keras.layers.Dropout(0.3),
    keras.layers.Dense(64, activation='relu'),
    keras.layers.Dropout(0.3),
    keras.layers.Dense(num_classes, activation='softmax')
])

# Compilação
model.compile(
    optimizer='adam',
    loss='categorical_crossentropy',
    metrics=['accuracy']
)

# Treinamento
history = model.fit(
    X_train, y_train,
    epochs=50,
    batch_size=32,
    validation_split=0.2,
    callbacks=[keras.callbacks.EarlyStopping(patience=5)]
)

# Avaliação
model.evaluate(X_test, y_test)
```

### Atividades Práticas

#### Laboratório 5.1: Classificador de Ataques com Deep Learning (3h)

**Dataset:** CICIDS2017 ou NSL-KDD

**Tarefas:**
1. Preparar dados (normalização, encoding)
2. Criar modelo MLP com Keras
3. Treinar com diferentes arquiteturas
4. Aplicar regularização
5. Avaliar no conjunto de teste
6. Comparar com modelos tradicionais (Random Forest)

**Entregável:** Notebook com modelo treinado e análise

### Avaliação da Aula

| Instrumento | Peso | Critérios |
|-------------|------|-----------|
| Lab 5.1 | 80% | Modelo funcional e análise |
| Quiz | 20% | Conceitos de Deep Learning |

### Referências

1. CHOLLET, François. **Deep Learning with Python**. 2nd ed. Manning, 2021.
2. GOODFELLOW, Ian et al. **Deep Learning**. MIT Press, 2016.

---

## AULA 6: Processamento de Linguagem Natural (NLP)

### Informações da Aula

| Item | Descrição |
|------|-----------|
| **Aula** | 6 de 8 |
| **Tema** | Processamento de Linguagem Natural |
| **Carga Horária** | 5 horas |
| **Teoria/Prática** | 2h teoria / 3h prática |

### Objetivos da Aula

**Objetivo Geral:**
Compreender técnicas de NLP e suas aplicações em segurança.

**Objetivos Específicos:**
1. Entender o pipeline de NLP
2. Aplicar pré-processamento de texto
3. Implementar representações de texto (BoW, TF-IDF, Word2Vec)
4. Criar classificador de phishing/spam
5. Entender embeddings e sua importância

### Conteúdo Programático

#### 1. Fundamentos de NLP (30 min)

**Pipeline:**
1. Tokenization
2. Lowercasing
3. Stop words removal
4. Stemming/Lemmatization
5. Representação vetorial

**Aplicações em Segurança:**
- Detecção de phishing
- Classificação de spam
- Análise de logs
- Threat intelligence (relatórios)
- Chatbots de segurança

#### 2. Representações de Texto (45 min)

**Bag of Words (BoW):**
```python
from sklearn.feature_extraction.text import CountVectorizer
vectorizer = CountVectorizer()
X = vectorizer.fit_transform(texts)
```

**TF-IDF:**
```python
from sklearn.feature_extraction.text import TfidfVectorizer
tfidf = TfidfVectorizer(max_features=5000)
X = tfidf.fit_transform(texts)
```

**Word Embeddings:**
- Word2Vec
- GloVe
- FastText

#### 3. Classificação de Texto (30 min)

```python
from sklearn.naive_bayes import MultinomialNB
from sklearn.pipeline import Pipeline

pipeline = Pipeline([
    ('tfidf', TfidfVectorizer(max_features=5000)),
    ('clf', MultinomialNB())
])

pipeline.fit(X_train, y_train)
predictions = pipeline.predict(X_test)
```

### Atividades Práticas

#### Laboratório 6.1: Detector de Phishing com NLP (3h)

**Dataset:** Phishing email dataset

**Tarefas:**
1. Carregar e explorar emails
2. Pré-processar texto
3. Criar features com TF-IDF
4. Treinar classificador (Naive Bayes, SVM)
5. Avaliar desempenho
6. Testar com novos emails

**Entregável:** Notebook com detector de phishing

### Avaliação da Aula

| Instrumento | Peso | Critérios |
|-------------|------|-----------|
| Lab 6.1 | 80% | Detector funcional |
| Quiz | 20% | Conceitos de NLP |

### Referências

1. JURAFSKY, Daniel; MARTIN, James H. **Speech and Language Processing**. 3rd ed. 2024.
2. BIRD, Steven et al. **Natural Language Processing with Python**. O'Reilly, 2009.

---

## AULA 7: Large Language Models (LLMs)

### Informações da Aula

| Item | Descrição |
|------|-----------|
| **Aula** | 7 de 8 |
| **Tema** | Large Language Models |
| **Carga Horária** | 5 horas |
| **Teoria/Prática** | 2h teoria / 3h prática |

### Objetivos da Aula

**Objetivo Geral:**
Compreender a arquitetura, funcionamento e aplicações de Large Language Models.

**Objetivos Específicos:**
1. Entender a arquitetura Transformer
2. Compreender como LLMs são treinados
3. Usar APIs de LLMs (OpenAI, Anthropic)
4. Aplicar prompting efetivo
5. Entender limitações e riscos de LLMs

### Conteúdo Programático

#### 1. Arquitetura Transformer (45 min)

**Self-Attention:**
- Query, Key, Value
- Attention weights
- Multi-head attention

**Componentes:**
- Encoder-Decoder (T5, BART)
- Decoder-only (GPT, Llama)
- Encoder-only (BERT)

**Treinamento:**
- Pre-training (self-supervised)
- Fine-tuning (supervised)
- RLHF (Reinforcement Learning from Human Feedback)

#### 2. Usando LLMs (45 min)

**APIs:**
```python
from openai import OpenAI
client = OpenAI()

response = client.chat.completions.create(
    model="gpt-4",
    messages=[
        {"role": "system", "content": "You are a cybersecurity expert."},
        {"role": "user", "content": "Analyze this log entry for threats..."}
    ]
)

print(response.choices[0].message.content)
```

**Prompting:**
- Zero-shot
- Few-shot
- Chain-of-thought
- System prompts

#### 3. LLMs em Segurança (30 min)

**Aplicações:**
- Análise de logs
- Geração de relatórios
- Assistente de SOC
- Code review
- Threat intelligence

**Riscos:**
- Prompt injection
- Data leakage
- Hallucinations
- Jailbreaking

### Atividades Práticas

#### Laboratório 7.1: Assistente de Segurança com LLM (3h)

**Objetivo:** Criar assistente para análise de logs

**Tarefas:**
1. Configurar acesso à API
2. Criar prompt system para analista de segurança
3. Implementar análise de logs com LLM
4. Testar com diferentes logs
5. Avaliar qualidade das respostas
6. Documentar limitações encontradas

**Entregável:** Notebook com assistente funcional

### Avaliação da Aula

| Instrumento | Peso | Critérios |
|-------------|------|-----------|
| Lab 7.1 | 80% | Assistente funcional |
| Participação | 20% | Discussão de aplicações |

### Referências

1. VASWANI, Ashish et al. "Attention is All You Need". NeurIPS, 2017.
2. OpenAI. **GPT-4 Technical Report**. 2023.
3. Anthropic. **Claude Documentation**. 2024.

---

## AULA 8: Ética em IA e CTF do Módulo

### Informações da Aula

| Item | Descrição |
|------|-----------|
| **Aula** | 8 de 8 |
| **Tema** | Ética em IA e CTF Avaliativo |
| **Carga Horária** | 5 horas |
| **Teoria/Prática** | 1.5h teoria / 3.5h prática |

### Objetivos da Aula

**Objetivo Geral:**
Discutir aspectos éticos de IA e consolidar conhecimentos através de CTF.

**Objetivos Específicos:**
1. Identificar vieses em sistemas de IA
2. Compreender questões de fairness e accountability
3. Conhecer regulamentações de IA
4. Resolver desafios práticos de CTF

### Conteúdo Programático

#### 1. Ética em IA (45 min)

**Vieses em IA:**
- Viés de dados (historical bias)
- Viés de seleção
- Viés de confirmação
- Exemplos: COMPAS, Amazon hiring

**Fairness:**
- Group fairness
- Individual fairness
- Métricas de fairness

**Accountability:**
- Explicabilidade
- Responsabilização
- Auditabilidade

#### 2. Regulamentações (30 min)

- EU AI Act
- NIST AI RMF
- LGPD e IA
- Guidelines éticos

### CTF do Módulo (3h)

**Categorias:**

1. **ML Basics (4 desafios)**
   - Identificar algoritmo por comportamento
   - Corrigir modelo com overfitting
   - Calcular métricas
   - Feature engineering

2. **NLP (3 desafios)**
   - Classificar textos
   - Extrair entidades
   - Detectar spam

3. **Deep Learning (3 desafios)**
   - Corrigir arquitetura
   - Tuning de hiperparâmetros
   - Transfer learning

4. **LLMs (3 desafios)**
   - Prompt engineering
   - Análise de segurança com LLM
   - Identificar limitações

5. **Ética (2 desafios)**
   - Identificar viés em dataset
   - Propor mitigações

### Avaliação da Aula

| Instrumento | Peso | Critérios |
|-------------|------|-----------|
| CTF | 100% | Pontuação obtida |

### Referências

1. JOBIN, Anna et al. "The Global Landscape of AI Ethics Guidelines". Nature Machine Intelligence, 2019.
2. NIST. **AI Risk Management Framework**. 2023.
3. European Commission. **Ethics Guidelines for Trustworthy AI**. 2019.

---

## Bibliografia Completa do Módulo

### Referências Básicas

1. GÉRON, Aurélien. **Mãos à Obra: Aprendizado de Máquina com Scikit-Learn, Keras e TensorFlow**. 3ª ed. Alta Books, 2023.
2. CHOLLET, François. **Deep Learning with Python**. 2nd ed. Manning, 2021.
3. JURAFSKY, Daniel; MARTIN, James H. **Speech and Language Processing**. 3rd ed. Draft, 2024.

### Referências Complementares

4. RUSSELL, Stuart; NORVIG, Peter. **Inteligência Artificial**. 4ª ed. GEN LTC, 2022.
5. GOODFELLOW, Ian et al. **Deep Learning**. MIT Press, 2016.
6. McKINNEY, Wes. **Python for Data Analysis**. 3rd ed. O'Reilly, 2022.

### Recursos Online

- Scikit-learn: https://scikit-learn.org/
- TensorFlow: https://www.tensorflow.org/
- PyTorch: https://pytorch.org/
- Hugging Face: https://huggingface.co/

---

*Documento parte integrante do PPC do MBA em Cibersegurança e Inteligência Artificial*

*CECyber - Academia de Cibersegurança*
