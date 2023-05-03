# Organización de una app de iOS

La forma de trabajar en iOS es mediante capas. Por ejemplo, tener el acceso a la API en una capa. 

Para organizar los elementos del proyecto, podemos crear nuevos grupos en la jerarquía (carpetas).

1.  Creamos un grupo Detail y añadimos el HeroDetailViewController.
2.  Creamos un grupo Home y añadimos el HomeViewController.
3.  Creamos un nuevo fichero swift en la carpeta Home llamado HomeViewController+TVDelegate. (El + se usa para especificar que el fichero es una extensión de una clase).
4.  Añadimos el exten del delegate en ese fichero.
5.  Hacemos lo mismo con HomeViewController+TVDataSource y el extend del DataSource.
6.  Crear en la carpeta Detail una clase HeroDetailViewModel, que manejará la lógica de la vista.
7.  Eliminar el hero de HeroDetailViewController, ya que ahora la info solo la tendrá el view model

## Dependencias externas

El gestor de dependencias más usado es SwiftPackageManager (SPM, integrado en Xcode) y después CocoaPods y Carthage

Si buscamos en un proyecto de dependencia como Kingfisher, nos saldrá la opción de añadir la dependencia con uno o más de estos gestores. 

Las dependencias mediante SPM se añaden:
1.  Seleccionar el proyecto.
2.  Seleccionar la tab Package Dependencies.
3.  En el botón + podemos agregar una dependencia.
4.  Vamos al github de Kingfisher, copiamos la URL y la pegamos en el buscador para que encuentre el paquete