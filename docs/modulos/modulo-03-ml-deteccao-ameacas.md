# Módulo 3: Machine Learning para Detecção de Ameaças

## Informações Gerais

| Item | Descrição |
|------|-----------|
| **Módulo** | 3 |
| **Trilha** | IA para Cibersegurança |
| **Disciplina** | Machine Learning para Detecção de Ameaças |
| **Carga Horária** | 40 horas |
| **Teoria/Prática** | 12h teóricas (30%) / 28h práticas (70%) |
| **Número de Aulas** | 8 aulas de 5 horas |
| **Pré-requisitos** | Módulos 1 e 2 |
| **Certificação Relacionada** | CompTIA CySA+ (parcial) |

## Ementa

Aplicação de Machine Learning em cibersegurança. Detecção de anomalias com algoritmos de clustering. Classificação de malware com técnicas supervisionadas. Análise comportamental com séries temporais. Feature engineering para dados de segurança. Detecção de intrusão com ML: IDS/IPS inteligentes. Análise de tráfego de rede com Deep Learning. User and Entity Behavior Analytics (UEBA). Detecção de phishing com NLP. Desafios: adversarial attacks em modelos de segurança.

## Objetivos de Aprendizagem

1. Desenvolver modelos de ML para detecção de anomalias em redes e sistemas
2. Implementar classificadores de malware eficientes
3. Criar sistemas de detecção de intrusão baseados em ML
4. Aplicar UEBA para identificação de ameaças internas
5. Construir detectores de phishing com técnicas de NLP
6. Compreender e mitigar ataques adversariais em modelos de segurança

---

# PLANOS DE AULA

---

## AULA 1: ML para Segurança - Visão Geral e Datasets

### Informações da Aula
| Item | Descrição |
|------|-----------|
| **Aula** | 1 de 8 |
| **Tema** | Introdução a ML para Segurança e Datasets |
| **Carga Horária** | 5 horas |
| **Teoria/Prática** | 2h / 3h |

### Objetivos
1. Entender o papel do ML em cibersegurança
2. Conhecer os principais datasets de segurança
3. Preparar dados de segurança para ML
4. Aplicar feature engineering específico para segurança

### Estrutura da Aula

| Tempo | Atividade | Tipo |
|-------|-----------|------|
| 0:00-0:45 | ML em Segurança: Panorama | Expositiva |
| 0:45-1:30 | Datasets de Segurança | Expositiva-dialogada |
| 1:30-2:00 | Feature Engineering | Demonstração |
| 2:00-2:15 | Intervalo | - |
| 2:15-3:45 | **Lab 1:** Preparação do Dataset CICIDS2017 | Prática |
| 3:45-4:45 | **Lab 2:** Feature Engineering | Prática |
| 4:45-5:00 | Encerramento | Discussão |

### Conteúdo Programático

#### ML em Segurança - Aplicações
- **Detecção de Malware:** Classificação estática e dinâmica
- **IDS/IPS Inteligente:** Detecção de intrusão baseada em ML
- **Análise de Tráfego:** Identificação de anomalias
- **UEBA:** Detecção de ameaças internas
- **Phishing Detection:** Classificação de emails e URLs
- **Fraud Detection:** Transações suspeitas

#### Datasets de Referência
| Dataset | Tipo | Características |
|---------|------|-----------------|
| CICIDS2017 | Network | 80+ features, ataques rotulados |
| NSL-KDD | Network | Versão melhorada do KDD99 |
| UNSW-NB15 | Network | 49 features, 9 tipos de ataque |
| Malware Bazaar | Malware | Amostras de malware real |
| Ember | Malware | 1M+ samples PE files |
| CERT Insider Threat | UEBA | Logs de comportamento |

#### Feature Engineering para Segurança
```python
# Exemplos de features derivadas
df['bytes_per_packet'] = df['total_bytes'] / df['packet_count']
df['flow_duration_sec'] = df['flow_duration'] / 1000000
df['is_weekend'] = df['timestamp'].dt.dayofweek >= 5
df['hour_of_day'] = df['timestamp'].dt.hour

# Agregações por janela temporal
df['requests_last_5min'] = df.groupby('source_ip')['timestamp'].transform(
    lambda x: x.rolling('5min').count()
)
```

