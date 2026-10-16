# Proyecto EntradUS

## Miembros del grupo L1-G5

1. Domínguez González, Mateo
1. Martínez Zamorano, Tomás
1. Frías Sáez, Antonio
1. Ortiz Camino, Raúl

## 1. Introducción al problema

En este proyecto vamos a crear una plataforma para venta de entradas. En esta vamos a tener dos tipos de usuario, cliente y proovedor. El cliente será el usuario que compre la entrada, y el proveedor el que publique los distintos eventos para los que se ofrece la venta de las entradas. Cada evento tiene asociado un recinto, que tendrá también asociado zonas con un aforo máximo. Para cada zona habrá tantas localidades como aforo máximo tenga esta. El cliente compra una localidad que tendrá una entrada asociada, con su respectivo id y la fecha en la que se efectuó la compra.

Partimos de la base recibida en las clases de teoría, la cual aplicaremos en este proyecto refinando nuestros conocimientos en un entorno real y práctico.

A la hora de desarrollar un proyecto de este tipo nos enfrentamos a problemas como conseguir una interfaz intuitiva para el usuario o almacenar todos los datos correpondientes para cada entidad. Para conseguirlo debemos definir un esquema claro para clasificar los diferentes elementos implicados.

Esperamos superar con éxito el objetivo, creando una plataforma funcional y fácil de utilizar.
    

## 2. Glosario de términos

## 3. Visión general del sistema

Este sistema se encargará de gestionar datos relacionados con los diferentes elementos que se ven implicados en la venta de entradas de los eventos.

Por una parte deberá almacenar la compra de localidades, asociándolas a una entrada y, por otra, guardar información sobre eventos y los recintos donde estos podrían llevarse a cabo.

### 3.1. Requisitos generales

#### R.G.01. Gestión de usuario
Como administrador quiero gestionar los diferentes usuarios del sistema para controlar su actividad cuando usen el servicio.

#### R.G.02. Gestión de eventos
Como administrador quiero gestionar los eventos en el sistema para poder organizarlos de forma eficiente.

#### R.G.03. Gestión de recintos
Como administrador quiero gestionar los recintos en el sistema para poder guardar información suya que pueda ser útil.

#### R.G.04. Gestión de localidades
Como administrador quiero gestionar las localidades del sistema para facilitar y agilizar la compra y venta de entradas.

#### R.G.05. Gestión de Zonas
Como administrador quiero gestionar las zonas del sistema para clasificar diferentes espacios en un recinto.

### 3.2. Usuarios del sistema
-Usuario Cliente: Cliente que accede a la plataforma para comprar las entradas.                                                                                    
-Usuario Proveedor: Empresa que publica la entrada de los diferentes eventos.

## 4. Catálogo de requisitos

### 4.1. Requisitos funcionales

#### R.F.01.01 Creación de usuarios
Quiero que se puedan crear usuarios en el sistema asignándoles un id, un correo electrónico, una contraseña y un número de teléfono. En caso de que el usuario sea un proveedor debe de asignársele también el NIF de la empresa, y si es un cliente, el DNI y la fecha de nacimiento de este. 

**Pruebas de aceptación**
- Al crear un nuevo usuario, este se almacena en la base de datos con todos sus datos correspondientes.
- Si se intenta crear un usuario pero falta alguno de los campos requeridos, el sistema da error y este no se almacena en la base de datos.
- Si el correo electrónico no es de la forma X...X@X...X.X...X (siendo X cualquier caracter y "..." una cantidad variable de caracteres) el sistema da error y no crea el usuario.
- Si el número de teléfono no es de la forma +XX XXXXXXXXX (siendo X un número del 0 al 9) el sistema da error y no crea el usuario.
- En caso de ser un usuario Cliente, si el DNI no es de la forma NNNNNNNNX (siendo N un número del 0 al 9 y X una letra) el sistema da error y no crea el usuario.
- En caso de ser un usuario Proovedor, si el NIF no es de la forma XNNNNNNNNN (siendo N un número del 0 al 9 y X una letra) el sistema da error y no crea el usuario.
- Si se intenta crear un usuario e introduce una contraseña con menos de 8 caractéres, el sistema da error y no se crea el usuario

#### R.F.01.02 Consulta de usuarios
Quiero poder consultar los datos de los usuarios con su correo electrónico y su número de telefono.

**Pruebas de aceptación**
- Si busco un correo electrónico o un número de teléfono en la base de datos, puedo consultar a qué usuario pertenece y ver el resto de sus datos.

#### R.F.01.03 Edición de usuarios
Quiero que se puedan modificar los datos de los usuarios, siempre que los nuevos datos no estén asociados a otro usuario del sistema, exceptuando la contraseña, que varios usuarios pueden compartir la misma.

**Pruebas de aceptación**
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
Quiero que se puedan crear eventos en el sistema asignándoles un id, un nombre, una descripción y una fecha, además de asociarle un recinto.

