## Definir metodo o funcion del widget

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

## Incompativilidad entre dependencias

Al intentar actualizar una dependencia es posible que te muestre el siguiente error

    Because bqn depends on google_fonts ^5.1.0 which depends on http ^1.0.0, http ^1.0.0 is required.
    So, because bqn depends on http ^0.13.5, version solving failed.

Este error se debe a que una dependencia depende de otra, y al actualizar una no puede funcionar debido a que de la que depende esta en una version antigua

Para soluciona este error, hay que actualizar desde el **_pubspeck.yaml_** la dependencia de la que depende la dependencia ya actualizada, en este caso, la dependencia **_http_**

---

## Error en la importacion de **_asset_manifest.dart_** en un widget

el siguiente erro

    /C:/Users/Carlos%20Rodriguez/AppData/Local/Pub/Cache/hosted/pub.dev/google_fonts-3.0.1/lib/src/google_fonts_base.dart:14:1: Error: 'AssetManifest' is imported from both 'package:flutter/src/services/asset_manifest.dart' and 'package:google_fonts/src/asset_manifest.dart'.
    import 'asset_manifest.dart';

Menciona que la **_asset_manifest.dart_** se esta mandando a llamar desde multiples lugares

Para solucionar esto. lo unico que hay que hacer es actualizar la dependencia, en este caso **_google_fonts_**

---
