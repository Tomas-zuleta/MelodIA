# MelodIA - Detector de géneros musicales mediante redes neuronales

## 1. Descripción

MelodIA es una aplicación web desarrollada con Python y React que permite cargar archivos de audio y detectar automáticamente el género musical al que pertenecen mediante técnicas de Machine Learning y Deep Learning.

La aplicación utiliza una red neuronal convolucional (CNN), implementada con TensorFlow y Keras, para analizar espectrogramas Mel y aprender patrones relacionados con el ritmo, el tempo, la melodía, el timbre y la percusión.

El sistema estará orientado a la clasificación de géneros musicales internacionales y colombianos, promoviendo el reconocimiento de la diversidad musical y cultural del país mediante la inteligencia artificial.

## 2. Objetivo

Desarrollar una aplicación web inteligente que permita identificar y clasificar géneros musicales mediante el procesamiento de audio y las redes neuronales convolucionales, mostrando al usuario el género musical detectado, las probabilidades de clasificación y el tempo estimado de la canción expresado en BPM.

También se busca comparar el rendimiento de la red neuronal convolucional con un modelo tradicional de Machine Learning basado en Random Forest.

## 3. Tecnologías

- Python.
- Librosa.
- NumPy.
- Pandas.
- Scikit-learn.
- Random Forest.
- TensorFlow.
- Keras.
- Redes neuronales convolucionales (CNN).
- FastAPI.
- React.
- Material UI.

## 4. Requisitos funcionales

RF-01: Permitir cargar archivos de audio en formato MP3 y WAV.

RF-02: Permitir reproducir el audio seleccionado.

RF-03: Validar que el archivo de audio sea compatible y pueda procesarse correctamente.

RF-04: Procesar el audio y extraer características musicales relacionadas con el ritmo, el tempo, la melodía, el timbre y la percusión.

RF-05: Generar un espectrograma Mel a partir del audio procesado.

RF-06: Analizar el espectrograma mediante una red neuronal convolucional previamente entrenada.

RF-07: Identificar y mostrar el género musical con mayor probabilidad estimada de clasificación.

RF-08: Mostrar los porcentajes de probabilidad estimados para los géneros musicales contemplados por el modelo.

RF-09: Mostrar el tempo estimado de la canción expresado en BPM.

RF-10: Permitir cargar una nueva canción y realizar otro análisis.

RF-11: Mostrar mensajes de error cuando un archivo no pueda ser procesado.

RF-12: Validar que el archivo de audio no supere los 50 MB.

RF-13: Validar que el archivo de audio tenga una duración mínima de 10 segundos.

RF-14: Analizar los primeros 30 segundos del audio. Si su duración es inferior, analizar el fragmento disponible siempre que cumpla la duración mínima.

RF-15: Detectar archivos vacíos o sin una señal sonora suficiente y mostrar un mensaje informativo.

RF-16: Mantener el estado de la aplicación cuando el usuario cancele la selección de un archivo.

RF-17: Mostrar el mensaje "Clasificación de baja confianza" cuando la probabilidad máxima estimada sea inferior al 50 %.

RF-18: Deshabilitar el botón de análisis cuando no exista un archivo válido seleccionado.

RF-19: Mostrar un mensaje de error cuando no sea posible establecer comunicación con el backend.

RF-20: Deshabilitar el botón de análisis mientras se procesa un archivo de audio.

RF-21: Mostrar un mensaje de error cuando la red neuronal no esté disponible o no pueda cargarse.

RF-22: Mostrar el mensaje "No fue posible determinar el tempo" cuando no se puedan estimar los BPM.

RF-23: Limpiar los resultados anteriores cuando el usuario seleccione un nuevo archivo de audio válido.

RF-24: Permitir a los desarrolladores entrenar y evaluar una red neuronal convolucional utilizando audios previamente etiquetados, mediante un módulo independiente de la interfaz web.

RF-25: Permitir a los desarrolladores entrenar y evaluar un modelo Random Forest como referencia para comparar el rendimiento de ambos modelos.

RF-26: Convertir el audio a una frecuencia de muestreo de 22.050 Hz y a un solo canal.

RF-27: Completar con ceros los audios válidos inferiores a 30 segundos para mantener dimensiones uniformes en la entrada de la red neuronal.

