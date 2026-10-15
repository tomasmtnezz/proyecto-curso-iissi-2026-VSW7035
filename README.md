# Proyecto LocalizadUS

## Miembros del grupo L1-G5

1. Domínguez González, Mateo
1. Martínez Zamorano , Tomás
1. Frías Sáez, Antonio
1. Ortiz Camino, Raúl

## 1. Introducción al problema

En este proyecto crearemos una plataforma de venta de entradas. Nuestra idea es ofrecer una forma sencilla de obtener entradas para diversos eventos, ya sean conciertos, festivales o espactáculos, para nuestros usuarios.A la hora de desarrollar un proyecto de este tipo nos enfrentamos a problemas como conseguir una interfaz intuitiva para el usuario o registrar información de la actividad en la aplicación.    

## 2. Glosario de términos

- Términos específicos del dominio del problema, ordenados alfabéticamente. Se valorará la presencia de información multimedia.
Aforo: Número máximo de personas que pueden acceder a un recinto.

Backstage: Zona reservada para artistas, técnicos y personal autorizado que se encuentra detrás del escenario.

Código QR: Código formado por un patrón de cuadrados que puede ser escaneado con un dispositivo móvil, normalmente es utilizado como entrada.

Pasarela de pago: Sistema que permite procesar de forma segura los pagos realizados por los usuarios al comprar entradas.

Ponente: Persona o grupo que participa en el evento.

Promotor: Entidad encargada de promocionar y, en muchos casos, de la venta de entradas.

Recinto: Espacio concreto en el que tiene lugar el evento.

Reembolso: Devolución total o parcial del dinero, que puede ser debido a diversos factores.

Transacción: Operación mediante la cual se realiza el pago de una entrada en la plataforma.

## 3. Visión general del sistema

### 3.1. Requisitos generales
-Queremos gestionar la venta de entradas de diferentes eventos para su venta.
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

  

#### 4.1.1. Requisitos de información

##### R.I.01. Título requisito de información

Como [tipo de usuario]
quiero [servicio]
para [razón]

**Prueba de aceptación**
- Descripción de la primera comprobación a realizar
- Descripción de la segunda comprobación a realizar
- ...

#### 4.1.2. Reglas de negocio

##### R.N.01. Límite individual de compra de entradas

Un mismo cliente no podrá comprar más de 6 localidades para un mismo evento, para evitar la posible reventa de entradas.

##### R.N.02. Límite general de compra de entradas

El número de localidades vendidas no puede superar el aforo.

### 4.2. Mapa de historias de usuario (opcional)

### 4.3. Requisitos no funcionales (opcional)

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


