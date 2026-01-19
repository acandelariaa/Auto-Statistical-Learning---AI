# Analisis Gráfico
Dada la alta variabilidad del peso individual, calculamos el **peso promedio** para cada categoría de obesidad. Esto nos permite identificar tendencias y patrones claros sin el ruido de los datos individuales.

**Subpoblación Seleccionada:** para este análisis gráfico, se seleccionó específicamente a la subpoblación masculina. Esta segmentación nos permite examinar la relación entre el peso y los niveles de obesidad de forma aislada, facilitando la detección de patrones de salud y tendencias de peso.

### Graficar Subpoblación

> Python Code
```python
# Establecer dataframe de hombres
df_hombres = df[df['Sexo'] == 'Male'] 

# Configuración del tamaño
plt.figure(figsize=(14, 8))

# Orden de las categorías
orden_niveles = [
    'Insufficient_Weight',
    'Normal_Weight',
    'Overweight_Level_I',
    'Overweight_Level_II',
    'Obesity_Type_I',
    'Obesity_Type_II',
    'Obesity_Type_III'
]

# 2. CREAR EL GRÁFICO (Usando solo df_hombres)
ax = sns.barplot(
    data=df_hombres,       # Usamos el dataframe filtrado
    x='NivelDeObesidad',        # Asegúrate que este sea el nombre real de tu columna
    y='Peso',            # Variable de peso
    order=orden_niveles,
    color='#ffb347',       # Un color naranja pastel (o usa palette='Oranges')
    errorbar=None,
    edgecolor='black'
)

# Poner los números arriba de las barras
for container in ax.containers:
    ax.bar_label(container, fmt='%.1f kg', padding=3, fontsize=11)

# Títulos y Etiquetas
plt.title('Peso Promedio por Nivel de Obesidad (Subpoblación Masculina)', fontsize=16, fontweight='bold')
plt.xlabel('Categoría de Obesidad', fontsize=12)
plt.ylabel('Peso Promedio (kg)', fontsize=12)
plt.xticks(rotation=45)
plt.grid(axis='y', linestyle='--', alpha=0.3)

plt.tight_layout()
plt.show()
```

![Graphic_analysis](Peso_hombres_y_mujeres.png)


**Interpretación de Resultados de Subpoblación Masculina:**

El gráfico revela un patrón consistente: la subpoblación masculina presenta un peso promedio más alto en todas las categorías de obesidad, en comparación con el valor de referencia femenino. Inicialmente, esta diferencia se mantiene estable, rondando los 10 kg en las primeras categorías.

Sin embargo, se observa una **distinción notable** en la categoría de "Obesidad Tipo III". En este caso, el peso promedio de los hombres se dispara a aproximadamente 173 kg, lo que crea una enorme diferencia de aproximadamente 50 kg en comparación con las mujeres de la misma categoría.

Esto sugiere que, si bien factores biológicos (como el indice de masa corporal) explican la diferencia moderada y consistente en los niveles más bajos, la clasificación de **Obesidad Tipo III** en los hombres representa un grupo donde la distinción es mucho mas notoria.

## Conclusión
La naturaleza del conjunto de datos es cualitativa y cuantitativa. Además, las variables que tenemos parecen ser básicas y subjetivas, lo cual es muy útil para el análisis general de datos, pero para el procesamiento de datos mas especifico suele ser difícil llegar a una conclusión sólida debido a la falta de otros factores, como la dieta específica, el ejercicio, la calidad del sueño, estilo de vida y otros factores que podrian modelar con mejor precision el comportamiento.

Hablando de ciertas areas de oportunidad, el conjunto de datos debería ser más específico en aspectos como "ConsumoDeAgua" y "ComeVegetales", debido a la falta de unidades de medida o especificación de frecuencia para estas variables, para este estudio, se consideraron como consumos relativos.

En general, como se mencionó anteriormente, este conjunto de datos sirve como un buen ejemplo para el procesamiento de datos de aprendizaje automático estadístico, ya que demuestra claramente cómo distintas variables pueden influir en un resultado categórico.
