# TASKS.md - Tareas de desarrollo de MelodIA

## 1. Instrucciones generales

El desarrollo de MelodIA se realizará siguiendo las tareas definidas en este documento.

Cada tarea deberá respetar CONSTITUTION.md, PROJECT_SPEC.md y PLAN.md.

Reglas:

- Implementar una tarea a la vez.
- Respetar el orden y las dependencias.
- Verificar el resultado esperado de cada tarea.
- Ejecutar las pruebas correspondientes.
- Documentar los cambios realizados.
- No marcar una tarea como completada sin verificarla.
- No modificar el alcance sin autorización.
- No inventar resultados ni métricas.
- Resolver los errores antes de avanzar.

Estados:

- [ ] Pendiente.
- [x] Completada y verificada.

Las referencias RF, RNF, RN y CA corresponden a PROJECT_SPEC.md.

---

## Fase 1. Preparación del entorno

### T01. Verificar el entorno de desarrollo

- [ ] Estado: pendiente.

Objetivo: verificar las versiones disponibles de Python y los recursos computacionales del equipo.

Resultado esperado: entorno compatible con TensorFlow y las tecnologías del proyecto.

Requisitos relacionados: RNF-02, RNF-22.

Dependencias: ninguna.

### T02. Crear el entorno virtual de Python

- [ ] Estado: pendiente.

Objetivo: aislar las dependencias del backend y los modelos.

Resultado esperado: entorno virtual creado y activado correctamente.

Requisitos relacionados: RNF-02, RNF-22.

Dependencias: T01.

### T03. Instalar las dependencias del backend

- [ ] Estado: pendiente.

Objetivo: instalar las bibliotecas autorizadas para el procesamiento de audio, entrenamiento y desarrollo del backend.

Resultado esperado: dependencias instaladas y registradas en requirements.txt.

Requisitos relacionados: RNF-01, RNF-22.

Dependencias: T02.

### T04. Crear la estructura del proyecto

- [ ] Estado: pendiente.

Objetivo: organizar las carpetas del frontend, backend, dataset, modelos, reportes y pruebas.

Resultado esperado: estructura coherente con PROJECT_SPEC.md.

Requisitos relacionados: RNF-02.

Dependencias: T03.

### T05. Configurar Git y el archivo .gitignore

- [ ] Estado: pendiente.

Objetivo: mantener un control organizado de los cambios y evitar publicar archivos innecesarios, temporales o datos no autorizados.

Resultado esperado: repositorio configurado y reglas de exclusión establecidas.

Requisitos relacionados: RNF-02, RNF-10, RNF-14.

Dependencias: T04.

---

## Fase 2. Preparación del dataset

### T06. Investigar fuentes de datos musicales

- [ ] Estado: pendiente.

Objetivo: identificar conjuntos de datos que permitan obtener audios de los géneros establecidos.

Resultado esperado: listado de fuentes disponibles y géneros cubiertos.

Requisitos relacionados: RNF-14, RNF-16, RNF-27.

Criterios relacionados: CA-45, CA-48.

Dependencias: T05.

### T07. Verificar licencias y disponibilidad

- [ ] Estado: pendiente.

Objetivo: comprobar que los audios puedan utilizarse de manera autorizada.

Resultado esperado: fuentes de datos verificadas y documentadas.

Requisitos relacionados: RNF-14, RNF-16.

Criterios relacionados: CA-45, CA-48.

Dependencias: T06.

### T08. Recopilar los archivos de audio

- [ ] Estado: pendiente.

Objetivo: recopilar canciones de los 20 géneros musicales establecidos.

Resultado esperado: conjunto inicial de audios internacionales y colombianos.

Requisitos relacionados: RNF-21, RNF-27, RN-11, RN-32.

Criterios relacionados: CA-45.

Dependencias: T07.

### T09. Definir los criterios de etiquetado

- [ ] Estado: pendiente.

Objetivo: establecer reglas consistentes para asignar un género principal a cada canción.

Resultado esperado: criterios de etiquetado documentados.

Requisitos relacionados: RNF-25, RN-25, RN-31.

Criterios relacionados: CA-48.

Dependencias: T08.