RF-28: Generar espectrogramas log-Mel utilizando 128 bandas Mel, un tamaño de FFT de 2.048 muestras y un hop length de 512 muestras.

RF-29: Validar la presencia de una señal sonora suficiente antes de realizar la normalización y el relleno del audio.

## 5. Requisitos no funcionales

RNF-01: Funcionar localmente sin depender de servicios externos de clasificación musical.

RNF-02: Mantener una estructura modular y organizada.

RNF-03: Mostrar mensajes de error claros y comprensibles.

RNF-04: Conservar los archivos de audio originales sin modificarlos.

RNF-05: Contar con una interfaz intuitiva, accesible y adaptable a diferentes tamaños de pantalla.

RNF-06: Mostrar un indicador de carga mientras se realiza el análisis musical.

RNF-07: Utilizar el mismo procedimiento de preprocesamiento durante el entrenamiento y la predicción de cada modelo.

RNF-08: Evaluar el rendimiento de los modelos mediante métricas de exactitud, precisión, recall, F1-score y matriz de confusión.

RNF-09: Mantener una comunicación adecuada entre el frontend y el backend mediante una API REST.

RNF-10: No almacenar permanentemente los archivos de audio cargados por los usuarios.

RNF-11: Establecer una meta de exactitud mínima del 80 % para la red neuronal sobre el conjunto de prueba.

RNF-12: Distribuir aproximadamente el 70 % de los datos para entrenamiento, el 15 % para validación y el 15 % para prueba.

RNF-13: Garantizar la eliminación de los archivos temporales después del procesamiento, incluso cuando ocurra un error.

RNF-14: Utilizar archivos de audio obtenidos de fuentes autorizadas.

RNF-15: Mantener la interfaz informada sobre los estados de selección, procesamiento, resultado y error.

RNF-16: Documentar el origen, la cantidad y la distribución de los audios utilizados.

RNF-17: Realizar los ajustes de los modelos utilizando los datos de entrenamiento y validación, reservando los datos de prueba para la evaluación final.

RNF-18: Mantener dimensiones de entrada uniformes para los espectrogramas utilizados por la red neuronal.

RNF-19: Supervisar las métricas de entrenamiento y validación para identificar posibles problemas de sobreajuste.

RNF-20: Guardar la red neuronal entrenada en formato .keras.

RNF-21: Mantener una representación adecuada de los géneros musicales en los conjuntos de datos.

RNF-22: Documentar los parámetros de preprocesamiento, entrenamiento y evaluación para facilitar la reproducción de los resultados.

RNF-23: Comparar los modelos CNN y Random Forest utilizando las mismas canciones del conjunto de prueba.

RNF-24: Mantener una configuración uniforme de generación de espectrogramas durante el entrenamiento, validación, prueba y predicción.

RNF-25: Documentar los criterios utilizados para etiquetar los géneros musicales.

RNF-26: Evaluar el rendimiento individual de cada género mediante métricas de precisión, recall y F1-score.

RNF-27: Verificar la disponibilidad y representación de los géneros musicales antes de realizar el entrenamiento definitivo.

RNF-28: Mantener la configuración de preprocesamiento y el orden de las etiquetas asociados al modelo entrenado.

## 6. Arquitectura

La aplicación tendrá seis componentes principales:

### 6.1. Interfaz de usuario

Desarrollada con React y Material UI.

Será responsable de:

- Permitir la selección de archivos de audio.
- Reproducir los archivos seleccionados.
- Permitir al usuario ejecutar el análisis musical.
- Mostrar indicadores de procesamiento.
- Visualizar el género musical detectado.
- Mostrar las probabilidades de clasificación.
- Mostrar el tempo estimado de la canción.
- Presentar mensajes de error y advertencias.

### 6.2. API REST

Desarrollada con Python y FastAPI.

Será responsable de:

- Recibir los archivos de audio enviados desde el frontend.
- Validar las solicitudes.
- Coordinar el procesamiento de audio.
- Ejecutar las predicciones de la red neuronal.
- Manejar los errores del backend.
- Devolver los resultados al frontend en formato JSON.
- Gestionar la eliminación de archivos temporales.

### 6.3. Servicio de procesamiento de audio

Desarrollado con Librosa y NumPy.

