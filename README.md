# LH_CD_WINICIUS_SILVA
 Desafio Processo Seletivo - Lighthouse Programa De Formação Em Dados (Remoto)

# Entregas

2.	Responda também às seguintes perguntas:
    a.	Supondo que uma pessoa esteja pensando em investir em um apartamento para alugar na plataforma, onde seria mais indicada a compra?


*	O local mais indicado para alugar um imóvel em Nova York é Manhattan, por dois motivos. O primeiro é que esse é o bairro mais procurado da cidade, com cerca de 21.661 locações disponíveis. O segundo é que esse é o bairro com o maior preço médio de locação, em torno de 196,88 dólares, muito acima da média dos outros bairros, mais desejado e disputado de imóveis.


    b.	O número mínimo de noites e a disponibilidade ao longo do ano interferem no preço?


Sim, o número mínimo de noites e a disponibilidade ao longo do ano interferem no preço dos imóveis em Nova York. Os gráficos mostram que:


*	Existe uma relação positiva entre o número mínimo de noites e o preço por noite dos imóveis. Quanto maior o número mínimo de noites, maior o preço por noite. Isso pode ser explicado por fatores como oferta, demanda, custos fixos e descontos. Por exemplo, os proprietários podem cobrar mais por noite para compensar a menor ocupação ou oferecer descontos para estadias mais longas.


*	Há uma grande variação nos preços por noite para cada categoria do número mínimo de noites. Os preços por noite variam de 10 a 10.000 dólares, dependendo da categoria. Isso pode refletir as diferentes características, localizações e qualidades dos imóveis disponíveis. Por exemplo, os imóveis mais caros podem ser mais espaçosos, confortáveis e bem localizados do que os mais baratos.


*	O preço médio por noite aumenta com o aumento do número de meses que o anúncio está disponível, exceto no 10º mês. O preço médio por noite varia de 136,64 dólares no primeiro mês a 197,64 dólares no 12º mês, com uma queda para 184,77 dólares no 10º mês. Isso pode indicar que os proprietários ajustam os seus preços de acordo com a sazonalidade e a demanda. Por exemplo, os preços podem ser mais altos nos meses de verão e de inverno, quando há mais turistas na cidade, e mais baixos no 10º mês, que corresponde a outubro, quando há menos procura.


    c.	Existe algum padrão no texto do nome do local para lugares de mais alto valor?


Sim, existe. Como você podemos ver no gráfico gerado no código presente no jupyter notebook, os locais com certos padrões de nome, como ‘NearWilliamsburg’, ‘Film’ ou ‘Fulton’, têm preços médios mais altos do que outros, como ‘Carol’ ou ‘SuperBowl’. Esses padrões de nome podem indicar locais mais sofisticados ou de qualidade superior, que levam a preços mais elevados.


3.	Explique como você faria a previsão do preço a partir dos dados. Quais variáveis e/ou suas transformações você utilizou e por quê? Qual tipo de problema estamos resolvendo (regressão, classificação)? Qual modelo melhor se aproxima dos dados e quais seus prós e contras? Qual medida de performance do modelo foi escolhida e por quê?


*	Para prever o preço dos imóveis, eu fiz um pré-processamento dos dados, removendo ou agrupando as colunas que não eram importantes ou que tinham muita variação. Por exemplo, eu removi o nome do anúncio, o id do anfitrião, id, host_name e bairro.Também removi os valores muito altos ou muito baixos que podiam distorcer o modelo, como os preços acima de 400 dólares, que eram outliers frequentes nos preços dos alugueis.


*	Depois, eu selecionei as variáveis que tinham mais relação com o preço, usando a matriz de correlação. Eu também transformei as variáveis categóricas em numéricas, usando o LabelEncoder e criando variáveis dummy com o hot encoder.


*	Em seguida, eu testei quatro modelos de regressão diferentes: Regressão Linear Múltipla, XGBoost, Regressão com Random Forest e Regressão com Vetores de Suporte. A regressão é um tipo de problema que tenta prever um valor contínuo, como o preço, a partir de outras variáveis.