### T10. Organizar y etiquetar las canciones

- [ ] Estado: pendiente.

Objetivo: clasificar los archivos del dataset según su género musical.

Resultado esperado: audios organizados con etiquetas consistentes.

Requisitos relacionados: RNF-21, RN-11, RN-25.

Criterios relacionados: CA-30, CA-45.

Dependencias: T09.

### T11. Validar la calidad y distribución del dataset

- [ ] Estado: pendiente.

Objetivo: identificar archivos dañados, duplicados, etiquetas inconsistentes y géneros con datos insuficientes.

Resultado esperado: dataset depurado y reporte de distribución por género.

Requisitos relacionados: RNF-16, RNF-21, RNF-27, RN-32.

Criterios relacionados: CA-45, CA-48.

Dependencias: T10.

### T12. Generar el archivo metadata.csv

- [ ] Estado: pendiente.

Objetivo: registrar la información de cada canción, su identificador, ubicación, género y fuente.

Resultado esperado: archivo de metadatos organizado y verificable.

Requisitos relacionados: RNF-16, RNF-22, RNF-25.

Criterios relacionados: CA-45, CA-48.

Dependencias: T11.

### T13. Dividir el dataset

- [ ] Estado: pendiente.

Objetivo: separar las canciones en entrenamiento, validación y prueba.

Resultado esperado: distribución aproximada del 70 %, 15 % y 15 %, sin duplicados ni fragmentos de una misma canción en diferentes conjuntos.

Requisitos relacionados: RNF-12, RNF-17, RN-08, RN-20, RN-33.

Criterios relacionados: CA-13, CA-32, CA-35.

Dependencias: T12.

---

## Fase 3. Procesamiento de audio

### T14. Implementar la carga de archivos de audio

- [ ] Estado: pendiente.

Objetivo: permitir la lectura de archivos MP3 y WAV mediante Librosa.

Resultado esperado: archivos de audio válidos cargados correctamente.

Requisitos relacionados: RF-01, RF-03, RN-01.

Criterios relacionados: CA-01, CA-03.

Dependencias: T13.

### T15. Implementar la validación de formatos y tamaño

- [ ] Estado: pendiente.

Objetivo: rechazar archivos incompatibles o superiores a 50 MB.

Resultado esperado: archivos inválidos rechazados con mensajes comprensibles.

Requisitos relacionados: RF-03, RF-11, RF-12.

Criterios relacionados: CA-09, CA-16.

Dependencias: T14.

### T16. Implementar la validación de duración

- [ ] Estado: pendiente.

Objetivo: verificar que los audios tengan una duración mínima de 10 segundos.

Resultado esperado: audios demasiado cortos rechazados correctamente.

Requisitos relacionados: RF-13, RN-12.

Criterios relacionados: CA-17.

Dependencias: T15.

### T17. Definir e implementar la detección de silencio

- [ ] Estado: pendiente.

Objetivo: establecer un umbral técnico y detectar audios vacíos o sin señal sonora suficiente.

Resultado esperado: audios silenciosos rechazados antes de normalizar o rellenar.

Requisitos relacionados: RF-15, RF-29, RN-29.

Criterios relacionados: CA-19, CA-44.

Dependencias: T16.

### T18. Convertir los audios a una configuración uniforme

- [ ] Estado: pendiente.

Objetivo: convertir los audios a 22.050 Hz y un solo canal.

Resultado esperado: señales de audio con frecuencia de muestreo y canales uniformes.

Requisitos relacionados: RF-26.

Criterios relacionados: CA-41.

Dependencias: T17.

### T19. Implementar el recorte y relleno de audio

- [ ] Estado: pendiente.

Objetivo: preparar una entrada uniforme de 30 segundos.

Resultado esperado: audios largos recortados y audios cortos completados con ceros, conservando los originales.

Requisitos relacionados: RF-14, RF-27, RNF-04, RN-28.

Criterios relacionados: CA-11, CA-18, CA-31, CA-42.

Dependencias: T18.

### T20. Definir e implementar la normalización

- [ ] Estado: pendiente.

Objetivo: establecer un procedimiento consistente de normalización de las entradas.