### Atividades Práticas

#### Lab 1: Preparação do Dataset CICIDS2017 (90 min)
**Tarefas:**
1. Download e carregamento do dataset
2. Análise exploratória
3. Tratamento de valores missing e infinitos
4. Balanceamento de classes (SMOTE, undersampling)
5. Encoding de variáveis categóricas

**Entregável:** Notebook com dataset preparado

#### Lab 2: Feature Engineering (60 min)
**Tarefas:**
1. Criar features derivadas
2. Seleção de features (correlação, mutual information)
3. Normalização/Standardização
4. Exportar dataset processado

### Materiais e Recursos
- Dataset CICIDS2017 (AWS/Kaggle)
- Jupyter Notebook template
- Artigo: "A Realistic Cyber Defense Dataset (CICIDS2017)"

### Abordagem Metodológica
- **Expositiva:** Conceitos de ML em segurança
- **Hands-on:** Preparação de dados
- **PBL:** Desafios de feature engineering

### Avaliação
| Instrumento | Peso |
|-------------|------|
| Lab 1 | 50% |
| Lab 2 | 50% |

### Referências
1. SHARAFALDIN, I. et al. "Toward Generating a New Intrusion Detection Dataset". ICISSP, 2018.
2. STAMP, Mark. **Introduction to Machine Learning with Applications in Information Security**. Cap. 1-2.

---

## AULA 2: Detecção de Anomalias e Clustering

### Informações da Aula
| Item | Descrição |
|------|-----------|
| **Aula** | 2 de 8 |
| **Tema** | Detecção de Anomalias com Clustering |
| **Carga Horária** | 5 horas |
| **Teoria/Prática** | 1.5h / 3.5h |

### Objetivos
1. Implementar detecção de anomalias com Isolation Forest
2. Usar clustering para identificar comportamentos anômalos
3. Aplicar One-Class SVM
4. Avaliar detectores de anomalias

### Conteúdo Programático

#### Técnicas de Detecção de Anomalias

**Isolation Forest:**
```python
from sklearn.ensemble import IsolationForest

iso_forest = IsolationForest(
    n_estimators=100,
    contamination=0.01,  # % esperada de anomalias
    random_state=42
)

# -1 = anomalia, 1 = normal
predictions = iso_forest.fit_predict(X)
anomalies = X[predictions == -1]
```

**Local Outlier Factor (LOF):**
```python
from sklearn.neighbors import LocalOutlierFactor

lof = LocalOutlierFactor(n_neighbors=20, contamination=0.01)
predictions = lof.fit_predict(X)
```

**One-Class SVM:**
```python
from sklearn.svm import OneClassSVM

ocsvm = OneClassSVM(kernel='rbf', nu=0.01)
predictions = ocsvm.fit_predict(X)
```

**DBSCAN para Clustering:**
```python
from sklearn.cluster import DBSCAN

dbscan = DBSCAN(eps=0.5, min_samples=5)
clusters = dbscan.fit_predict(X)
# Cluster -1 = noise/anomalias
```

#### Métricas para Detecção de Anomalias
- Precision, Recall, F1 (quando há labels)
- Silhouette Score (clustering)
- Reconstruction Error (autoencoders)

### Atividades Práticas

#### Lab: Detector de Anomalias de Rede (3.5h)

**Dataset:** CICIDS2017 (preparado na aula anterior)

**Tarefas:**
1. Treinar Isolation Forest
2. Treinar One-Class SVM
3. Aplicar DBSCAN
4. Comparar resultados
5. Identificar tipos de ataques detectados
6. Otimizar parâmetros

**Entregável:** Notebook com comparativo de técnicas

### Avaliação
| Instrumento | Peso |
|-------------|------|
| Lab completo | 80% |
| Quiz | 20% |

