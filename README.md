# Projeto: Análise de Vendas de Games (PS4)

###### Utilizando o dataset de vendas de jogos do Playstation 4 obtido no Kaggle ([link](https://www.kaggle.com/datasets/sidtwr/videogames-sales-dataset/download?datasetVersionNumber=1 "link")), foi demonstrado, por meio das libs, *pandas, matplotlib e seaborn*  e o volume de vendas dos principais jogos do mercado, além de ser realizado todo o tratamento de dados para obtenção dos melhores resultados.

###### Cabeçalho do Dataset
```python
database.head()
```
[![](https://i.imgur.com/9c58fRl.png)](https://i.imgur.com/9c58fRl.png)

###### Removendo valores nulos
```python
database.dropna(inplace = True)
database.head()
```
[![](https://i.imgur.com/6GGpMPQ.png)](https://i.imgur.com/6GGpMPQ.png)

###### Analisando a distribuição global de vendas por ano
```python
# Tamanho do gráfico
plt.figure( figsize=(10, 4) )
# Título
plt.title('Análise da distribuição Global (mi)')
# Plot
sns.boxplot( data=database, x='Year', y='Global');
```
[![](https://i.imgur.com/ImnDC7q.png)](https://i.imgur.com/ImnDC7q.png)

**OBS**: Temos alguns outliers causando variação entre as vendas dos jogos.

###### Realizando a limpeza dos anos 2019 e 2020

```python
# Removendo anos 2019 e 2020 e redefinindo índices
Analise = database.drop(database[database['Year'] >= 2019].index, inplace=True)

Analise = database.groupby( by=['Year'] ).sum().reset_index()

# analisando a proporção dos 100% de cada continemente comparado ao Total
America = [ America / Total * 100 for America, Total in zip( Analise['North America'], Analise['Global'] ) ]
Europa = [ Europa / Total * 100 for Europa, Total in zip( Analise['Europe'], Analise['Global'] ) ]
Japao = [ Japao / Total * 100 for Japao, Total in zip( Analise['Japan'], Analise['Global'] ) ]
Mundo = [ Mundo / Total * 100 for Mundo, Total in zip( Analise['Rest of World'], Analise['Global'] ) ]

# Exibindo valores
America, Europa, Japao, Mundo
```
##### Resultado da Análise de Dados
[![](https://i.imgur.com/AKwvg4z.png)](https://i.imgur.com/AKwvg4z.png)












