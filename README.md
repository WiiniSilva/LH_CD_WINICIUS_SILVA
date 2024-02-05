# LH_CD_WINICIUS_SILVA
 Desafio Processo Seletivo - Lighthouse Programa De Formação Em Dados (Remoto)



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

# carregar o modelo de um arquivo
with open('xgb_model.pkl', 'rb') as file:
  xgb_r = pickle.load(file)
```

2. Isso vai atribuir o seu modelo ao objeto xgb_r, que você pode usar para fazer previsões ou avaliações, como se ele fosse o mesmo objeto original.
 