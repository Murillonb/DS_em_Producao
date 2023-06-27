# Previsão de Vendas de uma Empresa Farmacêutica
<img src='img/img_readme.jpg'/>

---
# 1.0. Descrição

A Rossmann é uma empresa com mais de 3.000 drogarias em 7 países europeus.<br>
Os gerentes de loja da empresa têm a tarefa de prever suas vendas diárias com até seis semanas de antecedência, 
e para realizar essa previsão, procuraram o time de data science. O CFO da Rossmann solicitou essa previsão aos gerentes e, 
com os resultados, a empresa planeja utilizar o valor na reforma de suas lojas.

# 2.0. Questões do negócio

Qual a previsão de vendas diária das lojas para as próximas 6 semanas?

# 3.0. Premissas

Premissas adotadas para execução deste projeto:

* Imóveis com ‘competition_distance’ igual a NA serão substituídas por 200.000, pois será assumido que não há competidores próximos;
* Imóveis com ‘competition_open_since_month’ igual a NA serão substituídas pelo mês de abertura da loja;
* Imóveis com ‘competition_open_since_year’ igual a NA serão substituídas pelo ano de abertura da loja;
* Imóveis com ‘promo2_since_week’ igual a NA serão substituídas pela data da compra como semana do início da promoção na loja;
* Imóveis com ‘promo2_since_year’ igual a NA serão substituídas pela data da compra como ano do início da promoção na loja;
* Imóveis com ‘promo_interval’ igual a NA serão substituídas por 0, pois será adotado que não há promoção ativa.
	
# 4.0. Planejamento da Solução

## 4.1. Produto Final

Entrega das previsões de vendas das lojas através do celular (Telegram).<br>

<a href="https://youtu.be/GJuR8vbGthY?feature=share4" target="_blank"><img src="https://img.shields.io/badge/YouTube-FF0000?style=for-the-badge&logo=youtube&logoColor=white"/></a>

## 4.2. Ferramentas

* Python 3.8.16
*	Jupyter Notebook
* VS Code

## 4.3. Processo de Solução

Passo 01 - Descrição dos Dados: ganho de conhecimento sobre os dados que serão utilizados;<br>
Passo 02 - Feature Engineering: criação de novas features;<br>
Passo 03 - Filtragem das variáveis: remoção de linhas e colunas que não contribuem com o fenômeno estudado;<br>
Passo 04 - Análise Exploratória dos Dados (EDA): criação de hipóteses e análise da correlação entre as variáveis;<br>
Passo 05 - Preparação dos Dados: enconde, transformação e redimensionamento dos dados para melhor performance do modelo de machine learning;<br>
Passo 06 - Seleção de Features (Boruta): filtro das variáveis com maior correlação com o fenômeno estudado;<br>
Passo 07 - Modelagem do Machine Learning: teste de diferentes modelos de machine learning;<br>
Passo 08 - Ajuste Fino dos Hiperparâmetros: ajuste dos hiperparâmetros do melhor modelo de machine learning;<br>
Passo 09 - Tradução e Interpretação dos Erros: transformação dos dados encontrados em conhecimento de negócio;<br>
Passo 10 - Subir Modelo para Produção: disponibilização do modelo para uso das pessoas responsáveis por tomar as decisões de negócio.
	
# 5.0. Top Insights

**Lojas com promoções ativas por mais tempo deveriam vender mais.**<br>
**FALSA**. Lojas com promoções ativas por mais tempo vendem menos após um certo período de tempo de promoção.

**Lojas com mais promoções consecutivas deveriam vender mais.**<br>
**FALSA**. Lojas com mais promoções consecutivas vendem menos.

**Lojas deveriam vender mais ao longo dos anos.**<br>
**FALSA**. As lojas estão vendendo menos ao longo dos anos.

**Lojas deveriam vender mais no segundo semestre do ano.**<br>
**VERDADEIRA**. As lojas vendem mais no segundo semestre do ano.


# 6.0. Modelos de ML utilizados

* Average Model;
* Linear Regression Model;
* Linear Regression Regularized Model - Lasso;
* Random Forest Regressor;
* XGBoost Regressor.

# 7.0. Performance dos modelos

Performance dos modelos sem cross-validation:
<table>
  <tr>
    <th>Modelo</th>
    <th>MAE</th>
    <th>MAPE</th>
    <th>RMSE</th>
  </tr>
  <tr>
    <td>Random Forest Regressor</td>
    <td>679.687799</td>
    <td>0.099937</td>
    <td>1010.607837</td>
  </tr>
  <tr>
    <td>Average Model</td>
    <td>1354.800353</td>
    <td>0.206400</td>
    <td>1835.135542</td>
  </tr>
  <tr>
    <td>Linear Regression</td>
    <td>1867.089774</td>
    <td>0.292694</td>
    <td>2671.049215</td>
  </tr>
  <tr>
    <td>Lasso Model</td>
    <td>1869.571858</td>
    <td>0.288111</td>
    <td>2694.005137</td>
  </tr>
  <tr>
    <td>XGBoost Regressor</td>
    <td>6683.276451</td>
    <td>0.949412</td>
    <td>7330.624439</td>
  </tr>
</table>