**Pruebas de aceptación**
- Al crear un nuevo evento, este se almacena en la base de datos junto con su id, nombre, descripción, fecha, y recinto asociado.
- Si se intenta crear un evento y falta alguno de los campos obligatorios, el sistema da error y no almacena el evento en la base de datos.
- Si se intenta crear un evento con una fecha anterior a la actual, el sistema da error y no se almacena el evento en la base de datos.
- Si se intenta crear un evento cuyo nombre y fecha coincida con el nombre y fecha de un evento almacenado en la base de datos, el sistema da error y no se almacena el evento en la base de datos.

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
Quiero que se puedan crear recintos en el sistema asignándoles un id, un nombre y una ubicación.

**Pruebas de aceptación**
- Al crear un nuevo recinto, este se almacena en la base de datos junto con su id, su nombre y ubicación.
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
Quiero poder crear una localidad asociada a una zona y un evento, asignándole un id y un precio.

**Pruebas de aceptación**
- Al crear una nueva localidad, esta se almacena en la base de datos junto con su id y precio.
- Si se intenta crear una localidad sin asignarle un id y un precio, el sistema da error y esta no se almacena en la base de datos.
- Si se intenta crear una localidad sin asociarla a una zona y a un evento existente, el sistema da error y esta no se almacena en la base de datos.
- Si se intenta asociar una localidad a una zona que no pertenece al recinto asociado evento seleccionado, el sistema da error y no permite su creación.

#### R.F.04.02 Consulta de localidades
Quiero poder consultar los datos de las localidades registradas en el sistema mediante el evento y zona al que pertenecen.

**Pruebas de aceptación**
- Si busco una localidad mediante el evento y la zona al que pertenecen, el sistema muestra el precio y el id correspondiente de dicha localidad.
- Si se intenta consultar una localidad que no existe en la base de datos, el sistema informa de que no se ha encontrado ninguna localidad que coincida con los criterios de búsqueda.

#### R.F.04.03 Edición de localidades
Quiero que se pueda modificar el precio de las localidades registradas en el sistema, siempre que los nuevos datos sean válidos.

**Pruebas de aceptación**
- Si se modifica el precio o el id de una localidad, el cambio se almacena en la base de datos.
- Si se intenta modificar una localidad y su precio o id queda vacío, el sistema da error y no guarda los cambios.
- Si se intenta modificar el precio de una localidad por un valor negativo, el sistema da error y no guarda los cambios.


#### R.F.04.04 Eliminación de localidades
Quiero poder eliminar localidades registradas en el sistema.

**Pruebas de aceptación**
- Si se elimina una localidad, la base de datos deja de almacenar sus datos.
- Si no se elimina una localidad, esta permanece registrada en la base de datos.

#### R.F.05.01 Creación de zonas
Quiero que se puedan crear zonas en el sistema asignándoles un id, un nombre y aforo e id del recinto al que pertenece.

**Pruebas de aceptación**
- Al crear una nueva zona, esta se almacena en la base de datos junto con su id, nombre, aforo e id de su recinto correspondiente.
- Si se intenta crear una zona sin asignarle ningún id o nombre, el sistema da error y esta no se almacena en la base de datos.
- Si se intenta crear una zona sin asignarle el id de un recinto existente, el sistema da error y esta no se almacena en la base de datos.
- Si se intenta crear una zona con un aforo menor o igual que cero, el sistema da un error y esta no se almacena en la base de datos.

#### R.F.05.02. Consulta de zonas

Quiero poder consultar los datos de las zonas registradas en el sistema mediante el nombre y el id del recinto al que pertenece.

**Pruebas de aceptación**
- Si busco una zona mediante su nombre y el id del recinto al que pertenecen, el sistema muestra el aforo correspondiente de dicha zona.
- Si se intenta consultar una zona que no existe en la base de datos, el sistema informa de que no se ha encontrado ninguna zona que coincida con los criterios de búsqueda.

#### R.F.05.03. Edición de zonas

Quiero que se pueda modificar el nombre y el aforo de las zonas registradas en el sistema, siempre que los nuevos datos sean válidos.

**Pruebas de aceptación**
- Si se modifica el nombre o aforo de una localidad, el cambio se almacena en la base de datos.
- Si se intenta modificar una zona y su nombre o aforo queda vacío, el sistema da error y no guarda los cambios.
- Si se intenta modificar el aforo de una zona por un valor menor o igual que cero, el sistema da error y no guarda los cambios.


#### R.F.05.04. Eliminación de zonas

Quiero poder eliminar zonas registradas en el sistema.

**Pruebas de aceptación**
- Si se elimina una zona, la base de datos deja de almacenar sus datos.
- Si se cancela la eliminación de una zona, esta permanece registrada en la base de datos.


#### 4.1.1. Requisitos de información

#### RI.01.01. Información sobre los usuarios

Quiero disponer de la información correspondiente a los usuarios para llevar un seguimiento de su actividad. Los datos necesarios serán el id, el email, la contraseña, el nombre y el teléfono (además del NIF de la Empresa en caso de ser un proveedor y el dni y fecha de nacimiento en caso de ser un cliente). 

**Pruebas de aceptación**

