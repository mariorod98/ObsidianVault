# Implementar firebase al proyecto
1. Seleccionar el root del proyecto.
2. Seleccionar el proyecto.
3. Ir a la pestaña de Package Dependencies
4. Ir a la pagina de firebase y copiar la url del spm
5. Pegar la URL en el buscador de packages y seleccionar el package firebase-ios-sdk
6. Añadir el paquete en Add Package
7. Seleccionar todos los paquetes para instalar.
8. Una vez instalados, aparecerán en la barra derecha del proyecto.
9. Añadir import Firebase en algun archivo.
10. Si iniciamos la app ahora, crasheará. Esto es porque Firebase necesita el fichero de credenciales de Google Analytics para poder funcionar. 
11. Entrar en la pagina de firebase y crear un proyecto nuevo para la app.
12. Seguir los pasos de la pagina para añadir el fichero al proyecto.
13. El archivo no se puede añadir solo arrastrando al finder, se debe arrastrar dentro del proyecto en XCode. En las opciones que aparecen, clicar "Copy items if needed" para que copie el fichero la carpeta del proyecto.