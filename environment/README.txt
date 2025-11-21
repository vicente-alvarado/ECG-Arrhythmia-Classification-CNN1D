https://www.tensorflow.org/install/source_windows?hl=en

**Paso 1 **
conda create -n py310 python=3.10
conda activate py310
conda install -c conda-forge cudatoolkit=11.2 cudnn=8.1.0 "numpy<2"
python -m pip install "tensorflow==2.10"

** Paso 2 (Opcional)**
pip uninstall numpy -y
pip install  "numpy<2"

* Paso 3*
import tensorflow as tf
print("TensorFlow GPU detectada:", tf.config.list_physical_devices('GPU'))
print(tf.test.is_gpu_available())

* Paso 4*
pip install ipykernel
python -m ipykernel install --user --name tensorflow2-10 --display-name "Python 2.10 (TF 2.10 GPU)"