- El sistema almacena la información correspondiente a cada usuario, incluyendo su id, email, contraseña, nombre y teléfono (además de NIF de la Empresa en caso de tratarse de un proveedor y DNI y fecha de nacimiento en caso de tratarse de un cliente).
- La información almacenada queda asociada al usuario correspondiente, de forma que no se confunden los datos de distintos usuarios.
- Si se modifica la información de un usuario, el sistema conserva los nuevos datos y permite consultarlos posteriormente.


#### RI.02.01. Información sobre los eventos

Quiero disponer de la información correspondiente a los eventos para llevar a cabo su organización. Los datos necesarios serán el id, el nombre, la fecha y el tipo de evento del que se trata, además del id del proveedor y el id del recinto correspondientes. 

**Pruebas de aceptación**

- El sistema almacena la información correspondiente a cada evento, incluyendo su id, su nombre, fecha y el tipo de evento, además de los ids del proveedor y el recinto que le correspondan.
- La información almacenada queda asociada al evento correspondiente, de forma que no se confunden los datos de distintos eventos.
- Si se modifica la información de un evento, el sistema conserva los nuevos datos y permite consultarlos posteriormente.

#### RI.03.01. Información sobre los recintos

Quiero disponer de la información correspondiente a los recintos para administrar su uso. Los datos necesarios serán el id, la ubicación y el nombre.

**Pruebas de aceptación**

- El sistema almacena la información correspondiente a cada recinto, incluyendo su id, ubicación y nombre.
- La información almacenada queda asociada al recinto correspondiente, de forma que no se confunden los datos de distintos recintos.
- Si se modifica la información de un recinto, el sistema conserva los nuevos datos y permite consultarlos posteriormente.

#### RI.04.01. Información sobre los localidades

Quiero disponer de la información correspondiente a las localidades para que se desarrolle una correcta compra de entradas. Los datos necesarios serán el id, precio y el id del evento y el id de la zona correspondientes. 

**Pruebas de aceptación**

- El sistema almacena la información correspondiente a cada localidad, incluyendo su id, su precio y los ids del evento y la zona a los que pertenece.   
- La información almacenada queda asociada a la localidad correspondiente, de forma que no se confunden los datos de distintas localidades.
- Si se modifica la información de una localidad, el sistema conserva los nuevos datos y permite consultarlos posteriormente.

#### RI.05.01 Información sobre las zonas

Quiero disponer de la información correspondiente a las zonas para una correcta disposición de las localidades en los eventos. Los datos necesarios serán el id, nombre, el aforo y el id de su recinto asociado. 

**Pruebas de aceptación**

- El sistema almacena la información correspondiente a cada zona, incluyendo su id, su nombre, su aforo y el id del recinto al que pertenece.
- La información almacenada queda asociada a la zona correspondiente, de forma que no se confunden los datos de distintas zonas.
- Si se modifica la información de una zona, el sistema conserva los nuevos datos y permite consultarlos posteriormente.


#### 4.1.2. Reglas de negocio

##### R.N.01. Límite individual de compra de entradas
Un mismo cliente no podrá comprar más de 6 localidades para un mismo evento, para evitar la posible reventa de entradas.

**Pruebas de aceptación**
- Si un cliente intenta comprar más de 6 localidades para un mismo evento en una transacción, el sistema da error y muestra el siguiente mensaje: "Límite de entradas compradas para este evento alcanzado, 6 entradas."
- Si un cliente compra 6 localidades para un mismo evento en una transacción y posteriormente intenta volver a comprar otra localidad para ese mismo evento, el sistema da error y muestra el siguiente mensaje: "Límite de entradas compradas para este evento alcanzado, 6 entradas."

##### R.N.02. Límite general de compra de entradas
El número de localidades vendidas no puede superar el aforo.

**Pruebas de aceptación**
- Si se han vendido tantas localidades para una zona en un evento como aforo máximo tenga la misma, el sistema no permitirá comprar más localidades, mostrando el mensaje: "Entradas agotadas en esta zona."
- Si no se han vendido aún tantas localidades para una zona en un evento como aforo máximo tenga la misma, el sistema permitirá la compra de la localidad.


### 4.2. Mapa de historias de usuario 


### 4.3. Requisitos no funcionales 

#### R.N.F.01 Disponibilidad 24 horas del día
Como director del proyecto quiero que la plataformas esté activa lo más cercano posible a 24/7 para facilitar las compras de los clientes.

**Pruebas de aceptación**

#### R.N.F.02 Control de acceso
Como responsable de temas legales, quiero que solo puedan acceder a la base de datos del sistema los empleados de la organización para cumplir con la Ley de Protección de Datos.

**Pruebas de aceptación**

#### R.N.F.03 Escalabilidad
Como responsable de atención al cliente, quiero que el tiempo de respuesta del sistema sea menor a 2 segundos mientras haya 1000 usuarios concurrentes o menos.

**Pruebas de aceptación**

#### R.N.F.04 Tolerancia a fallos
Como responsable de atención al cliente, quiero que el sistema realice una copia de seguridad diaria de la base de datos.

**Pruebas de aceptación**


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


