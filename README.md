# Trabalho 1 - Inteligência Artificial

Links colab:
## Communities and Crime: https://colab.research.google.com/drive/1XUzJKLvT0yqW5hURo6TEZLDIi1Aq5CiT?usp=sharing
## Htru2: https://colab.research.google.com/drive/17IEzA-EbKofl6WpUeHaq5xQsemGQzRSo?usp=sharing
## Nursery: https://colab.research.google.com/drive/1v9_ecym57rtul_9RjNhwywZNzToswpoU?usp=sharing

## 4. Explique o dilema entre bias e variância e o seu relacionamento com underfitting e overfitting.

O dilema entre bias (viés) e variância se refere ao desafio de equilibrar simplicidade e complexidade em modelos de aprendizado de máquina. 

O **bias** representa o erro introduzido por suposições excessivamente simplificadoras do modelo em relação à realidade. Modelos com alto viés tendem a não capturar adequadamente os padrões dos dados, o que resulta em **underfitting** (subajuste). 

Já a **variância** corresponde à sensibilidade do modelo a pequenas variações no conjunto de treinamento. Modelos com alta variância acabam se ajustando não apenas aos padrões reais, mas também ao ruído dos dados, levando ao **overfitting** (sobreajuste). 

O dilema ocorre porque reduzir o viés geralmente aumenta a variância, enquanto reduzir a variância tende a elevar o viés. Assim, o objetivo do aprendizado de máquina é encontrar um ponto de equilíbrio entre os dois, para assim obter um modelo com boa capacidade de generalização. Para isso, podem ser utilizadas técnicas como validação cruzada, regularização e análise de curvas de aprendizado.

## 5. Comente sobre a veracidade das afirmações:

### a. "Quanto mais variáveis de entrada forem usadas em um modelo de aprendizado de máquina, melhor será a qualidade do modelo".

**Não seria uma afirmação verdadeira**, pois o aumento do número de variáveis de entrada não implica, de forma direta, em um ganho de desempenho no modelo de aprendizado de máquina. 

Em termos técnicos, a adição excessiva de atributos pode gerar confusão, redundância e ruído estatístico, levando ao fenômeno conhecido como **maldição da dimensionalidade** (curse of dimensionality). Isso eleva a complexidade do espaço de hipóteses e pode gerar overfitting, onde o modelo se ajusta ao ruído do conjunto de treino e perde capacidade de generalização. 

Portanto, a qualidade e a relevância das variáveis são mais determinantes do que a quantidade absoluta delas.

### b. "Independente da qualidade, quanto mais amostras forem obtidas para uma base de dados, maior a tendência de se obter modelos mais adequados".

**Não seria uma afirmação verdadeira**, pois o sucesso das amostras também depende da qualidade das amostras. 

Em teoria, o aumento do volume amostral contribui para a melhoria da capacidade de generalização do modelo, reduzindo a variância e tornando as estimativas dos parâmetros mais estáveis. No entanto, essa relação depende da representatividade e da qualidade dos dados. 

Grandes volumes de dados contaminados, enviesados ou não representativos podem induzir o modelo a padrões incorretos e comprometer o desempenho preditivo. Assim, embora a quantidade de dados seja um fator relevante, a curadoria e a consistência da base são condições essenciais para a construção de modelos realmente adequados.

### c. "Às vezes com simples manipulações na base de dados (limpeza, conversão de valores, etc.) pode-se conseguir melhoras significativas nos resultados, sem fazer nenhuma alteração na técnica de aprendizado de máquina usada".

**A afirmação é verdadeira**, pois o processo de pré-processamento e preparação dos dados exerce impacto direto na performance de modelos de aprendizado de máquina. 

Operações aparentemente simples, como a limpeza de inconsistências, tratamento de valores ausentes, normalização de escalas ou codificação de atributos categóricos, podem alterar significativamente a distribuição dos dados de entrada, favorecendo o processo de convergência e melhorando as métricas de desempenho. 