Performance dos modelos com cross-validation:
<table>
  <tr>
    <th>Modelo</th>
    <th>MAE CV</th>
    <th>MAPE CV</th>
    <th>RMSE CV</th>
  </tr>
  <tr>
    <td>Random Forest Regressor</td>
    <td>837.97+/-218.4</td>
    <td>0.12+/-0.02</td>
    <td>1256.45+/-318.73</td>
  </tr>
  <tr>
    <td>Linear Regression</td>
    <td>2081.73+/-295.63</td>
    <td>0.3+/-0.02</td>
    <td>2952.52+/-468.37</td>
  </tr>
  <tr>
    <td>Lasso Model</td>
    <td>2088.88+/-327.01</td>
    <td>0.3+/-0.01</td>    
    <td>2988.6+/-499.57</td>
  </tr>
  <tr>
    <td>XGBoost Regressor</td>
    <td>7049.26+/-588.69</td>
    <td>0.95+/-0.0</td>
    <td>7715.27+/-689.53</td>
  </tr>
</table>


O Average Model foi calculado através da média de vendas para cada loja, sendo utilizado de base para análise dos demais 
modelos.<br>
Após realizada a análise dos resultados encontrados percebemos que os modelos de regressão lineares não são ideais, pois 
mostraram que os dados não se comportam linearmente, apresentando erros maiores do que o do Average Model.<br>
Quanto aos modelos Random Forest e XGBoost, ambos utilizam árvores de decisão em sua implementação. E apesar do erro 
alto, neste primeiro ciclo CRISP iremos adotar o XGBoost como modelo de regressão para verificarmos se apresentará bons 
resultados.<br>

Através da técnica de random search, a qual testa o modelo com diferentes valores para cada hiperparâmetro com a intenção de 
encontrar a melhor combinação, foi feito os ajustes dos hiperparâmetros do algoritmo XGBoost.

Hiperparâmetros utilizados:
<table>
  <tr>
    <th>Hiperparâmetros</th>
    <th>Valores utilizados</th>
  </tr>
  <tr>
    <td>n_estimators</td>
    <td>3000</td>
  </tr>
  <tr>
    <td>eta</td>
    <td>0.03</td>
  </tr>
  <tr>
    <td>max_depth</td>
    <td>9</td>
  </tr>
  <tr>
    <td>subsample</td>
    <td>0.1</td>
  </tr>
  <tr>
    <td>colsample_bytree</td>
    <td>0.3</td>
  </tr>
  <tr>
    <td>min_child_weight</td>    
    <td>3</td>
  </tr>  
</table>

Obtendo assim uma melhor performance de generalização do modelo.
<table>
  <tr>
    <th>Modelo</th>
    <th>MAE</th>
    <th>MAPE</th>
    <th>RMSE</th>
  </tr>
  <tr>
    <td>XGBoost Regressor</td>
    <td>683.941775</td>
    <td>0.098911</td>
    <td>995.614786</td>
  </tr>
</table>

# 8.0. Resultados para o negócio

Com os valores de MAE e MAPE de cada loja, foi possível calcular o melhor e o pior cenário para cada estabelecimento, assim como verificar se a performance do modelo
foi boa para cada loja, separadamente.<br>
Com base nos valores da MAE, encontramos os resultados preditos das vendas de todas as lojas, com 06 semanas de antecedência, sendo o melhor e o pior cenário total:
<table>
  <tr>
    <th>Cenários</th>
    <th>Valores</th>
  </tr>
  <tr>
    <td>Predições</td>
    <td>$ 282,184,064.00</td>
  </tr>
  <tr>
    <td>Pior Cenário</td>
    <td>$ 281,417,670.62</td>
  </tr>
  <tr>
    <td>Melhor Cenário</td>
    <td>$ 282,950,489.49</td>
  </tr>
</table>

# 9.0. Conclusão
	
O algoritmo XGBoost não apresentou uma boa performance de aprendizagem no início, porém, após realizado os ajustes finos dos hiperparâmetros, conseguiu uma boa generalização na predição final.<br>
Com isso o objetivo foi alcançado, permitindo indicar o melhor e o pior cenário para cada loja. Possibilitando assim que o 
time de negócios tome as melhores decisões sobre as reformas a serem realizadas.<br>

Também foi disponibilizado o acesso às previsões de vendas das lojas através do Telegram, conforme mostrado no vídeo:<br>

<a href="https://youtu.be/GJuR8vbGthY?feature=share4" target="_blank"><img src="https://img.shields.io/badge/YouTube-FF0000?style=for-the-badge&logo=youtube&logoColor=white"/></a>

# 10.0. Próximos passos

Tratar as lojas com erro acima da média de forma separada, para fornecer a melhor predição possível.<br>
Testar o modelo com as demais colunas que não foram selecionadas pelo boruta para ver se melhora a performance.<br>
Verificar se há modos de melhorar o tratamento dos dados para tentar diminuir o erro e assim melhorar a performance 
do algoritmo.

----
Fontes:<br>
Imagem do Pexels (<a href="https://www.pexels.com/pt-br/foto/homem-com-camisa-xadrez-usando-smartphone-346734/">link</a>)<br>
Dados do Kaggle (<a href="https://www.kaggle.com/competitions/rossmann-store-sales/overview">link</a>).
