# VirtualPaint 
Virtual Ink with OpenCV in Python.
Este proyecto utiliza Computer Vision para transformar tu cámara web en un lienzo interactivo. A través del seguimiento de objetos por color en tiempo real, permite al usuario "pintar" en el aire y ver los resultados reflejados instantáneamente en la pantalla.

https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExZmF6MW5ibWxobHd1eWJsa3IzOHM5ZXpnM3Q0bGtsOGt3amh2NXZvcyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/vvxP56uvS9S6ADC2BH/giphy.gif

🌟 Características Destacadas
Detección Multicolores: Configurado para detectar y dibujar con 4 colores distintos simultáneamente (Naranja, Morado, Verde y Azul).

Persistencia de Trazo: Implementa un sistema de almacenamiento de puntos que mantiene el dibujo en pantalla mientras la aplicación esté ejecutándose.

Precisión de Contornos: Utiliza la aproximación de polígonos (approxPolyDP) y rectángulos delimitadores para encontrar el centro exacto de la "punta del marcador".

Filtrado de Ruido: Solo detecta objetos con un área mayor a 500 píxeles para evitar trazos accidentales por ruido visual.

🛠️ Detalles Técnicos
Segmentación en Espacio HSV
A diferencia del espacio RGB, el código utiliza HSV (Hue, Saturation, Value) para definir los rangos de color. Esto permite que la detección sea más robusta ante cambios de iluminación.

Rango de colores configurado:

Naranja/Amarillo

Morado

Verde

Azul

Lógica de Funcionamiento
findColor(): Convierte cada frame a HSV y aplica una máscara (cv2.inRange) por cada color definido. Si encuentra el color, extrae sus coordenadas.

getContours(): Analiza la máscara binaria, encuentra los contornos de los objetos y calcula el punto medio superior (x + w // 2, y) para simular la punta de un pincel.

drawOnCanvas(): Itera sobre la lista de puntos acumulados y los dibuja sobre el frame actual, creando el efecto de dibujo permanente.

🚀 Requisitos e Instalación
Dependencias:
Necesitas Python 3.x y las librerías opencv-python y numpy.

Bash
pip install opencv-python numpy
Ejecución:
Solo conecta tu webcam y ejecuta el script:

Bash
python main.py
Interacción:

Usa objetos de colores sólidos frente a la cámara.

Presiona la tecla 'q' para salir de la aplicación.

📈 Parámetros de Configuración
Puedes ajustar el comportamiento del pincel modificando estas variables en el código:

myColors: Modifica los valores HSV para detectar nuevos objetos.

area > 500: Aumenta este valor si hay mucho ruido en tu entorno o disminúyelo para detectar objetos más pequeños.

cv2.circle(..., 10, ...): Cambia el número 10 para hacer el trazo más grueso o más delgado.

Notas de autor
¡Las contribuciones son bienvenidas!
