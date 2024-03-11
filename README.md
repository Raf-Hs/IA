# IA
Documentación de Detección

Este repositorio contiene la documentación para proyectos de detección de objetos y personas utilizando diferentes modelos y herramientas.
Proyectos

    ContainerDeteccion: Proyecto para la detección de objetos en contenedores.
    LocalDeteccion: Proyecto para la detección de objetos en entorno local.

Inicio del Contenedor

Para iniciar el contenedor, utiliza los siguientes comandos:

bash

docker/run.sh
docker/run.sh --volume ~/Container-Local:/jetson-inference/Container-Local

Se requerirá ingresar la contraseña.
Detección de Personas

Puedes realizar la detección de personas utilizando los siguientes comandos:

bash

./detectnet.py /dev/video0
./imagenet.py /dev/video0
./facenet.py /dev/video0
./my-detection.py /dev/video0
python3 my-det.py --threshold 0.9
python3 cv.py
python3 /my_project/Chess.py --threshold 0.7
depthnet /dev/video0
posenet /dev/video0

Entrenamiento de Modelos

Para el entrenamiento de modelos, sigue este proceso:

    Crea un archivo de etiquetas:

bash

touch labels.txt
nano labels.txt

Escribe los nombres de las etiquetas, guarda el archivo (Ctrl + o) y cierra el editor (Ctrl + x).

    Abre la cámara:

bash

camera-capture /dev/video0

    Utiliza el comando para entrenar:

bash

python3 train_ssd.py --dataset-type=voc --data=data/plagas3 --model-dir=models/plagas3 --batch-size=2 --workers=1 --epochs=1

Para entrenar y apagar el sistema después del entrenamiento, utiliza:

bash

python3 train_ssd.py --dataset-type=voc --data=data/plagas3 --model-dir=models/plagas3 --batch-size=2 --workers=1 --epochs=1 && sudo shutdown -h +1

Recomendaciones

    Se recomienda crear una clase primero, entrenarla y luego agregar otras clases.
    Antes de modificar modelos entrenados, realiza una copia de seguridad.
    Después de entrenar un modelo nuevamente, se genera un nuevo archivo ONYX.

Escaneo de Personas

Para el escaneo de personas:

    Mirar directamente a la cámara.
    Tomar fotos desde 9 ángulos diferentes.
    Tomar 100 fotos por ángulo.
    Recoger el cabello y evitar joyas.
    No incluir orejas ni cabello, y definir bien los márgenes.

Otros Comandos Útiles

    Comando para borrar carpetas (¡CUIDADO!): rm -r
    Comando para copiar una carpeta: cp -r original copia
    Ver el archivo más reciente: ls -l | grep "^-" | wc -l
    Comando para dar permisos a una carpeta: sudo chmod -R a+rwx Container-Local
