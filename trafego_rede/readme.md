## **Fluxo de Trabalho para Captura, Processamento, Análise e Classificação de Tráfego de Rede**

## **1\. Captura de Dados**

- **Ferramentas**:  
  - [tcpdump](https://www.tcpdump.org/)
  - [Wireshark](https://www.wireshark.org/)
  - [tshark](https://www.wireshark.org/docs/man-pages/tshark.html) (modo CLI do Wireshark)  

- **Descrição**:  
    Captura do tráfego de rede em formato .pcap para posterior análise. Essa etapa consiste na interceptação e armazenamento do tráfego de rede em tempo real. Os dados capturados são geralmente salvos no formato PCAP, que pode ser analisado posteriormente. As ferramentas citadas permitem realizar capturas tanto de forma interativa (com interface gráfica) quanto automatizada (linha de comando).  

## **2\. Exportação dos PCAPs para CSV**

- **Ferramentas**:  
  - [tshark](https://www.wireshark.org/docs/man-pages/tshark.html) (opção -T fields para exportar campos específicos)  

  - Scripts em Python usando [](https://github.com/KimiNewt/pyshark)[scapy](https://scapy.net/) para extração customizada  

- **Descrição**:  
    Após a captura, os arquivos PCAP devem ser convertidos para um formato tabular como CSV (ou formato mais leve [.parquet](https://pypi.org/project/parquet/)), o que facilita a manipulação e análise dos dados em ferramentas de ciência de dados. As bibliotecas e ferramentas a citadas permitem fazer essa conversão e extrair atributos relevantes dos pacotes (ex.: IPs, portas, protocolos, tempo, tamanho de pacotes, flags).  

##

## **3\. Pré-processamento dos Dados**

- **Ferramentas**:  
  - [Pandas](https://pandas.pydata.org/) / [Numpy](https://numpy.org/) (Python)  

  - Scripts customizados em Python  

  - [scikit-learn](https://scikit-learn.org/stable/) (para normalização, codificação de variáveis)
- **Descrição**:

Essa fase envolve o tratamento de dados faltantes, normalização de valores, codificação de atributos categóricos e transformação de dados temporais ou textuais. O objetivo é preparar os dados para análise estatística ou treinamento de modelos de _machine learning_.  

## **4\. Análise Exploratória dos Dados**

- **Ferramentas**:  
  - [Pandas](https://pandas.pydata.org/) e [Seaborn](https://seaborn.pydata.org/) (Python)  

  - [Matplotlib](https://matplotlib.org/)
  - [Plotly](https://plotly.com/python/) (para gráficos interativos)  

- **Descrição**:  
    A análise exploratória dos dados ajuda a compreender a distribuição dos dados, detectar outliers, visualizar correlações e padrões iniciais. Etapa fundamental antes de qualquer modelagem, pois permite gerar hipóteses e selecionar características relevantes.  

##

##

##

## **5\. Correlação de Características**

- **Ferramentas**:  
  - [Seaborn](https://seaborn.pydata.org/) (heatmap)  

  - [Pandas](https://pandas.pydata.org/) (.corr())  

- **Descrição**:  
    Analisado a relação entre os atributos (features) do conjunto de dados para identificar redundâncias ou combinações úteis para a modelagem. Correlações fortes podem indicar atributos que carregam informações similares.

## **6\. Seleção e Engenharia de Características (opcional)**

- **Ferramentas**:  
  - [scikit-learn](https://scikit-learn.org/stable/) (SelectKBest, PCA)  

  - [Featuretools](https://featuretools.alteryx.com/en/stable/) (engenharia automática de características)  

- **Descrição**:  
    Esta etapa busca reduzir a dimensionalidade do conjunto de dados e construir novos atributos mais representativos. Isso pode melhorar o desempenho de modelos e reduzir o custo computacional.

### **7\. Modelagem**

- **Ferramentas**:  
  - [PyTorch](https://pytorch.org/) / [TensorFlow](https://www.tensorflow.org/?hl=pt-br) (modelos neurais)  

- **Descrição**
- Aplicação de algoritmos de machine learning para classificar, detectar anomalias ou agrupar tráfego.

### **8\. Avaliação de Modelos**

- **Ferramentas**
  - [Acurácia](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.accuracy_score.html), [Precisão](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.precision_score.html), [Revocação](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.recall_score.html), [F1-score](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.f1_score.html)
  - [Matriz de confusão](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.confusion_matrix.html)
  - [ROC-AUC](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.roc_auc_score.html)
- **Descrição**:
- Verificação da performance dos modelos treinados por meio de métricas quantitativas e validação cruzada.

**Observações**

Dependendo do projeto, podem ser usadas também técnicas de balanceamento como [SMOTE](https://imbalanced-learn.org/stable/references/generated/imblearn.over_sampling.SMOTE.html), ou métodos de redução de dimensionalidade como PCA e [t-SNE](https://lvdmaaten.github.io/tsne/). Todas as etapas devem ser documentadas para permitir a reprodutibilidade dos experimentos.
