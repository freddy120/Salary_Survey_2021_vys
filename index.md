
## Encuesta de Salario 2021
Este proyecto forma parte del curso de Visualización y storytelling de la Maestría en Inteligencia Analítica de Datos MIAD

Elaborado por: [Freddy Mendoza](about.md)


### Recursos:
* Jupyter notebook del modelado de datos [notebook](https://github.com/freddy120/Salary_Survey_2021_vys/blob/main/Ask_A_Manager_Salary_Survey_2021.ipynb) [![Foo](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/freddy120/Salary_Survey_2021_vys-/blob/main/Ask_A_Manager_Salary_Survey_2021.ipynb)
* Datos de salarios [dataset](https://docs.google.com/spreadsheets/d/1IPS5dBSGtwYVbjsfbaMCYIWnOuRmJcbequohNxCyGVw/edit?resourcekey#gid=1625408792)
* Dashboard en google data studio [dashboard](https://datastudio.google.com/reporting/c5b2c862-0ce9-4b05-9fe3-7027ceb9c09b)


#### Variables de la fuente de datos original:

| Nombre                                   | Tipo de dato   | Descripción                                             |
| ---------------------------------------- | -------------- | ------------------------------------------------------- |
| Timestamp                                | texto/datetime | fecha y hora de la respuesta a la encuesta              |
| How old are you?                         | texto          | rango de edad del encuestado                            |
| Industry                                 | texto          | industria en la que trabaja                             |
| Job title                                | texto          | título profesional que desempeña                        |
| Additional context on job title          | texto          | información adicional del título profesional            |
| Annual salary                            | número         | salario anual                                           |
| Other monetary comp                      | número         | compensación monetaria adicional                        |
| Currency                                 | texto          | moneda del salario                                      |
| Currency - other                         | texto          | otro tipo de moneda no incluida en la variable Currency |
| Additional context on income             | texto          | información adicional sobre sus ingresos                |
| Country                                  | texto          | país donde trabaja                                      |
| State                                    | texto          | si trabaja en USA, en qué estado trabaja                |
| City                                     | texto          | ciudad donde trabaja                                    |
| Overall years of professional experience | texto          | años de experiencia profesional total                   |
| Years of experience in field             | texto          | años de experiencia en su campo                         |
| Highest level of education completed     | texto          | nivel más alto de educación                             |
| Gender                                   | texto          | genero del encuestado                                   |
| Race                                     | texto          | raza del encuestado                                     |

#### Variables luego del procesamiento:

| Nombre                                   | Tipo de dato   | Descripción                                                                      |
| ---------------------------------------- | -------------- | -------------------------------------------------------------------------------- |
| Timestamp                                | texto/datetime | fecha y hora de la respuesta a la encuesta                                       |
| How old are you?                         | texto          | rango de edad del encuestado                                                     |
| Industry                                 | texto          | industria en la que trabaja                                                      |
| Job title                                | texto          | título profesional que desempeña                                                 |
| Additional context on job title          | texto          | información adicional del título profesional                                     |
| Annual salary                            | número         | salario anual                                                                    |
| Other monetary comp                      | número         | compensación monetaria adicional                                                 |
| Currency                                 | texto          | moneda del salario                                                               |
| Currency - other                         | texto          | otro tipo de moneda no incluida en la variable Currency                          |
| Additional context on income             | texto          | información adicional sobre sus ingresos                                         |
| Country                                  | texto          | país donde trabaja                                                               |
| State                                    | texto          | sí trabaja en USA, en qué estado trabaja                                         |
| City                                     | texto          | ciudad donde trabaja                                                             |
| Overall years of professional experience | texto          | años de experiencia profesional total                                            |
| Years of experience in field             | texto          | años de experiencia en su campo                                                  |
| Highest level of education completed     | texto          | nivel más alto de educación                                                      |
| Gender                                   | texto          | genero del encuestado                                                            |
| Race                                     | texto          | raza del encuestado                                                              |
| Country\_clean                           | texto          | país donde trabaja, luego de la limpieza y estandarización                       |
| City\_clean                              | texto          | ciudad donde trabaja, luego de la limpieza y estandarización                     |
| salario\_anual                           | número         | salario anual en pesos colombianos al tipo de cambio 12/02/2022                  |
| compensaciones                           | número         | compensaciones en pesos colombianos al tipo de cambio 12/02/2022                 |
| salario\_total                           | número         | suma de salario anual mas las compensaciones, ingreso total en pesos colombianos |

### Modelado

•	Se descarga la basa de datos en formato csv del enlace.
•	Se usa jupyter notebook para hacer el modelado, se puede usar colab para abrirlo.
•	Se carga el archivo 'Ask A Manager Salary Survey 2021 (Responses) - Form Responses 1.csv’ en la ubicación del notebook para poder cargarlo con pandas.
```python
df = pd.read_csv('Ask A Manager Salary Survey 2021 (Responses) - Form Responses 1.csv', thousands=',')
df.head()
```
•	Para la estandarización de la variable Country se usa el paquete dataprep que tiene una función clean_country en base a expresiones regulares para estandarizar el nombre de los países, como existen nombres que no son resueltos por esta función, entonces previamente se realiza una traducción manual usando un diccionario con solo los textos faltantes. El diccionario esta declarado en el jupyter notebook.

```python

# limpieza manual
country_dict = {'UK': 'U.K.', 'Scotland ': 'U.K.', 'England': 'U.K.', 'England ': 'U.K.', 'Scotland': 'U.K.', 'Uk': 'U.K.', 'England/UK': 'U.K.',
                'U.S>': 'USA', 'ISA': 'USA', 'United State': 'USA', 'America': 'USA', 'United State of America': 'USA', 'United Statws': 'USA', 'U.S': 'USA',
                'Unites States': 'USA', 'U. S. ': 'USA', 'United Sates': 'USA', 'Uniited States': 'USA', 'United Sates of America': 'USA',  'Unted States': 'USA',
                'United Stattes': 'USA', 'United Statea': 'USA', 'United Statea': 'USA', 'Unites States': 'USA', 'United Statees': 'USA', 'Uniyed states': 'USA', 
                'Uniyes States': 'USA', 'U.A.': 'USA', 'U. S.': 'USA', ' US of A': 'USA', 'United Kindom': 'U.K.', 'United Status': 'USA', 'Uniteed States': 'USA',
                'United Stares': 'USA', 'United Stares': 'USA', 'Unites states ': 'USA', 'The US': 'USA', 'UnitedStates': 'USA', 'United statew': 'USA',
                'United Statues': 'USA', 'United Statues': 'USA', 'Untied States': 'USA',  'Unitied States': 'USA', ' United Sttes': 'USA',
                'united stated': 'USA', ' Uniter Statez': 'USA', 'U. S ': 'USA', 'United Stateds': 'USA', 'Unitef Stated': 'USA',
                'United Stares ': 'USA', 'USaa': 'USA', 'america': 'USA', 'United Statss': 'USA', 'United  States': 'USA'}
df = df.replace({"Country": country_dict})



from dataprep.clean import clean_country
# clean country with dataprep
df = clean_country(df, 'Country')


# drop nan, unable to parse
df = df.dropna(subset=['Country_clean'])
```

Para actualizarlo debemos primero pasar la columna Country por la función clean_country y solo agregar al diccionario las expresiones que no son posibles de traducir. Esto nos ayuda a traducir manualmente pocos registros. Por último, quedan pocos registros que no pudieron ser estandarizados, pero como son menos del 1%, se opta por eliminarlos. Al terminar este procedimiento se crear una nueva variable Country_clean con los países estandarizados.

•	La estandarización de las ciudades es mas complicada, porque existen muchas más formas de describir una ciudad y además existen muchas más ciudades que países, en este trabajo hacemos el intento usando el paquete fuzzywuzzy que nos da una métrica de similitud entre textos, de esta manera disminuimos la cantidad de países únicos en aproximadamente 1500. Al terminar este procedimiento se crea una nueva variable City_clean con las ciudades estandarizadas.

```python
from fuzzywuzzy import process, fuzz

unique_city = df['City'].unique().tolist()
sorted(unique_city)[100:150]


for index, row in df.iterrows():
  c = high_score_sort[high_score_sort['match_sort'] == row['City']]
  if c.empty == False:
    df.loc[index, 'City_clean'] = c.iloc[0]['city_sort']
  else:
    df.loc[index, 'City_clean'] = row['City']
    
```
 
•	Se realiza la conversión de salario anual y compensaciones usando un diccionario con los tipos de cambio a la fecha 12/02/2022 sacados de https://www.xe.com/currencyconverter/.
Se crean las columnas salario_anual, compensaciones y salario_total
 
```python
# tipo de cambio obtenido el 12/02/2022 por https://www.xe.com/currencyconverter/
currency_dict = {'USD': 3929.82, 'GBP': 5330.46, 'CAD': 3088.08,'EUR': 4458.60, 'AUD/NZD': 2802.91, 'Other':3929.82, 'CHF': 4246.39, 
                 'ZAR': 258.12, 'SEK': 420.81, 'HKD': 503.79, 'JPY': 34.01}
                 
# convertir a pesos colombianos
df['salario_anual'] = df.apply(lambda row: row['Annual salary']*currency_dict[row['Currency']], axis=1)
df['compensaciones'] = df.apply(lambda row: row['Other monetary comp']*currency_dict[row['Currency']], axis=1)
df['salario_total'] = df.apply(lambda row:  row['salario_anual'] + row['compensaciones'] if ~np.isnan(row['compensaciones']) else row['salario_anual'], axis=1)
```


•	Por ultimo se crea un nuevo xlsx después de ejecutar todo el jupyter notebook, el cual utilizaremos para crear el dashboard.

```python
df.to_excel('Salary_survey_2021_procesado.xlsx',  index=False)
```