Resultado esperado: configuración de normalización documentada y aplicada uniformemente, sin utilizar datos de prueba para ajustar sus parámetros.

Requisitos relacionados: RNF-07, RNF-22, RNF-24.

Criterios relacionados: CA-38, CA-47.

Dependencias: T19.

### T21. Implementar la estimación del tempo

- [ ] Estado: pendiente.

Objetivo: calcular los BPM utilizando el fragmento de audio real.

Resultado esperado: tempo estimado o mensaje informativo cuando no pueda determinarse.

Requisitos relacionados: RF-09, RF-22, RN-19.

Criterios relacionados: CA-08, CA-26.

Dependencias: T20.

### T22. Implementar la extracción de características numéricas

- [ ] Estado: pendiente.

Objetivo: extraer características musicales para entrenar Random Forest.

Resultado esperado: vectores numéricos consistentes para cada canción.

Requisitos relacionados: RF-04, RF-25, RNF-07.

Criterios relacionados: CA-03, CA-35.

Dependencias: T21.

### T23. Implementar la generación de espectrogramas log-Mel

- [ ] Estado: pendiente.

Objetivo: generar las representaciones musicales utilizadas por la CNN.

Resultado esperado: espectrogramas generados con 128 bandas Mel, FFT de 2.048 muestras y hop length de 512 muestras.

Requisitos relacionados: RF-05, RF-28, RNF-24.

Criterios relacionados: CA-04, CA-43.

Dependencias: T20.

### T24. Validar las dimensiones de los espectrogramas

- [ ] Estado: pendiente.

Objetivo: verificar la compatibilidad de las matrices con la entrada de la red neuronal.

Resultado esperado: espectrogramas con dimensiones de 128 x 1292 x 1.

Requisitos relacionados: RNF-18, RN-24, RN-30.

Criterios relacionados: CA-38, CA-43.

Dependencias: T23.

### T25. Preparar los datos de entrada para los modelos

- [ ] Estado: pendiente.

Objetivo: generar los espectrogramas, vectores numéricos y etiquetas correspondientes a cada conjunto.

Resultado esperado: datos de entrenamiento, validación y prueba preparados sin fuga de datos.

Requisitos relacionados: RF-24, RF-25, RNF-07, RNF-12.

Criterios relacionados: CA-32, CA-38, CA-47.

Dependencias: T13, T22, T24.

---

## Fase 4. Desarrollo y entrenamiento de modelos

### T26. Definir la arquitectura de la CNN

- [ ] Estado: pendiente.

Objetivo: construir una arquitectura neuronal sencilla y compatible con los espectrogramas.

Resultado esperado: arquitectura con capas convolucionales, ReLU, MaxPooling, Global Average Pooling, Dense, Dropout y Softmax.

Requisitos relacionados: RF-24, RNF-18, RN-22.

Criterios relacionados: CA-04, CA-05.

Dependencias: T25.

### T27. Configurar los parámetros de entrenamiento

- [ ] Estado: pendiente.

Objetivo: definir los hiperparámetros iniciales de la red neuronal.

Resultado esperado: configuración documentada de optimizador, función de pérdida, épocas y tamaño de lote.

Requisitos relacionados: RNF-19, RNF-22.

Criterios relacionados: CA-37.

Dependencias: T26.

### T28. Entrenar la red neuronal convolucional

- [ ] Estado: pendiente.

Objetivo: permitir que la CNN aprenda los patrones de los géneros musicales.

Resultado esperado: red neuronal entrenada utilizando los datos autorizados de entrenamiento.

Requisitos relacionados: RF-24, RN-03, RN-22.

Criterios relacionados: CA-05.

Dependencias: T27.

### T29. Validar y ajustar la red neuronal

- [ ] Estado: pendiente.

Objetivo: supervisar el rendimiento de la CNN y reducir posibles problemas de sobreajuste.

Resultado esperado: modelo ajustado utilizando únicamente los conjuntos de entrenamiento y validación.

Requisitos relacionados: RNF-17, RNF-19.

Criterios relacionados: CA-37.

Dependencias: T28.

### T30. Guardar la CNN y su configuración

- [ ] Estado: pendiente.

