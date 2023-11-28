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
  ![image](https://github.com/codifymepro/sictsistema/assets/152323410/1ef46972-1530-4145-8a07-1a40fbcbcdee)


Donde si el usuario es administrador vuelve a hacer otra consulta la cual selecciona en este caso **solo** para los administradores donde el estado del menu sea 1 y submenu sea 1 o 7, existen 7 submenus.


   
    
