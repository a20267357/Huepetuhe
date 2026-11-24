# Huepetuhe
trabajo final geocomputación: Análisis de cobertura minera en Huepetuhe

Justificación: En las últimas décadas la minería aurífera se ha convertido en una seria problemática en el departamento de Madre de dios, entre ellos hay distritos que presentan mayor incidencia de esta actividad y uno de ellos es Huepetuhe. Por lo que será el centro del siguiente análisis del cambio de suelo.

Pregunta de investigación: 

¿En qué medida ha variado la superficie intervenida por la minería aurífera en Huepetuhe, Madre de Dios, entre los años 2016 y 2025? 

Objetivo general: 
Analizar la expansión de las superficies intervenidas por la minería aurífera en Huepetuhe, Madre de Dios, Perú, durante el año 2016 y 2025, mediante el procesamiento de imágenes satelitales representativas de dichos años.

Objetivos específicos:
1. Cuantificar la variación de la superficie vegetal y la intervenida por minería aurífera mediante el análisis comparativo de las coberturas.

2. Determinar clasificación de suelo necesaria para el propósito de la investigación a partir de información espectral.

3. Aplicar técnicas de clasificación supervisada e índices espectrales para identificar sectores que presentan mayor superficie minera y mayor expansión .


Hipótesis

H0: superficie intervenida en 2016 = superficie intervenida en 2025

H1: superficie intervenida en 2016 =/ superficie intervenida en 2025


Datos utilizados: archivo .shp del área de estudio, catálogo de imágenes satelitales de Planetary Computer, clasificación de MapBiomas.

Cómo operar el código: 

Cómo operar el código: 

primero debe abrir el notebook “1.Huepetuhe.ipynb”, ahí debe descargar los archivos del área de estudio para intentar el archivo shp posterior a instalar y descargar las librerías. Este paso es obligatorio, aunque puede realizarlo con otra área de su interés.

Al terminar con este proceso deberá correr el resto de comandos, puede modificar la fecha de su interés o la cantidad de nubes que cubren su área de interés.

Al llegar al último comando debería haber obtenido los índices ndvi, ndwi, mndwi, bsi y ndmi en una imagen Raster del satélite Sentinel 2. Puede visualizarlo en el penúltimo código.  

Ahora debe abrir el Notebook “2_clasificacion_Huepetuhe” en este debe agregar su archivo .geotiff resultante del ejercicio anterior. Pero si lo desdea puede agregar directamente desde el drive https://drive.google.com/drive/folders/1mf1qlQ9TBVUBh78AbAo5m-lwrAUZBuic 

Primero aplicamos la clasificación de suelos de MapBiomas Perú, su resultado debería ser un mapa inicial de la clasificación del área.

Sin embargo carece de cierta rigurosidad espectral, por lo que realizaremos un entrenamiento del modelo que identifica los valores de las bandas asociadas a cada categoría.

Se toma el archivo resultante de la clasificación de MapBiomas y se pasa a través de Random Forest, tras esto usted debería tener una clasificación supervisada de la categorización anterior.

Ahora podemos graficar la distribución de píxeles en hectáreas de cobertura y podemos mapear los píxeles que tengan alta probabilidad de ser mineros. 

lo siguiente que vamos a hacer será determinar el área de mayor cobertura minera, por lo que se dividirá el área de estudio en cuadrículas donde se seleccionara la de mayor porcentaje de píxeles mineros

este paso es opcional pero puede escoger el Top 3 de cuadrículas de mayor cantidad de minería modificando el .head y agregando por ejemplo 3 (para el top 3) top_1_ids = set(df_ranking["Cuadricula"].head(1))

ahora lo trasladamos a la clasificación de MapBiomas y podemos ver el detalle de la cuadrícula Top1 minera 

Al terminar de correr los comandos debería tener un grafico de la cobertura de su cuadrícula top 1 minera y un archivo excel.

Este paso lo puede repetir con 2016 y 2025 y ver el aumento de 100 hectáreas, equivalentes a 1.000.000 de km cuadrados de aumento de minería únicamente en esta cuadrícula.
