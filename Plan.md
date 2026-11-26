# PLAN.md - Plan de desarrollo de MelodIA

## 1. Introducción

MelodIA es una aplicación web de detección y clasificación de géneros musicales internacionales y colombianos mediante Machine Learning y Deep Learning.

El desarrollo se realizará utilizando la metodología Spec-Driven Development (SDD), respetando las reglas establecidas en CONSTITUTION.md y los requisitos definidos en PROJECT_SPEC.md.

El modelo principal será una red neuronal convolucional (CNN), desarrollada con TensorFlow y Keras.

También se desarrollará un modelo Random Forest como referencia para comparar el rendimiento de ambos modelos.

El proyecto se desarrollará de manera incremental, modular y organizada.

## 2. Arquitectura

MelodIA utilizará una arquitectura cliente-servidor, organizada en tres áreas principales:

### 2.1. Frontend

Desarrollado con React y Material UI.

Será responsable de la interacción con el usuario, la carga y reproducción de archivos de audio y la presentación de los resultados de clasificación.

### 2.2. Backend

Desarrollado con Python y FastAPI.

Será responsable de recibir las solicitudes del frontend, validar los archivos de audio, coordinar el procesamiento, ejecutar las predicciones y devolver los resultados.

### 2.3. Inteligencia artificial

Desarrollada con Python, Librosa, NumPy, Pandas, Scikit-learn, TensorFlow y Keras.

Será responsable de preparar los datos musicales, generar espectrogramas, entrenar los modelos, evaluar su rendimiento y clasificar nuevos archivos de audio.

El entrenamiento de los modelos se realizará de manera independiente al funcionamiento de la aplicación web.

La aplicación utilizará la red neuronal previamente entrenada para realizar predicciones.

## 3. Componentes y responsabilidades

### 3.1. Módulo de preparación del dataset

Archivo principal: prepare_dataset.py.

Responsabilidades:

- Identificar las fuentes de datos musicales.
- Verificar las licencias de los archivos de audio.
- Organizar las canciones por género musical.
- Validar las etiquetas musicales.
- Identificar archivos duplicados.
- Verificar la calidad de los audios.
- Documentar la cantidad de canciones por género.
- Generar el archivo metadata.csv.
- Dividir los datos por canción en entrenamiento, validación y prueba.
- Evitar la fuga de datos entre los conjuntos.

La distribución aproximada será:

- Entrenamiento: 70 %.
- Validación: 15 %.
- Prueba: 15 %.

### 3.2. Módulo de procesamiento de audio

Archivo principal: audio_processor.py.

Responsabilidades:

- Validar archivos MP3 y WAV.
- Verificar que el tamaño no supere los 50 MB.
- Validar una duración mínima de 10 segundos.
- Detectar archivos vacíos, dañados o silenciosos.
- Convertir el audio a un solo canal.
- Convertir el audio a una frecuencia de muestreo de 22.050 Hz.
- Seleccionar los primeros 30 segundos del audio.
- Completar con ceros los audios inferiores a 30 segundos.
- Normalizar los datos según la configuración establecida.
- Estimar el tempo de la canción utilizando el audio real.
- Conservar el archivo original sin modificaciones.

### 3.3. Módulo de extracción de características

Archivo principal: extract_features.py.

Responsabilidades:

- Extraer características numéricas del audio.
- Obtener características relacionadas con el ritmo y el timbre.
- Extraer coeficientes MFCC.
- Obtener características cromáticas.
- Calcular características espectrales.
- Obtener características de energía.
- Preparar los datos de entrada para Random Forest.

### 3.4. Módulo de generación de espectrogramas

Archivo principal: spectrogram.py.

Responsabilidades:

- Generar espectrogramas log-Mel.
- Mantener dimensiones uniformes.
- Aplicar los parámetros de procesamiento definidos.
- Normalizar los espectrogramas de manera consistente.
- Preparar las matrices de entrada para la red neuronal.

Configuración inicial:

- Frecuencia de muestreo: 22.050 Hz.
- Canales: mono.
- Duración de entrada: 30 segundos.
- Bandas Mel: 128.
- Tamaño de FFT: 2.048 muestras.
- Hop length: 512 muestras.
- Centrado de ventanas: activado.
- Dimensiones esperadas: 128 x 1292 x 1.