### Referências
1. LIU, F. T. et al. "Isolation Forest". ICDM, 2008.
2. CHANDOLA, V. et al. "Anomaly Detection: A Survey". ACM Computing Surveys, 2009.

---

## AULA 3: Classificação de Malware

### Informações da Aula
| Item | Descrição |
|------|-----------|
| **Aula** | 3 de 8 |
| **Tema** | Classificação de Malware com ML |
| **Carga Horária** | 5 horas |
| **Teoria/Prática** | 1.5h / 3.5h |

### Objetivos
1. Extrair features de arquivos PE
2. Implementar classificador de malware
3. Usar análise estática e dinâmica
4. Avaliar detecção de famílias de malware

### Conteúdo Programático

#### Features de Arquivos PE
```python
import pefile

def extract_pe_features(filepath):
    pe = pefile.PE(filepath)
    features = {
        'machine': pe.FILE_HEADER.Machine,
        'num_sections': pe.FILE_HEADER.NumberOfSections,
        'timestamp': pe.FILE_HEADER.TimeDateStamp,
        'entry_point': pe.OPTIONAL_HEADER.AddressOfEntryPoint,
        'image_size': pe.OPTIONAL_HEADER.SizeOfImage,
        'imports_count': len(pe.DIRECTORY_ENTRY_IMPORT) if hasattr(pe, 'DIRECTORY_ENTRY_IMPORT') else 0,
        'exports_count': len(pe.DIRECTORY_ENTRY_EXPORT.symbols) if hasattr(pe, 'DIRECTORY_ENTRY_EXPORT') else 0,
    }
    # Entropy de seções
    for section in pe.sections:
        features[f'entropy_{section.Name.decode().strip()}'] = section.get_entropy()
    return features
```

#### Pipeline de Classificação
```python
from sklearn.ensemble import RandomForestClassifier
from sklearn.model_selection import cross_val_score

# Dataset EMBER ou similar
X_train, y_train = load_ember_dataset('train')
X_test, y_test = load_ember_dataset('test')

# Random Forest para malware detection
rf = RandomForestClassifier(n_estimators=200, n_jobs=-1)
rf.fit(X_train, y_train)

# Avaliação
print(classification_report(y_test, rf.predict(X_test)))
```

### Atividades Práticas

#### Lab: Classificador de Malware (3.5h)

**Dataset:** EMBER ou dataset de features PE

**Tarefas:**
1. Carregar dataset de features
2. Treinar classificadores (RF, XGBoost, MLP)
3. Comparar desempenho
4. Analisar features mais importantes
5. Testar com amostras novas

**Entregável:** Modelo de classificação + análise

### Referências
1. SAXE, J.; BERLIN, K. "Deep Neural Network Based Malware Detection". AISEC, 2015.
2. ANDERSON, H. S.; ROTH, P. "EMBER: An Open Dataset for Training Static PE Malware Machine Learning Models". 2018.

---

## AULA 4: Detecção de Intrusão com ML (IDS/IPS)

### Informações da Aula
| Item | Descrição |
|------|-----------|
| **Aula** | 4 de 8 |
| **Tema** | IDS/IPS Baseado em Machine Learning |
| **Carga Horária** | 5 horas |
| **Teoria/Prática** | 1.5h / 3.5h |

### Objetivos
1. Entender arquitetura de IDS baseado em ML
2. Implementar detecção de múltiplos tipos de ataque
3. Criar modelo multi-classe
4. Avaliar em cenário realista

### Conteúdo Programático

#### Tipos de Ataques para Detecção
- **DoS/DDoS:** Flood, Slowloris, Goldeneye
- **Probe:** Port scan, vulnerability scan
- **R2L:** Brute force, SQL injection, XSS
- **U2R:** Buffer overflow, privilege escalation
- **Botnet:** C&C communication