Será responsable de:

- Validar los archivos de audio.
- Verificar su formato, tamaño y duración.
- Detectar archivos silenciosos o dañados.
- Convertir los audios a una frecuencia de muestreo uniforme.
- Convertir las señales de audio a un solo canal.
- Recortar o completar los audios según la duración establecida.
- Normalizar y preparar las señales de audio.
- Extraer características musicales.
- Generar espectrogramas log-Mel.
- Estimar el tempo de las canciones.
- Preparar los datos de entrada para los modelos.

### 6.4. Módulo de Machine Learning

Desarrollado con Pandas y Scikit-learn.

Será responsable de:

- Organizar los datos musicales.
- Extraer características numéricas del audio.
- Preparar los datos de entrenamiento.
- Entrenar un modelo Random Forest.
- Evaluar el rendimiento del modelo.
- Comparar los resultados con la red neuronal convolucional.

Las características numéricas podrán incluir:

- MFCC.
- Chroma Features.
- Spectral Centroid.
- Spectral Bandwidth.
- Spectral Rolloff.
- Zero Crossing Rate.
- RMS Energy.
- Tempo.
- Características rítmicas y armónicas.

Random Forest será utilizado exclusivamente como modelo de referencia para comparar su rendimiento con la red neuronal.

### 6.5. Módulo de Deep Learning

Desarrollado con TensorFlow y Keras.

Será responsable de:

- Construir la arquitectura de la red neuronal.
- Preparar los espectrogramas para el entrenamiento.
- Entrenar la red neuronal convolucional.
- Validar el rendimiento durante el entrenamiento.
- Identificar posibles problemas de sobreajuste.
- Evaluar la red neuronal con datos independientes.
- Guardar el modelo entrenado.
- Cargar el modelo para realizar nuevas predicciones.
- Clasificar los géneros musicales.

La red neuronal utilizará espectrogramas log-Mel como entrada y aprenderá patrones asociados a los diferentes géneros musicales.

La CNN será el modelo principal utilizado por la aplicación para realizar predicciones.

#### Arquitectura conceptual de la red neuronal

La red neuronal convolucional estará compuesta inicialmente por las siguientes capas:

1. Capa de entrada (Input).

   Recibirá los espectrogramas log-Mel con dimensiones uniformes.

2. Capas convolucionales (Conv2D).

   Identificarán patrones relacionados con las frecuencias, el ritmo y otras características musicales.

3. Capas de activación (ReLU).

   Permitirán aprender relaciones no lineales entre las características musicales.

4. Capas de agrupación (MaxPooling).

   Reducirán las dimensiones de las representaciones internas.

5. Capa Global Average Pooling.

   Resumirá las características aprendidas por las capas convolucionales.

6. Capas densas (Dense).

   Relacionarán las características aprendidas con las categorías musicales.

7. Capas Dropout.

   Ayudarán a reducir el sobreajuste durante el entrenamiento.

8. Capa de salida (Softmax).

   Generará una distribución de probabilidades entre los 20 géneros musicales contemplados inicialmente.

La cantidad definitiva de capas, filtros, épocas y demás hiperparámetros se determinará durante la implementación y validación del modelo.

### 6.6. Servicio de resultados

Será responsable de organizar:

- El género musical detectado.
- Las probabilidades estimadas de clasificación.
- El tempo estimado de la canción.
- Las advertencias de baja confianza.
- Los mensajes de error correspondientes.

Los resultados serán enviados al frontend mediante la API REST.

La lógica de procesamiento de audio y clasificación musical estará separada de la interfaz gráfica.

### 6.7. Configuración técnica del procesamiento de audio

La configuración inicial de procesamiento será:

- Frecuencia de muestreo: 22.050 Hz.
- Canales de audio: mono.
- Duración de entrada: 30 segundos.
- Duración mínima del audio original: 10 segundos.
- Tamaño máximo del archivo: 50 MB.
- Representación: espectrograma log-Mel.
- Bandas Mel: 128.
- Tamaño de FFT: 2.048 muestras.
- Hop length: 512 muestras.
- Centrado de ventanas: activado (center=True).
- Dimensiones esperadas: 128 x 1292 x 1.
- Audios inferiores a 30 segundos: relleno con ceros.
- Audios superiores a 30 segundos: recorte de los primeros 30 segundos.
- Normalización: escalado consistente de los valores del espectrograma.

