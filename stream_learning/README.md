# Tutorial CapyMOA: Aprendizado de Máquina em Streams de Dados

Este repositório contém um tutorial sobre como usar a biblioteca `CapyMOA` para aprendizado de máquina em streams de dados.

## O que é CapyMOA?

CapyMOA é uma biblioteca para aprendizado de máquina com stream de dados (aprendizado contínuo) que integra funcionalidades das bibliotecas MOA (stream learners), PyTorch (redes neurais) e scikit-learn (aprendizado de máquina).

### Por que utilizar?

O aprendizado contínuo, tratando um dado por vez (instância), oferece vantagens valiosas, especialmente no contexto de redes:
-   Economia de memória e armazenamento
-   Tratamento e atualização de dados em tempo real
-   Escalabilidade
-   Adaptação automática a mudanças (concept drift)

CapyMOA é rápido e permite o desenvolvimento com baixo nível de código.

## Começando

### Pré-requisitos

Para executar os exemplos, você precisará de:
-   JAVA
-   Bibliotecas Python: `torch` e `torchvision`

Você pode verificar a instalação do JAVA com:
```bash
java -version
```

### Instalação

1.  Instale o PyTorch e o Torchvision:
    ```bash
    pip install torch torchvision --index-url https://download.pytorch.org/whl/cpu
    ```

2.  Instale o CapyMOA:
    ```bash
    pip install capymoa
    ```

## Uso

O notebook `capymoa_tutorial.ipynb` neste repositório demonstra como:
-   Preparar dados para streaming de fontes como arquivos CSV.
-   Usar classificadores como `OSNN` e `OnlineBagging`.
-   Avaliar modelos de aprendizado de máquina em stream de dados.

Para executar o tutorial, abra e execute as células no `capymoa_tutorial.ipynb` em um ambiente Jupyter.

## Estrutura do Projeto

-   `capymoa_tutorial.ipynb`: O notebook principal com o tutorial.
-   `data/`: Contém os datasets usados no tutorial.
-   `README.md`: Este arquivo.
