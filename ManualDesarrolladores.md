
# Configuración para la extracción de datos
## Manual para desarrolladores: Extracción de información de noticias en el contexto del proyecto portada
Este manual se ha creado básicamente para ayudar a los desarrolladores del proyecto **_PortAda_** a configurar la aplicación *[jportada_boat_fact_extractor](https://github.com/portada-git/jportada_boat_fact_extractor)* para conseguir extraer los datos referentes a las embarcaciones llegadas a los diferentes puertos de estudio referenciadas en los periódicos estudiados.

## Consideraciones previas 
La aplicación *[jportada_boat_fact_extractor](https://github.com/portada-git/jportada_boat_fact_extractor)*  está basada en la biblioteca *[jportada_auto_news_extractor_lib](https://github.com/portada-git/jportada_auto_news_extractor_lib)*, la cual presenta 3 funcionalidades necesarias para realizar la extracción en el contexto del proyecto portada.

### Funcionalidades de *jportada_auto_news_extractor_lib*
#### Ensamblador de archivos digitales
Esta funcionalidad permite unir, en un solo archivo, los múltiples textos pertenecientes a una misma unidad informativa, que el procesador OCR haya generado a partir de los periódicos digitalizados. Aunque la biblioteca permitiría usar otras metodologías, en el proyecto **_PortAda_** se decidió usar el enfoque basado en el nombre de los archivos generados por el procesador OCR. Durante el proceso de obtención del texto a partir de las imágenes de los periódicos analizados, las imágenes se fraccionan en bloques para facilitar su ordenación y transcripción textual. En el proyecto se ha optado por nombrar cada bloque con un nombre que permita identificar la fecha, el nombre del periódico, la edición del ejemplar (mañana, tarde, ...), así como el tipo de noticia, la página y el número de bloque procesado por el OCR. 

Este formato nos permite determinar que todos los archivos de texto pertenecientes a una misma fecha, periódico, y edición, pueden contener información relacionada de una misma unidad de información y, por tanto, necesitamos unirla en un solo texto para poder disponer de un texto bien ordenado. 

Además, al tiempo que se realiza la unión, se consigue obtener información extra que no se encuentra en la noticia, objeto de nuestro análisis y posterior extracción. No referimos a los datos indicados en el nombre: Fecha del ejemplar, lugar de edición, nombre del periódico, edición del ejemplar, tipo de noticia y páginas de las que se realizará la extracción. Dicha información será incorporada, al resto de datos extraídos. Por ello **es importante que el nombre de los archivos sigan el patrón descrito: AAAA_MM_DD_PUE_NP_E_T_PG_BLOC.txt, donde AAAA corresponde al año de edición, MM al mes y DD al día;  PUE indica el nombre del puerto al que hace referencia la noticia a extraer (BCN, BUE, HAB, MAR); NP se refiere al nombre del periódico (DB por diario de Barcelona, DM por diario de la marina, EN por el nacional, LP por la prensa, SM por le semafore de marseille, ...); E indica la edición del ejemplar (M por mañana, T por tarde, N por noche o U por única) .
T indica el t  (por ejemplo, el archivo 1854_04_25_BUE_LP_U_E_08_005.txt indicaría que se trata del quinto bloque de la página 8 de las noticias referidas a las entradas de buques del periódico)

 