Objetivo: conservar el modelo entrenado, las etiquetas y los parámetros de procesamiento.

Resultado esperado:

- cnn_model.keras.
- labels.json.
- preprocessing_config.json.

Requisitos relacionados: RNF-20, RNF-28.

Criterios relacionados: CA-34, CA-47.

Dependencias: T29.

### T31. Entrenar Random Forest

- [ ] Estado: pendiente.

Objetivo: construir un modelo tradicional de Machine Learning para comparar su rendimiento con la CNN.

Resultado esperado: modelo Random Forest entrenado con características numéricas del audio.

Requisitos relacionados: RF-25, RN-23.

Criterios relacionados: CA-35.

Dependencias: T25.

### T32. Validar y guardar Random Forest

- [ ] Estado: pendiente.

Objetivo: ajustar el modelo utilizando los datos de validación y conservarlo para su evaluación.

Resultado esperado: modelo random_forest.pkl y configuración documentada.

Requisitos relacionados: RNF-17, RNF-22, RNF-23.

Criterios relacionados: CA-35, CA-36.

Dependencias: T31.

---

## Fase 5. Evaluación de los modelos

### T33. Evaluar la CNN

- [ ] Estado: pendiente.

Objetivo: medir el rendimiento final de la red neuronal con canciones independientes.

Resultado esperado: métricas reales de exactitud, precisión, recall y F1-score.

Requisitos relacionados: RNF-08, RNF-11, RNF-26.

Criterios relacionados: CA-13, CA-28, CA-33.

Dependencias: T30.

### T34. Evaluar Random Forest

- [ ] Estado: pendiente.

Objetivo: medir el rendimiento del modelo de referencia.

Resultado esperado: métricas obtenidas utilizando las mismas canciones de prueba de la CNN.

Requisitos relacionados: RNF-08, RNF-23.

Criterios relacionados: CA-33, CA-35.

Dependencias: T32, T33.

### T35. Generar matrices de confusión

- [ ] Estado: pendiente.

Objetivo: identificar los géneros que presentan mayores errores de clasificación.

Resultado esperado: matrices de confusión independientes para ambos modelos.

Requisitos relacionados: RNF-08, RNF-26.

Criterios relacionados: CA-33, CA-39, CA-46.

Dependencias: T33, T34.

### T36. Generar curvas de entrenamiento

- [ ] Estado: pendiente.

Objetivo: analizar el comportamiento de la CNN durante su entrenamiento.

Resultado esperado: gráficas de exactitud y pérdida de entrenamiento y validación.

Requisitos relacionados: RNF-19, RNF-22.

Criterios relacionados: CA-37.

Dependencias: T30.

### T37. Comparar los modelos

- [ ] Estado: pendiente.

Objetivo: comparar el rendimiento de la CNN y Random Forest.

Resultado esperado: reporte comparativo de métricas generales e individuales por género.

Requisitos relacionados: RNF-23, RNF-26.

Criterios relacionados: CA-35, CA-36, CA-39, CA-46.

Dependencias: T35, T36.

### T38. Documentar y revisar los resultados

- [ ] Estado: pendiente.

Objetivo: comprobar si la CNN alcanza la meta del 80 % y documentar sus limitaciones.

Resultado esperado: archivo metrics.json y reporte de evaluación con resultados reales.

Requisitos relacionados: RNF-11, RNF-22.

Criterios relacionados: CA-28, CA-33, CA-36.

Dependencias: T37.

Si la meta no se alcanza, se deberá documentar el incumplimiento y revisar el modelo antes de aprobar su integración definitiva.

---

## Fase 6. Desarrollo del backend

### T39. Implementar la carga de la CNN entrenada

- [ ] Estado: pendiente.

Objetivo: cargar el modelo .keras, sus etiquetas y su configuración.

Resultado esperado: modelo disponible para realizar predicciones.

Requisitos relacionados: RF-21, RNF-20, RNF-28.

Criterios relacionados: CA-25, CA-34, CA-47.

Dependencias: T30, T38.

### T40. Implementar el módulo de predicción

- [ ] Estado: pendiente.

Objetivo: generar predicciones musicales utilizando espectrogramas log-Mel.

