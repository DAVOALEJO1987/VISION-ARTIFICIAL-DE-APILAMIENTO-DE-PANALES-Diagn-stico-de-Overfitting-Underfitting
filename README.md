
---

## ⚙️ Pipeline de Trabajo

### 1. Montaje de Drive y Preparación de Carpetas
- Se crean automáticamente las carpetas necesarias.
- Se cargan las imágenes en la carpeta `data/`.

### 2. Exploratory Data Analysis (EDA)
- Distribución de clases.
- Matriz de correlación de propiedades de imagen (dimensiones, brillo, blur).
- Histogramas RGB por clase y ejemplos de imágenes.

### 3. Preprocesamiento y Balanceo
- Redimensionado a **224×224** píxeles.
- Limpieza de dataset (imágenes corruptas o duplicadas).
- Split estratificado en **train/val/test**.
- **Balanceo con SMOTE** en el espacio de embeddings.

### 4. Entrenamiento con CNN (ResNet-18)
- Transfer Learning desde modelo preentrenado en ImageNet.
- Fine-tuning de la última capa.
- Optimización con **Adam** y **CrossEntropyLoss**.
- Registro de métricas por época (loss, accuracy).

### 5. Métricas de Eficiencia
- **Accuracy global**
- **mAP (Mean Average Precision)** ≥ 0.70
- **IoU (Intersection over Union)** > 0.50
- **FPS (Frames por segundo)** > 30

### 6. Inferencia
- Subida de una imagen en Colab.
- Clasificación en **BIEN / MAL apilado**.
- Visualización de probabilidades por clase.

---

## 📊 Resultados Esperados
- **Curvas de aprendizaje** claras (train vs val).
- Identificación automática de **overfitting / underfitting / comportamiento óptimo**.
- Reporte de métricas cuantitativas:
  - Accuracy
  - mAP
  - mIoU
  - FPS
- Clasificador robusto en tiempo real para entornos industriales.

---

## 🧠 Diagnóstico Sistemático
El notebook integra reglas automáticas de diagnóstico:
- **Overfitting**: gap creciente entre train y val, val_loss ↑ mientras train_loss ↓.
- **Underfitting**: ambas accuracy bajas, curvas convergen en valores altos de loss.
- **Óptimo**: gap pequeño y estable, rendimiento balanceado en train y val.

---

## 🚀 Requisitos
- Python 3.9+
- Google Colab o entorno local con GPU
- Librerías principales:
  - `torch`, `torchvision`
  - `scikit-learn`, `imbalanced-learn`
  - `opencv-python`, `PIL`
  - `matplotlib`, `seaborn`

---

## 📌 Uso
1. Subir imágenes a la carpeta `data/` con las subcarpetas:

