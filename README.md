# 📊 Análisis de Casos COVID-19 en Argentina

## 📝 Descripción del proyecto

Este proyecto realiza un **análisis exploratorio de datos (EDA)** sobre los casos de COVID-19 en Argentina, usando un dataset filtrado y optimizado.  
El objetivo es extraer información clave sobre mortalidad, distribución por edad, sexo, provincia, uso de cuidados intensivos y asistencia respiratoria mecánica, y analizar la carga de pacientes en los sistemas de salud público y privado.
---

## 🔹 Tecnologías y librerías utilizadas
-Python → lenguaje principal para análisis y procesamiento de datos  
-Jupyter Notebook → entorno para ejecutar y documentar el análisis paso a paso  
-Pandas → manejo y limpieza de datos  
-Numpy → cálculos numéricos  
-matplotlib y seaborn → visualizaciones gráficas  
---

##🚀 Guía Rápida para Ejecutar el Proyecto
1. 📥 Descargar el dataset
Covid19Casos.csv – Datos.gob.ar
https://datos.gob.ar/dataset/salud-covid-19-casos-registrados-republica-argentina/archivo/salud_fd657d02-a33a-498b-a91b-2ef1a68b8d16

3. ⚙️ Instalar librerías necesarias
Asegúrate de tener Python instalado y luego instala:
pip install numpy pandas matplotlib seaborn jupyter

4. 📂 Preparar el proyecto
Coloca el archivo Covid19Casos.csv en la carpeta raíz del proyecto.
Abre Jupyter Notebook y carga el cuaderno principal.

5. ▶️ Ejecutar los módulos
Se deben ejecutar los 5 módulos del proyecto en orden:
Filtrado y limpieza del dataset
Carga y exploración inicial
Optimización de tipos de datos
Análisis exploratorio
Visualización de gráficos
---

## 🧪 Módulo 1: Filtrado y limpieza inicial

### ✅ Objetivo
Reducir el tamaño y la complejidad del archivo original para facilitar su análisis posterior y optimizar el uso de memoria.

### 📂 Archivo original
- Nombre: `Covid19Casos.csv`
- Tamaño: ~6.4 GB
- Columnas: 25
- Filas: ~29.9 millones
- Problemas: muchas columnas irrelevantes o con alta cantidad de datos faltantes

### 🔍 Filtrado
Se seleccionaron **8 columnas clave**:

- `sexo`
- `edad`
- `residencia_provincia_nombre`
- `cuidado_intensivo`
- `fallecido`
- `asistencia_respiratoria_mecanica`
- `origen_financiamiento`
- `clasificacion`

💡 Estas columnas fueron elegidas por su relevancia epidemiológica y porque tienen datos más completos.

### 🧹 Limpieza
- Eliminación de filas con valores faltantes (`dropna()`)  
- Esto garantiza un dataset limpio y listo para análisis posteriores

### 💾 Método de carga
- Lectura en bloques de 100.000 filas (`chunksize`) para evitar desbordar memoria  
- Cada bloque fue limpiado y guardado progresivamente en `covid_8_columnas.csv`

### 📁 Archivo resultante
- Nombre: `covid_8_columnas.csv`
- Tamaño final: ~2.0 GB
- Columnas: 8
- Filas: ~29 millones (aprox.)

---
##🧪 Módulo 2: Carga del archivo filtrado y exploración inicial

Se carga el archivo CSV reducido covid_8_columnas.csv en un DataFrame llamado df.
Se inspecciona la estructura con df.info():
Cantidad total de registros
Tipos de datos de cada columna
Presencia de valores faltantes
Se visualizan las primeras filas con df.head() para verificar la estructura.

💡 Esta etapa permite entender los tipos de datos antes de aplicar transformaciones o análisis.
---

## 🧪 Módulo 3: Optimización de tipos de datos

### 🎯 Objetivo
Reducir el uso de memoria y mejorar rendimiento del DataFrame.