Resultado esperado: género principal y probabilidades estimadas de clasificación.

Requisitos relacionados: RF-06, RF-07, RF-08.

Criterios relacionados: CA-05, CA-06, CA-07, CA-30.

Dependencias: T39.

### T41. Implementar la advertencia de baja confianza

- [ ] Estado: pendiente.

Objetivo: identificar predicciones con probabilidad máxima inferior al 50 %.

Resultado esperado: advertencia de baja confianza cuando corresponda.

Requisitos relacionados: RF-17, RN-14, RN-27.

Criterios relacionados: CA-21.

Dependencias: T40.

### T42. Configurar FastAPI

- [ ] Estado: pendiente.

Objetivo: establecer el servidor y la estructura inicial de la API REST.

Resultado esperado: backend ejecutándose correctamente.

Requisitos relacionados: RNF-01, RNF-09.

Criterios relacionados: CA-12, CA-14.

Dependencias: T03, T41.

### T43. Definir el contrato de comunicación de la API

- [ ] Estado: pendiente.

Objetivo: establecer los datos de entrada, respuestas JSON y mensajes de error.

Resultado esperado: contrato documentado para la comunicación entre frontend y backend.

Requisitos relacionados: RNF-09, RNF-15.

Criterios relacionados: CA-12.

Dependencias: T42.

### T44. Implementar el endpoint de clasificación

- [ ] Estado: pendiente.

Objetivo: recibir archivos de audio mediante POST /predict.

Resultado esperado: endpoint capaz de recibir archivos y devolver resultados de clasificación.

Requisitos relacionados: RF-01, RF-06, RF-07, RF-08, RNF-09.

Criterios relacionados: CA-01, CA-05, CA-06, CA-07, CA-12.

Dependencias: T43.

### T45. Integrar el tempo y los resultados

- [ ] Estado: pendiente.

Objetivo: organizar el género detectado, probabilidades, BPM y advertencias.

Resultado esperado: respuesta JSON completa y consistente.

Requisitos relacionados: RF-07, RF-08, RF-09, RF-17, RF-22.

Criterios relacionados: CA-06, CA-07, CA-08, CA-21, CA-26.

Dependencias: T21, T44.

### T46. Implementar el manejo de errores del backend

- [ ] Estado: pendiente.

Objetivo: gestionar archivos inválidos, errores de procesamiento y modelos no disponibles.

Resultado esperado: respuestas de error comprensibles sin generar predicciones falsas.

Requisitos relacionados: RF-11, RF-21, RNF-03.

Criterios relacionados: CA-09, CA-25.

Dependencias: T45.

### T47. Implementar la eliminación de archivos temporales

- [ ] Estado: pendiente.

Objetivo: evitar el almacenamiento permanente de los audios cargados.

Resultado esperado: archivos temporales eliminados después de análisis exitosos y errores.

Requisitos relacionados: RNF-10, RNF-13, RN-17.

Criterios relacionados: CA-15, CA-29.

Dependencias: T46.

### T48. Verificar la disponibilidad del backend y del modelo

- [ ] Estado: pendiente.

Objetivo: comprobar el funcionamiento de la API y la disponibilidad de la CNN.

Resultado esperado: endpoint GET /health y verificación del estado del servicio, si se aprueba el endpoint propuesto.

Requisitos relacionados: RF-21, RNF-09.

Criterios relacionados: CA-12, CA-25.

Dependencias: T47.

---

## Fase 7. Desarrollo del frontend

### T49. Preparar el entorno de React

- [ ] Estado: pendiente.

Objetivo: configurar el entorno de desarrollo del frontend.

Resultado esperado: proyecto React ejecutándose correctamente con las herramientas autorizadas.

Requisitos relacionados: RNF-02, RNF-05.

Dependencias: T04, T43.

### T50. Configurar Material UI

- [ ] Estado: pendiente.

Objetivo: preparar los componentes visuales de la aplicación.

Resultado esperado: Material UI integrado correctamente.

Requisitos relacionados: RNF-05.

Criterios relacionados: CA-40.

Dependencias: T49.

### T51. Diseñar la interfaz principal

- [ ] Estado: pendiente.

