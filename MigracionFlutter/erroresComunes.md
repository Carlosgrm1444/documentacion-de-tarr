## Errores comunes en widget badge

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
