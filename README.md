# Reconstrucción Estéreo 3D: Geometría Epipolar, SGBM y RAFT-Stereo

Este repositorio contiene la implementación completa de un pipeline de visión por computadora para la reconstrucción 3D a partir de un sistema estéreo de dos cámaras paralelas. Incluye la calibración monocular y estéreo mediante el método de Zhang, rectificación epipolar, estimación de disparidad comparando un enfoque clásico (StereoSGBM) con Deep Learning (RAFT-Stereo) y la proyección a espacio tridimensional métrico.

---

## 📁 Estructura del Repositorio

```text
.
├── data/
│   ├── calibracion/            # Imágenes originales del tablero de ajedrez (Cámara Izq / Der)
│   └── objetos/                # Pares estéreo originales de los 3 objetos analizados
├── notebooks/
│   └── Reconstruccion_Estereo.ipynb  # Cuaderno con la ejecución completa y visualizaciones 3D
├── resultados/
│   ├── deteccion_esquinas/     # 10 pares de imágenes con las esquinas del tablero detectadas
│   ├── parametros_calibracion/ # Archivos (.npz y .txt) con matrices K, R, T, E, F y distorsión
│   └── rectificacion_estereo/  # Matriz de reproyección Q e imágenes rectificadas por objeto
├── README.md                   # Documentación técnica del proyecto
```

> **Nota sobre los resultados:** Para optimizar el almacenamiento del repositorio y cumplir con las limitaciones de espacio de GitHub, los datos de inspección livianos (detección de esquinas, matrices calculadas e imágenes rectificadas) se encuentran subidos en la carpeta `resultados/`. Los mapas de disparidad pesados de alta resolución y las nubes de puntos 3D interactivas se conservan generados y listos para su inspección directa dentro del cuaderno ejecutable `notebooks/Reconstruccion_Estereo.ipynb`.

---

## ⚙️ Flujo de Trabajo

1. **Calibración Estéreo (Algoritmo de Zhang):**
   * Detección de esquinas sub-píxel en el tablero de ajedrez.
   * Estimación de parámetros intrínsecos ($K_L, K_R$), coeficientes de distorsión y parámetros extrínsecos de rotación ($R$) y traslación ($T$).
2. **Rectificación Epipolar:**
   * Alineación de líneas epipolares horizontales para restringir la búsqueda de correspondencias al eje $X$.
   * Generación de la matriz de reproyección $Q$.
3. **Mapas de Disparidad:**
   * **StereoSGBM:** Algoritmo semi-global clásico basado en correlación de bloques.
   * **RAFT-Stereo:** Red neuronal profunda recurrente que estima disparidad densa en zonas lisas o sin textura.
4. **Reconstrucción 3D:**
   * Proyección de la disparidad a coordenadas métricas $(X, Y, Z)$ en milímetros usando la matriz $Q$.

---

## 🚀 Visualización:
   Abre el cuaderno `notebooks/Reconstruccion_Estereo.ipynb` en Google Colab o Jupyter Notebook para revisar las celdas ejecutadas con las métricas, mapas de disparidad y renderizado 3D de cada objeto.