### 🔧 Cambios aplicados
- Columnas tipo `object` convertidas a `category` (`sexo`, `fallecido`, `cuidado_intensivo`, etc.)  
- Columna `edad` convertida de `float64` a `int16` o `int32` para ahorrar memoria

### 📌 Beneficios
- Menor consumo de RAM  
- Mayor velocidad en operaciones de filtrado, agrupamiento y ordenamiento

---

## 🧪 Módulo 4: Carga y exploración inicial

- Carga del archivo filtrado `covid_8_columnas.csv` en un DataFrame `df`  
- Revisión de la estructura del dataset (`df.info()`)  
- Visualización de las primeras filas (`df.head()`)  
- Inspección de valores únicos por columna y calidad de datos

---

## 🔍 Funcionalidades principales del análisis

1. **Carga y estructura básica**
   - Valores únicos por columna
   - Revisión de tipos de datos y nulos

2. **Análisis de distribuciones**
   - Variables categóricas: sexo, estado de fallecimiento, clasificación de casos

3. **Análisis numérico**
   - Estadísticas descriptivas para la edad (media, desviación, percentiles)

4. **Métricas clave**
   - Total de casos
   - Casos positivos confirmados
   - Porcentaje de casos positivos
   - Tasa de mortalidad general

5. **Calidad de datos**
   - Identificación de valores faltantes por columna

6. **Análisis adicional (opcional)**
   - Distribución de casos por provincia

---

## 📊 Salidas generadas

- Resumen de valores únicos por columna  
- Distribuciones de variables categóricas  
- Estadísticas descriptivas de edad  
- Métricas principales: totales y porcentajes  
- Reporte de calidad de datos (nulos)  
- Distribución por provincia (si aplica)  
---

##**🧪 Módulo 5: Visualizaciones y gráficos**

✅ Objetivo
Generar gráficos que permitan visualizar patrones y relaciones entre variables clave del dataset covid_8_columnas.csv.

🔹 Gráficos realizados
Distribución de fallecidos por edad
Histograma con línea de densidad para observar la edad más afectada.

Permite identificar rangos etarios de mayor mortalidad.
Top provincias con mayor cantidad de casos positivos

Gráfico de barras horizontales mostrando las provincias con mayor circulación del virus.
Facilita identificar regiones más afectadas.

Uso de cuidados intensivos según estado de fallecimiento
Diagramas circulares (pie charts) comparando la proporción de pacientes que ingresaron a UTI entre fallecidos y no fallecidos.

Tasa de mortalidad general
Gráfico de barras mostrando la proporción de fallecidos y no fallecidos.

Uso de asistencia respiratoria mecánica en fallecidos
Gráfico circular mostrando la proporción de fallecidos que recibieron asistencia respiratoria.

Distribución de fallecidos por sexo
Gráfico circular para visualizar la proporción de hombres y mujeres entre los fallecidos.

Pacientes en cuidados intensivos por tipo de financiamiento
Gráfico de barras mostrando la distribución entre sistema público y privado.

💡 Observaciones
Los gráficos permiten visualizar relaciones entre variables categóricas y numéricas.
Facilitan la interpretación de la mortalidad por edad, sexo y región.
Ayudan a identificar la carga sobre los sistemas de salud según tipo de financiamiento y uso de UTI/ARM.
---
```
✅ Síntesis general

📈 La positividad fue del 30.8%, con una mayoría de casos descartados.
👨‍🦳 La mortalidad se concentró en adultos mayores, especialmente a partir de los 65 años.
👨 Hombres presentaron mayor mortalidad que mujeres.
🏥 El uso de UTI y ARM estuvo altamente asociado a la muerte.
🌍 Buenos Aires y CABA fueron los principales focos de circulación viral.
🏛️ El sector público llevó la mayor carga de pacientes críticos.



✍️ *Proyecto desarrollado y analizado por Sebastián Medina*
