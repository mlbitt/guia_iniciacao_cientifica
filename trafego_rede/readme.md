## **Fluxo de Trabalho para Captura, Processamento, Análise e Classificação de Tráfego de Rede**

## 1. Captura de Dados

### Objetivo
Capturar o tráfego de rede em tempo real para posterior análise e extração de informações relevantes.

---

### Ferramentas
- [tcpdump](https://www.tcpdump.org/)
- [Wireshark](https://www.wireshark.org/)
- [tshark](https://www.wireshark.org/docs/man-pages/tshark.html) (modo CLI do Wireshark)

---

### Descrição
Captura do tráfego de rede em formato `.pcap` para análise posterior. Essa etapa envolve a interceptação e armazenamento de pacotes de rede em tempo real. Os dados são frequentemente salvos no formato PCAP, que pode ser analisado com ferramentas de ciência de dados. As ferramentas listadas permitem realizar capturas tanto de forma interativa (com interface gráfica) quanto automatizada (linha de comando).

---

## 2. Exportação dos PCAPs para CSV

### Objetivo
Converter arquivos PCAP para um formato tabular como CSV, para facilitar a análise de dados em ferramentas de ciência de dados.

---

### Ferramentas
- [tshark](https://www.wireshark.org/docs/man-pages/tshark.html) (opção `-T fields` para exportar campos específicos)
- Scripts em Python usando [PyShark](https://github.com/KimiNewt/pyshark) e [Scapy](https://scapy.net/) para extração customizada

---

### Descrição
Após a captura, os arquivos PCAP precisam ser convertidos para um formato tabular, como CSV ou outros formatos mais leves, como `.parquet`. Esse processo facilita a manipulação e análise dos dados em ferramentas como Pandas. As ferramentas citadas permitem a extração de atributos importantes dos pacotes, como IPs, portas, protocolos, tamanho de pacotes e flags.

---

## 3. Pré-processamento dos Dados

### Objetivo
Limpar e transformar os dados para garantir que estejam prontos para análise estatística ou treinamento de modelos de IA.

---

### Ferramentas
- [Pandas](https://pandas.pydata.org/) / [Numpy](https://numpy.org/) (Python)
- Scripts customizados em Python
- [Scikit-learn](https://scikit-learn.org/stable/) (para normalização, codificação de variáveis)

---

### Descrição
Essa fase envolve o tratamento de dados faltantes, normalização de valores, codificação de atributos categóricos e transformação de dados temporais ou textuais. O objetivo é preparar os dados para análises estatísticas ou para o treinamento de modelos de IA. A manipulação de dados é essencial para garantir que os modelos não sejam impactados por dados inadequados ou inconsistentes.

---

## 4. Análise Exploratória dos Dados

### Objetivo
Explorar e entender a estrutura dos dados, identificar padrões e detectar potenciais problemas, como valores ausentes ou outliers.

---

### Ferramentas
- [Pandas](https://pandas.pydata.org/) e [Seaborn](https://seaborn.pydata.org/) (Python)
- [Matplotlib](https://matplotlib.org/)
- [Plotly](https://plotly.com/python/) (para gráficos interativos)

---

### Descrição
A análise exploratória dos dados (EDA) é uma etapa essencial para entender a distribuição e a estrutura dos dados. Durante essa fase, podem ser detectados outliers, verificadas correlações entre variáveis e visualizados padrões de dados. A EDA também ajuda a gerar hipóteses e a decidir quais características dos dados são relevantes para a modelagem.

---

## 5. Correlação de Características

### Objetivo
Identificar relações entre as variáveis do conjunto de dados, o que pode ajudar a selecionar as características mais importantes para a modelagem.

---

### Ferramentas
- [Seaborn](https://seaborn.pydata.org/) (heatmap)
- [Pandas](https://pandas.pydata.org/) (.corr())
- [Scikit-Learn](https://scikit-learn.org/stable/modules/generated/sklearn.feature_selection.mutual_info_classif.html) (Informação Mútua)
- [Pingouin](https://pingouin-stats.org/build/html/index.html) (correlação de Kendall, Spearman, etc.)

---

### Descrição
A análise de correlação entre as características do conjunto de dados visa identificar redundâncias ou combinações úteis para a modelagem. Ferramentas como o cálculo da correlação de Pearson e a análise de informações mútuas podem ser usadas para entender como as variáveis estão relacionadas. A visualização através de heatmaps facilita a identificação de padrões e dependências entre as variáveis.

---

## 6. Seleção e Engenharia de Características (Opcional)

### Objetivo
Selecionar ou criar características mais representativas, melhorando o desempenho do modelo e reduzindo a complexidade computacional.

---

### Ferramentas
- [PCA](https://scikit-learn.org/stable/modules/generated/sklearn.decomposition.PCA.html) (Principal Component Analysis)
- [RFE](https://scikit-learn.org/stable/modules/generated/sklearn.feature_selection.RFE.html) (Recursive Feature Elimination)
- [SelectKBest](https://scikit-learn.org/stable/modules/generated/sklearn.feature_selection.SelectKBest.html)
- [SVM](https://scikit-learn.org/stable/modules/svm.html#classification) (com coef_ para seleção)
- [Featuretools](https://featuretools.alteryx.com/en/stable/) (engenharia automática de características)

---

### Descrição
Esta etapa visa selecionar as características mais relevantes ou criar novas, mais representativas. Técnicas como PCA são usadas para reduzir a dimensionalidade dos dados, enquanto métodos como RFE e SVM podem identificar atributos relevantes com base nos pesos dos modelos. Isso pode melhorar tanto o desempenho do modelo quanto reduzir o custo computacional.

---


## 7. Modelagem

### Objetivo
Aplicar algoritmos de *Machine Learning* e *Deep Learning* para resolver tarefas como **classificação**, **regressão** ou **clusterização** com base no tráfego de rede analisado.

---

### Divisão da Base de Dados
Antes do treinamento de modelos, é essencial dividir os dados em conjuntos:

- **Treino** (ex: 70%) – utilizado para treinar o modelo.
- **Validação** (ex: 15%) – usado para ajuste de hiperparâmetros.
- **Teste** (ex: 15%) – utilizado para avaliação final do modelo.

#### Técnicas e Ferramentas Utilizadas

- [`train_test_split`](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.train_test_split.html): divisão simples dos dados em treino e teste.
- [`KFold`](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.KFold.html): divide os dados em *k* partes para validação cruzada.
- [`StratifiedKFold`](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.StratifiedKFold.html): como o `KFold`, mas mantendo a proporção entre classes.
- [`cross_val_score`](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.cross_val_score.html): avalia o desempenho de um modelo com validação cruzada de forma simples.

---

### Tarefas Comuns
- **Classificação**: Identificação de ataques, categorização de tráfego.
- **Regressão**: Previsão de variáveis contínuas como latência, throughput.
- **Clusterização**: Descoberta de padrões não rotulados.

---

### Algoritmos Supervisionados
- [K-Nearest Neighbors (KNN)](https://scikit-learn.org/stable/modules/generated/sklearn.neighbors.KNeighborsClassifier.html)
- [Random Forest](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestClassifier.html)
- [Support Vector Machine (SVM)](https://scikit-learn.org/stable/modules/generated/sklearn.svm.SVC.html)
- [Naive Bayes](https://scikit-learn.org/stable/modules/naive_bayes.html)
- [XGBoost](https://xgboost.readthedocs.io/en/stable/)

---

### Algoritmos Não Supervisionados
- [K-Means](https://scikit-learn.org/stable/modules/generated/sklearn.cluster.KMeans.html)
- [DBSCAN](https://scikit-learn.org/stable/modules/generated/sklearn.cluster.DBSCAN.html)

---

### Redes Neurais / Deep Learning

#### Objetivo
Utilizar arquiteturas mais profundas para capturar padrões complexos, especialmente úteis em grandes volumes de dados ou sequências temporais.

#### Modelos
- [MLP (Multilayer Perceptron)](https://scikit-learn.org/stable/modules/generated/sklearn.neural_network.MLPClassifier.html)
- [CNN (Convolutional Neural Network)](https://www.tensorflow.org/tutorials/images/cnn) – ótimo para dados espaciais e bidimensionais.
- [RNN / LSTM](https://www.tensorflow.org/tutorials/structured_data/time_series) – ideal para séries temporais ou tráfego contínuo.

#### Frameworks Populares
- [TensorFlow](https://www.tensorflow.org/)
- [PyTorch](https://pytorch.org/)

---

> 🔄 **Dica**: Utilize validação cruzada (ex: K-Fold) sempre que possível para garantir maior robustez nos resultados.


## 8. Avaliação de Modelos

### Objetivo
Medir o desempenho dos modelos em dados não vistos e garantir sua capacidade de generalização para novos dados.

---

### Etapas

1. **Separação dos Dados**:
   - Caso ainda não tenha sido feita, divida os dados em conjuntos de **treino**, **validação** e **teste**. Isso ajuda a garantir que o modelo não seja sobreajustado (overfitting) aos dados de treino.

2. **Validação Cruzada**:
   - Aplique técnicas como **validação cruzada** (*cross-validation*) para obter estimativas mais confiáveis sobre o desempenho do modelo. Isso ajuda a reduzir a variabilidade dos resultados.

---

### Métricas

- **Acurácia**: Proporção de previsões corretas em relação ao total de amostras.
  - [Acurácia - Scikit-learn](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.accuracy_score.html)

- **Precisão**: Medida da capacidade do modelo de identificar corretamente as instâncias positivas.
  - [Precisão - Scikit-learn](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.precision_score.html)

- **Revocação (Recall)**: Medida da capacidade do modelo de identificar todas as instâncias positivas.
  - [Revocação - Scikit-learn](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.recall_score.html)

- **F1-Score**: Média harmônica entre a precisão e a revocação. Útil quando há desbalanceamento entre classes.
  - [F1-Score - Scikit-learn](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.f1_score.html)

- **Matriz de Confusão**: Tabela que mostra o desempenho do modelo em relação a cada classe. Utilizada para calcular outras métricas como precisão, revocação, etc.
  - [Matriz de Confusão - Scikit-learn](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.confusion_matrix.html)

- **ROC-AUC**: Medida que avalia a capacidade do modelo de discriminar entre as classes positivas e negativas. Quanto mais próximo de 1, melhor.
  - [ROC-AUC - Scikit-learn](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.roc_auc_score.html)

**Observações**
Dependendo do projeto, podem ser usadas também técnicas de balanceamento como [SMOTE](https://imbalanced-learn.org/stable/references/generated/imblearn.over_sampling.SMOTE.html), ou métodos de redução de dimensionalidade como [t-SNE](https://lvdmaaten.github.io/tsne/). Todas as etapas devem ser documentadas para permitir a reprodutibilidade dos experimentos.
