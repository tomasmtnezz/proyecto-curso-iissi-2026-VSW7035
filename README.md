# Proyecto EntradUS

## Miembros del grupo L1-G5

1. Domínguez González, Mateo
1. Martínez Zamorano , Tomás
1. Frías Sáez, Antonio
1. Ortiz Camino, Raúl

## 1. Introducción al problema

En este proyecto crearemos una plataforma de venta de entradas. Nuestra idea es ofrecer una forma sencilla de obtener entradas para diversos eventos, ya sean conciertos, festivales o espectáculos, para nuestros usuarios.A la hora de desarrollar un proyecto de este tipo nos enfrentamos a problemas como conseguir una interfaz intuitiva para el usuario o registrar información de la actividad en la aplicación.    

## 2. Glosario de términos

## 3. Visión general del sistema

### 3.1. Requisitos generales

#### R.G.01. Gestión de usuario
Como administrador quiero gestionar los usuarios del sistema.

#### R.G.02. Gestión de eventos
Como administrador quiero gestionar los eventos en el sistema.

#### R.G.03. Gestión de recintos
Como administrador quiero gestionar los recintos en el sistema.

#### R.G.01. Gestión de localidades
Como administrador quiero gestionar las localidades del sistema.


### 3.2. Usuarios del sistema
-Usuario Cliente: Cliente que accede a la plataforma para comprar las entradas.                                                                                    
-Usuario Proveedor: Empresa que publica la entrada de los diferentes eventos.

## 4. Catálogo de requisitos

### 4.1. Requisitos funcionales

#### R.F.01. Compra entradas

Como cliente
quiero comprar entradas
para ir a un evento.

**Prueba de aceptación**

- Se busca un evento, se selecciona y se muestran sus datos, la fecha, el lugar y el precio.

- Se selecciona el número de entradas que se desea comprar y se comprueba que hay suficientes entradas disponibles.

- Se confirma la compra, se realiza el pago y se muestra un mensaje de confirmación.

- Se consulta el apartado «Mis entradas» y aparecen las entradas compradas.


#### R.F.02. Inicio Sesión
Como desarrollador quiero que los usuarios puedan iniciar sesión en la plataforma con un correo electrónico y su contraseña.

**Prueba de aceptación**

- Si el usuario introduce un correo electrónico que no está en la base de datos, el sistema dará error y rediccionará al usuario a la pagina de creación de cuenta.

- Si la contraseña que introduce el usuario no coincide con la almacenada en la base de datos para ese correo electrónico, el sistema dará error y pedirá que se introduzca de nuevo la contraseña.

#### R.F.03. Comprobación de edad
Como responsable de temas legales, quiero que el cliente no pueda crear una cuenta si no es mayor de 16 años.

**Pruebas de aceptación**

- Si el usuario introduce una fecha de nacimiento que indique que es menor de 16 años, el sistema dara error y no dejará crear la cuenta.

- Si el usuario introduce una fecha de nacimiento que indique que es mayor de 16 años, el sistema creará la cuenta.

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


