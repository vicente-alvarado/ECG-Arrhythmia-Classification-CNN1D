## Clasificación de arritmias en ECG con CNN 1D

Este repositorio contiene un ejemplo sencillo de **clasificación de arritmias en señales ECG** usando una **CNN 1D** implementada en el notebook `CNN_ECG_Workshop.ipynb`.

![Arquitectura CNN1D](assets/ArquitectureCNN1D.png)

### ¿Qué incluye?

- Notebook `CNN_ECG_Workshop.ipynb` con:
  - carga de las señales ECG desde `dataset/`,
  - Dataset previamente procesado listo para entrenar,
  - definición, entrenamiento y evaluación de la CNN 1D.
- Carpeta `dataset/` con los conjuntos de entrenamiento, validación y prueba.
- Carpeta `assets/` con la figura de la arquitectura de la red.

El modelo entrenado (`CNN_ECG_model.h5`) se distribuye como **asset de una Release** en GitHub y debe colocarse en la carpeta `model/` para usarlo desde el notebook.

### Pasos adicionales si se trabaja en Google Colab

### Opción 1:
### 1. Montar la carpeta drive de Google Colab
from google.colab import drive
drive.mount('/content/drive')

import os
drive_path = '/content/drive/MyDrive/Colab Notebooks/ECG-Arrhythmia-Classification-CNN1D/ECG-Arrhythmia-Classification-CNN1D-main/'

### 2. Entrar en la carpeta del proyecto (¡Paso crucial!)
import os
os.chdir(drive_path)

### 3. Verificar que estamos dentro (deberías ver archivos como 'README.md', carpetas de datos, etc.)
print("Directorio actual:", os.getcwd())
!ls

### Opción 2:
### 1. Clonar tu repositorio específico
!git clone https://github.com/vicente-alvarado/ECG-Arrhythmia-Classification-CNN1D.git

### 2. Entrar en la carpeta del proyecto (¡Paso crucial!)
import os
os.chdir('ECG-Arrhythmia-Classification-CNN1D')

### 3. Verificar que estamos dentro (deberías ver archivos como 'README.md', carpetas de datos, etc.)
print("Directorio actual:", os.getcwd())
!ls
