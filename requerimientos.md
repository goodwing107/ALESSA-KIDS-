# Especificación de requerimientos

## Sistema de catálogo y gestión de pedidos ALESSA KIDS

Basado en IEEE 830-1998  
Versión 1.0 · 24 de noviembre de 2026

---

## 1. Introducción

### 1.1 Propósito

Definir los requerimientos funcionales y no funcionales del sistema web de
catálogo y gestión de pedidos de ALESSA KIDS, de modo que se pueda comprobar
objetivamente si el producto entregado cumple con los objetivos del proyecto.

### 1.2 Alcance

El sistema centralizará la consulta del catálogo de indumentaria infantil, la
gestión estacional de las prendas de verano e invierno, el registro y
seguimiento de pedidos para envío o retiro en tienda y la generación periódica
de respaldos. También incluirá autenticación para proteger las funciones
administrativas.

El sistema continuará la interfaz de catálogo existente, que actualmente usa
un archivo JSON, incorporando una base de datos relacional MySQL y la lógica de
servidor necesaria para conservar y consultar la información.

Quedan fuera de esta versión:

- cobros en línea y facturación electrónica;
- control exhaustivo de almacén, kardex, mermas o movimientos de inventario;
- notificaciones automáticas por WhatsApp, correo electrónico o SMS;
- gestión de múltiples sucursales.

### 1.3 Definiciones

| Término | Significado en este documento |
|---|---|
| **Prenda** | Artículo de indumentaria infantil con nombre, descripción, talla, color, precio, temporada y disponibilidad. |
| **Pedido** | Solicitud de una o más prendas con datos del cliente, cantidad, modalidad y fecha prevista de entrega o retiro. |
| **Pendiente** | Pedido vigente que todavía no ha sido entregado ni anulado. |
| **Operador** | Persona autorizada para consultar el catálogo y registrar o actualizar pedidos. |
| **Administrador** | Operador autorizado, además, para administrar prendas, usuarios y respaldos. |
| **Respaldo** | Exportación de los registros del sistema para su conservación y posterior recuperación. |

### 1.4 Referencias

- Propuesta del proyecto integrador ALESSA KIDS, noviembre de 2026.
- Instrumento de recolección de datos, entrevista y observación del 13 al 18
  de noviembre de 2026.
- Marco teórico del proyecto, noviembre de 2026.
- IEEE Std 830-1998 e ISO/IEC/IEEE 29148:2018.

---

## 2. Requerimientos funcionales

Los requerimientos con prioridad **alta** son indispensables para considerar
completo el alcance de esta versión. Los de prioridad **media** son necesarios
para la operación habitual, y los de prioridad **baja** quedan sujetos al
tiempo disponible sin afectar el objetivo principal.

| ID | Requerimiento | Prioridad | Origen |
|---|---|---|---|
| RF-01 | El sistema debe permitir iniciar sesión mediante usuario y contraseña y cerrar la sesión activa. | Alta | Propuesta: autenticación y reglas de acceso |
| RF-02 | El administrador debe poder registrar, consultar, modificar y desactivar prendas con nombre, descripción, talla, color, precio, temporada y disponibilidad. | Alta | Objetivo específico 1; instrumento: consulta de talles y colores |
| RF-03 | El sistema debe mostrar el catálogo de prendas disponibles con su nombre, imagen, precio, talla, color y temporada. | Alta | Objetivo general; alcance de la propuesta |
| RF-04 | El sistema debe permitir filtrar y buscar prendas por nombre, temporada, talla, color y disponibilidad. | Alta | Instrumento: verificación física de talles y colores; gestión estacional |
| RF-05 | El sistema debe permitir seleccionar la temporada activa entre verano e invierno para organizar la consulta del catálogo. | Media | Propuesta: cambios de temporada |
| RF-06 | El sistema debe permitir registrar un pedido asociado al nombre del cliente, dato de contacto, una o más prendas, talla, cantidad, modalidad de entrega y fecha prevista. | Alta | Problema central; entrevista y observación |
| RF-07 | El sistema debe rechazar el registro si falta algún dato obligatorio del cliente, la prenda, la talla, la cantidad, la modalidad o la fecha prevista. | Alta | Observación: pedidos anotados con datos incompletos |
| RF-08 | El sistema debe validar que la cantidad sea un número entero mayor que cero y que la fecha prevista sea válida. | Alta | Integridad de los pedidos |
| RF-09 | El sistema debe permitir registrar, sin procesar el cobro, el medio de pago y la referencia o comprobante informado para un pedido. | Media | Instrumento: conciliación manual de comprobantes y medios de pago |
| RF-10 | El sistema debe permitir registrar los datos de despacho o retiro, incluyendo dirección para envío o indicación de retiro en tienda. | Alta | Instrumento: redacción de datos de despacho; entrevista |
| RF-11 | El sistema debe asignar a cada pedido uno de los estados pendiente, empaquetado, enviado, entregado o anulado. | Alta | Instrumento: seguimiento de estados de despacho; ciclo de vida del pedido |
| RF-12 | El operador debe poder actualizar el estado de un pedido y el sistema debe conservar la fecha de la última actualización. | Alta | Alcance: gestión de entregas |
| RF-13 | El sistema debe listar los pedidos pendientes ordenados desde la fecha de entrega más próxima. | Alta | Problema central; preparación diaria de entregas |
| RF-14 | El sistema debe permitir filtrar los pedidos por fecha de entrega, rango de fechas, estado y modalidad. | Alta | Objetivo general; entrevista y alcance |
| RF-15 | El sistema debe mostrar el total de pedidos pendientes para la fecha actual y permitir consultar ese total para otra fecha. | Media | Entrevista: preparación de pedidos del día |
| RF-16 | El operador debe poder buscar un pedido por nombre o dato de contacto del cliente. | Media | Entrevista: consulta de conversaciones y cuaderno |
| RF-17 | El sistema debe mostrar el detalle de un pedido, incluyendo cliente, prendas, cantidades, datos de entrega, pago registrado, estado y fechas. | Alta | Necesidad de consulta centralizada |
| RF-18 | El administrador debe poder generar y descargar un respaldo de los registros de prendas, clientes y pedidos. | Alta | Objetivo específico 4; problema de ausencia de respaldo |
| RF-19 | El sistema debe permitir consultar la fecha y el resultado de la última generación de respaldo. | Media | Objetivo específico 4; trazabilidad de respaldos |

