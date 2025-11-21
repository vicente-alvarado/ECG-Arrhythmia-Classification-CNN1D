## Clasificación de arritmias en ECG con CNN 1D

Este repositorio contiene el material de la charla/taller **ECG Arrhythmia Classification con redes convolucionales 1D (CNN1D)**.  
El flujo principal está implementado en el notebook `CNN_ECG_Workshop.ipynb`, donde se carga el dataset de ECG, se entrena una CNN 1D y se evalúa su rendimiento.

## Contenido del repositorio

- **`CNN_ECG_Workshop.ipynb`**: notebook principal con el pipeline de:
  - carga de datos de ECG,
  - preprocesamiento,
  - definición de la arquitectura CNN1D,
  - entrenamiento y evaluación.
- **`assets/`**:
  - `ArquitectureCNN1D.png`: esquema de la arquitectura convolucional 1D utilizada.
- **`dataset/`**:
  - `train_x.txt`, `train_y.txt`: datos y etiquetas de entrenamiento.
  - `val_x.txt`, `val_y.txt`: datos y etiquetas de validación.
  - `test_x.txt`, `test_y.txt`: datos y etiquetas de prueba.
- **`environment/README.txt`**:
  - instrucciones para crear el entorno de ejecución con **TensorFlow 2.10 GPU** mediante Conda.
- **`model/`** (ignorada por git):
  - contiene el archivo de pesos entrenados `CNN_ECG_model.h5`, que se distribuye como **asset de una GitHub Release**, no como parte del repo.

## Entorno de ejecución (TensorFlow 2.10 GPU)

Resumen de los pasos indicados en `environment/README.txt`:

```bash
conda create -n py310 python=3.10
conda activate py310
conda install -c conda-forge cudatoolkit=11.2 cudnn=8.1.0 "numpy<2"
python -m pip install "tensorflow==2.10"

# Opcional
pip uninstall numpy -y
pip install "numpy<2"

# Verificar que TensorFlow ve la GPU
python -c "import tensorflow as tf; print(tf.config.list_physical_devices('GPU')); print(tf.test.is_gpu_available())"

# (Opcional) Kernel de Jupyter
pip install ipykernel
python -m ipykernel install --user --name tensorflow2-10 --display-name \"Python 3.10 (TF 2.10 GPU)\"
```

## Modelo pre-entrenado y Releases de GitHub

El archivo de pesos **`CNN_ECG_model.h5`** no se versiona en el repositorio (está ignorado en `.gitignore`) y se publica como **asset de una Release** en GitHub.

Pasos para crear/actualizar la release:

1. Ir al repositorio en GitHub:  
   `https://github.com/vicente-alvarado/ECG-Arrhythmia-Classification-CNN1D`
2. Abrir la pestaña **Releases** → **Draft a new release** (o **Edit** una release existente).
3. Elegir un tag, por ejemplo: `v1.0.0`.
4. Título sugerido: `Modelo CNN ECG v1.0.0`.
5. Arrastrar el archivo `model/CNN_ECG_model.h5` a la sección **Attach binaries by dropping them here**.
6. Publicar la release.

## Uso del modelo en el notebook

Una vez descargado `CNN_ECG_model.h5` desde la Release de GitHub y colocado en la carpeta `model/`, se puede cargar con Keras (ejemplo típico):

```python
from tensorflow.keras.models import load_model

model = load_model("model/CNN_ECG_model.h5")
preds = model.predict(x_test)  # donde x_test son las señales de ECG de prueba
```

El notebook `CNN_ECG_Workshop.ipynb` se puede adaptar para:

- cargar directamente estos pesos pre-entrenados, o  
- continuar el entrenamiento (fine-tuning) sobre otros conjuntos de datos de ECG.


