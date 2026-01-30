# desigualdade-crescimento-gmm
Estudo Empírico doo comportamento relacional entre crescimento econômico e a desigualdade de distribuição de renda, tendo como base a implementação do Generalized Method of Moments (GMM), proposto por Arellano e Bond (1991) e utilizando a ferramenta computacional pacote R pdynmc, desenvolvida por Fritsch, Pua e Schnurbus (2021).
# Método Generalizado dos Momentos (GMM)
O Método Generalizado dos Momentos (GMM) é uma técnica estatística utilizada para estimar parâmetros em modelos econométricos. É um método de estimativa flexível que pode ser usado em uma variedade de configurações, incluindo modelos de dados em painel. O estimador GMM explora de forma ótima todas as restrições de momento linear que seguem da suposição de nenhuma correlação serial nos erros, em uma equação que contém efeitos individuais, variáveis dependentes defasadas e não variáveis estritamente exógenas. O estimador GMM oferece ganhos de eficiência significativos em comparação com alternativas mais simples de variáveis instrumentais (IV) e produz estimativas bem determinadas em modelos de dados em painel dinâmico (ARELLANO e BOND, 1991).
# Variáveis
A variável dependente foi a taxa de crescimento do PIB total (cresc) e o vetor de variáveis explicativas contém as seguintes variáveis: população (pop), número de pessoas empregadas (emp), estoque de capital (rnna), consumo das famílias (csh_c), consumo do governo (csh_g) e PIB real do lado da despesa (pib_d) e o índice de desigualdade de renda (gini). Assim, o modelo base, sem especificidade, neste trabalho, pode ser representado da seguinte forma:
	cresc=β_1+β_2  pop+ β_3  emp+β_4  rnna+ β_5  csh"_c"+ β_6  csh"_g"+ β_7  pib"_d"+ β_8  gini+ε	Eq. 1
Onde β_1  "," ⋯,β_8 são os coeficientes de regressão e ε é o termo de erro.
A estimativa da relação entre desigualdade e crescimento pode ser enviesada por simultaneidade, variáveis omitidas e erro de medida, uma vez que a heterogeneidade é pertinente por tratar-se de dados de diferentes países. Para uma estimativa consistente procura-se eliminar ou, ao menos, mitigar os efeitos não observados através de modelos de efeitos fixos (EF) e efeitos aleatórios (EA). Entretanto, devido à característica de painel dinâmico, as estimativas de EF e EA podem ser tendenciosas e inconsistente. Outra possível implementação de estimativa do modelo (Eq. 1) seria o método de variáveis instrumentais (VI), porém, encontrar instrumentos válidos não é simples. Dado o contexto cross-country, o Método Generalizado dos Momentos (GMM) seja capaz de ser mais adequado (NAGUIB, 2017).
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
