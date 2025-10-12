# regressao-seguro-saude
Análise de regressão linear e polinomial com dados de seguro médico

Este projeto foi desenvolvido como parte da disciplina de **Aprendizado de Máquina** no curso de **Mestrado**, com o objetivo de aplicar técnicas de regressão linear e polinomial em um conjunto de dados reais.

## Objetivo

Prever os custos médicos individuais (`charges`) cobrados por planos de saúde, com base em características pessoais como idade, índice de massa corporal (IMC), número de filhos, sexo, tabagismo e região.

## Dataset

Utilizamos o conjunto de dados [Insurance](https://www.kaggle.com/datasets/mirichoi0218/insurance) disponível no Kaggle. Ele contém 1.338 registros com 7 variáveis.

## Etapas realizadas

1. **Regressão Linear sem pré-processamento**  
   - Avaliação com Holdout e validação cruzada  
   - Utilização apenas de variáveis numéricas (`age`, `bmi`, `children`)  
   - Resultados mostraram baixa performance (R² ≈ 0.11)

2. **Pré-processamento dos dados**  
   - Padronização de variáveis numéricas com `StandardScaler`  
   - Codificação de variáveis categóricas com `OneHotEncoder`  
   - Montagem de pipeline com `ColumnTransformer`

3. **Regressão Linear com dados pré-processados**  
   - Avaliação com validação cruzada 5-fold  
   - Resultados significativamente melhores (R² ≈ 0.74)

4. **Regressão Polinomial com dados pré-processados**  
   - Teste com grau 2 e grau 3 usando `PolynomialFeatures`  
   - Grau 2 obteve o melhor desempenho (R² ≈ 0.83)  
   - Grau 3 teve leve queda, indicando possível overfitting

5. **Resumo dos resultados**  
   - O modelo polinomial grau 2 foi o mais eficaz  
   - O pré-processamento foi essencial para melhorar o desempenho  
   - A variável `smoker` (fumante) teve forte impacto nos custos

## Como usar o `kaggle.json`

Para baixar o dataset diretamente no Colab, é necessário autenticar sua conta do Kaggle via API. Siga os passos abaixo:

1. Acesse sua conta no [Kaggle](https://www.kaggle.com/account)
2. Vá até a seção **API** e clique em **"Create New API Token"**
3. Um arquivo chamado `kaggle.json` será baixado
4. No Colab, faça o upload com:

```python
from google.colab import files
files.upload()  # selecione o arquivo kaggle.json

