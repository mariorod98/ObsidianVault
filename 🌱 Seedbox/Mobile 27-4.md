# User Default

1.  Crear proyecto de xcode
2.  En el storyboard,  añadir un stack view y centrarlo en todo.
3.  Añadir un texto y un botón al stack view.
4.  Poner el texto con constraints top, lead, trail y bottom a view.
5.  Poner el boton con top al texto y lead, trail y bottom a view.
6.  Enlazar el boton al view controller y ponerle nombre en camelCase (myButton).
7.  Enlazar el textfield al view controller (myTextField).
8.  Enlazar el botón al view controller para crear la accion saveEmail.
9.  Almacenar el campo del texto en el user defaults al pulsar el botón
![[Pasted image 20230503120301.png]]
10.  Cargar el campo de email al cargar la vista para mostrar su valor en el textfield.
![[Pasted image 20230503120354.png]]
11.  Crear un struct
![[Pasted image 20230503120403.png]]
12. Para guardar el struct en el UserDefault, hay que hacerla Codable.
![[Pasted image 20230503120428.png]]
13. Save and load struct to UserDefaults
![[Pasted image 20230503120439.png]]