---

## 3. Requerimientos no funcionales

| ID | Requerimiento | Cómo se verifica |
|---|---|---|
| RNF-01 | El registro de un pedido debe completarse en un máximo de 60 segundos por un operador con capacitación básica, usando datos disponibles. | Cronometrar tres registros completos y calcular el tiempo de cada uno. |
| RNF-02 | La interfaz de registro debe mostrar como máximo 10 campos obligatorios y señalar los campos faltantes antes de enviar el formulario. | Contar los campos y probar un envío incompleto. |
| RNF-03 | La interfaz debe funcionar en una pantalla móvil de 360 px de ancho sin desplazamiento horizontal. | Abrir las pantallas principales en un emulador de 360 px y revisar el desplazamiento. |
| RNF-04 | Los botones y controles principales para interacción táctil deben tener un área mínima de 44 × 44 px. | Medir los controles con las herramientas de inspección del navegador. |
| RNF-05 | En una conexión estable de al menos 10 Mbps, las consultas del catálogo y de pedidos deben mostrar resultados en un máximo de 3 segundos con hasta 1.000 registros. | Ejecutar cinco consultas con el conjunto de prueba y medir el tiempo de respuesta. |
| RNF-06 | El sistema debe conservar un pedido confirmado aunque el operador cierre y vuelva a abrir el navegador. | Registrar un pedido, cerrar el navegador, iniciar sesión nuevamente y comprobar su existencia. |
| RNF-07 | Las contraseñas no deben almacenarse en texto visible y las funciones administrativas deben requerir una sesión autenticada. | Revisar el almacenamiento de credenciales e intentar acceder a una función protegida sin iniciar sesión. |
| RNF-08 | El sistema debe validar en el servidor los campos obligatorios, cantidades, fechas y estados, aunque la validación del navegador sea desactivada. | Enviar solicitudes de prueba con datos vacíos o inválidos y comprobar que no se guarden. |
| RNF-09 | El respaldo descargado debe poder abrirse y contener los registros de prendas, clientes y pedidos existentes al momento de generarlo. | Generar un respaldo, abrirlo en el formato definido y comparar sus registros con la base de datos. |
| RNF-10 | Las operaciones de registro, modificación de estado y generación de respaldo deben mostrar un mensaje de éxito o un mensaje de error comprensible. | Ejecutar cada operación en condiciones correctas y con datos inválidos. |
| RNF-11 | La disponibilidad mensual del sistema publicado debe ser de al menos 95 %, sin contar mantenimientos programados. | Revisar los registros de disponibilidad del hosting durante un mes. |
| RNF-12 | El sistema debe ser compatible con las dos versiones estables más recientes de Chrome, Firefox y Edge, y con el navegador móvil utilizado por el cliente. | Ejecutar el conjunto de pruebas funcionales en los navegadores indicados. |

---

## 4. Trazabilidad y criterios de aceptación

Los requerimientos se derivan de los objetivos y hallazgos documentados:

- **Registro y consulta de pedidos:** RF-06 a RF-17 responden al problema de
  información distribuida entre WhatsApp, redes sociales y cuaderno.
- **Catálogo y temporadas:** RF-02 a RF-05 responden al catálogo previo en
  JSON y a los cambios entre temporadas de verano e invierno.
- **Respaldo:** RF-18 y RF-19 responden a la ausencia de una copia centralizada.
- **Uso móvil y operación rápida:** RNF-01 a RNF-05 responden a la observación
  del uso del celular durante la atención.
- **Seguridad, integridad y persistencia:** RNF-06 a RNF-10 protegen la
  información y hacen verificables las operaciones.

El sistema se considerará aceptado cuando los requerimientos de prioridad alta
sean demostrados mediante casos de prueba aprobados y no existan errores que
impidan registrar, consultar, actualizar o respaldar la información.

---

## 5. Requerimientos omitidos de la norma

La IEEE 830 contempla secciones que no aplican a este proyecto y se omiten
explícitamente:

- **Interfaces de hardware:** el sistema no controla lectores, impresoras,
  balanzas ni otros dispositivos.
- **Requisitos de tiempo real:** no existen procesos industriales ni
  restricciones de respuesta en milisegundos; el límite operativo se define en
  RNF-05.
- **Facturación electrónica y pagos en línea:** están fuera del alcance
  declarado; RF-09 solo registra información proporcionada por el operador.
- **Múltiples sucursales:** el negocio opera actualmente en un único local.