La configuración deberá mantenerse durante el entrenamiento, validación, prueba y predicción.

### 3.5. Módulo de arquitectura neuronal

Archivo principal: cnn_model.py.

Responsabilidades:

- Definir la arquitectura de la red neuronal convolucional.
- Establecer las dimensiones de entrada.
- Definir las capas convolucionales.
- Incorporar funciones de activación ReLU.
- Incorporar capas MaxPooling.
- Incorporar Global Average Pooling.
- Incorporar capas densas.
- Incorporar Dropout para reducir el sobreajuste.
- Definir una capa de salida Softmax.
- Configurar los parámetros necesarios para el entrenamiento.

La capa de salida tendrá inicialmente 20 neuronas, correspondientes a los 20 géneros musicales establecidos.

La arquitectura definitiva deberá ajustarse utilizando los datos de entrenamiento y validación.

### 3.6. Módulo de entrenamiento de la CNN

Archivo principal: train_cnn.py.

Responsabilidades:

- Cargar los datos de entrenamiento y validación.
- Preparar los espectrogramas y sus etiquetas.
- Entrenar la red neuronal convolucional.
- Supervisar las métricas de entrenamiento.
- Supervisar las métricas de validación.
- Identificar posibles problemas de sobreajuste.
- Ajustar los hiperparámetros utilizando la validación.
- Guardar el modelo entrenado en formato .keras.
- Guardar el orden de las etiquetas musicales.
- Guardar la configuración del preprocesamiento.
- Generar las curvas de entrenamiento y validación.

Los datos de prueba no podrán utilizarse para ajustar la red neuronal.

### 3.7. Módulo de entrenamiento de Random Forest

Archivo principal: train_random_forest.py.

Responsabilidades:

- Cargar las características numéricas del audio.
- Preparar los datos de entrenamiento y validación.
- Entrenar el modelo Random Forest.
- Ajustar sus hiperparámetros utilizando la validación.
- Guardar el modelo entrenado en formato .pkl.
- Preparar el modelo para su evaluación comparativa.

Random Forest será utilizado únicamente como modelo de referencia.

### 3.8. Módulo de evaluación de modelos

Archivo principal: evaluate_models.py.

Responsabilidades:

- Cargar los modelos previamente entrenados.
- Utilizar el conjunto de prueba independiente.
- Evaluar la red neuronal convolucional.
- Evaluar Random Forest.
- Calcular las métricas de rendimiento.
- Generar matrices de confusión.
- Analizar el rendimiento individual por género.
- Comparar los resultados de ambos modelos.
- Documentar las métricas reales obtenidas.

Las métricas utilizadas serán:

- Accuracy.
- Precision.
- Recall.
- F1-score.
- F1-score macro.
- Matriz de confusión.
- Métricas individuales por género musical.

La meta inicial de exactitud de la CNN será del 80 %.

Si la meta no se alcanza, se documentarán los resultados y se revisará el modelo sin utilizar los datos de prueba para ajustar sus hiperparámetros.

### 3.9. Módulo de predicción

Archivo principal: predict.py.

Responsabilidades:

- Cargar la red neuronal entrenada.
- Verificar la disponibilidad del modelo.
- Cargar las etiquetas musicales.
- Cargar la configuración del preprocesamiento.
- Recibir el espectrograma del audio seleccionado.
- Ejecutar la predicción.
- Obtener las probabilidades estimadas de clasificación.
- Identificar el género con mayor probabilidad.
- Identificar predicciones de baja confianza.
- Organizar los resultados.

La clasificación será realizada exclusivamente mediante la CNN.

### 3.10. Módulo de API REST

Archivo principal: main.py.

Responsabilidades:

- Inicializar FastAPI.
- Recibir archivos de audio desde el frontend.
- Validar las solicitudes.
- Coordinar el procesamiento del audio.
- Ejecutar la predicción mediante la CNN.
- Obtener el tempo estimado.
- Devolver los resultados en formato JSON.
- Manejar errores del servidor.
- Eliminar los archivos temporales.
- Permitir la comunicación con el frontend.