Objetivo: organizar la página principal de MelodIA.

Resultado esperado: interfaz intuitiva, accesible y adaptable.

Requisitos relacionados: RNF-05.

Criterios relacionados: CA-40.

Dependencias: T50.

### T52. Implementar el componente de carga de audio

- [ ] Estado: pendiente.

Objetivo: permitir la selección de archivos MP3 y WAV.

Resultado esperado: componente AudioUpload.jsx funcional.

Requisitos relacionados: RF-01, RF-03, RF-16.

Criterios relacionados: CA-01, CA-20.

Dependencias: T51.

### T53. Implementar las validaciones iniciales del frontend

- [ ] Estado: pendiente.

Objetivo: verificar el formato, tamaño y duración del archivo seleccionado cuando sea posible.

Resultado esperado: mensajes informativos y botón de análisis deshabilitado cuando no exista un archivo válido.

Requisitos relacionados: RF-12, RF-13, RF-18.

Criterios relacionados: CA-16, CA-17, CA-22.

Dependencias: T52.

### T54. Implementar el reproductor de audio

- [ ] Estado: pendiente.

Objetivo: permitir reproducir y pausar la canción seleccionada.

Resultado esperado: componente AudioPlayer.jsx funcional.

Requisitos relacionados: RF-02.

Criterios relacionados: CA-02.

Dependencias: T52.

### T55. Implementar el servicio de comunicación con FastAPI

- [ ] Estado: pendiente.

Objetivo: enviar archivos de audio y recibir las respuestas de clasificación.

Resultado esperado: archivo api.js conectado con el backend.

Requisitos relacionados: RF-19, RNF-09.

Criterios relacionados: CA-12, CA-23.

Dependencias: T48, T53.

### T56. Implementar el botón de análisis

- [ ] Estado: pendiente.

Objetivo: permitir iniciar el procesamiento del audio seleccionado.

Resultado esperado: botón conectado con el servicio de comunicación.

Requisitos relacionados: RF-06, RF-18, RF-20.

Criterios relacionados: CA-05, CA-22, CA-24.

Dependencias: T55.

### T57. Implementar los estados de carga

- [ ] Estado: pendiente.

Objetivo: informar al usuario mientras se realiza el procesamiento.

Resultado esperado: indicador de carga y bloqueo de análisis simultáneos.

Requisitos relacionados: RF-20, RNF-06, RNF-15.

Criterios relacionados: CA-24.

Dependencias: T56.

### T58. Implementar la visualización del género musical

- [ ] Estado: pendiente.

Objetivo: mostrar el género con mayor probabilidad estimada.

Resultado esperado: componente GenreResults.jsx mostrando la clasificación principal.

Requisitos relacionados: RF-07.

Criterios relacionados: CA-06.

Dependencias: T57.

### T59. Implementar la visualización de probabilidades

- [ ] Estado: pendiente.

Objetivo: mostrar los porcentajes estimados de los géneros musicales.

Resultado esperado: distribución de probabilidades presentada de forma comprensible.

Requisitos relacionados: RF-08, RN-06.

Criterios relacionados: CA-07, CA-30.

Dependencias: T58.

### T60. Implementar la visualización del tempo

- [ ] Estado: pendiente.

Objetivo: mostrar los BPM estimados o el mensaje correspondiente cuando no puedan determinarse.

Resultado esperado: información del tempo visible en los resultados.

Requisitos relacionados: RF-09, RF-22.

Criterios relacionados: CA-08, CA-26.

Dependencias: T59.

### T61. Implementar las advertencias y mensajes de error

- [ ] Estado: pendiente.

Objetivo: informar al usuario sobre errores de conexión, archivos inválidos y predicciones de baja confianza.

Resultado esperado: mensajes comprensibles presentados en la interfaz.

Requisitos relacionados: RF-11, RF-17, RF-19, RF-21, RNF-03.

Criterios relacionados: CA-09, CA-21, CA-23, CA-25.

Dependencias: T60.

### T62. Implementar el nuevo análisis

- [ ] Estado: pendiente.

Objetivo: permitir seleccionar otra canción y limpiar los resultados anteriores.

