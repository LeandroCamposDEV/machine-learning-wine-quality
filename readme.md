# Projeto de Machine Learning Automatizado no Azure ML

Este repositório documenta o processo de criação, treinamento e implantação de um modelo de Machine Learning Automatizado no Azure Machine Learning Studio. O modelo foi desenvolvido para prever a qualidade de vinhos com base em suas características químicas.

---

## **1. Configuração do Ambiente**

### Pré-requisitos
- Uma conta no [Microsoft Azure](https://azure.microsoft.com).
- Assinatura ativa do Azure.
- Azure Machine Learning Workspace configurado.

### Ferramentas
- [Azure Machine Learning Studio](https://ml.azure.com/).
- CLI do Azure instalada (opcional).

---

## **2. Importação dos Dados**

### Passos:
1. No Azure Machine Learning Studio, vá até **Dados**.
2. Clique em **+ Criar** > **Upload de Arquivo**.
3. Selecione o dataset `WineQualityDataset.csv` e faça o upload.
4. Configure o dataset com as seguintes opções:
   - Tipo de dados: **Tabular**.
   - Defina a coluna de destino como `quality`.

---

## **3. Treinamento Automático**

### Passos:
1. Navegue até **ML Automatizado** > **+ Criar Novo Trabalho**.
2. Configure as etapas iniciais:
   - **Nome do Trabalho**: `WineQualityExperiment`.
   - **Dataset de entrada**: `WineQualityDataset`.
3. Escolha a **tarefa de previsão**:
   - Tipo: `Classificação`.
   - Coluna de destino: `quality`.
4. Configure o cluster de computação:
   - Clique em **Criar Cluster de Cálculo**.
   - Escolha o tamanho `Standard_DS3_v2` e defina:
     - **Nós mínimos**: `0`.
     - **Nós máximos**: `1`.
   - Salve e avance.
5. Execute o treinamento e aguarde a conclusão.

---

## **4. Registro do Modelo**

### Passos:
1. Após o treinamento, vá até a aba **Modelos**.
2. Localize o melhor modelo treinado e clique em **Registrar**.
3. Insira as seguintes informações:
   - **Nome do Modelo**: `WineQualityModel`.
   - **Descrição**: `Modelo para prever a qualidade de vinhos`.
   - Deixe as demais configurações padrão e conclua o registro.

---

## **5. Implantação do Modelo**

### Passos:
1. Vá até **Pontos de Extremidade** > **+ Criar Implantação**.
2. Configure a implantação:
   - **Nome do Ponto de Extremidade**: `laboratorioai900-rbtbd`.
   - **Modelo**: Selecione `WineQualityModel`.
   - **Ação de saída**: Acrescentar linha.
   - **Arquivo de saída**: `predictions.csv`.
3. Crie um **Cluster de Cálculo** (caso necessário) com as configurações padrão.
4. Avance e conclua a implantação.

---

## **6. Obtenção do Ponto de Extremidade**

Após a implantação:
- Acesse o ponto de extremidade em **Pontos de Extremidade**.
- Copie o **URL do Ponto de Extremidade REST** para usar nos testes.

---

## **7. Testes**

Siga o [guia de teste](#) para realizar chamadas ao ponto de extremidade e validar o funcionamento do modelo.

---

## **8. Limpeza de Recursos**

Para evitar cobranças no Azure:
1. Exclua o ponto de extremidade em **Pontos de Extremidade**.
2. Apague os clusters de computação em **Computação**.
3. Remova quaisquer outros ativos (datasets, modelos, etc.) não utilizados.

---

## **Referências**

- [Azure Machine Learning Studio](https://ml.azure.com/)
- [Documentação oficial do Azure ML](https://learn.microsoft.com/pt-br/azure/machine-learning/)
