# Constitución de MelodIA

## Tecnologías

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

## Reglas de desarrollo

- Organizar el código en módulos.
- Separar el frontend, el backend y los modelos de inteligencia artificial.
- Utilizar nombres descriptivos para variables, funciones y archivos.
- Manejar los errores durante la carga y el procesamiento de audios.
- Validar los formatos de audio antes de procesarlos.
- Conservar los archivos de audio originales sin modificarlos.
- Admitir archivos de audio en formato MP3 y WAV.
- Eliminar los archivos temporales después del procesamiento.
- Documentar las funcionalidades desarrolladas.
- Implementar una tarea a la vez.

## Reglas de Machine Learning y Deep Learning

- Utilizar aprendizaje supervisado.
- Utilizar una red neuronal convolucional (CNN) como modelo principal.
- Utilizar TensorFlow y Keras para construir y entrenar la red neuronal.
- Utilizar Random Forest como modelo de referencia para comparar resultados.
- Generar espectrogramas Mel como entrada de la red neuronal.
- Utilizar archivos de audio previamente etiquetados por género musical.
- Incluir géneros musicales internacionales y colombianos.
- Utilizar conjuntos de datos obtenidos de fuentes autorizadas.
- Mantener una representación adecuada de los géneros musicales.
- Separar los datos de entrenamiento, validación y prueba.
- Evitar que fragmentos de una misma canción aparezcan en diferentes conjuntos de datos.
- Utilizar el mismo procedimiento de preprocesamiento durante el entrenamiento y la predicción de cada modelo.
- Supervisar el entrenamiento para identificar y reducir el sobreajuste.
- Evaluar los modelos antes de integrarlos en la aplicación.
- Utilizar métricas de exactitud, precisión, recall, F1-score y matriz de confusión.
- Comparar ambos modelos utilizando el mismo conjunto de prueba.
- Guardar la red neuronal entrenada en formato .keras.
- Documentar los resultados reales del entrenamiento y la evaluación.
- No utilizar los datos de prueba para ajustar los modelos.

## Restricciones

- No utilizar servicios externos de clasificación musical.
- No implementar reconocimiento de artistas.
- No implementar identificación de canciones por su nombre.
- No implementar generación de música.
- No implementar análisis de letras.
- No implementar detección en tiempo real mediante micrófono.
- No utilizar bases de datos en esta primera versión.
- No implementar registro ni autenticación de usuarios.
- No almacenar permanentemente los audios cargados por los usuarios.
- No agregar funcionalidades no solicitadas.

## Reglas para la IA

- Leer la constitución y las especificaciones antes de programar.
- Respetar las tecnologías establecidas.
- No cambiar tecnologías sin autorización.
- No modificar el alcance del proyecto sin autorización.
- Explicar los cambios realizados en el código.
- Verificar cada funcionalidad implementada.
- No avanzar a la siguiente tarea sin completar la anterior.
- No inventar resultados de entrenamiento, predicciones ni métricas.
- No declarar pruebas exitosas sin ejecutarlas.
- Mantener el código organizado, comprensible y documentado.
