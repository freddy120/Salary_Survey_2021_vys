
## Ask A Manager Salary Survey 2021
Este proyecto forma parte del curso de Visualización y storytelling de la Maestría en Inteligencia Analítica de Datos MIAD

Elaborado por: [Freddy Mendoza](about.md)


### Recursos:
* Jupyter notebook del modelado de datos [notebook](https://github.com/freddy120/Salary_Survey_2021_vys/blob/main/Ask_A_Manager_Salary_Survey_2021.ipynb) [![Foo](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/freddy120/Salary_Survey_2021_vys-/blob/main/Ask_A_Manager_Salary_Survey_2021.ipynb)
* Datos de salarios [dataset](https://docs.google.com/spreadsheets/d/1IPS5dBSGtwYVbjsfbaMCYIWnOuRmJcbequohNxCyGVw/edit?resourcekey#gid=1625408792)
* Dashboard en google data studio [dashboard](https://)

### Modelado

#### Variables de la fuente de datos:

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
| Years of experience in field             | texto          | años de experiencia en su campo

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

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

```
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
```






