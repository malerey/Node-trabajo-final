# Node Trabajo Final

El objetivo del trabajo final es hacer un servidor que pueda exponer una API para los usuarios, permitiendo consultar, agregar, modificar y eliminar informacion de una base de datos hecha en MongoDB.

Una cadena de hoteles argentinos necesita una API para conectar su front-end. La aplicacion lista hoteles de manera publica, pudiendo los usuarios finales consultar un listado filtrable de todos los hoteles disponibles y tambien consultar un hotel en particular 

## Funcionalidades básicas (obligatorias)

Al pedir informacion de todos los hoteles la API debe enviar por cada uno de ellos: 

- ID
- Nombre
- Ubicación (ciudad y provincia) *(extra: investigar como guardar geolocalización en MongoDB, sino, hacerlo como objeto)*
- Categoria de habitaciones *(ejemplo: presidencial, premium, comun)*
- Por cada categoria, precio por noche. 
- Cantidad de habitaciones en total. 
- Cantidad de habitaciones ocupadas en total. 
- Porcentaje de ocupacion en total. 
- Puntaje (del 0 al 5)

La API debe permitir filtrar los resultados del listado por:
- Ciudad
- Provincia
- Nombre 
- Precio por noche de habitacion disponible *(ejemplo: el usuario pide solo hoteles con habitaciones cuyo precio por noche sea menor a $1000)
- Puntaje *(ejemplo: el usuario pide solo hoteles con un puntaje mayor a 3)*

La API debe permitir ordenar los resultados por:
- Nombre (de la A a la Z o viceversa)
- Puntaje (de mayor a menor o viceversa)
- Precio de las habitaciones (de mayor a menor o viceversa, en cualquier categoría)
- Porcentaje de ocupación (de mayor a menor o viceversa)

Al consultar por un hotel en particular, a la informacion anterior se debe agregar:

- Por cada categoria, cantidad de habitaciones en total 
- Por cada categoria, cantidad de habitaciones ocupadas
- Por cada categoria, cantidad de habitaciones disponibles 
- Por cada categoria, porcentaje de ocupacion.
- Criticas de los usuarios, que se componen de un puntaje que va de 0 a 5 y un texto breve. (El "puntaje" de cada hotel debe calcularse con el promedio de estas criticas)

La API debe permitir el registro publico de usuarios en una ruta facilmente accesible como `/signup` y el inicio de sesión via una ruta facilmente accesible como `/signin`. Los usuarios que se registren podran acceder a la posibilidad de dejar criticas de los hoteles (cada critica esta compuesta por un puntaje que va de 0 a 5 y un texto). La autenticacion debe hacerse con token. Cada token tiene una duracion de 5 horas. 

Toda vez que la API devuelva mas de un resultado, debe hacerlo en paginas. El cliente puede definir cuantos resultados quiere por pagina, y que pagina quiere ver. Si no lo especifica, se deben devolver 20 resultados por pagina y la pagina 1. 

- La base de datos debe estar hosteada en MongoDB Atlas

- La API debe estar deployada (por ejemplo, en Heroku). 


## Funcionalidades avanzadas (optativas):

La API debe distinguir entre cuatro roles de usuarios:

- admins: pueden consultar cualquier endpoint, modificar cualquier información y crear otros usuarios definiendo su rol. Pueden ver y editar la informacion completa sobre todos los usuarios, con excepcion de la contraseña. Puede ver un listado de todos los usuarios y filtrar los resultados por rol, nombre o email. 

- managers: pueden crear, actualizar y borrar hoteles y cualquier información contenida en ellos (modificar precio de habitaciones, marcar habitaciones como ocupadas, etc), con excepción del puntaje y las criticas de los usuarios. 

- moderadores: pueden borrar criticas dejadas por los usuarios o editar su contenido, pero no pueden editar el puntaje. 

- usuarios: pueden guardar criticas sobre un hotel y consultar a otros usuarios, pero sin ver informacion privada (ni email, ni contraseña, ni rol). No pueden acceder a un listado de todos los usuarios. Los usuarios que se registren via la ruta /signin seran creados con este rol. Solo los admins pueden crear usuarios con otro rol, accediendo a una ruta privada. 

La API debe estar debidamente documentada. 