*	Para escolher o melhor modelo, eu usei o MAPE que calcula a média dos erros percentuais entre os valores reais e previstos de um modelo de regressão, o coeficiente de determinação (R²), que mede o quanto o modelo consegue explicar a variação do preço, e o erro quadrático médio (MSE) e o erro quadrático médio raiz (RMSE), que medem o quanto o modelo erra nas previsões.


*	Dos modelos de regressão testados, os que obteve o melhores resultados foram o Random Forest, que usa várias árvores de decisão para fazer as previsões. Esse modelo teve um MAPE de 28.54%, um R² de 0.55, um MSE de 2797.53 e um RMSE de 52.91. O modelo XGBoost, que também é baseado em árvores de decisão e que utiliza uma técnica chamada de gradient boosting, teve um MAPE de 28.66%, um R² de 0.55, um MSE de 2788.53 e um RMSE de 52.81. Ambos os modelos tiveram resultados semelhantes, sendo considerados um empate técnico, mas eu escolhi usar o XGBoost por ter um tempo menor de treinamento.


*	Observando os gráficos de dispersão entre os valores reais e os valores previstos, notei que ambos os modelos tinham uma concentração nos valores mais baixos e uma dispersão nos valores mais altos. Isso significa que eles funcionavam melhor para previsões de valores mais baixos, mas pioravam para valores mais altos.


*	Em conclusão, o XGBoost e Random Forest são bons modelos para prever o preço dos imóveis em Nova York, mas ainda tinha espaço para melhoria, especialmente para previsões de valores mais altos.


* Prós do modelo XGBoost:
    * Altamente flexível, pois permite ajustar vários parâmetros e
      funções de perda para diferentes problemas de regressão,
      classificação ou ranking.

      * Usa o poder do processamento paralelo, o que torna o
        treinamento e a inferência mais rápidos e eficientes.

      * Suporta regularização, que é uma técnica para reduzir o
        sobreajuste e melhorar a generalização do modelo.

      * Tem uma implementação escalável e de alta performance, que
        pode lidar com grandes e complexos conjuntos de dados.

* Contras do modelo XGBoost:
      * É mais complexo do que outros modelos de regressão, pois requer
        mais ajustes de parâmetros e mais cuidado com a escolha da
        função de perda e da taxa de aprendizado.

      * Pode sofrer de sobreajuste, especialmente se o número de árvores
        for muito alto ou se os dados forem ruidosos ou esparsos.

      * Usa mais memória do que o outros modelos menos complexos,
        pois armazena todas as árvores na memória durante o
        treinamento e a inferência.

      * É menos transparente do que modelos como Decision tree e
        random forest, pois é mais difícil interpretar o significado e a
        importância das árvores individuais e dos seus nós.

*	Todos os passos descritos acima estão melhores explicados no Jupyter notebook enviado.


4.	Supondo um apartamento com as seguintes características:

{'id': 2595,
 'nome': 'Skylit Midtown Castle',
 'host_id': 2845,
 'host_name': 'Jennifer',
 'bairro_group': 'Manhattan',
 'bairro': 'Midtown',
 'latitude': 40.75362,
 'longitude': -73.98377,
 'room_type': 'Entire home/apt',
 'price': 225,
 'minimo_noites': 1,
 'numero_de_reviews': 45,
 'ultima_review': '2019-05-21',
 'reviews_por_mes': 0.38,
 'calculado_host_listings_count': 2,
 'disponibilidade_365': 355}

Qual seria a sua sugestão de preço?

O valor real era de 225 e o modelo previu 209.18396. Isso significa que o seu modelo teve um erro de 17.81604.


## Como Executar o Projeto

1. Clone o repositório:
```
git clone https://github.com/WiiniSilva/LH_CD_WINICIUS_SILVA.git
```

2. Instale as dependências necessárias (recomenda-se utilizar um ambiente virtual):

3. Execute os Jupyter Notebooks para visualizar as análises e resultados.

## Como usar o arquivo .pkl

1. Você pode usar esse arquivo para carregar o modelo em outro código, usando o seguinte código:
```
# importar a biblioteca pickle
import pickle

# carregar o modelo pkl
with open('xgb_model.pkl', 'rb') as file:
  xgb_r = pickle.load(file)
```

2. Isso vai atribuir o seu modelo ao objeto xgb_r, que você pode usar para fazer previsões ou avaliações, como se ele fosse o mesmo objeto original.
 