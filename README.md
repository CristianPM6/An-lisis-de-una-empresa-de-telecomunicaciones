# Analisis de una empresa de telecomunicaciones

Este proyecto presenta un análisis exploratorio de datos de ConnectaTel, una empresa de telecomunicaciones con operaciones en México y Colombia. El objetivo es comprender cómo los clientes utilizan realmente los servicios móviles —principalmente llamadas y mensajes—, identificar patrones de consumo, detectar comportamientos atípicos y construir segmentos de clientes que permitan obtener información útil para la toma de decisiones comerciales.

El análisis trabaja con información registrada hasta el año 2024 y busca responder preguntas como:

- ¿Qué segmentos de clientes presentan mayor o menor uso de llamadas y mensajes?
- ¿Qué valores atípicos aparecen en el comportamiento de los usuarios?
- ¿Cómo varía el uso según la edad y el tipo de plan?
- ¿Qué patrones pueden contribuir al diseño o mejora de los planes comerciales?

🎯 Objetivos

Los principales objetivos del proyecto son:

- Integrar y limpiar bases de datos provenientes de tres fuentes distintas.
- Aplicar técnicas de validación, estandarización de tipos de datos y detección de valores inconsistentes.
- Construir un perfil estadístico del uso (llamadas y mensajes) por cliente y por segmentos demográficos.
- Detectar outliers y comportamientos atípicos mediante métodos estadísticos y visuales.
- Crear segmentaciones de clientes basadas en edad, país y comportamiento de uso.
- Visualizar diferencias entre segmentos y extraer insights comerciales relevantes.
- Documentar todo el proceso en un Jupyter Notebook, junto con un README reproducible para subirlo a GitHub.


## 🗂️ Datasets utilizados

El proyecto utiliza tres datasets principales:

1. plans.csv

Contiene información sobre los planes ofrecidos por ConnectaTel, incluyendo variables relacionadas con:

Precio del plan.
Minutos incluidos.
GB incluidos.
Costos asociados al consumo adicional.

2. users_latam.csv

Contiene información de los clientes, incluyendo datos como:

Edad.
Ciudad.
Fecha de registro.
Plan contratado.
Fecha de churn.

3. usage.csv

Contiene el detalle de uso de los servicios por parte de los usuarios, incluyendo:

Tipo de actividad.
Fecha.
Duración de las llamadas.
Longitud de los mensajes.

**Relación entre los datasets**

Los tres datasets se complementan para relacionar:

**Clientes → Plan contratado → Uso real**
Esta integración permite analizar el comportamiento de los usuarios desde una perspectiva demográfica y de consumo.

## 🛠️ Herramientas utilizadas

El análisis fue desarrollado en Python mediante un Jupyter Notebook.

Principales librerías:

pandas — manipulación y análisis de datos.
numpy — operaciones numéricas.
seaborn — visualización estadística.
matplotlib — generación y personalización de gráficos.

## 🔄 Etapas del análisis

**1. Carga y exploración inicial**

Se cargaron los tres datasets mediante pandas y se realizó una primera revisión utilizando:

.head()
.shape
.info()

Esta etapa permitió conocer la estructura, dimensiones, columnas y tipos de datos de cada fuente.

**2. Identificación de problemas de calidad**

Se revisaron:

Valores nulos.
Proporción de valores faltantes.
Valores únicos de variables categóricas.
Estadísticas descriptivas.
Posibles valores inválidos o sentinels.

Entre los problemas identificados se encontraron valores faltantes en variables de users_latam.csv y usage.csv.

**3. Tratamiento de valores faltantes**

Se evaluaron diferentes alternativas de imputación, incluyendo:

Media.
Mediana.
Imputación diferenciada por tipo de actividad.

**4. Estadística descriptiva**

Se calcularon medidas estadísticas para conocer el comportamiento de las variables numéricas, incluyendo:

Media.
Mediana.
Cuartiles.
Valores mínimos y máximos.
Distribución de las variables.

