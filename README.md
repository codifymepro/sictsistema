# SICT SISTEMA 
Este sistema de gestion de datos es una plataforma integral diseñada para administrar eficientemente informacion clave relacionada con empleados, equipos de computo, impresoras, tics en general, y comunicaciones.
Con capacidades para crear, eliminar, leer y actualizar registros, este sistema ofrece un control completo sobre los datos escenfciales de una organizacion, en este caso para la organizacion gubernamental SICT (**Secretaria de Infraestructura, Comunicaciones y Transportes**)
## ¿Que funciones tiene?
Un sistema CRUD funciona mediante 4 acciones, crear, eliminar, leer y actualizar, la cual cada donde el usuario puede realizar dichas tareas para tener todo tanto como organizado, estructurado como digitalizado en una plataforma que trabaja con las tecnologias actuales, mismas que pueden ser escalables.
1. **Crea** registros mediante formularios, ya sea dependiendo el caso de uso que se le de, en este caso un ejemplo, para dar de alta un empleado, un equipo de computo, o algun reporte
<p>
  <img src="https://github.com/codifymepro/sictsistema/assets/152323410/6b005859-626a-4e61-8f1c-f184d4e4e150">
</p>

2. **Elimina** registros la cual ya no son necesarios, funcionales o son redundantes, se muestra un formulario para confirmar la eliminacion de dicho elemento.
  <p>
  <img src="https://github.com/codifymepro/sictsistema/assets/152323410/5e7f0e17-a996-4cbb-801e-d3364d35760f">
  </p>
3. **Actualiza** registros que ya fueron subidos a la base de datos del sistema, estos pueden ser editados/actualizados, ya sea uno o varios campos, tambien se muestra un formulario la cual ahi mismo confirma uno la informacion seleccionada.
  <p>
  <img src="https://github.com/codifymepro/sictsistema/assets/152323410/c1000e04-4be1-4524-82c3-5abb7a37e170">
  </p>
4. **Leer** registros mediante una tabla, estos registros solo son mostrados si son levantados, mientras no se mostrara, la tabla cuenta con x columnas, ya que cada pagina/vista tiene diferente informacion, cada fila tiene 2 botones, uno para *editar* y *eliminar*.
  <p>
  <img src="https://github.com/codifymepro/sictsistema/assets/152323410/75efce53-0845-4d3e-8c94-e22d211252d2">
  </p>

Cada formulario cuenta con dos botones, uno para hacer accion (color azul) y otro para cancelar (color rojo) la operacion.