Resultado esperado: nuevos análisis sin reiniciar la aplicación y sin mostrar resultados desactualizados.

Requisitos relacionados: RF-10, RF-16, RF-23.

Criterios relacionados: CA-10, CA-20, CA-27.

Dependencias: T61.

### T63. Verificar el diseño adaptable y la accesibilidad

- [ ] Estado: pendiente.

Objetivo: comprobar el funcionamiento de la interfaz en diferentes tamaños de pantalla y mediante teclado.

Resultado esperado: interfaz organizada, accesible y adaptable.

Requisitos relacionados: RNF-05.

Criterios relacionados: CA-40.

Dependencias: T62.

---

## Fase 8. Integración y pruebas

### T64. Ejecutar pruebas del procesamiento de audio

- [ ] Estado: pendiente.

Objetivo: verificar los procedimientos de carga, validación y transformación del audio.

Resultado esperado: reporte de pruebas de formatos, tamaño, duración, silencio, frecuencia de muestreo, recorte, relleno y espectrogramas.

Requisitos relacionados: RF-03, RF-12, RF-13, RF-14, RF-15, RF-26, RF-27, RF-28, RF-29.

Criterios relacionados: CA-03, CA-04, CA-09, CA-16, CA-17, CA-18, CA-19, CA-31, CA-38, CA-41, CA-42, CA-43, CA-44.

Dependencias: T25.

### T65. Ejecutar pruebas de calidad del dataset

- [ ] Estado: pendiente.

Objetivo: verificar las etiquetas, distribución y separación de los datos.

Resultado esperado: reporte que confirme la calidad del dataset y la ausencia de fuga de datos.

Requisitos relacionados: RNF-12, RNF-16, RNF-21, RNF-25, RNF-27.

Criterios relacionados: CA-32, CA-45, CA-48.

Dependencias: T13, T25.

### T66. Ejecutar pruebas del modelo neuronal

- [ ] Estado: pendiente.

Objetivo: verificar la carga del modelo, sus dimensiones de entrada, etiquetas y predicciones.

Resultado esperado: reporte de funcionamiento de la CNN y consistencia de sus resultados.

Requisitos relacionados: RF-06, RF-07, RF-08, RNF-18, RNF-20, RNF-28.

Criterios relacionados: CA-05, CA-06, CA-07, CA-30, CA-34, CA-38, CA-47.

Dependencias: T40, T64, T65.

### T67. Ejecutar pruebas del backend

- [ ] Estado: pendiente.

Objetivo: comprobar los endpoints, respuestas JSON, manejo de errores y eliminación de archivos temporales.

Resultado esperado: reporte de funcionamiento de la API REST.

Requisitos relacionados: RNF-03, RNF-09, RNF-10, RNF-13.

Criterios relacionados: CA-09, CA-12, CA-14, CA-15, CA-25, CA-29.

Dependencias: T48, T66.

### T68. Ejecutar pruebas del frontend

- [ ] Estado: pendiente.

Objetivo: verificar la carga, reproducción, estados, resultados y mensajes de error.

Resultado esperado: reporte de pruebas funcionales de la interfaz.

Requisitos relacionados: RF-01, RF-02, RF-10, RF-16, RF-18, RF-19, RF-20, RF-23, RNF-05.

Criterios relacionados: CA-01, CA-02, CA-10, CA-20, CA-22, CA-23, CA-24, CA-27, CA-40.

Dependencias: T63.

### T69. Ejecutar pruebas de integración

- [ ] Estado: pendiente.

Objetivo: comprobar el funcionamiento conjunto del frontend, backend y red neuronal.

Resultado esperado: flujo completo de clasificación musical funcionando correctamente.

Requisitos relacionados: RF-01, RF-06, RF-07, RF-08, RF-09, RNF-09.

Criterios relacionados: CA-01, CA-05, CA-06, CA-07, CA-08, CA-12.

Dependencias: T67, T68.

### T70. Verificar los criterios de aceptación

- [ ] Estado: pendiente.

Objetivo: comprobar todos los criterios definidos en PROJECT_SPEC.md.

Resultado esperado: matriz de aceptación con el estado y evidencia de CA-01 a CA-48.

