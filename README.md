# Teste Desenvolve
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

df = pd.read_csv('sales_data_sample.csv', encoding='latin1')

print(df.head())
print("\nShape:", df.shape)
print("\nColunas:", df.columns)
print("\nTipos de dados:", df.dtypes)

nomes = list(df['PRODUCTLINE'])
print("\nPrimeiros nomes de PRODUCTLINE:")
for nome in nomes[:5]:
    print(nome)

dicionario = dict(zip(df['PRODUCTLINE'][:3], df['CUSTOMERNAME'][:3]))
print("\nDicionário gerado:", dicionario)

linha0 = df.iloc[0]
tupla_info = (linha0['PRODUCTLINE'], linha0['CUSTOMERNAME'], linha0['PRICEEACH'])
print("\nTupla da primeira linha:", tupla_info)

valor = df['PRICEEACH'].iloc[0]
if valor > 100: 
    print("Valor muito alto")
elif valor > 50:
    print("Valor médio")
else:
    print("Valor baixo")

soma = 0
for n in df['PRICEEACH'][:5]:
 soma += n  
print("Soma dos primeiros valores:", soma)

i = 0
lista = list(df['PRICEEACH'][:5])
encontrado = False
while i < len(lista):
    if lista[i] > 90:
        print("Primeiro valor > 90:", lista[i])
        encontrado = True
        break
    i += 1
if not encontrado:
    print("Nenhum valor > 90 encontrado")

arr = np.array(df['QUANTITYORDERED'])
print("Array:", arr[:5])
arr_plus = arr + 10
arr_squared = arr ** 2
print("Array somado:", arr_plus[:5])
print("Array ao quadrado:", arr_squared[:5])
print("Soma:", np.sum(arr))
print("Média:", np.mean(arr))

filtro = df[df['QUANTITYORDERED'] > 40]
print("Vendas com mais de 40 unidades:")
print(filtro[['PRODUCTLINE', 'QUANTITYORDERED']].head())

print("Contagem por categoria:")
print(df['PRODUCTLINE'].value_counts())

agrupamento = df.groupby('PRODUCTLINE')['SALES'].sum()
print("Total de vendas por categoria:")
print(agrupamento)
