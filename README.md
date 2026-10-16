# Proyecto EntradUS

## Miembros del grupo L1-G5

1. Domínguez González, Mateo
1. Martínez Zamorano , Tomás
1. Frías Sáez, Antonio
1. Ortiz Camino, Raúl

## 1. Introducción al problema

Tenemos la tarea de crear una plataforma de venta de entradas. Nuestra idea es ofrecer una forma sencilla de obtener entradas para diversos eventos, ya sean conciertos, festivales o espectáculos, para nuestros usuarios y de organizar la información eficazmente.  

A la hora de desarrollar un proyecto de este tipo nos enfrentamos a problemas como conseguir una interfaz intuitiva para el usuario o registrar información de la actividad en el servicio de venta. Para conseguirlo debemos definir un esquema claro para clasificar los diferentes elementos implicados, para facilitar un trabajo más sencillo con la información.
    

## 2. Glosario de términos

## 3. Visión general del sistema

Este sistema se encarga de gestionar datos relacionados con los diferentes elementos que se ven implicados en la venta de entradas de los eventos.

Por una parte, deberá almacenar la compra de localidades asociándolas a una entrada y, por otra, guardar información de los eventos y los recintos donde estos podrían llevarse a cabo.

### 3.1. Requisitos generales

#### R.G.01. Gestión de usuario
Como administrador quiero gestionar los diferentes usuarios del sistema para controlar su actividad cuando usen el servicio.

#### R.G.02. Gestión de eventos
Como administrador quiero gestionar los eventos en el sistema para poder gestionarlos de forma eficiente.

#### R.G.03. Gestión de recintos
Como administrador quiero gestionar los recintos en el sistema para poder guardar información suya que pueda ser útil.

#### R.G.04. Gestión de localidades
Como administrador quiero gestionar las localidades del sistema para facilitar y agilizar la compra y venta de entradas.


### 3.2. Usuarios del sistema
-Usuario Cliente: Cliente que accede a la plataforma para comprar las entradas.                                                                                    
-Usuario Proveedor: Empresa que publica la entrada de los diferentes eventos.

## 4. Catálogo de requisitos

### 4.1. Requisitos funcionales

#### R.F.01.01 Creación de usuarios
Quiero que se puedan crear usuarios en el sistema asignándoles un correo electrónico, una contraseña y un número de teléfono. En caso de que el usuario sea un proovedor debe de asignársele también el NIF de la empresa, y si es un cliente, el DNI y la fecha de nacimiento de este. 

**Prueba de aceptación**
- Al crear un nuevo usuario, este se almacena en la base de datos con todos sus datos correspondientes.
- Si se intenta crear un usuario pero falta alguno de los campos requeridos, el sistema da error y este no se almacena en la base de datos.
- Si el correo electrónico no es de la forma X...X@X...X.X...X (siendo X cualquier caracter y "..." una cantidad variable de caracteres) el sistema da error y no crea el usuario.
- Si el número de teléfono no es de la forma +XX XXXXXXXXX (siendo X un número del 0 al 9) el sistema da error y no crea el usuario.
- En caso de ser un usuario Cliente, si el DNI no es de la forma NNNNNNNNX (siendo N un número del 0 al 9 y X una letra) el sistema da error y no crea el usuario.
- En caso de ser un usuario Proovedor, si el NIF no es de la forma XNNNNNNNNN (siendo N un número del 0 al 9 y X una letra) el sistema da error y no crea el usuario.

#### R.F.01.02 Consulta de usuarios
Quiero poder consultar los datos de los usuarios con su correo electrónico y su número de telefono.

**Prueba de aceptación**
- Si busco un correo electrónico o un número de teléfono en la base de datos, puedo consultar a qué usuario pertenece y ver el resto de sus datos.

#### R.F.01.03 Edición de usuarios
Quiero que se puedan modificar los datos de los usuarios, siempre que los nuevos datos no estén asociados a otro usuario del sistema, exceptuando la contraseña, que varios usuarios pueden compartir la misma.

**Prueba de aceptación**
- Si se edita cualquier dato de un usuario, dicho cambio se almacena en la base de datos.
- Si se intenta editar el correo electrónico de un usuario y el correo al que se quiere cambiar ya se encuentra en la base de datos, el sistema da error y pide que se introduzca un correo electrónico distinto.
- Si se intenta editar el número de teléfono de un usuario y el número al que se quiere cambiar ya se encuentra en la base de datos, el sistema da error y pide que se introduzca un número de teléfono distinto.
- Si se intenta modificar un usuario y alguno de los campos obligatorios queda vacío, el sistema da error y no guarda los cambios.

