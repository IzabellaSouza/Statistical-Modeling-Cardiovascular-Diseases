
![Statistical-Modeling-Cardiovascular-Diseases](https://user-images.githubusercontent.com/91201232/134407924-2b463c3f-eb8f-4a02-8a74-dce353e04ef5.png)
<br>
<br>

## Índice

- [Problema](#problema)
- [Dados](#dados)
- [Etapas](#etapas)
- [Progresso](#progresso)
- [Criador](#criador)

<br>

## Problema

A Organização Mundial de Saúde estima que 12 milhões de mortes ocorrem em todo o mundo, todos os anos devido a doenças cardíacas. Metade das mortes nos Estados Unidos e em outros países desenvolvidos se deve a doenças cardiovasculares. O prognóstico precoce de doenças cardiovasculares pode ajudar na tomada de decisões sobre mudanças no estilo de vida em pacientes de alto risco e, por sua vez, reduzir as complicações. Esta análise pretende identificar os fatores de risco mais relevantes para doenças cardíacas.

Framingham Heart Study
https://datacatalog.med.nyu.edu/dataset/10046

O Framingham Heart Study (FHS) é dedicado à identificação de fatores ou características comuns que contribuem para doenças cardiovasculares. Em 1948, uma amostra de 5.209 homens e mulheres entre 30 e 62 anos foi recrutada em Framingham, Massachusetts para o estudo. Outras amostras foram coletadas em 1971, 1994, 2002 e 2004. A pesquisa principal do conjunto de dados concentra-se em doenças cardiovasculares. Os dados incluem amostras biológicas, dados genéticos moleculares, dados de fenótipo, imagens, dados de funcionamento vascular do participante, dados fisiológicos, dados demográficos e dados de ECG. É um projeto colaborativo do National Heart, Lung and Blood Institute e Universidade de Boston.

O conjunto de dados fornece as informações dos pacientes. Cada atributo é um fator de risco potencial. Existem fatores de risco demográficos, comportamentais e médicos.

O objetivo do projeto é analisar a relação das variáveis preditoras com a variável alvo, pacientes que tiveram ou não doenças cardiovasculares! E responder a seguinte pergunta: Quais fatores mais contribuem para que um paciente venha a desenvolver doenças cardiovasculares em um período de 10 anos?

Para compreender mais sobre o problema, acesse:

https://www.who.int/en/news-room/fact-sheets/detail/cardiovascular-diseases-(cvds)
<br>

## Dados

O conjunto de dados fornece as informações dos pacientes. Cada atributo é um fator de risco potencial. Existem fatores de risco demográficos, comportamentais e médicos.

### Arquivos

Estão localizados no diretório `dados`

> - espectativa_vida.csv 
> - pacientes.csv 


### Campos de dados

- Demográfico:

  Sex: masculino ou feminino (variável categórica)

  Age: idade do paciente (variável numérica)

  Education: nenhuma informação adicional é fornecida (variável categórica)


- Comportamental:

  Current Smoker: se o paciente é ou não fumante atual (variável categórica)

  Cigs Per Day: o número de cigarros que a pessoa fumava em média em um dia (variável numérica)


- Informações sobre histórico médico:

  BP Meds: se o paciente estava ou não fazendo uso de medicamentos para pressão arterial (variável categórica)

  Prevalent Stroke: se o paciente já teve ou não um AVC (variável categórica)

  Prevalent Hyp: se o paciente era ou não hipertenso (variável categórica)

  Diabetes: se o paciente teve ou não diabetes (variável categórica)


- Informações sobre a condição médica atual:

  Tot Chol: nível total de colesterol (variável numérica)

  Sys BP: pressão arterial sistólica (variável numérica)

  Dia BP: pressão arterial diastólica (variável numérica)

  BMI: Índice de Massa Corporal (variável numérica)

  Heart Rate: frequência cardíaca (variável numérica)

  Glucose: nível de glicose (variável numérica)


- Variável de destino:

  TenYearCHD - Risco de 10 anos de doença cardíaca coronária (CHD - Coronary Heart Disease ) - (binário: "1" significa "Sim", "0" significa "Não")
<br>

## Etapas

- [x] Importação e Identificação do Dados
- [x] Análise Exploratória e Limpeza dos dados
- [x] Modelos de Regressão Logística
- [x] Deploy Modelo
- [x] Conclusão
- [x] Ferramentas Utilizadas
<br>

## Progresso

### Importação e Identificação do Dados
- Importação bibliotecas e pacotes
- Caregamento dos dados
- Entendimento do Problema

### Análise Exploratória e Limpeza dos dados
- Checagem de registros duplicados
- Checagem de valores ausentes
- Criação de Função para visualizar a distribuição de cada variável
- Criação de Função para calcular a associação entre variáveis categóricas
- Corrigindo os N/A e Outliers com base em conhecimento de negócio
- Pré-Processamento dos Dados

### Modelos de Machine Learning
- Criação de cinco versões de modelo de Regressão Logística com StatsModels
- Criação de duas versões de modelo GLM
- Seleção de Atributos (Feature Selection)
- Feature Selection: Backward Elimination (P-value Approach)

### Depoy Modelo
- Modelo Final

```python

##Versão 5 - Regressão Logística com StatsModels

# Quinta versão do modelo

# Separa X e y
X = X_final_importance
y = y_final

# Cria o modelo sem os atributos com maior valor-p
logit_modelo_v5 = back_feature_elem(X, y, cols_names)

# Print do resultado
print(logit_modelo_v5.summary())


# Confusion Matrix do Modelo
logit_modelo_v5.pred_table()

# Imprimindo 10 previsões do modelo
predictions_v5 = logit_modelo_v5.predict()
print(predictions_v5[0:10])

# Defininido um limite para a classificação
y_pred_v5 = [0 if x < 0.5 else 1 for x in predictions_v5]

# Relatório de Classificação
print(classification_report(y, y_pred_v5))

```

- Extração dos parâmetros e apresentar em formato de tabela
```python

# Print do resultado do modelo_v5 (nossa escolha)
print(logit_modelo_v5.summary())


```
- Calcular o exponencial de cada um dos coeficientes para gerar os índices de chances (Odds Ratio)

```python

logit_modelo_v5.params

np.exp(logit_modelo_v5.params)

logit_modelo_v5.conf_int()
np.exp(logit_modelo_v5.conf_int())

logit_modelo_v5.pvalues

# Extrai os parâmetros e intervalos de confiança
params = np.exp(logit_modelo_v5.params)
conf = np.exp(logit_modelo_v5.conf_int())
conf['OR'] = params

# Extra os valores-p
pvalue = round(logit_modelo_v5.pvalues, 3)
conf['Valor-p'] = pvalue

# Imprime os resultados
conf.columns = ['IC 95%(2.5%)', 'IC 95%(97.5%)', 'Odds Ratio', 'Valor-p']
print((conf))

```
<br>

### Conclusão

O coeficiente para a idade (age) diz que, mantendo todos os outros constantes, veremos um aumento de 8% nas chances de ser diagnosticado com doença cardíaca em um período de 10 anos, para um aumento de um ano na idade pois:

exp (0.074848) = 1.077721.

Da mesma forma, com cada cigarro extra que se fuma, há um aumento de 3% nas chances de ser diagnosticado com doença cardíaca em um período de 10 anos.

Há um aumento de 1,6% nas chances de ser diagnosticado com doença cardíaca em um período de 10 anos para cada aumento unitário da pressão arterial sistólica.

Há um aumento de 2,2% nas chances de ser diagnosticado com doença cardíaca em um período de 10 anos para cada aumento unitário do índice de massa corporal.

Para o nível total de colesterol e glicose, não há alterações significativas.

### Ferramentas Utilizadas

- Scipy
- Numpy
- SMOTE
- Pandas
- Sklearn
- Seaborn
- Imblearn
- Matplotlib
- Tensorflow
- Statsmodels
<br>

## Criador

**Izabella Souza** 