Esto permitió establecer una referencia sobre el comportamiento típico y extremo de los usuarios.

**5. Visualización y detección de outliers**

Se utilizaron histogramas y boxplots para identificar:

Distribuciones sesgadas.
Concentraciones de usuarios.
Valores extremos.
Diferencias en el comportamiento de consumo.
El análisis mediante IQR permitió identificar posibles valores atípicos en:
- Cantidad de mensajes.
- Cantidad de llamadas.
- Cantidad de minutos de las llamadas.

**6. Construcción del perfil de usuario**

Se consolidó información de los usuarios y su actividad para construir un perfil de consumo que incluyera variables como:

Edad.
Cantidad de mensajes.
Cantidad de llamadas.
Cantidad de minutos de llamada.

Esto permitió pasar del análisis individual de los datasets a una visión agregada del comportamiento de cada cliente.

**7. Segmentación de clientes**

Se construyeron dos tipos principales de segmentación.
Segmentación por nivel de uso
Se creó la variable grupo_uso:
- Bajo uso: menos de 5 llamadas y menos de 5 mensajes.
- Uso medio: menos de 10 llamadas y menos de 10 mensajes, sin pertenecer al grupo de bajo uso.
- Alto uso: resto de casos.
Segmentación por edad

Se creó la variable grupo_edad:
- Joven: menor de 30 años.
- Adulto: entre 30 y menos de 60 años.
- Adulto Mayor: 60 años o más.

Posteriormente se utilizaron gráficos de conteo para visualizar la distribución de usuarios en cada segmento.

**8. Insight ejecutivo**

Finalmente, los resultados se tradujeron en conclusiones orientadas al negocio.

El notebook identifica:

- Una mayor concentración de usuarios en el segmento Adulto frente a los demás grupos de edad.
- Una mayor concentración de usuarios en el segmento de Uso medio.
- Distribuciones con sesgo positivo en variables relacionadas con llamadas, mensajes y minutos.
- Un grupo reducido de usuarios con consumos considerablemente superiores al comportamiento general.

A partir de estos patrones se plantean oportunidades relacionadas con la diferenciación de planes, el estímulo del segmento de alto uso y propuestas adicionales dirigidas a determinados grupos de edad.

## ▶️ Cómo ejecutar el notebook

**Opción recomendada: Google Colab**

 1) Descarga o clona este repositorio.
 2) Abre Google Colab.
 3) Selecciona Archivo → Subir cuaderno.
 4) Selecciona el archivo:
    S7 Version-Estudiante-Project-ConnectaTel.ipynb
 5) Asegúrate de que los datasets estén disponibles en el entorno de ejecución.
 6) Ejecuta las celdas en orden desde el inicio hasta el final.

## 🔁 Guía breve de reproducción

Para reproducir el análisis:

 1. Obtener los tres archivos CSV
         ↓
 2. Abrir el notebook en Google Colab o Jupyter
         ↓
 3. Instalar/verificar las librerías necesarias
         ↓
 4. Cargar plans.csv, users_latam.csv y usage.csv
         ↓
 5. Explorar estructura y tipos de datos
         ↓
 6. Detectar valores nulos e inconsistencias
         ↓
 7. Aplicar el tratamiento de datos documentado
         ↓
 8. Calcular estadísticas descriptivas
         ↓
 9. Crear visualizaciones y analizar outliers
         ↓
 10. Construir el perfil de usuarios
         ↓
 11. Crear segmentos por uso y edad
         ↓
 12. Analizar los resultados
         ↓
 13. Elaborar el insight ejecutivo

Para obtener resultados consistentes, se recomienda ejecutar las celdas en el orden en que aparecen en el notebook, ya que algunas transformaciones dependen de objetos creados en etapas anteriores.

**📁 Estructura sugerida del repositorio**

connectatel-analysis/
│
├── README.md
├── S7 Version-Estudiante-Project-ConnectaTel.ipynb
│
└── datasets/
    ├── plans.csv
    ├── users_latam.csv
    └── usage.csv

   