#### Modelo Multi-Classe
```python
from sklearn.preprocessing import LabelEncoder
from sklearn.ensemble import GradientBoostingClassifier

# Encoding de labels
le = LabelEncoder()
y_train_encoded = le.fit_transform(y_train)

# Modelo multi-classe
gb = GradientBoostingClassifier(n_estimators=100)
gb.fit(X_train, y_train_encoded)

# Predição
predictions = le.inverse_transform(gb.predict(X_test))
```

#### Métricas por Classe
```python
from sklearn.metrics import classification_report, confusion_matrix
import seaborn as sns

print(classification_report(y_test, predictions))

cm = confusion_matrix(y_test, predictions)
sns.heatmap(cm, annot=True, fmt='d', xticklabels=le.classes_, yticklabels=le.classes_)
```

### Atividades Práticas

#### Lab: IDS Multi-Classe (3.5h)

**Dataset:** CICIDS2017 (todas as classes)

**Tarefas:**
1. Preparar dataset multi-classe
2. Treinar modelo (GradientBoosting, XGBoost)
3. Avaliar por tipo de ataque
4. Analisar confusion matrix
5. Identificar classes difíceis de detectar
6. Propor melhorias

**Entregável:** Notebook com IDS funcional

### Referências
1. BUCZAK, A. L.; GUVEN, E. "A Survey of Data Mining and Machine Learning Methods for Cyber Security Intrusion Detection". IEEE Communications Surveys, 2016.

---

## AULA 5: Análise de Tráfego de Rede

### Informações da Aula
| Item | Descrição |
|------|-----------|
| **Aula** | 5 de 8 |
| **Tema** | Análise de Tráfego de Rede com ML/DL |
| **Carga Horária** | 5 horas |
| **Teoria/Prática** | 1.5h / 3.5h |

### Objetivos
1. Analisar capturas de pacotes (PCAP)
2. Extrair features de fluxos de rede
3. Implementar classificador de tráfego
4. Usar Deep Learning para análise de pacotes

### Conteúdo Programático

#### Extração de Features de PCAP
```python
from scapy.all import rdpcap, IP, TCP, UDP

def extract_flow_features(pcap_file):
    packets = rdpcap(pcap_file)
    flows = {}

    for pkt in packets:
        if IP in pkt:
            key = (pkt[IP].src, pkt[IP].dst,
                   pkt[TCP].sport if TCP in pkt else pkt[UDP].sport,
                   pkt[TCP].dport if TCP in pkt else pkt[UDP].dport)

            if key not in flows:
                flows[key] = {'packets': [], 'bytes': 0, 'start': pkt.time}

            flows[key]['packets'].append(pkt)
            flows[key]['bytes'] += len(pkt)

    return flows
```

#### CNN para Análise de Payloads
```python
import tensorflow as tf

# Payload como imagem (bytes → pixels)
model = tf.keras.Sequential([
    tf.keras.layers.Reshape((32, 32, 1), input_shape=(1024,)),
    tf.keras.layers.Conv2D(32, 3, activation='relu'),
    tf.keras.layers.MaxPooling2D(),
    tf.keras.layers.Conv2D(64, 3, activation='relu'),
    tf.keras.layers.MaxPooling2D(),
    tf.keras.layers.Flatten(),
    tf.keras.layers.Dense(64, activation='relu'),
    tf.keras.layers.Dense(num_classes, activation='softmax')
])
```

### Atividades Práticas

#### Lab: Classificador de Tráfego (3.5h)

**Tarefas:**
1. Processar arquivos PCAP
2. Extrair features de fluxos
3. Treinar classificador tradicional
4. Implementar CNN para payloads
5. Comparar abordagens

**Entregável:** Pipeline de análise de tráfego

### Referências
1. WANG, W. et al. "Malware Traffic Classification Using CNN for Representation Learning". ICOIN, 2017.

---

## AULA 6: User and Entity Behavior Analytics (UEBA)

### Informações da Aula
| Item | Descrição |
|------|-----------|
| **Aula** | 6 de 8 |
| **Tema** | UEBA - Análise Comportamental |
| **Carga Horária** | 5 horas |
| **Teoria/Prática** | 1.5h / 3.5h |

