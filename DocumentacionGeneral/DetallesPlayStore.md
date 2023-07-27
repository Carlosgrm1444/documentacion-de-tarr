## Key/sellos/firma incompatibles

Desde hace un par de años empezo a ser un requisito obligatorio para subir una aplicacion a la PlayStore que tu aplicacion trajera una firma, esta termina dando la funcion de ser como un tipo de identificador unico o una firma de tu trabajo sobre tus desarrollos, algo similar a lo que los artistas hacen con sus obras de arte, entonces puede ocurrir un error muy frecuente sobre una incompatibilidad en la firma al actualizar aplicaciones muy antiguas, diciendo que la firma o los sellos no son igual a los que ya se tenian antes, esto es porque aunque en un inicio no se tenia una firma en el proyecto, este internamente se creaba una para mantenerse identificado, y ahora que queremos crear una firma nos damos cuenta de que en la playstore este ya estaba registrado con otra firma, lo mejor para esto es generar una key nueva, (en donde puedes encontrar informacion de como hacerlo en esta misma documentacion en [Generacion de la key](/DocumentacionGeneral/GeneracionKey.md "Ir a Generacion de la key")), y subirlo como una aplicacion nueva a la PlayStore.

---

## Tu app usa permisos que requieren una politica de privacidad ***android.permission.CAMERA***