
![Statistical-Modeling-Cardiovascular-Diseases](https://user-images.githubusercontent.com/91201232/134407924-2b463c3f-eb8f-4a02-8a74-dce353e04ef5.png)
<br>
<br>

## Índice

- [Problema](#problema)
- [Dados](#dados)
- [Etapas](#etapas)
- [Progresso](#progresso)
- [Dependências](#dependencias)
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

## Etapas

- [x] Importação e Identificação do Dados
- [x] Análise Exploratória e Limpeza dos dados
- [x] Modelos de Regressão Logística
- [x] Interpretação e Tradução dos Resultados
- [x] Conclusão


## Progresso

### Importação e Identificação do Dados

