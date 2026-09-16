# Reconstrucción Estéreo 3D: Geometría Epipolar, SGBM y RAFT-Stereo

Este proyecto implementa un flujo completo de visión por computadora para la reconstrucción tridimensional de objetos a partir de imágenes estéreo. Incluye la calibración de cámaras mediante el método de Zhang, la rectificación epipolar, la estimación de disparidad comparando un algoritmo clásico (StereoSGBM) con Deep Learning (RAFT-Stereo), y la proyección a nubes de puntos 3D métricas.

---

## 📁 Estructura del Repositorio

```text
├── data/
│   ├── calibracion/       # Imágenes del tablero de ajedrez (Cámara Izq / Der)
│   └── objetos/           # Pares estéreo de los 3 objetos analizados
├── notebooks/
│   └── Reconstruccion_Estereo.ipynb  # Cuaderno principal con el pipeline
├── resultados/
│   ├── nubes_3d/          # Modelos tridimensionales exportados (.ply, .html)
│   └── comparativas/      # Mapas de disparidad y vistas comparativas
├── README.md              # Documentación técnica del proyecto
└── requirements.txt       # Dependencias del sistema