Se propone utilizar los siguientes endpoints:

GET /health

Permitirá verificar la disponibilidad del backend y del modelo.

POST /predict

Permitirá recibir un archivo de audio y devolver los resultados de clasificación.

La respuesta de clasificación incluirá:

- Género musical detectado.
- Probabilidad máxima estimada.
- Probabilidades de los géneros musicales.
- Tempo estimado en BPM.
- Advertencia de baja confianza, cuando corresponda.

Si no es posible estimar el tempo, se devolverá un valor nulo acompañado de un mensaje informativo.

### 3.11. Módulo de interfaz web

Tecnologías: React y Material UI.

Componentes principales:

AudioUpload.jsx:

- Permitir seleccionar archivos MP3 y WAV.
- Realizar validaciones iniciales.
- Mostrar información del archivo seleccionado.
- Manejar la cancelación de la selección.

AudioPlayer.jsx:

- Reproducir el archivo seleccionado.
- Permitir pausar y controlar la reproducción.

GenreResults.jsx:

- Mostrar el género musical detectado.
- Mostrar las probabilidades de clasificación.
- Mostrar el tempo estimado en BPM.
- Mostrar advertencias de baja confianza.
- Presentar los resultados de forma comprensible.

Home.jsx:

- Organizar los componentes principales.
- Controlar el estado de la aplicación.
- Gestionar el proceso de análisis.
- Mostrar indicadores de carga.
- Manejar los mensajes de error.
- Permitir realizar un nuevo análisis.

api.js:

- Enviar archivos de audio al backend.
- Recibir las respuestas de la API REST.
- Gestionar errores de comunicación.

App.jsx:

- Integrar la página principal de MelodIA.

## 4. Dependencias

### 4.1. Dependencias del backend

- Python: lenguaje de programación principal.
- Librosa: procesamiento de audio.
- NumPy: operaciones numéricas y matrices.
- Pandas: organización de datos.
- Scikit-learn: preparación de datos, Random Forest y evaluación.
- TensorFlow: entrenamiento y ejecución de redes neuronales.
- Keras: construcción de la arquitectura neuronal.
- FastAPI: desarrollo de la API REST.

Dependencias técnicas auxiliares propuestas:

- Uvicorn: ejecución del servidor FastAPI.
- python-multipart: recepción de archivos mediante formularios HTTP.
- Matplotlib: generación de matrices de confusión y curvas de entrenamiento.

Las dependencias auxiliares deberán ser aprobadas antes de incorporarlas al proyecto.

Las versiones deberán seleccionarse verificando su compatibilidad con Python y TensorFlow.

### 4.2. Dependencias del frontend

- React: construcción de la interfaz web.
- Material UI: diseño de componentes visuales.

Se propone utilizar Node.js, npm y Vite como herramientas auxiliares para preparar y ejecutar el entorno de desarrollo de React.

Su incorporación deberá ser aprobada antes de la implementación.

La comunicación con FastAPI se realizará mediante solicitudes HTTP utilizando la API Fetch del navegador.

### 4.3. Dependencias entre componentes

- La preparación del dataset deberá completarse antes del entrenamiento.
- El procesamiento de audio deberá estar disponible antes de generar espectrogramas.
- La generación de espectrogramas deberá completarse antes de entrenar la CNN.
- La extracción de características numéricas deberá completarse antes de entrenar Random Forest.
- Ambos modelos deberán entrenarse antes de realizar la evaluación comparativa.
- La CNN deberá estar entrenada y evaluada antes de integrarla en el módulo de predicción.
- El módulo de predicción deberá estar disponible antes de integrar el endpoint de clasificación.
- El frontend podrá desarrollarse después de definir el contrato de comunicación de la API.
- Las pruebas de integración deberán realizarse cuando el frontend y el backend estén disponibles.

## 5. Géneros musicales

La aplicación contemplará inicialmente los siguientes 20 géneros musicales:

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

Antes de iniciar el entrenamiento definitivo se verificará que existan suficientes canciones autorizadas y correctamente etiquetadas para cada género.

