## Hay modificaciones dentro del directorio de flutter SDK
es posible que al querer aplicar el

    flutter upgrade

te muestre el siguiente error

>Your flutter checkout has local changes that would be erased by upgrading.

esto es porque la direccion del SDK es reconocida como un repositorio, entonces al actualizarla la detecta como si de un pull se tratara, pero mediante el tiempo de uso se han modificado ciertos archivos y detecta que hay cambios, entonces lo que hay que hacer es irse a la carpeta del SDK de flutter y ya sea en GIT BASH o en la forma que mas te sea comoda, realizar el commit y ya podras actualizar flutter

---