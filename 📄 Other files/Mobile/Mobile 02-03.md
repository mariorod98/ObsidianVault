
# Cambiar el UITableView por un UICollectionView

El UICollectionView da más versatilidad que el UITableView ya que se pueden colocar los elementos en la disposición en la que queramos (pagina de wallapop)

1.  Crear una carpeta nueva, Collection, para el nuevo view controller: Click derecho en carpeta-> nuevo grupo.
2.  Crear en esa carpeta una nueva clase de Cocoa Pods UIViewController llamada “HeroCollectionViewController”
3.  Añadir el view controller al Main storyboard. Ir al storyboard, click en el botón + y añadir nuevo view controller. Cambiar la clase del view controller añadido por HeroCollectionViewController
4.  Añadir una clase swift a Collection llamada “HeroCollectionModel” para hacer el modelo
5.  Añadir un collection view al ViewController
6.  Ponerle las constraints (0 en todas las direcciones)
7.  Añadir el collection view como variable para el View Controller
8.  Añadir dos extensions del HeroCollectionViewController, uno para el UICollectionViewDelegate y el UICollectionViewDataSource