### Objetivos
1. Entender conceitos de UEBA
2. Modelar comportamento de usuários
3. Detectar ameaças internas (insider threats)
4. Criar baselines comportamentais

### Conteúdo Programático

#### Conceitos de UEBA
- **Baseline:** Comportamento normal do usuário
- **Anomaly Score:** Desvio do baseline
- **Risk Score:** Combinação de múltiplos indicadores
- **Peer Analysis:** Comparação com grupo similar

#### Features Comportamentais
```python
# Features de comportamento de usuário
user_features = {
    'login_hours': np.mean(login_times),
    'login_locations': len(unique_locations),
    'files_accessed_daily': np.mean(daily_file_access),
    'email_recipients_unique': len(unique_recipients),
    'after_hours_activity': after_hours_count / total_count,
    'data_transferred_mb': np.sum(data_transferred),
    'failed_logins': failed_login_count,
    'privilege_escalations': priv_esc_count
}
```

#### Detecção de Insider Threats
```python
from sklearn.ensemble import IsolationForest

# Modelo por usuário ou grupo
for user_group in groups:
    group_data = df[df['group'] == user_group]
    iso = IsolationForest(contamination=0.05)
    group_data['anomaly_score'] = iso.fit_predict(group_data[features])
```

### Atividades Práticas

#### Lab: Sistema UEBA (3.5h)

**Dataset:** CERT Insider Threat Dataset (versão sintética)

**Tarefas:**
1. Carregar logs de atividade
2. Criar features comportamentais
3. Estabelecer baselines
4. Detectar comportamentos anômalos
5. Calcular risk scores
6. Identificar possíveis insiders

**Entregável:** Sistema UEBA básico

### Referências
1. CERT. "Insider Threat Dataset". CMU SEI.
2. TUOR, A. et al. "Deep Learning for Unsupervised Insider Threat Detection". 2017.

---

## AULA 7: Detecção de Phishing e Spam com NLP

### Informações da Aula
| Item | Descrição |
|------|-----------|
| **Aula** | 7 de 8 |
| **Tema** | Detecção de Phishing com NLP |
| **Carga Horária** | 5 horas |
| **Teoria/Prática** | 1.5h / 3.5h |

### Objetivos
1. Analisar características de phishing
2. Classificar emails e URLs
3. Usar embeddings para detecção
4. Implementar detector robusto

### Conteúdo Programático

#### Features de Phishing
```python
# Features de URL
def extract_url_features(url):
    return {
        'length': len(url),
        'num_dots': url.count('.'),
        'has_ip': bool(re.match(r'\d+\.\d+\.\d+\.\d+', url)),
        'has_at_symbol': '@' in url,
        'has_suspicious_words': any(w in url.lower() for w in ['login', 'verify', 'account']),
        'entropy': calculate_entropy(url),
        'num_subdomains': len(url.split('/')[2].split('.')) - 2
    }

# Features de email
def extract_email_features(email):
    return {
        'subject_length': len(email['subject']),
        'body_length': len(email['body']),
        'num_links': len(re.findall(r'http[s]?://', email['body'])),
        'has_attachment': email['has_attachment'],
        'urgency_words': count_urgency_words(email['body']),
        'sender_domain_age': get_domain_age(email['from'])
    }
```

#### Classificador com BERT
```python
from transformers import BertTokenizer, BertForSequenceClassification

tokenizer = BertTokenizer.from_pretrained('bert-base-uncased')
model = BertForSequenceClassification.from_pretrained('bert-base-uncased', num_labels=2)

# Fine-tuning para phishing detection
inputs = tokenizer(emails, padding=True, truncation=True, return_tensors='pt')
outputs = model(**inputs, labels=labels)
```

### Atividades Práticas

#### Lab: Detector de Phishing Multi-modal (3.5h)

**Tarefas:**
1. Preparar dataset de emails/URLs
2. Extrair features estruturais
3. Treinar classificador tradicional
4. Implementar classificador com embeddings
5. Combinar abordagens (ensemble)
6. Avaliar em dados recentes

