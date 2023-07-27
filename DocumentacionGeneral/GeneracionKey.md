# Generacion de la key

La key sera necesaria si o si al intentar generar un appBundle o intentar subir alguna aplicacion a la PlayStore, asi que es muy posible que te topes con problemas en el gradle y la key al intentar generar el appBundle o incompatibilidades de la misma, para ello, aqui encontraras la informacion para generarla.

Lo primero que tendras que hacer es ejecutar el siguiente comando, aqui un ejemplo

> keytool -genkey -v -keystore ~/key.jks -keyalg RSA -keysize 2048 -validity 10000 -alias key

puedes ejecutar este comando tal y como en el ejemplo, aunque algo que si es recomendable cambiar al menos es el **_-alias '''_**, puesto que este sera el nombre de tu key. aun asi, esto no sera visible para nadie, asi que no es nada mas que pura estetica interna.

Una vez generado el key.jks te pedira una contraseña, la cual debes de guardar, pues con ella podras acceder a tu key, y te sera requerida un par de veces en el futuro.

Despues de escribir tu contraseña y confirmarla, te empezara a pedir informacion sobre los desarrolladores, como el nombre del desarrollador, nombre de la organizacion, nombre de la unidad dentro de la organizacion, nombre de la ciudad o localidad, nombre del estado o provincia, y el codigo de pais en dos letras. Para finalizar te preguntara si la informacion esta correcta y tendras que confirmar si asi es, o corregir de nuevo los datos solicitados.

**_Nota: es muy importante guardar este archivo "key", puesto que de el depende tu proyecto si deseas subirlo y darle mantenimiento en la PlayStore, al perder este archivo no podras subir mas actualizaciones de tu aplicacion, pues esta se queda registrada con la primer firma con la que fue subida. Al igual que si es una aplicacion muy antigua con la que no se requeria una key y fue subida con la key, al intentar generar una nueva key se tendra que subir como una aplicacion totalmente nueva. Al igual, cabe recalcar que este archivo hay que mantenerlo privado, no se debe compartir y no olvides evitarlo en un repositorio publico._**

despues de generar el key.jks, tendremos que crear un archivo llamado **_key.properties_** en la carpeta **_/android/_** de tu proyecto, de tal manera que quede de la siguiente manera **_/android/key.properties_**, en este archivo tendremos que poner la siguiente informacion

```properties
storePassword=<contraseña del paso anterior>
keyPassword=<contraseña del paso anterior>
keyAlias=NombreDeLaKey
storeFile=<localización del archivo, por ejemplo /Users/<user name>/key.jks>
```

Por ejemplo:

```properties
storePassword=48532189
keyPassword=48532189
keyAlias=key
storeFile=C:/Repositories/app_flutter/android/key.jks
```

Ahora lo que tendremos que hacer es configurarla dentro de nuestro gradle, para ello nos iremos al archivo

> /android/app/build.gradle.

y antes del apartado de **_Android_** pondremos las siguientes lineas de codigo:

```gradle
def keystoreProperties = new Properties()
def keystorePropertiesFile = rootProject.file('key.properties')
if (keystorePropertiesFile.exists()) {
    keystoreProperties.load(new FileInputStream(keystorePropertiesFile))
}
```

esto para mandar a llamar nuestro archivo **_key.properties_**, y poder acceder a sus propiedades. Despues, antes de la etiqueta **_buildTypes_** pegaremos las siguientes lineas de codigo:

```gradle
signingConfigs {
    release {
        keyAlias keystoreProperties['keyAlias']
        keyPassword keystoreProperties['keyPassword']
        storeFile file(keystoreProperties['storeFile'])
        storePassword keystoreProperties['storePassword']
    }
}
```

de esta manera configuramos nuestra key en el gradle, con los datos guardados en el **_key.properties_**, en si al final deberia de quedar de una manera similar al siguiente codigo:

```gradle
def keystoreProperties = new Properties()
def keystorePropertiesFile = rootProject.file('key.properties')
if (keystorePropertiesFile.exists()) {
    keystoreProperties.load(new FileInputStream(keystorePropertiesFile))
}

android {
    ... ...
    signingConfigs {
        release {
            keyAlias keystoreProperties['keyAlias']
            keyPassword keystoreProperties['keyPassword']
            storeFile file(keystoreProperties['storeFile'])
            storePassword keystoreProperties['storePassword']
        }
    }
    buildTypes {
        ... ...
    }
    ... ...
}
```

Despues de esto, ya tenemos una key lista para ser usada en la generacion de nuestro appBundle.

---