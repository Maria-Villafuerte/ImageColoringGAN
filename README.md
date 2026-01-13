# Image Colorization GAN

Proyecto final del curso "Deep Learning y Sistemas Inteligentes" - Colorización automática de imágenes en escala de grises usando Redes Generativas Adversarias (GANs).

## Descripción

Este proyecto implementa una GAN condicional que aprende a colorizar imágenes en escala de grises de manera automática. El sistema utiliza una arquitectura híbrida VGG16-U-Net como generador y PatchGAN como discriminador, trabajando en el espacio de color LAB para optimizar el proceso de aprendizaje.

## Arquitectura

- **Generador**: VGG16-U-Net con transfer learning, mecanismos de atención y colorización condicional por clase (8 categorías)
- **Discriminador**: PatchGAN para evaluación local del realismo
- **Dataset**: 6,899 imágenes en 8 clases (airplane, car, cat, dog, flower, fruit, motorbike, person)
- **Resolución**: 128×128 píxeles

## Instalación

```bash
# Clonar el repositorio
git clone https://github.com/DiegoDuaS/ImageColoringGAN
cd ImageColoringGAN

# Crear entorno virtual
python -m venv myenv
source myenv/bin/activate  # En Windows: myenv\Scripts\activate

# Instalar dependencias
pip install -r requirements.txt
```

## Preparación de Datos

```bash
# Descomprimir dataset procesado
unzip ImagesProcessed.zip

# O procesar desde cero (imágenes raw en ImagesRaw/)
python convert.py
```

## Entrenamiento

```bash
python train_gan.py
```

El entrenamiento incluye:
- Checkpointing automático cada 5 épocas
- Monitoreo con TensorBoard
- Samples de validación periódicos
- Learning rate scheduling

## Análisis Explicable (XAI)

```bash
python Explainable_AI.py
```

Genera visualizaciones de:
- Mapas de saliencia
- Grad-CAM
- Atribución de características por categoría

## Resultados

- **PSNR**: 27.79 dB (media)
- **SSIM**: 0.943 (alta similitud estructural)
- **Inception Score**: 2.59
- Mejor época: 16

## Autores

Grupo #6:
- Fabiola Contreras (22787)
- Diego Duarte (22075)
- José Marchena (22398)
- Sofía Velásquez (22049)
- María José Villafuerte (22129)

**Profesor**: Luis Alberto Suriano Saravia  
**Universidad del Valle de Guatemala** - 2025

## Referencias

- [Pix2Pix Paper](https://arxiv.org/abs/1611.07004)
- [U-Net Architecture](https://arxiv.org/abs/1505.04597)
- [VGG16](https://arxiv.org/abs/1409.1556)

---

**Nota**: El proyecto requiere GPU para entrenamiento. El modelo pre-entrenado está disponible en `checkpoints/checkpoint_epoch_0016.pth`.