La validación de duración y presencia de señal sonora se realizará antes de normalizar y completar el audio con ceros.

El tempo se estimará utilizando el fragmento de audio real, sin incluir el relleno artificial.

La configuración utilizada durante el entrenamiento deberá conservarse junto con el modelo para garantizar que las predicciones utilicen el mismo procedimiento de procesamiento.

Los parámetros definitivos de normalización y validación de silencio deberán documentarse antes del entrenamiento.

### 6.8. Preparación del conjunto de datos

Para entrenar los modelos se utilizarán conjuntos de datos musicales previamente etiquetados.

Las fuentes de datos propuestas serán:

- GTZAN.
- Free Music Archive (FMA).
- MTG-Jamendo.
- Dataset propio de géneros musicales colombianos.

Los conjuntos de datos deberán revisarse para verificar sus licencias, disponibilidad, calidad y compatibilidad con los géneros seleccionados.

No se asumirá que los conjuntos públicos contienen todos los géneros requeridos.

La distribución aproximada de los datos será:

- 70 % para entrenamiento.
- 15 % para validación.
- 15 % para prueba.

El conjunto de entrenamiento permitirá que los modelos aprendan patrones musicales.

El conjunto de validación permitirá ajustar los hiperparámetros y supervisar el rendimiento durante el entrenamiento.

El conjunto de prueba permitirá evaluar el rendimiento final de los modelos utilizando canciones independientes.

La división se realizará por canción antes de generar fragmentos o aplicar técnicas de aumento de datos.

Se evitará que canciones duplicadas o fragmentos de una misma canción aparezcan en diferentes conjuntos.

Las técnicas de aumento de datos, si se utilizan, se aplicarán exclusivamente al conjunto de entrenamiento.

Los modelos CNN y Random Forest deberán evaluarse utilizando las mismas canciones del conjunto de prueba.

### 6.9. Evaluación de los modelos

Los modelos serán evaluados mediante las siguientes métricas:

- Accuracy (exactitud).
- Precision (precisión).
- Recall (sensibilidad).
- F1-score.
- F1-score macro.
- Matriz de confusión.
- Métricas individuales por género musical.

Para la red neuronal también se generarán:

- Curva de exactitud de entrenamiento.
- Curva de exactitud de validación.
- Curva de pérdida de entrenamiento.
- Curva de pérdida de validación.

Estas métricas permitirán analizar el comportamiento de los modelos, identificar posibles problemas de sobreajuste y determinar qué géneros musicales presentan mayores dificultades de clasificación.

Se establece una meta inicial de exactitud del 80 % para la red neuronal.

La meta deberá comprobarse mediante la evaluación del modelo y no representa un resultado garantizado.

### 6.10. Estructura del proyecto

MelodIA/
├── CONSTITUTION.md
├── PROJECT_SPEC.md
├── PLAN.md
├── TASKS.md
├── README.md
├── .gitignore
├── backend/
│   ├── main.py
│   ├── requirements.txt
│   ├── dataset/
│   │   ├── raw/
│   │   ├── processed/
│   │   └── metadata.csv
│   ├── models/
│   │   ├── cnn_model.keras
│   │   ├── random_forest.pkl
│   │   ├── labels.json
│   │   └── preprocessing_config.json
│   ├── reports/
│   │   ├── metrics.json
│   │   ├── confusion_matrix_cnn.png
│   │   ├── confusion_matrix_rf.png
│   │   └── training_curves.png
│   ├── src/
│   │   ├── __init__.py
│   │   ├── audio_processor.py
│   │   ├── extract_features.py
│   │   ├── spectrogram.py
│   │   ├── prepare_dataset.py
│   │   ├── cnn_model.py
│   │   ├── train_cnn.py
│   │   ├── train_random_forest.py
│   │   ├── evaluate_models.py
│   │   └── predict.py
│   └── tests/
└── frontend/
    ├── package.json
    ├── index.html
    └── src/
        ├── App.jsx
        ├── main.jsx
        ├── components/
        │   ├── AudioUpload.jsx
        │   ├── AudioPlayer.jsx
        │   └── GenreResults.jsx
        ├── pages/
        │   └── Home.jsx
        └── services/
            └── api.js

Esta será la estructura inicial propuesta para el proyecto.

Los archivos de implementación, los modelos entrenados, los conjuntos de datos y los reportes se crearán durante las etapas correspondientes.

## 7. Reglas de negocio

RN-01: Solo se procesarán archivos de audio válidos en formato MP3 y WAV.

RN-02: El sistema no modificará los archivos de audio originales.

RN-03: La red neuronal deberá estar entrenada antes de realizar predicciones.

RN-04: El sistema únicamente clasificará los géneros musicales incluidos en el entrenamiento del modelo.

RN-05: El género principal será aquel que obtenga la mayor probabilidad estimada de clasificación.

RN-06: La suma de las probabilidades de clasificación deberá ser aproximadamente igual al 100 %, considerando el redondeo.

RN-07: Si un archivo no puede ser procesado, se mostrará un mensaje informativo al usuario.

RN-08: Los datos de entrenamiento, validación y prueba deberán mantenerse separados.

RN-09: Las probabilidades mostradas serán estimaciones del modelo y no garantizarán que la clasificación sea correcta.

RN-10: No se almacenarán permanentemente los archivos de audio procesados.

RN-11: Los géneros musicales contemplados inicialmente serán los siguientes:

### Géneros urbanos

1. Hip hop.
2. Trap.
3. Reguetón.
4. Drill.

### Géneros internacionales

5. Pop.
6. Rock.
7. Electrónica.
8. Jazz.
9. Música clásica.
10. R&B.

### Géneros tropicales

11. Salsa.
12. Bachata.
13. Merengue.

### Géneros colombianos

14. Vallenato.
15. Cumbia.
16. Champeta.
17. Porro.
18. Bambuco.
19. Currulao.
20. Música popular colombiana.

RN-12: No se procesarán archivos que superen los 50 MB o tengan una duración inferior a 10 segundos.

RN-13: El sistema analizará un máximo de 30 segundos de audio real por archivo.

RN-14: Si la probabilidad máxima estimada es inferior al 50 %, el sistema mostrará una advertencia de baja confianza junto con los resultados.

RN-15: El sistema realizará una clasificación multiclase, seleccionando un género musical principal entre las categorías disponibles.

RN-16: Solo se permitirá un análisis simultáneo por interfaz de usuario.

RN-17: Los archivos temporales deberán eliminarse independientemente de si el procesamiento fue exitoso o presentó errores.

RN-18: No se generarán predicciones cuando la red neuronal no esté disponible.

RN-19: La ausencia de una estimación válida de BPM no impedirá mostrar el resultado de clasificación, siempre que el espectrograma pueda procesarse correctamente.

RN-20: Los fragmentos pertenecientes a una misma canción no podrán distribuirse entre los conjuntos de entrenamiento, validación y prueba.

RN-21: Las predicciones estarán limitadas a los géneros conocidos por el modelo.

RN-22: La red neuronal convolucional será el modelo principal de clasificación musical.

RN-23: Random Forest será utilizado como modelo de referencia y comparación.

RN-24: Los espectrogramas deberán tener dimensiones y parámetros de procesamiento consistentes con los utilizados durante el entrenamiento.

RN-25: Los archivos de entrenamiento deberán contar con una etiqueta de género musical previamente definida.

RN-26: Los géneros musicales que no dispongan de suficientes datos autorizados deberán revisarse antes de iniciar el entrenamiento definitivo.

RN-27: Una probabilidad elevada no garantiza que una canción pertenezca realmente a alguno de los géneros conocidos por el modelo.

RN-28: Los audios válidos inferiores a 30 segundos serán completados con ceros para preparar la entrada de la red neuronal.

RN-29: La validación de duración y señal sonora se realizará antes de completar el audio con ceros.

RN-30: Los espectrogramas deberán generarse utilizando los mismos parámetros técnicos durante todas las etapas del modelo.

RN-31: Cada audio de entrenamiento tendrá una etiqueta de género principal definida mediante criterios consistentes.

RN-32: Si un género musical no cuenta con suficientes datos autorizados, se deberá revisar su inclusión antes del entrenamiento definitivo y solicitar autorización para modificar el alcance.

RN-33: El conjunto de prueba permanecerá reservado para la evaluación final de los modelos.