#### R.F.01.04 Eliminación de usuarios
Quiero poder eliminar usuarios del sistema.

**Pruebas de aceptación**
- Si se elimina a un usuario del sistema, la base de datos dejará de almacenar sus datos.
- Si no se elimina un usuario, la base de datos seguirá almacenando sus datos.

#### R.F.01.05 Comprobación de edad
Como responsable de temas legales, quiero que no se pueda crear un usuario si el cliente no es mayor de 16 años.

**Pruebas de aceptación**
- Si el usuario introduce una fecha de nacimiento que indique que es menor de 16 años, el sistema dara error y creará el usuario.
- Si el usuario introduce una fecha de nacimiento que indique que es mayor de 16 años, el sistema creará el usuario.

#### R.F.02.01 Creación de eventos
Quiero que se puedan crear eventos en el sistema asignándoles un nombre, una descripción y una fecha, además de asociarle un recinto.

**Pruebas de aceptación**
- Al crear un nuevo evento, este se almacena en la base de datos junto con su nombre, descripción, fecha, y recinto asociado.
- Si se intenta crear un evento y falta alguno de los campos obligatorios, el sistema da error y no almacena el evento en la base de datos.
- Si se intenta crear un evento con una fecha anterior a la actual, el sistema da error y no permite su creación.

#### R.F.02.02 Consulta de eventos
Quiero poder consultar los datos de los eventos registrados en el sistema con su nombre o fecha.

**Pruebas de aceptación**
- Si busco un evento por su nombre o fecha, el sistema muestra los eventos con dicho nombre o fecha y el resto de sus datos.

#### R.F.02.03 Edición de eventos
Quiero que se puedan modificar los datos de los eventos registrados en el sistema, siempre que los nuevos datos sean válidos.

**Pruebas de aceptación**
- Si se modifica cualquier dato de un evento, el cambio se almacena en la base de datos.
- Si se intenta modificar un evento y alguno de los campos obligatorios queda vacío, el sistema da error y no guarda los cambios.
- Si se intenta modificar la fecha de un evento por una fecha anterior a la actual, el sistema da error y no guarda los cambios.

#### R.F.02.04 Eliminación de eventos
Quiero poder eliminar eventos registrados en el sistema.
**Pruebas de aceptación**
- Si se elimina un evento del sistema, la base de datos deja de almacenar sus datos.
- Si no se elimina un evento, este permanece registrado en la base de datos.

#### R.F.03.01 Creación de recintos
Quiero que se puedan crear recintos en el sistema asignándoles un nombre y una ubicación.

**Pruebas de aceptación**
- Al crear un nuevo recinto, este se almacena en la base de datos junto con su nombre y ubicación.
- Si se intenta crear un recinto y falta alguno de los campos obligatorios, el sistema da error y no almacena el recinto en la base de datos.
- Si se intenta crear un recinto y la ubicación ya se encuentra en la base de datos, el sistema da error y no almacena el recinto en la base de datos.

#### R.F.03.02 Consulta de recintos
Quiero poder consultar los datos de los recintos registrados en el sistema mediante su nombre o su ubicación.

**Pruebas de aceptación**
- Si se busca un recinto por su ubicación, el sistema muestra el recinto con sus datos correspondientes
- Si se busca un recinto por su nombre, el sistema muestra los recintos que coinciden con el nombre introducido, cada uno con su respectiva ubicación.
- Si se intenta consultar un recinto que no existe en la base de datos, el sistema informa de que no se ha encontrado ningún recinto que coincida con los criterios de búsqueda.

#### R.F.03.03 Edición de recintos
Quiero que se puedan modificar los datos de los recintos registrados en el sistema.

**Pruebas de aceptación**
- Si se modifica cualquier dato de un recinto, el cambio se almacena en la base de datos.
- Si se intenta modificar un recinto y alguno de los campos obligatorios queda vacío, el sistema da error y no guarda los cambios.
- Si se intenta modificar un recinto y la nueva ubicación ya se encuentra en la base de datos, el sistema da error y no guarda el cambio.

#### R.F.03.04 Eliminación de recintos
Quiero poder eliminar recintos del sistema.

