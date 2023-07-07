## Definir metodo o funcion del widget badge

    Badge' isn't a function.
    Try correcting the name to match an existing function, or define a method or function named 'Badge'

Este error se da debido a que necesitamos una referencia a el widget para acceder a sus propiedades, entonces lo solucionaremos de la siguiente manera.

En la importacion del package **_Badges_** tendremos que hacer una referencia de ella de esta manera

```dart
import 'package:badges/badges.dart' as Badge;
```

Entonces ahora al usarla tendremos que acceder a sus propiedades por medio de la siguiente manera

```dart
Badge.Badge
```

Y un ejemplo podria ser el siguiente

Antes

```dart
    Badge(
        shape: BadgeShape.circle,
        ... ...
    )
```

Despues

```dart
    Badge.Badge(
        shape: Badge.BadgeShape.circle,
        ... ...
    )
```
---