No se modificarán los géneros establecidos sin autorización.

## 6. Flujo de procesamiento

### 6.1. Flujo de preparación y entrenamiento

1. Identificar las fuentes de datos musicales.
2. Recopilar los archivos de audio autorizados.
3. Organizar y etiquetar las canciones.
4. Validar la calidad de los audios.
5. Identificar y eliminar duplicados del conjunto de datos.
6. Dividir las canciones en entrenamiento, validación y prueba.
7. Procesar los archivos de audio.
8. Generar espectrogramas log-Mel.
9. Extraer características numéricas.
10. Entrenar la red neuronal convolucional.
11. Entrenar Random Forest.
12. Validar ambos modelos.
13. Ajustar los hiperparámetros utilizando la validación.
14. Evaluar los modelos con el conjunto de prueba.
15. Comparar los resultados.
16. Documentar las métricas obtenidas.
17. Guardar los modelos, etiquetas y configuración.
18. Integrar la CNN en el backend.

### 6.2. Flujo de funcionamiento de la aplicación

1. El usuario abre MelodIA.
2. Selecciona un archivo de audio MP3 o WAV.
3. El frontend realiza las validaciones iniciales.
4. El usuario puede reproducir el audio.
5. El usuario selecciona la opción de analizar.
6. El frontend envía el archivo a FastAPI.
7. El backend valida el archivo.
8. El sistema procesa el audio.
9. Se estima el tempo utilizando el fragmento real.
10. Se genera el espectrograma log-Mel.
11. La CNN analiza el espectrograma.
12. Se obtienen las probabilidades de clasificación.
13. Se identifica el género con mayor probabilidad.
14. Se verifica si existe baja confianza.
15. Se organizan los resultados.
16. Se eliminan los archivos temporales.
17. El backend devuelve los resultados.
18. El frontend muestra el género, las probabilidades y los BPM.
19. El usuario puede seleccionar una nueva canción.

### 6.3. Flujo alternativo de errores

Si el archivo no cumple las condiciones establecidas:

1. Se detiene el procesamiento.
2. Se identifica el motivo del error.
3. Se eliminan los archivos temporales, si existen.
4. Se devuelve un mensaje informativo.
5. El usuario puede seleccionar otro archivo.

Si la red neuronal no está disponible:

1. Se detiene la predicción.
2. Se eliminan los archivos temporales, si existen.
3. Se devuelve un mensaje de error.
4. No se generan resultados falsos.

Si no es posible estimar el tempo:

1. Se continúa la clasificación cuando el espectrograma sea válido.
2. Se informa que no fue posible determinar los BPM.
3. Se muestran los resultados musicales disponibles.

## 7. Estrategia de desarrollo

El proyecto se desarrollará en las siguientes fases:

### Fase 1. Preparación del entorno

- Verificar la compatibilidad de Python y TensorFlow.
- Preparar el entorno virtual.
- Instalar las dependencias autorizadas.
- Organizar la estructura de carpetas.
- Configurar el entorno de desarrollo del frontend.

### Fase 2. Preparación del dataset

- Seleccionar las fuentes de datos.
- Verificar las licencias.
- Recopilar audios internacionales y colombianos.
- Organizar y etiquetar las canciones.
- Validar los archivos.
- Identificar duplicados.
- Dividir los datos en entrenamiento, validación y prueba.

### Fase 3. Procesamiento de audio

- Implementar la validación de archivos.
- Definir el umbral de silencio.
- Procesar las señales de audio.
- Establecer el procedimiento de normalización.
- Generar espectrogramas log-Mel.
- Extraer características numéricas.
- Estimar el tempo.

### Fase 4. Desarrollo de los modelos

- Diseñar la arquitectura de la CNN.
- Entrenar la red neuronal.
- Supervisar las métricas de validación.
- Entrenar Random Forest.
- Ajustar los hiperparámetros.
- Guardar los modelos entrenados.

### Fase 5. Evaluación de los modelos

- Evaluar ambos modelos con las mismas canciones de prueba.
- Calcular las métricas de rendimiento.
- Generar matrices de confusión.
- Analizar las curvas de entrenamiento.
- Evaluar el rendimiento por género.
- Comparar los resultados.
- Documentar las métricas reales.

