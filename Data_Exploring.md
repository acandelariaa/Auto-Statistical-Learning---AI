# Exploración de Datos
## Introducción
La obesidad es uno de los retos sanitarios más urgentes en Latinoamérica, actuando como detonante de múltiples enfermedades crónicas más allá de la estética. Este reporte analiza datos reales de individuos de Colombia, Perú y México con un objetivo claro: identificar qué hábitos y factores biológicos determinan los distintos niveles de obesidad, para comprender sus causas subyacentes más allá de las cifras simples.

### Disclaimer
Como se mencionó anteriormente, vamos a utilizar herramientas de programación de Python + IA, más específicamente en Google Colab debido a su flexibilidad y facilidad de uso.

### Carga de Datos
> Python code

```python
# importar dataset y librerias necesarias
from google.colab import drive
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

df = pd.read_csv('/content/drive/MyDrive/Inteligencia Artificial I/A1.1 Obesidad.csv')
```
Vamos a cargar el dataset para ver cuánta información tenemos.

![Data Loading](Data_loading.png)

El conjunto de datos parece tener 2111 filas y 10 columnas, lo cual es un buen tamaño para un conjunto de datos. Ahora veamos con qué tipo de variables vamos a trabajar.

> Python code
```python
# ver el tipo de variable
df.dtypes
```

### Variables en el dataset y su tipo de datos
|Variable|Tipo de dato|
|--------|------------|
|Sexo	|object|
|Edad	|float64|
|Estatura	|float64|
|Peso|	float64|
|FamiliarConSobrepeso|	object|
|ComeMuchasCalorias|	object|
|ComeVegetales	|float64|
|Fumador	|object|
|ConsumoDeAgua|float64|
|NivelDeObesidad |object|


Como apreciamos, tenemos dos tipos de variables, “float64” y “Object”, variables que para efectos técnicos vamos a expresar como cuantitativas (números) y cualitativas (categorías) respectivamente.

# Aspectos Generales
A simple vista, el conjunto de datos parece bastante general y básico, nada específico; después de todo, solo contamos con diez variables. Además, algunas variables parecen ser subjetivas más que específicas, como *"ComeMuchasCalorias"*. Considerando el factor humano, necesitaríamos establecer un rango de cuántas calorías se consideran muchas y cuántas se consideran menos. En cualquier caso, también debemos considerar que la persona promedio en Colombia, México y Perú no puede responder a un rango específico de calorías; por lo tanto, parece apropiado tratar esta variable como una categoría en lugar de un número. Sin embargo, a modo de sugerencia, sería más específico usar categorías como *(Alto/Normal/Bajo).*

Otras variables también parecen ser muy subjetivas, como *"ComeVegetales"* y *"ConsumoDeAgua"*, ya que el conjunto de datos no especifica si las cifras de ambas variables tienen una unidad de medida. Por lo tanto, parece correcto tratarlas como un consumo relativo, pero sería muy útil que se especificaran las cifras como frecuencia semanal, litros, galones o cualquier otra unidad.

Ahora bien, si hablamos de niveles de obesidad, podemos centrarnos en esa variable, que parece categórica. Para ver cuántas personas tienen diferentes niveles de obesidad, vamos a graficar los datos para ver la distribución.

> Python code

```python
conteo = df["NivelDeObesidad"].value_counts()
total = conteo.sum()

plt.figure()
plt.bar(conteo.index, conteo.values)

for i, valor in enumerate(conteo.values):
    porcentaje = valor / total * 100
    plt.text(i, valor, f"{porcentaje:.1f}%",
             ha="center", va="bottom")

plt.xlabel("Tipo de obesidad")
plt.ylabel("Número de personas")
plt.title("Distribución de personas por tipo de obesidad")
plt.xticks(rotation=90)
plt.show()
```

![Obesity distribution](Obesity_levels_categories.png)
> Distribución Porcentual de Niveles de Obesidad

Según el gráfico, los niveles de obesidad parecen estar bastante bien distribuidos entre sus diferentes categorías, siendo la obesidad tipo 1 la más común entre los datos.

Ahora, instintivamente, debe haber una tendencia de obesidad según el género, exploremos la distribución en función del género para ver si los hombres o las mujeres tienden a estar en una categoría específica de obesidad, veamos si lo anterior va por buen camino.

![Obesity genre](Obesity_type_genre.png)
> Tipo de Obesidad Por genero

Al observar el gráfico con atención, se observa un patrón sorprendente en los niveles de obesidad severa: el tipo II está dominado por hombres, mientras que el tipo III es casi exclusivamente femenino. En cambio, las demás categorías de peso muestran una distribución mucho más equilibrada entre sexos.