Otras de las funciones que tiene es la creacion de codigos QR, y subida de archivos pdf, jpg, png, jpeg, estos mismos en su respectivo formulario de vista relacionada, por ejemplo en *Conexiones/patch-panel*, *Tipos/recursos-materiales* para generacion de Qr`s y para la carga de imagenes y/o pdf's en la seccion de *reportes* o *tics*
![image](https://github.com/codifymepro/sictsistema/assets/152323410/48d51f25-f2b1-4e6d-923d-40e636323006)

## Instalacion
No se requiere instalacion alguna, simplemente debe estar en linea el servidor nginx o apache ya sea su caso y tambien el servicio de Mysql ya que ahi es donde se almacenan todos los datos

## ¿Que tecnologias usamos?
Como entorno de desarrolo usamos Linux con su distribucion de OpenSUSE Leap 15.5
Usamos como IDE Visual Studio Code 1.84.2
- Lenguajes de programacion:
    1. **PHP**: Usamos Principalmente para el backend php en su version 8.0
    2. **HTML, CSS**: Usamos como frontend html y css para mostrar las consultas del CRUD para poder visualizar cada accion que hagamos en este sistema
    3. **Javascript**: Usamos algo de JavaScript para funciones adicionales como las notificaciones, fuentes, colores, animaciones, y demas.
    4. **MySql**: Usamos como base de datos Mysql en su version 10.6.15
- Servicios:
    1. **Apache2**: Integramos principalmente Apache2 en su version 2.4 como servidor inicial
    2. **phpMyAdmin**: Como administrador de la base de datos usamos phpMyAdmin, para asi poder realizar acciones de gestion en la BBDD.
    3. **MySql Workbench Community**: Junto a este programa tambien para poder gestionar la BBDD, en su version 8.0.20.
    4. **Nginx**: Ultimamente usamos el servicio de servidor web, en su version 1.24.0, para poder desplegar el sistema y pueda ser usable por todos los usuarios de la organizacion.  

## Estructuracion del codigo
1. Conexion a la base de datos:
   Para hacer la conexion a la base de datos usamos la siguiente funcion
   ![image](https://github.com/codifymepro/sictsistema/assets/152323410/7a932050-71a4-4c42-ab40-c4975af47549)
   En una variable, en este caso *$con* guardamos lo que viene siendo la conexion a la base de datos, mismo que le enviamos los parametros para conectarnos, como el host, el usuario de la base de datos, la contraseña y nuestra base de datos, seguido de eso viene un if para validar la conexion a la base de datos, en caso de que no se envie va a morir el proceso y arrojara  el error que se mostrara en caso de que no pueda conectarse a ella misma.

2. Validamos si el usuario ya se registro o inicio sesion a la base de datos del sistema.
   ![image](https://github.com/codifymepro/sictsistema/assets/152323410/5deabea2-f9e5-4513-bb27-08c7146e3bbe)
   dado que el usuario no haya iniciado conexion e ingrese indebidamente al sistema, este sera redirigido automaticamente a la pagina de login, esto esta implementado en cada inicio de codigo del sistema, en cada pagina para evitar modificaciones indebidas en datos importantes

3. Menu lateral desplegable:
   Este menu tiene sus rutas en la base de datos, la cual cuando se añada un nuevo menu aparecera automaticamente en el sistema, mismo que cada seccion tiene submenus.
   <p>
  <img src="https://github.com/codifymepro/sictsistema/assets/152323410/ed30e997-e723-4ee5-b0f5-057f2e61adb7">
  </p> 
  Lo primero que hacemos es validar si el usario es administrador o simplemente es normal, lo cual se hace con una consulta SQL donde selecciona el rol del          usuario con el nombre de la sesion activa.
  <p>
  <img src="https://github.com/codifymepro/sictsistema/assets/152323410/1ef46972-1530-4145-8a07-1a40fbcbcdee">
  </p>

  <p>
  <img src="https://github.com/codifymepro/sictsistema/assets/152323410/247c8f49-782c-47db-a355-6ce0dc250283">
  </p>

Donde si el usuario es administrador vuelve a hacer otra consulta la cual selecciona en este caso **solo** para los administradores donde el estado del menu sea 1 y submenu sea 1 o 7, existen 7 submenus.
Seguido de eso, se crean los div de las secciones que tendran los submenus ya sea desde el 1 al 7
![image](https://github.com/codifymepro/sictsistema/assets/152323410/ad41359b-7382-45f3-bc76-e15aca62b2a0)

4. Como hacer una consulta CRUD
   - Crear:
     Lo primero que debemos hacer es la validacion de conexion a la base de datos, despues si el usuario esta logeado.
     Despues almacenar en variables los elementos del formulario, en este caso los *input* cada input debe tener un nombre, ya que eso vamos a mandarle al archivo donde tiene la funcion/accion de crear algo.
   ![image](https://github.com/codifymepro/sictsistema/assets/152323410/7ba9bf95-ddba-4419-af28-865c89e2a895)
    Seguido en unas variables en php *$estaesunavariable*, con el simbolo de $ dinero, estamos invocando que esto es una variable, la cual tendra el valor del metodo POST dependiendo donde estamos trabajando la cual tendra como valor el nombre del input o campo que hemos declarado antes en el formulario, por ejemplo:
   ![image](https://github.com/codifymepro/sictsistema/assets/152323410/1d2059d5-ac42-40ec-9a27-9cd94edb6aa0)
   Ya que hayamos declarado nuestras variables, lo que hacemos es hacer otra variable la cual con esta podremos hacer la consulta SQL y enviar la peticion al servidor, dentro de la variable tendra con comilla doble ("") la query de mysql en este caso insertar.
   ![image](https://github.com/codifymepro/sictsistema/assets/152323410/2ef60bb8-001c-43c1-a9d9-2e718985c7ee)
   Una vez hecho esto, enviamos la peticion, llamando con una variable la conexion, y el metodo query de php con el parametro de nuestra variable anterior.
   En caso de que haya sido correctamente enviada, sera redirigido a la vista donde estaba y se muestran todos los datos, en este caso edificio.
   De caso contrario, sera redirigido al formulario de insercion de datos.
   ![image](https://github.com/codifymepro/sictsistema/assets/152323410/a0ec18ba-b37f-4fb4-810a-c30b0d4d4d0e)
  - Actualizar:
   Teniendo en cuenta los primeros 2 pasos, podemos seguir el mismo camino, lo unico que cambia es la query SQL, ya que aqui vamos a indicar que va a cambiar y a quien se lo vamos a aplicar.
   ![image](https://github.com/codifymepro/sictsistema/assets/152323410/1b680318-e9e0-4aab-8042-2dd37ae8e686)
  - Eliminar: 
   Aqui teniendo los pasos anteriores, solo que solo vamos a invocar el ID del elemento que vamos a eliminar.
   ![image](https://github.com/codifymepro/sictsistema/assets/152323410/1a2c11a0-c047-4657-a36c-d42e16bd299c)

   - Leer:
       Para leer algo, en este caso la informacion que hemos subido, editado o simplemente ver cambios vamos a usar una tabla, y una consulta select simple o usando where para hacer busqueda, siguiendo la sintaxis anterior.
     ![image](https://github.com/codifymepro/sictsistema/assets/152323410/727c3fb2-d111-44a2-ae31-51773c7208d4)
     para nuestra busqueda es un poco diferente en la query ya que vamos a usar la clausula **WHERE** y **LIKE** donde vamos a enviarle desde un input un valor que sea o parezca al que existe en la base de datos.
     Debemos seguir la estructura de un formulario, mismo que debe tener su action, method, y el input su value y name.
     ![image](https://github.com/codifymepro/sictsistema/assets/152323410/ca75ed90-ee46-45d7-9403-0907ac1ed586)
     ![image](https://github.com/codifymepro/sictsistema/assets/152323410/2d1f8f35-1be9-4ec9-aee1-ff366c102353)
     en caso de que exista el elemento buscado vamos a mostrarlo en una tabla html.
     Con un while en php llamamos a la variable que asignamos anteriormente $row donde row va a mostrar por cada elemento una columna y dato ordenadamente.
     ![image](https://github.com/codifymepro/sictsistema/assets/152323410/63e47009-703e-4ed0-9a3b-16fe2b268557)
     dentro del cuerpo de la tabla, con las etiquetas tr, th, mostramos lo que es el cuerpo de nuestra tabla
     ![image](https://github.com/codifymepro/sictsistema/assets/152323410/ab425a21-33f8-4d14-9261-bf0a5bbcf5c4)
     Donde en **td** va a incluir un echo en php la variable $row junto el nombre de la columna en la tabla de mysql de nuestra base de datos.

5. Frameworks que usamos
   Como estilos usamos **Bootstrap 5.0.2**, es una libreria de estilos ya predefinidos, al menos el 85% del codigo html.
   ![image](https://github.com/codifymepro/sictsistema/assets/152323410/fedc9f4b-4328-4f96-a63f-4ec4b13bbc08)

   ![image](https://github.com/codifymepro/sictsistema/assets/152323410/fffca85f-eb10-4222-9a03-af19c002f057)
   Para las fuentes de texto usamos **Google Fonts**, una libreria igual cientas de fuentes, la fuente que escogimos fue Montserrat
   ![image](https://github.com/codifymepro/sictsistema/assets/152323410/a3da9750-8246-40f7-838a-e376b24dc900)
![image](https://github.com/codifymepro/sictsistema/assets/152323410/abbc321d-a83d-4b81-8dee-a58526020ce3)
  Para nuestros colores, usamos **Adobe colors**, una libreria de colores, la cual puedes explorar una infinita variedad de paletas de colores
![image](https://github.com/codifymepro/sictsistema/assets/152323410/f8278eb2-dd47-4ac9-874d-82e066a22817)

## Extra
  ¿Còmo inspeccionar un elemento en html con ayuda de el navegador?:
    1-Estando en nuestra pagina, vista o sitio web, en cualqueir parte del sitio damos click derecho y aparecera un menu, vamos a dar click en inspeccionar, tambien usando la tecla F12.
    <p>
    <img src="https://github.com/codifymepro/sictsistema/assets/152323410/3ccdadd1-5842-4f73-9882-c9c05f15f51d">
    </p>
    Enseguida se nos abrira una ventana llamada Heramientas de desarrollo, la cual nos ayuda para hacer pruebas de depuracion en tiempo real, inspeccionar codigo y editarlo, tanto puro como sus propiedades, tambien la carga de archivos en red y la respuesta que toma para cargar todo el contenido, etc
<p>
  <img src="https://github.com/codifymepro/sictsistema/assets/152323410/82ffd553-06d8-439d-8a44-8d63501ab4f2">
</p>



# Creditos
 Este sistema es creado a partir como iniciativa de nuestro servicio social, la cual nos ayuda a tener la experiencia necesaria, la idea de como es trabajar en un entorno laboral de informatica, y saber hacer las cosas bien.
 Probablemente no sea el mejor programa, pero poco a poco vamos aprendiendo, pues de los errores se aprende.

### Lider del proyecto
   **Juan Manuel Razura, Director del departamento de informatica SICT**
### Desarrollado
  *Sistema desarrollado y diseñado por Carlos Eduardo Hernandez Montes y Jose David Lopez Villarreal*







> "La inspiracion desbloquea el futuro"
 Hiyao Miyazaki 2013