Esse efeito ocorre mesmo sem modificações no algoritmo de aprendizado em si, demonstrando que a engenharia e a qualidade dos dados são elementos tão importantes quanto a escolha da técnica de modelagem.

## 6. Em uma empresa é adotado um método de Aprendizado de Máquina para detectar defeito de fabricação de peças mecânicas, sendo que raramente acontece este tipo de problema na fábrica. Um funcionário anuncia empolgado que o sistema alcançou uma acurácia de 99%, porém seu gerente não achou o resultado tão relevante. Responda:

### a. Por que o gerente não ficou empolgado com o resultado achado?

O gerente não se empolgou com a acurácia de 99% porque, apesar de o número parecer alto, ela não reflete o real desempenho do modelo em um cenário onde os defeitos são raros. 

Quando há um forte desbalanceamento entre as classes (ou seja, quase todas as peças são boas e poucas têm defeito), o modelo pode simplesmente classificar todas as peças como "sem defeito" e ainda assim alcançar alta acurácia. 

Por exemplo, se apenas 1% das peças apresenta defeito, um modelo que nunca detecta nenhum defeito ainda teria 99% de acerto, mas falharia totalmente em seu objetivo, que é identificar as peças defeituosas. 

Por isso, nesse tipo de problema, métricas alternativas como precisão (precision), revocação (recall), F1-score e matriz de confusão são muito mais informativas do que a acurácia isolada.

### b. O que o funcionário poderia fazer para confirmar se o método empregado é adequado para o problema?

O funcionário poderia verificar se o método é realmente adequado utilizando métricas específicas para classes desbalanceadas e aplicando técnicas de validação apropriadas. Algumas ações recomendadas seriam:

- **Analisar a matriz de confusão**, para verificar quantas peças defeituosas o modelo realmente identificou (verdadeiros positivos) e quantas ele deixou passar (falsos negativos).

- **Calcular precisão, recall e F1-score**, métricas que mostram o equilíbrio entre identificar corretamente os defeitos e evitar falsos alarmes.

- **Aplicar validação cruzada estratificada**, garantindo que as amostras de defeitos estejam proporcionalmente distribuídas nas divisões de treino e teste.

- **Testar técnicas de balanceamento de classes**, como oversampling (ex.: SMOTE) ou undersampling, para melhorar a capacidade do modelo em detectar defeitos raros.

- **Se possível, utilizar métodos de avaliação baseados em curva ROC e AUC**, que mostram o desempenho do modelo independentemente do limiar de decisão.

Essas análises ajudariam a determinar se o modelo realmente aprende a identificar defeitos ou apenas se beneficia do grande número de exemplos da classe majoritária.

## 7. Como pode ser usada uma árvore (de regressão ou de decisão) para avaliar uma amostra quando ela possui uma ou mais variáveis faltantes?

Quando uma amostra contém uma ou mais variáveis faltantes, uma árvore de decisão ou de regressão pode lidar com esses valores de diferentes formas, dependendo da implementação do algoritmo. 

Uma estratégia comum é o uso dos chamados **ramos substitutos** (surrogate splits). Nessa abordagem, a árvore identifica, durante o treinamento, variáveis alternativas que produzem divisões semelhantes à variável principal. Assim, quando um valor estiver ausente em uma amostra, o modelo utiliza o ramo substituto mais correlacionado para decidir o caminho de classificação ou de predição, mantendo a consistência do processo decisório.

Outra possibilidade é a **imputação de valores faltantes** antes da construção da árvore, utilizando médias, medianas ou métodos baseados em vizinhança (como k-NN imputation), permitindo que todas as amostras sejam avaliadas sem descarte de dados.

Em resumo, as árvores de decisão conseguem avaliar amostras incompletas por meio de ramos substitutos, imputação de dados ou mecanismos internos de aprendizado para lidar com ausência de valores, evitando perda de informações e preservando o desempenho do modelo.
