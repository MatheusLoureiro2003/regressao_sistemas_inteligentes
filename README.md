# regressao_sistemas_inteligentes
Regressão que aprende a estimar a probabilidade de sobrevivência de uma vítima representado pela característica sobr



Tarefa 2: Regressa o
Resgate de Vítimas de Catástrofes Naturais, Desastres ou Grandes Acidentes
Objetivo da tarefa
Construir um modelo de regressão com CART e outro com Redes Neurais MLP (RN): dadas as
características de 1 a 10 (ver descrição dos atributos), o modelo deve aprender a estimar a
probabilidade de sobrevivência de uma vítima representado pela característica sobr. Essa
característica é um número real no intervalo [0, 1], sendo zero a menor probabilidade de
sobrevivência e 1, a maior.
Requisitos
1. O formato do dataset para treinamento está aqui.
2. Não é permitido utilizar as seguintes características como entradas de treinamento:
11 gcs, 12 avpu, 13 tri e 14 sobr.
3. Saída:
14 sobr:
Você pode se inspirar nos códigos disponíveis no Google Colab:
Regressor CART
Regressor rede neural MLP
Procedimento e relatório
TREINAMENTO/VALIDAÇÃO
1) Gere um dataset de treinamento/validação com o programa gerar_dados_vitimas.py
O número de vítimas deve ser entre 2.000 e 10.000 vítimas (utilize uma semente fixa
para fins de reprodutibilidade).
a. Descreva os parâmetros de criação do dataset: número de vítimas, idade,
desvio padrão, ruído e tipo de acidente.
b. Defina o número de folds para realizar a validação cruzada
2) Treine o CART com o dataset de treinamento/validação com o método da validação
cruzada.
a. utilize três ou mais hiperparametrizações variando max_depth,
min_samples_leaf e criterion dentre outros,
b. escolha a melhor com base no MSE (mean squared error, erro quadrático
médio) e
c. apresente a melhor hiperparametrização.
3) Treine a RN com o dataset de treinamento/validação com validação cruzada.
a. utilize três ou mais hiperparametrizações: número de camadas ocultas,
número de neurônios/camada, função de ativação e taxa de aprendizado
b. escolha a melhor com base no MSE médio da validação cruzada e
c. apresente a melhor hiperparametrização.
UTFPR/Curitiba - SISTEMAS INTELIGENTES 1 – 2026/1 – Prof. Tacla
Compare os resultados do melhor modelo CART x melhor modelo de RN com base no
MSE e nas tabelas que seguem.
d. Viés: compare o MSE médio de treino com o MSE médio de validação
(aproximação empírica do viés estatístico pelas médias calculadas sobre os kfolds). Utilize a tabela abaixo como modelo sendo ϵ𝑡 o MSE de treino e 𝜖𝑣
, o
de validação.
𝑀𝑆𝐸: 𝜖 =
1
𝑛
∑(𝑦𝑖 − 𝑦̂𝑖
)
2
𝑛
𝑖=1
onde:
𝑛= número de observações (exemplos utilizados no treinamento ou na validação)
𝑦𝑖= valor real da variável de saída
𝑦̂𝑖= valor predito pelo modelo
(𝑦𝑖−𝑦̂𝑖)
2= erro quadrático da observação 𝑖
𝜖̅ =
1
𝑘
∑ 𝜖𝑖
𝑘
𝑖=1
 (MSE médio dos k-folds)
MSE CART RN
treino 𝜀̅t 𝜖̅𝑡
Validação 𝜀v̅ 𝜖v̅
Diferença abs. |ϵ̅𝑡 − ϵ𝑣
| |ϵ̅𝑡 − ϵ𝑣
|
e. Variância: comparar as variâncias de MSE calculadas sobre os k-folds (como
uma aproximação empírica da variância estatística e medida de estabilidade
do modelo). A diferença entre a variância de treino e de validação é um
indicador empírico de overfitting.
𝑉𝑎𝑟 =
1
𝑘
∑(𝜖𝑖 − 𝜖̅)
2
𝑘
𝑖=1
VARIÂNCIA (MSE) CART RN
treino 𝑉𝑎𝑟𝑡 𝑉𝑎𝑟𝑡
Validação 𝑉𝑎𝑟𝑣 𝑉𝑎𝑟𝑣
Diferença abs. 𝑉𝑎𝑟𝑡 − 𝑉𝑎𝑟𝑣 𝑉𝑎𝑟𝑡 − 𝑉𝑎𝑟𝑣
TESTES CEGOS
4) Retreino: com todo o dataset de treino/validação e com as melhores
hiperparametrizações de CART e da RN obtidas nas etapas 2 e 3:
a. treine um novo modelo com CART e
b. treine um novo modelo com RNs.
5) Teste cego: com o dataset de teste cego (1000v), compare os valores de MSE do
modelo CART (5a) x modelo RNs (5b). Use o dataset de teste cego somente neste item,
se for usado em qualquer outra etapa de treino/validação, configura-se vazamento de
dados (data leakage).
UTFPR/Curitiba - SISTEMAS INTELIGENTES 1 – 2026/1 – Prof. Tacla
6) Analise:
a. observando os resultados de teste cego, comente sobre a capacidade de
generalização dos modelos CART (5a) x modelo RNs (5b) levando em conta os
conceitos de overfitting e underfitting;
b. com base em um gráfico de dispersão do valor real x valor predito, os
intervalos das saídas reais que não apresentam problemas e as que
apresentam problemas para o regressor. Justifique.
c. por fim, se o modelo que apresentou os melhores resultados na etapa de
treino/validação (1-4) obteve melhor desempenho nos testes cegos. Caso não,
justifique.