**Pruebas de aceptación**
- Si se elimina un recinto del sistema, la base de datos deja de almacenar sus datos.
- Si no se elimina un recinto, este permanece registrado en la base de datos.

#### R.F.04.01 Creación de localidades

Quiero poder crear una localidad asociada a una zona de un evento, asignándole un precio.

**Pruebas de aceptación**
- Al crear una nuevo localidad, esta se almacena en la base de datos junto con su precio.
- Si se intenta crear una localidad sin asignarle ningún precio, el sistema da error y esta no se almacena en la base de datos.
- Si se intenta crear una localidad sin asociarla a una zona de un evento existente, el sistema da error y esta no se almacena en la base de datos.
- Si se intenta asociar una localidad a una zona que no pertenece al recinto del evento seleccionado, el sistema da error y no permite su creación.

###R.F.04.02 Consulta de localidades

Quiero poder consultar los datos de las localidades registradas en el sistema mediante el evento y zona al que pertenecen.

**Pruebas de aceptación**
- Si busco una localidad mediante el evento y la zona a la que pertenecen, el sistema muestra el precio correspondiente de dicha localidad.
- Si se intenta consultar una localidad que no existe en la base de datos, el sistema informa de que no se ha encontrado ninguna localidad que coincida con los criterios de búsqueda.

###R.F.04.03 Edición de localidades

Quiero que se pueda modificar el precio de las localidades registradas en el sistema, siempre que los nuevos datos sean válidos.

**Pruebas de aceptación**
- Si se modifica el precio de una localidad, el cambio se almacena en la base de datos.
- Si se intenta modificar una localidad y su precio queda vacío, el sistema da error y no guarda los cambios.
- Si se intenta modificar el precio de una localidad por un valor negativo, el sistema da error y no guarda los cambios.


###R.F.04.04 Eliminación de localidades

Quiero poder eliminar localidades registradas en el sistema.

**Pruebas de aceptación**
- Si se elimina una localidad, la base de datos deja de almacenar sus datos.
- Si se cancela la eliminación de una localidad, esta permanece registrada en la base de datos.

  
#### R.F.04. Notificaciones
Como desarrollador, quiero que el sistema envíe un correo electrónico al cliente cuando queden 48 horas para que empiece el evento para el cual ha adquirido una localidad.
**Pruebas de aceptación**
- Si quedan 48 horas para empezar un evento, el sistema enviará un correo electrónico a todos los usuarios que hayan comprado una locacalidad para ese evento recordándoselo.
- Si aún no quedan 48 horas para comenzar un evento, no se notificará a los usuarios.
- Si quedan menos de 48 horas para comenzar un evento, se notificará a los usuarios, a no ser que ya hayan sido notificados.

#### R.F.05. Unicidad de correo electrónico
Como desarrollador, quiero que no se pueda crear más de una cuenta con el mismo correo electrónico.

**Pruebas de aceptación**

- Si un usuario intenta crear una cuenta con un correo electrónico que ya se encuentra en la base de datos, el sistema dará error y redigirá al usuario a la página de inicio de sesión.


#### R.F.06. Unicidad de NIF de empresas
Como desarrollador, quiero que no se pueda crear más de una cuenta de proovedor con un mismo NIF.

**Pruebas de aceptación**

- Si un usuario intenta crear una cuenta con un NIF que ya se encuentra en la ase de datos asociado a un proovedor, el sistema dará error y redigirá al ususairo a la página de inicio de sesión.

#### R.F.07. Unicidad eventos
Como desarrollador, quiero que no se puedan crear dos eventos con el mismo nombre y fecha.

**Pruebas de aceptación**

- Si un proovedor intenta publicar un evento cuyo nombre y fecha ya está registrado en la base de datos, dará error y pedirá cambiar el nombre del evento o la fecha de este.

- Si un proovedor intenta publicar un evento cuyo nombre ya esta en la base de datos pero la fecha asociada no, el sistema creará el evento.

- Si un proovedor intenta publicar un evento cuyo nombre no se ecnuentra en la base de datos pero la fecha asociada si, el sistema creará el evento.


#### R.F.08. Seguridad contraseñas
Como encargado de seguridad, quiero que la contraseña asociada a un usuario no puede ser de menos de 8 caracteres.

