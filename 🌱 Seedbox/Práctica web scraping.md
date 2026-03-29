Analisis del sitio
analisis de la pagina
Portatiles

Paginas web que permiten el scraping y almacenamiento de sus datos

**Goodreads**
- Red social, buscador, biblioteca online de libros.
- Gestion de usuarios
- Gestión de javascript
- Contexto: analizar las tendencias de lectura de los usuarios por pais, edad, etc y de forma temporal.

**eldiario.es** (u otro periodico)
- Analizar el sesgo de los periódicos. Cuánto hablan sobre un tema en comparación de otros. Cuanto mencionan a un politico en sus titulares. Cuales son los temas mas prominentes de la semana.
- Tiene derecho de autor, asi que no prodiamos almacenar imagenes o la noticia entera, pero si keywords.
- Gestion de javascript

Selenium para tocar ofertas. En las ofertas filtrar portatil u ordenador
Coolodown entre peticiones
Dimension de tiempo
Descarga de imagenes

[python - Selenium headless: How to bypass Cloudflare detection using Selenium - Stack Overflow](https://stackoverflow.com/questions/68289474/selenium-headless-how-to-bypass-cloudflare-detection-using-selenium)

[python - Selenium headless: How to bypass Cloudflare detection using Selenium - Stack Overflow](https://stackoverflow.com/questions/68289474/selenium-headless-how-to-bypass-cloudflare-detection-using-selenium)



**Guión vídeo**
- Presentar proyecto.
	- **Inspiración** Hablar de PCComponentes, por qué lo hemos elegido.
	- **Propietario** lo que sea que haya que escribir en el documento, explicar aqui tmb
	- Explicar las pautas éticas que hemos seguido a la hora de realizar el proyecto.
- Dataset
	- Explicar qué datos queríamos rescatar y por qué. 
	- Mostrar el dataset y explicar brevemente los campos.
- Desarrollo
	- Explicar la estructura del proyecto, las diferentes clases que lo componen
	- Explicar cómo construimos la estructura de datos, cómo descargamos las imágenes.
	- Explicar los problemas que hemos encontrado y cómo los hemos resuelto.
		- Bloqueo del sitio para robots
		- Selenium y los captcha
		- Bloqueo temporal durante la descarga de archivos
- Mostrar el dataset en zenodo y explicar la licencia que hemos escogido

TODO: 
- [ ] Meter scrapping de ofertas en el dataset
- [ ] Meter reacondicionados con selenium, no funcionan con page
- [ ] Meter descarga de imagenes en el scrapping