## 8. Criterios de aceptación

CA-01: La aplicación permite cargar archivos de audio en formato MP3 y WAV.

CA-02: El usuario puede reproducir el archivo de audio seleccionado.

CA-03: La aplicación procesa correctamente los archivos de audio válidos.

CA-04: El sistema genera un espectrograma Mel compatible con la entrada de la red neuronal.

CA-05: La red neuronal entrenada procesa el espectrograma y genera una predicción.

CA-06: La interfaz muestra el género musical con mayor probabilidad estimada de clasificación.

CA-07: La aplicación muestra los porcentajes de probabilidad de los géneros musicales incluidos en el modelo.

CA-08: La aplicación muestra el tempo estimado de la canción expresado en BPM.

CA-09: Un archivo incompatible, vacío o dañado genera un mensaje de error comprensible.

CA-10: El usuario puede realizar un nuevo análisis sin reiniciar la aplicación.

CA-11: Los archivos de audio originales permanecen sin modificaciones después del procesamiento.

CA-12: El frontend recibe y presenta correctamente los resultados enviados por el backend.

CA-13: La red neuronal es evaluada con canciones que no fueron utilizadas durante su entrenamiento ni validación.

CA-14: La aplicación realiza la clasificación sin depender de servicios externos de inteligencia artificial.

CA-15: Los archivos temporales de audio se eliminan después del procesamiento.

CA-16: Un archivo superior a 50 MB es rechazado mediante un mensaje informativo.

CA-17: Un audio con duración inferior a 10 segundos genera un mensaje de error.

CA-18: Un audio con duración superior a 30 segundos es procesado utilizando únicamente sus primeros 30 segundos.

CA-19: Un archivo sin una señal sonora suficiente genera un mensaje informativo y no produce una clasificación.

CA-20: Cancelar la selección de un archivo no genera errores ni modifica el estado anterior de la aplicación.

CA-21: Una predicción con probabilidad máxima estimada inferior al 50 % muestra una advertencia de baja confianza.

CA-22: El botón de análisis permanece deshabilitado cuando no existe un archivo válido seleccionado.

CA-23: Si el backend no está disponible, la interfaz muestra un mensaje de error de conexión.

CA-24: Durante el procesamiento, el botón de análisis permanece deshabilitado y se muestra un indicador de carga.

CA-25: Si la red neuronal entrenada no está disponible, la aplicación muestra un mensaje de error sin generar resultados falsos.

CA-26: Cuando no sea posible estimar los BPM, se muestra un mensaje informativo en el apartado correspondiente.

CA-27: Al seleccionar un nuevo audio válido, los resultados anteriores desaparecen.

CA-28: La red neuronal alcanza la meta propuesta de exactitud mínima del 80 % sobre el conjunto de prueba independiente. Si no se alcanza, se documentará el incumplimiento y se revisará el modelo.

CA-29: Los archivos temporales son eliminados tanto después de un análisis exitoso como después de un error.

CA-30: Los géneros mostrados en los resultados corresponden a las categorías utilizadas durante el entrenamiento.

CA-31: Un audio válido con una duración entre 10 y 30 segundos es analizado utilizando su duración disponible y completado según los parámetros de entrada de la red neuronal.

CA-32: Se verifica que ningún fragmento de una misma canción esté presente en diferentes conjuntos de entrenamiento, validación y prueba.

CA-33: La documentación contiene las métricas reales obtenidas durante la evaluación de los modelos.

CA-34: La red neuronal entrenada se guarda en formato .keras y puede cargarse para realizar predicciones.

CA-35: Random Forest y la red neuronal convolucional son evaluados utilizando las mismas canciones del conjunto de prueba.

CA-36: Se documentan las diferencias de rendimiento entre ambos modelos.

CA-37: Se generan las curvas de entrenamiento y validación de la red neuronal para analizar su comportamiento y posibles problemas de sobreajuste.

CA-38: Los espectrogramas generados durante la predicción tienen las mismas dimensiones y parámetros de procesamiento utilizados durante el entrenamiento.

CA-39: Se evalúa el rendimiento individual de los géneros musicales, incluyendo los géneros colombianos.

CA-40: Se verifica que la interfaz se adapte correctamente a diferentes tamaños de pantalla.