**Entregável:** Detector de phishing completo

### Referências
1. SAHINGOZ, O. K. et al. "Machine Learning Based Phishing Detection from URLs". Expert Systems with Applications, 2019.

---

## AULA 8: Adversarial ML e CTF do Módulo

### Informações da Aula
| Item | Descrição |
|------|-----------|
| **Aula** | 8 de 8 |
| **Tema** | Adversarial ML e CTF Avaliativo |
| **Carga Horária** | 5 horas |
| **Teoria/Prática** | 1h / 4h |

### Objetivos
1. Entender ataques adversariais em ML
2. Conhecer técnicas de evasão
3. Implementar defesas
4. Aplicar conhecimentos em CTF

### Conteúdo Programático

#### Adversarial Machine Learning
- **Evasion Attacks:** Modificar input para enganar modelo
- **Poisoning Attacks:** Corromper dados de treinamento
- **Model Stealing:** Extrair modelo via queries
- **Model Inversion:** Recuperar dados de treinamento

#### Técnicas de Evasão
```python
# FGSM (Fast Gradient Sign Method)
import tensorflow as tf

def fgsm_attack(model, x, y, epsilon=0.1):
    with tf.GradientTape() as tape:
        tape.watch(x)
        prediction = model(x)
        loss = tf.keras.losses.categorical_crossentropy(y, prediction)

    gradient = tape.gradient(loss, x)
    perturbation = epsilon * tf.sign(gradient)
    adversarial_x = x + perturbation
    return adversarial_x
```

#### Defesas
- **Adversarial Training:** Treinar com exemplos adversariais
- **Input Preprocessing:** Detectar/remover perturbações
- **Ensemble Methods:** Múltiplos modelos
- **Defensive Distillation:** Suavizar outputs

### CTF do Módulo (3.5h)

**Categorias:**

1. **Anomaly Detection (4 desafios)**
   - Configurar Isolation Forest corretamente
   - Identificar anomalias em dataset
   - Otimizar threshold
   - Combinar múltiplos detectores

2. **Malware Classification (3 desafios)**
   - Classificar amostras
   - Feature engineering
   - Identificar família de malware

3. **Network Analysis (4 desafios)**
   - Detectar ataque em PCAP
   - Classificar tipo de ataque
   - Identificar C&C communication

4. **Adversarial ML (3 desafios)**
   - Evadir detector de malware
   - Identificar dados envenenados
   - Defender modelo de ataque

5. **UEBA (2 desafios)**
   - Identificar insider threat
   - Calcular risk score

### Avaliação
| Instrumento | Peso |
|-------------|------|
| CTF | 100% |

### Referências
1. BIGGIO, B.; ROLI, F. "Wild Patterns: Ten Years After the Rise of Adversarial Machine Learning". Pattern Recognition, 2018.
2. APRUZZESE, G. et al. "The Role of Machine Learning in Cybersecurity". ACM Computing Surveys, 2023.

---

## Bibliografia Completa do Módulo

### Referências Básicas
1. STAMP, Mark. **Introduction to Machine Learning with Applications in Information Security**. 2nd ed. CRC Press, 2022.
2. SAXE, Joshua; SANDERS, Hillary. **Malware Data Science**. No Starch Press, 2018.

### Referências Complementares
3. BUCZAK, A. L.; GUVEN, E. "A Survey of Data Mining and Machine Learning Methods for Cyber Security Intrusion Detection". IEEE Communications Surveys, 2016.
4. APRUZZESE, G. et al. "The Role of Machine Learning in Cybersecurity". ACM Computing Surveys, 2023.
5. SOMMER, R.; PAXSON, V. "Outside the Closed World: On Using Machine Learning for Network Intrusion Detection". IEEE S&P, 2010.

### Datasets
- CICIDS2017: https://www.unb.ca/cic/datasets/ids-2017.html
- EMBER: https://github.com/elastic/ember
- CERT Insider Threat: https://resources.sei.cmu.edu/library/

---

*CECyber - Academia de Cibersegurança*
