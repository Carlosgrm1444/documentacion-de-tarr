uno de los errores mas comunes en el gradle es la version de compilacion

    Warning: The plugin device_info_plus requires Android SDK version 33.

para esto tienes que buscar cual es la version necesaria para tu proyecto, que comunmente te lo dice en el error y modificarlo dentro del

> **_android/app/build.gradle_**

en este caso tengo esta version antigua

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

pero la que ocupo es la versin 33, entonces lo cambiare a la siguiente manera

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