### Fase 6. Desarrollo del backend

- Implementar el módulo de predicción.
- Configurar FastAPI.
- Definir los endpoints.
- Integrar el procesamiento de audio.
- Integrar la red neuronal entrenada.
- Implementar el manejo de errores.
- Gestionar los archivos temporales.

### Fase 7. Desarrollo del frontend

- Crear la estructura de React.
- Configurar Material UI.
- Diseñar la interfaz principal.
- Implementar la selección de archivos.
- Implementar el reproductor.
- Implementar la visualización de resultados.
- Gestionar los estados de carga y error.
- Conectar el frontend con FastAPI.

### Fase 8. Integración y pruebas

- Verificar la comunicación entre los componentes.
- Ejecutar pruebas funcionales.
- Ejecutar pruebas de validación.
- Ejecutar pruebas de integración.
- Verificar los criterios de aceptación.
- Corregir los errores encontrados.

### Fase 9. Documentación final

- Documentar la instalación del proyecto.
- Documentar la ejecución del backend y frontend.
- Documentar el entrenamiento de los modelos.
- Documentar los resultados obtenidos.
- Documentar las limitaciones.
- Actualizar README.md.
- Verificar el cumplimiento de las especificaciones.

## 8. Estrategia de pruebas

### 8.1. Pruebas unitarias

Se verificarán los componentes de manera independiente.

Casos principales:

- Validación de archivos MP3 y WAV.
- Rechazo de formatos incompatibles.
- Validación del tamaño máximo.
- Validación de la duración mínima.
- Detección de archivos dañados.
- Detección de archivos silenciosos.
- Conversión de frecuencia de muestreo.
- Conversión a un solo canal.
- Recorte de audios superiores a 30 segundos.
- Relleno de audios inferiores a 30 segundos.
- Generación de espectrogramas.
- Validación de las dimensiones de entrada.
- Estimación del tempo.
- Organización de las probabilidades.

### 8.2. Pruebas de calidad del dataset

Se verificará:

- La disponibilidad de los géneros musicales.
- La cantidad de canciones por género.
- La validez de las etiquetas.
- Las licencias de los audios.
- La ausencia de duplicados entre conjuntos.
- La separación de entrenamiento, validación y prueba.
- La ausencia de fragmentos de una misma canción en diferentes conjuntos.
- La aplicación de aumento de datos únicamente al entrenamiento, si se utiliza.

### 8.3. Pruebas de Machine Learning y Deep Learning

Se verificará:

- El correcto entrenamiento de la CNN.
- El correcto entrenamiento de Random Forest.
- La compatibilidad de las dimensiones de entrada.
- La correspondencia entre las etiquetas y las salidas del modelo.
- La generación de predicciones válidas.
- La suma aproximada del 100 % de las probabilidades.
- La detección de posibles problemas de sobreajuste.
- La exactitud de los modelos.
- El rendimiento individual por género musical.
- El almacenamiento y recuperación de los modelos.
- La comparación utilizando el mismo conjunto de prueba.

### 8.4. Pruebas de integración

Se verificará:

- La comunicación entre React y FastAPI.
- El envío de archivos de audio.
- La recepción de solicitudes.
- La integración del procesamiento con la CNN.
- La devolución de resultados en formato JSON.
- La presentación de los resultados en el frontend.
- El manejo de errores del backend.
- La eliminación de archivos temporales.

### 8.5. Pruebas funcionales

Se comprobará que el usuario pueda:

- Seleccionar un archivo de audio.
- Reproducir la canción.
- Ejecutar el análisis.
- Visualizar el género musical.
- Consultar las probabilidades.
- Consultar los BPM.
- Visualizar advertencias de baja confianza.
- Realizar un nuevo análisis.
- Recibir mensajes de error comprensibles.

### 8.6. Pruebas de interfaz

Se verificará:

