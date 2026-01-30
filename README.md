# desigualdade-crescimento-gmm
Estudo Empírico doo comportamento relacional entre crescimento econômico e a desigualdade de distribuição de renda, tendo como base a implementação do Generalized Method of Moments (GMM), proposto por Arellano e Bond (1991) e utilizando a ferramenta computacional pacote R pdynmc, desenvolvida por Fritsch, Pua e Schnurbus (2021).
# Método Generalizado dos Momentos (GMM)
O Método Generalizado dos Momentos (GMM) é uma técnica estatística utilizada para estimar parâmetros em modelos econométricos. É um método de estimativa flexível que pode ser usado em uma variedade de configurações, incluindo modelos de dados em painel. O estimador GMM explora de forma ótima todas as restrições de momento linear que seguem da suposição de nenhuma correlação serial nos erros, em uma equação que contém efeitos individuais, variáveis dependentes defasadas e não variáveis estritamente exógenas. O estimador GMM oferece ganhos de eficiência significativos em comparação com alternativas mais simples de variáveis instrumentais (IV) e produz estimativas bem determinadas em modelos de dados em painel dinâmico (ARELLANO e BOND, 1991).
# Modelo Econométrico
# Modelo Econométrico

A variável dependente utilizada foi a **taxa de crescimento do PIB total** (`cresc`).  
O vetor de variáveis explicativas contém:

- **pop** – população  
- **emp** – número de pessoas empregadas  
- **rnna** – estoque de capital  
- **csh_c** – consumo das famílias  
- **csh_g** – consumo do governo  
- **pib_d** – PIB real pelo lado da despesa  
- **gini** – índice de desigualdade de renda  

## Especificação do Modelo

O modelo base, sem especificidade, pode ser representado da seguinte forma:

$$
\text{cresc} = \beta_1 
+ \beta_2 \,\text{pop}
+ \beta_3 \,\text{emp}
+ \beta_4 \,\text{rnna}
+ \beta_5 \,\text{csh\_c}
+ \beta_6 \,\text{csh\_g}
+ \beta_7 \,\text{pib\_d}
+ \beta_8 \,\text{gini}
+ \varepsilon
$$

**Eq. 1**

Onde $\beta_1, \ldots, \beta_8$ são os coeficientes de regressão e $\varepsilon$ é o termo de erro.

## Possíveis Fontes de Viés

A estimativa da relação entre desigualdade e crescimento pode ser enviesada devido a:

- **Simultaneidade**  
- **Variáveis omitidas**  
- **Erro de medida**

Esses problemas são especialmente relevantes em dados **cross-country**, dada a heterogeneidade entre países.

## Métodos de Estimação

Para mitigar efeitos não observados, utilizam-se:

- **Modelos de Efeitos Fixos (EF)**
- **Modelos de Efeitos Aleatórios (EA)**

Entretanto, em painéis dinâmicos, EF e EA podem gerar estimativas **tendenciosas e inconsistentes**.

Outra alternativa seria o uso de **Variáveis Instrumentais (VI)**, embora encontrar instrumentos válidos seja desafiador.

Dado o contexto internacional, o **Método Generalizado dos Momentos (GMM)** tende a ser mais adequado (NAGUIB, 2017).

# Modelo de dados em painel dinâmico linear
Em particular, um modelo de dados em painel dinâmico linear é dado da seguinte forma (FRITSCH, PUA e SCHNURBUS, 2021):
	y_(i,t)=αy_(i,t-1)+βx_(i,t)+u_(i,t)
u_(i,t)=η_i+ε_(i,t)
i=1,⋯,n                 t=2,⋯,T
Eq. 2
onde  y_(i,t) e y_(i,t-1) são a variável dependente e seu atraso (lag), α é o parâmetro de atraso e x_(i,t) representa a variável explicativa com β sendo seu coeficiente de inclinação. Esse modelo permite um termo de erro composto, u_(i,t), que pode ser desmembrado em um termo não observado de efeito individual específico (η_i ) e um componente idiossincrático 〖(ε〗_(i,t)). A partir do modelo descrito pela Eq. 2, a especificidade do modelo do presente trabalho é:
	〖cresc〗_(i,t)=α〖cresc〗_(i,t-1)+β_1 pop+ β_2 emp+β_3 rnna+ β_4 csh"_c"+ β_5 csh"_g"+ β_6 pib"_d"+ β_7 gini+u_(i,t)
u_(i,t)=η_i+ε_(i,t)
i=1,⋯,n                 t=2,⋯,T
Eq. 3
Como trata-se de um modelo de painel dinâmico com variáveis explicativas predeterminadas, mas não estritamente exógenas. Implementa-se o Método Generalizado dos Momentos - Diferença (GMM-Dif) de Arellano e Bond (1991). O GMM-Dif pode ser representado matematicamente por:
	y_it-y_(i,t-1)=β(X_it-X_(i,t-1) )+u_it
Eq. 4
onde y_it representa a variável dependente, X_it representa um conjunto de variável explicativas, β é o vetor de parâmetros do modelo, u_it é o termo de erro não observado no período t do país i, (y_it-y_(i,t-1) ) e (X_it-X_(i,t-1) ) representa o efeito diferença. O método de GMM-Dif utiliza defasagens de variáveis contidas no modelo com variáveis instrumentais para controlar o efeito de endogeneidade.
