## Actualizar la version de compilacion

uno de los errores mas comunes en el gradle es la version de compilacion

    Warning: The plugin device_info_plus requires Android SDK version 33.

para esto tienes que buscar cual es la version necesaria para tu proyecto, que comunmente te lo dice en el error y modificarlo dentro del

> **_android/app/build.gradle_**

en este caso tengo esta version antigua en el **_compileSdkVersion_** y en el **_targetSdkVersion_**

```gradle
android {
    compileSdkVersion 31
    ... ...
  defaultConfig {
        minSdkVersion 21
        targetSdkVersion 31
        versionCode 51
        ... ...
  }
  ... ...
}
```

pero la que ocupo es la version 33, entonces lo cambiare a la siguiente manera

```gradle
android {
    compileSdkVersion 33
    ... ...
  defaultConfig {
        minSdkVersion 21
        targetSdkVersion 33
        versionCode 51
        ... ...
  }
  ... ...
}
```

---

## Actualizar version del gradle en el proyecto

Otro error puede ser el siguiente

```
* Where:
Build file 'C:\Users\Carlos Rodriguez\AppData\Local\Pub\Cache\hosted\pub.dev\device_info_plus-9.0.2\android\build.gradle' line: 30

* What went wrong:
A problem occurred evaluating project ':device_info_plus'.
> Could not find method namespace() for arguments [dev.fluttercommunity.plus.device_info] on extension 'android' of type com.android.build.gradle.LibraryExtension.
```

Este error se da debido a la incompatibilidad entre las dependencias ya cargadas en el proyecto, pues las dependencias tienen una version mas actualizada del gradle dentro de ellas pero el gradle tiene una version mas antigua que con la que son compatibles.

Para solucionar esto tienes que actualizar el gradle del proyecto, dentro de tu proyecto vas a la direccion

> **_android/build.gradle_**

y actualizas la version del gradle en las lineas

```gradle
buildscript {
  ... ...
    dependencies {
        classpath 'com.android.tools.build:gradle:4.1.0'
        ... ...
    }
}
```

a la nueva version de la siguiente manera

```gradle
buildscript {
  ... ...
    dependencies {
        classpath 'com.android.tools.build:gradle:7.3.0'
        ... ...
    }
}
```

---

## Actualizar version de gradle en las dependencias

Despues del error anterior es posible que te de un error similar al siguiente cuando intentes ejecutar tu aplicacion

```
* What went wrong:
The Android Gradle plugin supports only Kotlin Gradle plugin version 1.5.20 and higher.
The following dependencies do not satisfy the required version:
project ':hexcolor' -> org.jetbrains.kotlin:kotlin-gradle-plugin:1.3.50
```

este error es muy similar al anterior, su motivo es que ahora la version del gradle es demasiado actual para la version del gradle de las dependencias, para este la mejor opcion es actualizar cada dependencia que genera conflicto para que tenga mayor compatibilidad y funcione con la version mas reciente de gradle que tienes dentro de tu proyecto.

---

## El proyecto necesita una nueva version de **_Kotlin Gradle._**

Es posible que al ejecutar el proyecto muestre el siguiente error

    ┌─ Flutter Fix
    [!] Your project requires a newer version of the Kotlin Gradle plugin.
    Find the latest version on https://kotlinlang.org/docs/releases.html#release-details, then update C:\Source\beqon_flutter\android\build.gradle:
    ext.kotlin_version = '<latest-version>'
    Exception: Gradle task assembleDebug failed with exit code 1

Este error indica que la version del **_Kotlin Gradle_** es muy antigua para las necesidades del proyecto, para esto solo ocupamos cambiar la version en la siguiente directtion

> **_android/build.gradle_**

y actualizas la version del gradle en las lineas

```gradle
buildscript {
    ext.kotlin_version = '1.6.10'
    repositories {
      ... ...
    }
    ... ...
}
```

a la nueva version de la siguiente manera

```gradle
buildscript {
    ext.kotlin_version = '1.9.0'
    repositories {
      ... ...
    }
    ... ...
}
```

---

## Cambio de version de app

cada que necesitamos subir una nueva actualizacion de nuestra aplicacion en la tienda, tendremos que cambiar de version de app para que la tienda nos permita subirla, para ello nos dirigiremos al archivo

> **_android/app/build.gradle_**

y en la seccion de **_android/deafultConfig_** modificamos la version en el apartado de **_versionName_**, por ejemplo:

```gradle
android {
  ... ...
    defaultConfig {
        applicationId "bqn.tarrsolutions.bqn"
        minSdkVersion 21
        targetSdkVersion 33
        versionCode 53
        versionName "1.1.52"
        multiDexEnabled true
    }
    ... ...
}
```

lo cambiamos por:

```gradle
android {
  ... ...
    defaultConfig {
        applicationId "bqn.tarrsolutions.bqn"
        minSdkVersion 21
        targetSdkVersion 33
        versionCode 53
        versionName "1.1.53"
        multiDexEnabled true
    }
    ... ...
}
```

asi es como pasa de la version **_"1.1.52"_** a la **_"1.1.53"_**

---

## Error **_.tasks.FinalizeBundleTask$BundleToolRunnable_** al generar appBundle

sl intentar generar el appbundle de tu aplicacion es posible que muestre el siguiente error

```
Execution failed for task ':app:signReleaseBundle'.
 A failure occurred while executing com.android.build.gradle.internal.tasks.FinalizeBundleTask$BundleToolRunnable
    java.lang.NullPointerException (no error message)
```

en esta caso, este se debio a que nuestro proyecto no contaba con firma/key en la aplicacion, y ahora esto es necesario para generar los appBundle y subirlo a la playstore, suele ocurrir cuando intentas actualizar una aplicacion muy antigua, pues antes no era necesario tener una key para generar el appbundle, ahora que es obligatorio sucede este error, en esta misma documentacion hay un apartado para recibir ayuda sobre la [Generacion de la key](/DocumentacionGeneral/GeneracionKey.md "Ir a Generacion de la key").
