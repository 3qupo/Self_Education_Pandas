# Работа 2

# Задание 1. Продолжаем работу с dataframe. Для этого импортируем библиотеки для работы с dataset и сделаем настройки отображения данных
# Задание 2. Импортируем библиотеки numpy, pandas, matplotlib
import csv
import numpy as np
import pandas as pd
import matplotlib
import matplotlib.pyplot as plt
import matplotlib.ticker
import seaborn as sns

# Сделаем настройки отображения данных
pd.set_option('display.expand_frame_repr', False) # Предотвратим перенос строк внутри столбцов
pd.set_option('display.colheader_justify', 'center') # Сделаем выравнивание заголовков столбцов по центру

df = pd.read_csv('zoo.csv', delimiter=',')
# Задание 3. Найдём пропущенные значения и дубликаты

print("Количество пропущенных значений:")
for column in df.columns.values.tolist(): # Поиск количества пропущенных значений в каждом столбце
    print(column)
    print(df[column].value_counts())

print("Количество пропущенных значений в каждой колонке (1): ", df.isnull().sum())
print("Количество пропущенных значений в каждой колонке (2): ", df.isna().sum())

# Проверим на дубликаты
print("Количество дубликатов: ", df.duplicated().sum())

unique_values = df['animal'].unique()
print("Уникальные значения столбца\n", unique_values)

counts_value = df['animal'].value_counts()
print("Количество каждого значения в столбце:\n", counts_value)

count_exists_yes = len(df[df['animal'] == 'zebra'])
total_count = len(df)
fraction_exists = count_exists_yes / total_count
print("Доля значений, которые есть в столбце 'animal':", fraction_exists)

count_exists_not = len(df[df['animal'] == 'noname'])
total_count = len(df)
fraction_exists = count_exists_not / total_count
print("Доля значений, которых нет в столбце 'animal':", fraction_exists)

mean2 = df['animal'].str.contains('tiger').mean()
print(mean2.round(2))

# Отфильтруем данные в алфавитном порядке
filter_df = df.sort_values(by='animal')
print(filter_df)

# Посчитаем необходимое количество воды для каждого животного и покажем это на графике
sum_water_need = df.groupby('animal')['water_need'].sum()
print(sum_water_need)

# Отобразим полученные значения на графике
# Создать из этих значений круговую диаграмму.
fig, ax = plt.subplots()
ax.pie(sum_water_need)
ax.set_title("Water for animal")
ax.pie(sum_water_need,
       labels = df['animal'].unique(),
       autopct = '%1.1f%%',
       shadow = True,
       startangle=190)

# Показать круговую диаграмму.
plt.show()

# Создадим столбчатую диаграмму для показа количества животных
animals = df['animal'].unique()
animal_count = df.groupby('animal').size()
print(animal_count)

plt.bar(animals,
        animal_count,
        color='chartreuse',
        edgecolor='darkblue',
        linewidth=7)

plt.title("Количество животных",
          fontsize=20) # Заголовок
plt.xlabel("Имя животного") # Подпись оси Х
plt.ylabel("Количество") # Подпись оси Y

plt.show()