CA-41: Los audios procesados tienen una frecuencia de muestreo de 22.050 Hz y un solo canal.

CA-42: Los audios válidos inferiores a 30 segundos son completados con ceros para obtener una entrada de duración uniforme.

CA-43: Los espectrogramas log-Mel son generados utilizando los parámetros establecidos en la especificación y tienen dimensiones de 128 x 1292 x 1.

CA-44: Se verifica que los audios silenciosos sean rechazados antes de la normalización y el relleno.

CA-45: Se documenta la cantidad de canciones disponibles por cada género musical.

CA-46: Se documentan las métricas individuales de clasificación para los géneros internacionales y colombianos.

CA-47: Se verifica que la configuración de procesamiento y el orden de las etiquetas coincidan con los utilizados durante el entrenamiento del modelo.

CA-48: Se documentan los criterios de etiquetado y las decisiones tomadas frente a géneros musicales ambiguos o con datos insuficientes.

## 9. Instrucciones para la IA

- Leer CONSTITUTION.md y PROJECT_SPEC.md antes de programar.
- Consultar PLAN.md y TASKS.md cuando estén disponibles.
- Respetar las tecnologías definidas.
- No modificar el alcance del proyecto sin autorización.
- No agregar funcionalidades no solicitadas.
- Mantener el código modular y organizado.
- Separar el frontend, el backend y los modelos de inteligencia artificial.
- Utilizar nombres descriptivos para archivos, variables y funciones.
- Utilizar una red neuronal convolucional como modelo principal.
- Utilizar TensorFlow y Keras para construir y entrenar la red neuronal.
- Utilizar Random Forest como modelo de referencia.
- Respetar los géneros musicales establecidos.
- No eliminar ni agregar géneros musicales sin autorización.
- Implementar las tareas en el orden establecido.
- Explicar cada cambio realizado.
- Manejar adecuadamente los errores.
- Mantener un procedimiento consistente de preprocesamiento de audio.
- Respetar los parámetros técnicos de generación de espectrogramas.
- Evitar la fuga de datos entre entrenamiento, validación y prueba.
- No utilizar los datos de prueba para ajustar los modelos.
- Supervisar el entrenamiento de la red neuronal.
- Identificar posibles problemas de sobreajuste.
- Documentar los hiperparámetros utilizados.
- Verificar la disponibilidad y calidad de los conjuntos de datos.
- No inventar archivos de audio, etiquetas, resultados de clasificación ni métricas de evaluación.
- No declarar pruebas exitosas sin ejecutarlas.
- Verificar cada funcionalidad antes de avanzar a la siguiente tarea.
- Respetar las restricciones establecidas en la constitución del proyecto.
- Solicitar autorización cuando una decisión implique modificar las especificaciones.

## 10. Restricciones y alcance

La primera versión de MelodIA no incluirá:

- Reconocimiento de artistas.
- Identificación de canciones por su nombre.
- Generación de música mediante inteligencia artificial.
- Análisis de letras de canciones.
- Detección musical en tiempo real mediante micrófono.
- Registro y autenticación de usuarios.
- Bases de datos.
- Almacenamiento permanente de los audios de los usuarios.
- Servicios externos de clasificación musical.
- Entrenamiento de la red neuronal desde la interfaz de usuario.
- Funcionalidades adicionales que no estén contempladas en las especificaciones.

## 11. Decisiones técnicas pendientes

Antes del entrenamiento definitivo deberán resolverse los siguientes aspectos:

- Seleccionar y verificar los conjuntos de datos definitivos.
- Determinar la cantidad de canciones disponibles por género musical.
- Verificar las licencias y autorizaciones de los audios.
- Definir los criterios definitivos de etiquetado musical.
- Establecer el umbral de validación de silencio.
- Definir el procedimiento definitivo de normalización.
- Determinar la cantidad de capas y filtros de la red neuronal.
- Seleccionar los hiperparámetros de entrenamiento.
- Verificar los recursos computacionales disponibles.
- Evaluar la viabilidad de alcanzar la meta de exactitud del 80 %.
- Validar el umbral inicial de baja confianza del 50 %.

Estas decisiones deberán documentarse y resolverse durante las etapas correspondientes, sin modificar el alcance del proyecto sin autorización.
