# Análisis de Audiencias Públicas (2004 - 2022)

En este proyecto unimos y analizamos bases de datos de audiencias de gestión de intereses (lobby) de Argentina. El objetivo fue ver el perfil de gestión de cada gobierno.

El principal desafío fue que la base del período 2004-2016 y la de 2016-2025 tenían nombres de columnas distintos y los datos estaban cargados con diferentes criterios. Identificamos qué columnas eran compatibles entre sí, normalizamos nombres y  limpiamos errores de carga manual con lo cual llegamos a un dataset único de casi 100.000 filas.

Como la base original carecía de categorías estandarizadas acerca del motivo de la audiencia, desarrollamos un clasificador propio para organizarlas 14 áreas clave:

* Energía y Minería
* Agroindustria
* Infraestructura y Vivienda
* Finanzas y Economía
* Industria y Comercio
* Salud y Ambiente
* Educación y Ciencia
* Justicia y Derechos
* Trabajo y Gremios
* Transporte y TICs
* Social, Cultura y Deporte
* Seguridad y Defensa
* Relaciones Exteriores
* Gestión Federal

El código prioriza la dependencia del funcionario (ej: Ministerio de Salud -> Salud).
Para organismos políticos o generalistas (jefatura, presidencia, etc.), el codigo ignora la dependencia y busca patrones de texto en el motivo de la audiencia usando expresiones regulares y palabras clave.

Con esta técnica de NLP y procesamiento de contexto, se lograron rescatar miles de filas que antes quedaban sin clasificar.

## Estructura del Repositorio


* `audiencias_2004.xlsx` y `audiencias_2016.xlsx` son las fuentes originales sin procesar.
* `audiencias_2004_2022.xlsx` es el dataset final ya normalizado y limpio que se utiliza en el script 

*  **`categorias_audiencias.ipynb`**: Notebook principal. Carga la base limpia, aplica el algoritmo de clasificación temática y genera las visualizaciones por período presidencial.
