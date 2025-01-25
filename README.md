# PROYECTO DEEP LEARNING ALEJANDRO RÍOS SILVA

Este proyecto tiene como objetivo desarrollar un **modelo de Deep Learning híbrido** para predecir el nivel de engagement de puntos de interés turísticos, integrando tanto características visuales como metadatos. Con esta aproximación, podemos optimizar estrategias de contenido y obtener *insights* valiosos para la toma de decisiones.

---

## Tabla de Contenidos
1. [Exploración de Datos](#exploración-de-datos)  
2. [Arquitectura del Modelo](#arquitectura-del-modelo)  
3. [Resultados del Entrenamiento](#resultados-del-entrenamiento)  
4. [Evaluación del Modelo](#evaluación-del-modelo)  
5. [Conclusión](#conclusión)

---

## Exploración de Datos

- **Registros totales:** 1,589  
- **Variables:** 7 características principales  
- **Valores nulos:** No se identificaron datos faltantes  
- **Transformación de tipos:** La variable `tags` estaba almacenada como tipo *object*, se transformó para su correcto procesamiento en el modelo

### Definición de la Variable de Engagement

El **engagement score** se definió como:  
engagement_score = likes - dislikes + bookmarks

yaml
Copiar
Esta fórmula fue seleccionada por considerarse la mejor representación del compromiso de los usuarios con los puntos de interés turísticos.

**Distribución del Engagement Score**  
- Presenta una alta concentración en valores cercanos a 0, con algunos *outliers* destacados.  

**División del dataset**  
- 70 % para entrenamiento  
- 15 % para validación  
- 15 % para prueba  

---

## Arquitectura del Modelo

El modelo híbrido combina una **ResNet50** preentrenada para la extracción de características de las imágenes y una **red fully connected** para procesar los metadatos.

1. **ResNet50**  
   - Modelo preentrenado en ImageNet para la extracción de características visuales.

2. **Red Fully Connected**  
   - Uso de *Dropout* para prevenir sobreajuste.  
   - Representación numérica de los `tags` utilizando *embeddings*.

3. **Regularización**  
   - Aplicación de técnicas como *Dropout*, *Early Stopping* y reducción de la tasa de aprendizaje para evitar estancamiento.

4. **Entrenamiento**  
   - **Función de Pérdida**: *CrossEntropyLoss*.  
   - **Optimizador**: *Adam* con *weight decay*.  
   - **Número de epochs**: 50.  

---

## Resultados del Entrenamiento

- Reducción rápida de la pérdida en las primeras épocas, con estabilización posterior.  
- Buen equilibrio entre las pérdidas de entrenamiento y validación.  
- La precisión de validación superó a la de entrenamiento en varias ocasiones, indicando buena capacidad de generalización.

---

## Evaluación del Modelo

Tras analizar la matriz de confusión:

- **Falsos negativos:** 15 casos  
- **Precisión general:** 92 %

**Interpretaciones:**
- El modelo logra alta precisión en la predicción del nivel de engagement para la mayoría de los puntos de interés turísticos.  
- Se obtuvo un buen equilibrio entre las métricas de precisión y *recall*.  
- El desempeño en la clase minoritaria (*High Engagement*) podría ser mejorado.

---

## Conclusión

El modelo logra una **precisión general del 92 %**, siendo efectivo al predecir el engagement de la mayoría de los POIs. Aunque aún existe margen de mejora, especialmente en la clase minoritaria (*High Engagement*), se considera que el desempeño global es muy bueno al mantener un equilibrio sólido entre precisión y *recall*.

---

### Autor
**Alejandro Ríos Silva**
