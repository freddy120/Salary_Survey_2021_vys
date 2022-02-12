
## Ask A Manager Salary Survey 2021
Este proyecto forma parte del curso de Visualización y storytelling de la Maestría en Inteligencia Analítica de Datos MIAD

Elaborado por: [Freddy Mendoza](about.md)


### Recursos:
* Jupyter notebook del modelado de datos [notebook](https://github.com/freddy120/Salary_Survey_2021_vys/blob/main/Ask_A_Manager_Salary_Survey_2021.ipynb) [![Foo](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/freddy120/Salary_Survey_2021_vys-/blob/main/Ask_A_Manager_Salary_Survey_2021.ipynb)
* Datos de salarios [dataset](https://docs.google.com/spreadsheets/d/1IPS5dBSGtwYVbjsfbaMCYIWnOuRmJcbequohNxCyGVw/edit?resourcekey#gid=1625408792)
* Dashboard en google data studio [dashboard](https://)


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






