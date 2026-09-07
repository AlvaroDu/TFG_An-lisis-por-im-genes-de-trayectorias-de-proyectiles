[README.md](https://github.com/user-attachments/files/31927703/README.md)
# Análisis por imágenes de trayectorias de proyectiles

Código y datos de ejemplo del Trabajo de Fin de Grado *Análisis por imágenes de
trayectorias de proyectiles* (Grado en Ingeniería Mecánica, Universidad Carlos III
de Madrid). El trabajo compara dos enfoques de visión por computador —un modelo de
segmentación por aprendizaje profundo (**SAM**) frente a **visión clásica** con
OpenCV— aplicados al seguimiento de cuerpos en movimiento y a la caracterización de
imágenes, a lo largo de cinco casos de dificultad creciente.

Cada carpeta es autocontenida: incluye el código final del caso y una carpeta
`datos/` con las imágenes de entrada que ese código lee. Al ejecutar, los resultados
se escriben en una carpeta `resultados/` (creada automáticamente).

## Estructura

```
Escritorio/       Primer contacto con SAM sobre una escena de composición desconocida
Extensiometria/   Seguimiento de dos marcadores en un ensayo de tracción (SAM vs OpenCV)
Micrografia/      Caracterización de fibras en micrografías (post-proceso de watershed)
Abaqus/           Validación del método sobre simulaciones de movimiento conocido
Casos_reales/     Aplicación a un ensayo de impacto real grabado con cámara rápida
```

Dentro de cada carpeta:

- `*_final.ipynb` — el código final del caso.
- `datos/` — imágenes o fotogramas de entrada.
- `resultados/` — se genera al ejecutar (no incluida en el repositorio).

## Requisitos

- Python 3.10+ (el trabajo se desarrolló con un entorno `conda`).
- Paquetes comunes: `numpy`, `opencv-python`, `matplotlib`, `openpyxl`.
- Solo para los códigos de SAM (Escritorio y `SAM_tiff_*`): `torch`,
  `torchvision` y `segment-anything`.

Instalación rápida de las dependencias comunes:

```bash
pip install numpy opencv-python matplotlib openpyxl
```

Para los códigos de SAM, además:

```bash
pip install torch torchvision segment-anything
```

### Checkpoint de SAM (no incluido)

Los notebooks de SAM cargan el checkpoint `vit_h.pth` (~2,5 GB), que **no se
incluye** en el repositorio por su tamaño. Se descarga desde el repositorio oficial
de *Segment Anything* (Meta AI) y se coloca junto al notebook (o se ajusta la
variable `ruta_checkpoint` a su ubicación).

## Cómo ejecutar

1. Abrir el notebook del caso.
2. Comprobar que la carpeta `datos/` contiene las imágenes de entrada (ya incluidas).
3. Ejecutar las celdas de arriba abajo. Las salidas aparecen en `resultados/`.

Las rutas de entrada y salida están definidas como variables relativas al principio
de cada notebook (`ruta_...`, `carpeta_...`, `raiz_...`); basta con editarlas si se
quiere trabajar con otras imágenes o guardar los resultados en otro sitio.

## Nota sobre los datos incluidos

Para mantener el repositorio ligero solo se incluyen los datos que cada código
necesita para ejecutarse:

- **Extensiometría**: se incluye un único ensayo de ejemplo (`T2_01`). El código
  procesa por defecto todas las carpetas que encuentre dentro de `datos/`, de modo
  que pueden añadirse más ensayos con el mismo formato.
- **Abaqus**: se incluyen solo los fotogramas (`.png`) que los códigos leen, no los
  vídeos originales de la simulación.
- **Casos reales**: se incluye solo la ventana de vuelo libre de cada ensayo (los
  fotogramas que el código utiliza), no la secuencia completa.

## Autor

Álvaro Durán Escudero — Trabajo de Fin de Grado, UC3M.