- La adaptación a diferentes tamaños de pantalla.
- La claridad de los textos.
- La organización de los componentes.
- La navegación mediante teclado.
- La accesibilidad de los controles.
- La presentación de indicadores de carga.
- El comportamiento de los botones.
- La limpieza de resultados anteriores.
- La cancelación de la selección de archivos.

### 8.7. Pruebas de aceptación

Se utilizarán los criterios CA-01 a CA-48 definidos en PROJECT_SPEC.md.

Cada criterio deberá comprobarse mediante una prueba o evidencia verificable.

No se declarará una prueba como exitosa sin haberla ejecutado.

## 9. Gestión de riesgos

### Riesgo 1. Datos insuficientes de géneros colombianos

Estrategia:

- Verificar la disponibilidad de canciones antes del entrenamiento.
- Buscar fuentes autorizadas.
- Documentar los géneros con datos insuficientes.
- Solicitar autorización antes de modificar el alcance.

### Riesgo 2. Sobreajuste de la red neuronal

Estrategia:

- Supervisar las métricas de entrenamiento y validación.
- Utilizar Dropout.
- Ajustar la arquitectura y los hiperparámetros.
- Considerar aumento de datos exclusivamente durante el entrenamiento.

### Riesgo 3. Desequilibrio entre géneros musicales

Estrategia:

- Analizar la distribución de canciones.
- Mantener una representación adecuada de cada género.
- Evaluar las métricas individuales y el F1-score macro.

### Riesgo 4. Fuga de datos

Estrategia:

- Dividir el dataset por canción.
- Identificar archivos duplicados.
- Mantener separados los conjuntos.
- No utilizar el conjunto de prueba para ajustar los modelos.

### Riesgo 5. Recursos computacionales insuficientes

Estrategia:

- Verificar la memoria y capacidad de procesamiento disponibles.
- Utilizar una arquitectura neuronal sencilla.
- Ajustar el tamaño de los lotes de entrenamiento.
- Evitar configuraciones innecesariamente complejas.

### Riesgo 6. Rendimiento inferior a la meta establecida

Estrategia:

- Revisar la calidad del dataset.
- Analizar las matrices de confusión.
- Revisar las métricas de validación.
- Ajustar los hiperparámetros utilizando la validación.
- Documentar los resultados reales.

Si se modifica el modelo después de consultar los resultados finales de prueba, deberá utilizarse un nuevo conjunto independiente para una nueva evaluación final.

### Riesgo 7. Clasificación incorrecta de géneros desconocidos

Estrategia:

- Informar que la clasificación se limita a los géneros entrenados.
- Mostrar advertencias de baja confianza.
- No presentar las predicciones como resultados garantizados.

### Riesgo 8. Incompatibilidad entre dependencias

Estrategia:

- Verificar la compatibilidad de las versiones.
- Utilizar un entorno virtual.
- Documentar las versiones instaladas.
- Mantener un archivo requirements.txt.

## 10. Restricciones

Durante el desarrollo se respetarán las restricciones establecidas en CONSTITUTION.md y PROJECT_SPEC.md.

No se implementarán:

- Reconocimiento de artistas.
- Identificación de canciones por su nombre.
- Generación de música.
- Análisis de letras.
- Detección mediante micrófono en tiempo real.
- Registro o autenticación de usuarios.
- Bases de datos.
- Servicios externos de clasificación musical.
- Almacenamiento permanente de los audios de los usuarios.
- Entrenamiento de modelos desde la interfaz web.
- Funcionalidades adicionales no autorizadas.

## 11. Resultado esperado

Al finalizar el desarrollo se espera obtener:

- Una aplicación web funcional.
- Un backend desarrollado con FastAPI.
- Una interfaz desarrollada con React y Material UI.
- Una red neuronal convolucional entrenada.
- Un modelo Random Forest de referencia.
- Un sistema de procesamiento de audio.
- Un sistema de generación de espectrogramas.
- Un sistema de clasificación musical.
- Resultados de evaluación documentados.
- Una comparación entre los modelos.
- Pruebas funcionales y de integración.
- Documentación técnica del proyecto.

El desarrollo se realizará siguiendo las tareas establecidas en TASKS.md.

No se avanzará a una nueva tarea sin verificar el resultado esperado de la tarea anterior.