Requisitos relacionados: todos los requisitos del proyecto.

Criterios relacionados: CA-01 a CA-48.

Dependencias: T38, T69.

### T71. Corregir los errores identificados

- [ ] Estado: pendiente.

Objetivo: resolver los errores encontrados durante las pruebas.

Resultado esperado: errores corregidos y pruebas afectadas ejecutadas nuevamente.

Requisitos relacionados: requisitos afectados por los errores.

Criterios relacionados: criterios de aceptación afectados.

Dependencias: T70.

---

## Fase 9. Documentación final

### T72. Documentar la instalación y ejecución

- [ ] Estado: pendiente.

Objetivo: explicar cómo instalar las dependencias y ejecutar MelodIA.

Resultado esperado: instrucciones de instalación y ejecución documentadas en README.md.

Requisitos relacionados: RNF-01, RNF-22.

Dependencias: T71.

### T73. Documentar el dataset y los modelos

- [ ] Estado: pendiente.

Objetivo: registrar las fuentes de datos, etiquetas, parámetros de procesamiento, arquitectura neuronal e hiperparámetros.

Resultado esperado: documentación técnica del proceso de entrenamiento.

Requisitos relacionados: RNF-16, RNF-22, RNF-25, RNF-28.

Criterios relacionados: CA-45, CA-47, CA-48.

Dependencias: T38, T71.

### T74. Documentar los resultados y limitaciones

- [ ] Estado: pendiente.

Objetivo: registrar las métricas reales, comparación de modelos, limitaciones y resultados de las pruebas.

Resultado esperado: informe final de evaluación del proyecto.

Requisitos relacionados: RNF-08, RNF-11, RNF-23, RNF-26.

Criterios relacionados: CA-28, CA-33, CA-35, CA-36, CA-37, CA-39, CA-46.

Dependencias: T73.

### T75. Realizar la revisión final del proyecto

- [ ] Estado: pendiente.

Objetivo: comprobar que MelodIA cumple las especificaciones, restricciones y criterios de aceptación.

Resultado esperado: proyecto funcional, documentado y revisado, con los incumplimientos pendientes registrados.

Requisitos relacionados: todos los requisitos del proyecto.

Criterios relacionados: CA-01 a CA-48.

Dependencias: T72, T74.

---

## 3. Resumen de tareas

| Fase | Descripción | Cantidad |
|------|-------------|----------|
| 1 | Preparación del entorno | 5 |
| 2 | Preparación del dataset | 8 |
| 3 | Procesamiento de audio | 12 |
| 4 | Desarrollo y entrenamiento de modelos | 7 |
| 5 | Evaluación de modelos | 6 |
| 6 | Desarrollo del backend | 10 |
| 7 | Desarrollo del frontend | 15 |
| 8 | Integración y pruebas | 8 |
| 9 | Documentación final | 4 |
| Total | | 75 |

## 4. Condiciones para completar una tarea

Una tarea podrá marcarse como completada cuando:

- Se haya alcanzado su objetivo.
- Se haya obtenido el resultado esperado.
- Se hayan respetado los requisitos relacionados.
- Se hayan ejecutado las pruebas correspondientes.
- Se hayan documentado los cambios.
- Se hayan corregido los errores que impidan su cumplimiento.

No se marcarán tareas como completadas únicamente porque se haya generado código.

## 5. Condiciones para finalizar el proyecto

El proyecto podrá considerarse finalizado cuando:

- La aplicación web funcione correctamente.
- La CNN esté entrenada, evaluada e integrada.
- Random Forest haya sido evaluado como modelo de referencia.
- Los géneros musicales autorizados estén contemplados.
- El frontend y el backend estén integrados.
- Los resultados de clasificación se visualicen correctamente.
- Se hayan ejecutado las pruebas correspondientes.
- Se hayan revisado los 48 criterios de aceptación.
- Se hayan documentado los resultados reales.
- Se hayan respetado las restricciones del proyecto.
- Los incumplimientos pendientes hayan sido resueltos o aceptados expresamente por los responsables del proyecto.

El desarrollo deberá seguir el orden establecido y no podrá incorporar funcionalidades adicionales sin autorización.
