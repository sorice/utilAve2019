### Introductory notes for this text
* Las preguntas que verán son secuencias en mi mente respecto de lo que debemos hacer.
* Puede haber preguntas tontas o muy complejas, esta es una técnica para rellenar lagunas.
* Las pondré de la forma: Pregunta - Objetivo por el cual necesita ser respondida esa pregunta.
* todas las preguntas están dirigidas a problemas para trabajar localmente e integrar el download de data y upload de modelos to the cloud
* Este texto está escrito en English y Español, en el futuro estará solo in English

# Infrastructure Team

## Store and Load BigData Locally

- Anonymization (like GDPR[General Data Protection Regulation] in US)
	* Obj: AI Data-Backup do not contain personal Data.
- Se puede instalar una instancia de BigQuery localmente?
	* Obj: We need a local copy for AI purpose.
- Hay forma de procesar streaming con tensorflow como lo hace Spark?
	* Obj: En el sistema real donde esto se aplica, los datos crecerán dinámicamente, es necesario evaluar compatibilidad con Data Streamming.
- Ambientes de python: Dask vs Spark?
	* Obj: ganar interoperabilidad entre tecnologías y estandarization para resolver issues en menos tiempo. 
- Cómo cargar data a tensorflow desde HFS o BigQuery?
	* Problem: hacer upload de grandes volúmenes de datos es un proceso lento.
	* existe tensorflow.data
	* googleapis too permite integrar hacer ML directamente con bigquery
- Manejo de BigData en Hard Disk: Binary, columned oriented data format. parquet, feather, hdf5? Integración/compatibility con todo lo demás.
- Manejo de BigData en memoria: Apache Arrow, alguna otra cosa? Integración/compatibility con todo lo demás?
- Usar JSON para intercambiar datos en vez de todo este complex system de formatos?


# Feature Engineering
=====================

- Que preprocesamiento puedo hacer con Spark?
	* stopwords, stemming, lemmatization, collocations, correference resolution, negation substitution.
- Que transformaciones puedo hacer con Tensorflow?
- Feature Extraction from text: BoG, W2V, wordnet integration,
- implementación de distancias basadas en chars/tokens (Euclidean, Manhatan),
- Sparce matrix support
- native outlier treatment
- Hyper parameter optimization support or integration with sklearn
- Partial_fit support
- native parallelization 
- Possibilities to integrate into pipelines

# Model Engineering (Math & ML Team)

## About Math
- SVD modifications

## About ML techniques
- Esemble methos support (Boosting and Bagging)
- Possibilities to integrate into pipelines
- Partial_fit support
- native parallelization 

# Testing
- RAM performance in a 3.5Gb dataset