**Pruebas de aceptación**
-Si un usuario intenta crear una cuenta e introduce una contraseña con menos de 8 caractéres, el sistema dará error y pedirá al usuario introducir una contraseña distinta.
-Si un usuario intenta crear una cuenta e introduce una contraseña con 8 caractéres o más, el sistema creará la cuenta.


#### R.F.09. Unicidad de número de teléfono
Como desarrollador, quiero que no se pueda crear más de una cuenta con el mismo número de teléfono.

**Pruebas de aceptación**

- Si un usuario intenta crear una cuenta con un número de teléfono que ya se encuentra en la base de datos, el sistema dará error y redigirá al usuario a la página de inicio de sesión.


#### 4.1.1. Requisitos de información

##### R.I.01. Título requisito de información

Como director
quiero disponer de la siguiente información sobre las localidades:

-Que cliente la ha comprado.

-Para que evento es.

-Cual es la empresa proovedora de ese evento.

-Cuantas localidades ha comprado ese cliente para ese evento.

-Cúando ha comprado el cliente la/s localidad/es.

**Prueba de aceptación**
- El sistema almacena la relación del cliente con la localidad adquirida.
- El sistema almacena la relación entre cada localidad con su respectivo evento.
- El sistema almacena la relación entre la empresa proovedora y el evento.
- El sistema almacena el número de localidades compradas por un cliente para un evento y cuándo se efectuó la compra.

#### 4.1.2. Reglas de negocio

##### R.N.01. Límite individual de compra de entradas

Un mismo cliente no podrá comprar más de 6 localidades para un mismo evento, para evitar la posible reventa de entradas.

##### R.N.02. Límite general de compra de entradas

El número de localidades vendidas no puede superar el aforo.

### 4.2. Mapa de historias de usuario 

### 4.3. Requisitos no funcionales 

**R.F.N. 01 Disponibilidad 24 horas del día.**

Como desarrollador quiero que la venta de entradas esté habilitada las veinticuatro horas del día para facilitar las compras a los clientes.

**R.F.N. 02 Proveedores de confianza.**

Como desarrollador quiero que los eventos disponibles en la aplicación estén organizados por proveedores de confianza para evitar posibles fraudes.

-- fin entregable 1 --

## 5. Modelo conceptual

### 5.1. Diagramas de clases UML

- con restricciones.

### 5.2. Escenarios de prueba

- con descripción textual y diagrama de objetos UML.

## 6. Matrices de trazabilidad

- Matriz de trazabilidad entre los elementos del modelo conceptual y los requisitos.

|       | EntidadX   | AsociaciónX  | RestricciónX  | Entidad2 ...   | 
|:------|:-----------|:-----------|:-----------|:-----------|
| RI-1  | X          | X          | X          | X          |
| RI-2  |            | X          |            | X          |
| RF-1  |            | X          |            | X          |
| RF-2  | X          |            | X          | X          |
| RN-1  |            | X          |            |            |
| RN-2  | X          | X          | X          |            |
| ...   |            |            |            |            |

-- fin entregable 2 --

## 7. Modelo relacional en 3FN

- Relaciones obtenidas al aplicar la transformación del modelo conceptual.

### 7.1.  Justificación de la estrategia de transformación de jerarquías

- si se identificaron jerarquías en el MC.


### 8. Matriz de trazabilidad MC/SQL (opcional):

- Restricciones sobre el MC / Elementos del modelo tecnológico (SQL) (Triggers, checks, etc.)
- Incluir Reglas de negocio — Constraints/Triggers en las matrices de trazabilidad para el entregable 3

|       | EntidadX   | AsociaciónX  | RestricciónX  | Entidad2 ...   | 
|:-------|:-------|:-------|:-------|:-------|
| TABLA-1 |        |        |        |        |
| TABLA-2 |        |        |        |        |
| TABLA-3 |        |        |        |        |
| TABLA-4 |        |        |        |        |
| TRIG-1 |        |        |        |        |
| TRIG-2 | X      | X      |        | X      |
| TRIG-3 |        | X      |        | X      |
| TRIG-4 |        |        | X      |        |
| CONST-1 |        |        |        |        |
| CONST-2 | X      | X      |        | X      |
| CONST-3 |        | X      |        | X      |
| CONST-4 |        |        | X      |        |

Se consideran todo tipo de constraints declarativas (aquellas definidas durante el CREATE TABLE).
-- fin entregable 3 --

## Referencias


