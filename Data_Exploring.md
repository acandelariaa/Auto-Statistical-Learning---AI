# Exploración de Datos
En primer lugar, debemos entender la naturaleza del dataset, necesitamos saber cosas como, cuántos datos están disponibles en el conjunto de datos, con qué tipo de variables estamos tratando, debemos saber si son números, palabras o cualquier otro tipo de información.

### Disclaimer
Como se mencionó anteriormente, vamos a utilizar herramientas de programación de Python + IA, más específicamente en Google Colab debido a su flexibilidad y facilidad de uso.

### Carga de Datos
Vamos a cargar el dataset para ver cuánta información tenemos.
![Data Loading](Data_loading.png)
> Carga de Datos y display de ciertas columnas

El conjunto de datos parece tener 2111 filas y 10 columnas, lo cual es un buen tamaño para un conjunto de datos. Ahora veamos con qué tipo de variables vamos a trabajar.

### Variables en el dataset y su tipo de datos
![Data type](Data_type.png)
> Variables y su tipo de dato

Como apreciamos, tenemos dos tipos de variables, “float64” y “Object”, variables que para efectos técnicos vamos a expresar como cuantitativas (números) y cualitativas (categorías) respectivamente.

# Aspectos Generales
A simple vista, el conjunto de datos parece bastante general y básico, nada específico; después de todo, solo contamos con diez variables. Además, algunas variables parecen ser subjetivas más que específicas, como *"ComeMuchasCalorias"*. Considerando el factor humano, necesitaríamos establecer un rango de cuántas calorías se consideran muchas y cuántas se consideran menos. En cualquier caso, también debemos considerar que la persona promedio en Colombia, México y Perú no puede responder a un rango específico de calorías; por lo tanto, parece apropiado tratar esta variable como una categoría en lugar de un número. Sin embargo, a modo de sugerencia, sería más específico usar categorías como *(Alto/Normal/Bajo).*

Otras variables también parecen ser muy subjetivas, como *"ComeVegetales"* y *"ConsumoDeAgua"*, ya que el conjunto de datos no especifica si las cifras de ambas variables tienen una unidad de medida. Por lo tanto, parece correcto tratarlas como un consumo relativo, pero sería muy útil que se especificaran las cifras como frecuencia semanal, litros, galones o cualquier otra unidad.

Ahora bien, si hablamos de niveles de obesidad, podemos centrarnos en esa variable, que parece categórica. Para ver cuántas personas tienen diferentes niveles de obesidad, vamos a graficar los datos para ver la distribución.

![Obesity distribution](Obesity_levels_categories.png)
> Distribución Porcentual de Niveles de Obesidad

Según el gráfico, los niveles de obesidad parecen estar bastante bien distribuidos entre sus diferentes categorías, siendo la obesidad tipo 1 la más común entre los datos.

Ahora, instintivamente, debe haber una tendencia de obesidad según el género, exploremos la distribución en función del género para ver si los hombres o las mujeres tienden a estar en una categoría específica de obesidad, veamos si lo anterior va por buen camino.

![Obesity genre](Obesity_type_genre.png)
> Tipo de Obesidad Por genero

Al observar el gráfico con atención, se observa un patrón sorprendente en los niveles de obesidad severa: el tipo II está dominado por hombres, mientras que el tipo III es casi exclusivamente femenino. En cambio, las demás categorías de peso muestran una distribución mucho más equilibrada entre sexos.
