
# Sistema de gestión de pedidos para tienda de ropa ALESSA KIDS

**Propuesta de Proyecto Integrador**
Programa Académico Desconcentrado "Técnico Superior en Informática"
UMSA · Sede Colquencha

Autor: [Calani Mamani Ludwing]
Fecha: noviembre de 2026

---

## Tipo de proyecto

**Proyecto integrador.** Se resuelve un problema concreto de un cliente real
construyendo un producto de software funcional, acompañado de la documentación
de ingeniería que respalda las decisiones tomadas.

No es una monografía: no se estudia el estado del arte de los sistemas de
pedidos, sino que se construye una solución aplicada. Tampoco constituye una
investigación, dado que no se responde a una pregunta teórica abierta, sino que
se resuelve una problemática operativa conocida en un negocio familiar.

---

## El punto de partida

Este proyecto continúa el trabajo del módulo de Programación Web, en el que se
construyó el frontend: una página funcional, publicada, con los datos del
cliente en un archivo JSON.

Para completar el proyecto falta lo siguiente:

| Ya existe | Se construye este módulo |
|---|---|
| Catálogo de prendas en un archivo JSON | Base de datos relacional real en MySQL |
| Interfaz web funcional y publicada | Autenticación y reglas de registro, consulta y respaldo |
| Funcionamiento en entorno local | Requerimientos, pruebas, costos y puesta en producción |

## El cliente

**ALESSA KIDS**, Av. Emilio Castro 4771, Ciudad Autónoma de Buenos Aires,
Argentina. Teléfono: 1130923280.

Es un negocio familiar atendido por dos personas. Funciona desde 2018 y comenzó
el trámite de registro de la marca en 2021. Vende indumentaria para niñas y
niños de temporadas de invierno y verano, tanto mediante venta directa como
por encargo.

**Cómo trabaja hoy:** Los pedidos llegan por WhatsApp, Facebook Marketplace y
TikTok, y todos se redirigen a un número de WhatsApp exclusivo para ventas y
envíos. Los encargos se registran y el stock se controla de forma manual a partir
de las conversaciones. Actualmente no existe un registro unificado ni una vista
centralizada que permita consultar las prendas disponibles, los pedidos
pendientes y las entregas programadas para cada día. Tampoco existe una copia
de respaldo centralizada de esta información.

**Fuente de esta información:** entrevista en línea con la propietaria,
realizada el 15 de noviembre de 2026 por encontrarse en otro país. La
información se registró en notas y fue validada con ella al día siguiente.

---

## Formulación del problema

El negocio de indumentaria para niñas y niños ALESSA KIDS vende por tres canales
virtuales: Facebook Marketplace, WhatsApp y TikTok. Los pedidos se reciben en
formatos diferentes y se redirigen a una cuenta exclusiva de WhatsApp, donde
la información queda registrada dentro de cada conversación.

Este flujo operativo presenta dificultades documentadas durante la entrevista
realizada con la propietaria:

**Imposibilidad de consulta.** Las plataformas utilizadas priorizan el uso desde
dispositivos móviles y no ofrecen un catálogo unificado ni una consulta cómoda
desde computadora. Para conocer los pedidos pendientes de una fecha determinada,
el propietario debe revisar por separado las conversaciones de las aplicaciones,
lo que consume tiempo durante la atención diaria.

**Ausencia de cantidad verificable.** La entrevista no permitió documentar
cuántos pedidos se reciben por mes ni cuántos se confunden o pierden. Por ello,
estas cifras deben obtenerse mediante el registro histórico y la medición de
varias semanas antes de afirmar una pérdida cuantificada.

**Ausencia de respaldo.** Los historiales de chat son el único medio central de
almacenamiento. No existe una copia unificada: ante la pérdida del dispositivo,
el borrado accidental de conversaciones o una falla de la cuenta, la información
de los encargos podría perderse y tendría que reconstruirse contactando
nuevamente a cada cliente.
 
### Árbol de problemas

```
   EFECTOS      Riesgo de atender pedidos con datos incompletos
                Posible pérdida de encargos o clientes
                Tiempo dedicado a reconstruir información dispersa
                          ↑
   PROBLEMA     El registro de pedidos por encargo de ALESSA KIDS no permite
   CENTRAL      consultar de forma confiable qué entregas corresponden a cada día
                          ↑
   CAUSAS       Los pedidos quedan distribuidos en varios canales
                Las conversaciones no están organizadas por fecha de entrega
                No existe una copia centralizada ni un registro único
```

### Problema central

> El registro distribuido de pedidos por encargo de ALESSA KIDS no permite
> consultar de manera confiable las entregas pendientes ni conservar una copia
> centralizada de la información.

---

## Objetivos

### Objetivo general

Desarrollar un sistema web de registro y consulta de productos y pedidos para
la tienda de indumentaria ALESSA KIDS, que permita visualizar el catálogo por
temporada, filtrar los encargos pendientes y entregados según su fecha de
entrega y garantizar la conservación de los datos mediante respaldos periódicos.

### Objetivos específicos

1. Modelar una base de datos relacional normalizada que gestione la información
   de clientes, prendas, temporadas y pedidos, organizada por fecha de entrega
   y estado.
2. Implementar el módulo de registro de nuevos encargos mediante una interfaz
   web con validaciones de integridad en los campos obligatorios.
3. Desarrollar el módulo de consulta y filtrado dinámico para visualizar los
   pedidos pendientes según su fecha de entrega.
4. Establecer un mecanismo automatizado de respaldo para garantizar la
   persistencia y recuperación de los registros históricos.

## Justificación

**Práctica.** Las dificultades descritas tienen una solución directa con una
aplicación web centralizada. El sistema permitirá revisar en una sola vista
los pedidos pendientes, las prendas asociadas y las fechas de entrega. Además,
podrá presentar el catálogo por temporada y conservar el historial de los
encargos sin depender de conversaciones dispersas.

**Técnica.** Se elige una aplicación web y no una de escritorio porque el
negocio ya tiene el frontend construido y publicado, y porque debe consultarse
desde el celular del mostrador y desde la computadora de la trastienda sin
instalar nada. Se usa PHP y MySQL porque funcionan sobre hosting compartido de
bajo costo, que es accesible para un negocio de este tamaño y facilita futuras
modificaciones. Las herramientas previstas son de uso libre y no requieren
hardware especializado ni la sustitución de los equipos que actualmente utiliza
la tienda.

**Social.** El registro centralizado reduce el riesgo de perder encargos y
evita que la propietaria tenga que reconstruir información dispersa
contactando nuevamente a los clientes.

## Factibilidad

**Técnica.** El sistema requiere un servidor con PHP 8 y MySQL, que es la
configuración estándar de cualquier hosting compartido. El desarrollo se hace
con XAMPP en local, que funciona sin conexión. El frontend ya está construido y
publicado. No se requiere ninguna tecnología que el equipo no haya usado antes.

**Operativa.** El sistema lo van a usar el propietario y su esposa, ambos con
teléfono con navegador y experiencia usando aplicaciones de mensajería y banca
móvil. La operación diaria se reduce a registrar un pedido y consultar la lista
del día, dos acciones que se resuelven en una pantalla cada una.

*Riesgo identificado:* el registro depende de que cada pedido que llega por los
tres canales se cargue en el sistema en el momento. Si los pedidos siguen
quedando solo en los chats "para pasarlos después", el sistema no resuelve
nada. Se mitiga dejando el registro accesible desde el celular, sin instalar
nada, de modo que cargar un pedido tome menos tiempo que leer el mensaje que
lo originó.

**Económica.** El desarrollo se realiza como parte del módulo, sin costo para
el cliente. La operación anual estimada es:

| Concepto | Costo anual (Bs) |
|---|---|
| Hosting compartido con PHP y MySQL | 350 |
| Dominio .com | 270 |
| **Total** | **620** |

El negocio puede cubrir el costo estimado de 620 bolivianos por año como gasto
de operación informática, siempre que el monto sea confirmado al contratar el
hosting y el dominio. La viabilidad económica depende también de que el uso
del sistema evite pérdida de encargos y reduce el tiempo invertido en revisar
los canales de mensajería.

## Alcances y límites

### Alcance

El sistema entregado incluye:
- Registro de pedidos asociado a los datos del cliente, el artículo solicitado,
  la cantidad y la fecha de entrega establecida.
- Consulta y filtrado dinámico de los pedidos pendientes según la fecha de
  entrega.
- Gestión de entregas mediante la actualización del estado operativo de cada
  pedido.
- Administración del catálogo y los precios desde la base de datos relacional.
- Exportación periódica de los datos para preservar los registros de los pedidos.
- Gestión estacional del catálogo para los cambios entre verano e invierno.

### Límites

El sistema **no** incluye, y en cada caso se indica por qué:

- **Cobros ni facturación electrónica.** ALESSA KIDS realiza sus operaciones de
  facturación mediante un talonario manual. Incorporar pasarelas de pago o
  facturación digital excede el problema central del registro de pedidos.

- **Control exhaustivo de inventario y stock.** El proyecto se concentra en
  organizar la dispersión de pedidos y preservar su información. Una gestión
  completa de almacén requeriría módulos adicionales y ampliaría la complejidad
  técnica.

- **Notificaciones automáticas al cliente.** Esta característica dependería de
  servicios externos de mensajería y recursos adicionales, por lo que queda
  propuesta como una mejora futura.

- **Múltiples sucursales.** El negocio opera con un único local físico. La
  arquitectura se limitará a esa ubicación y podrá ampliarse en una expansión
  posterior.

---

## Cronograma de actividades

### Descomposición del trabajo

```
1. Propuesta
   1.1 Formulación del problema
   1.2 Objetivos y justificación
   1.3 Factibilidad, alcances y límites
   1.4 Cronograma

2. Análisis
   2.1 Instrumento de recolección y entrevista
   2.2 Marco teórico
   2.3 Requerimientos funcionales y no funcionales
   2.4 Historias de usuario

3. Construcción
   3.1 Modelo de datos y base de datos creada
   3.2 Endpoints de registro y consulta
   3.3 Frontend conectado al backend

4. Verificación y cierre
   4.1 Matriz de casos de prueba ejecutada
   4.2 Respaldo y plan de puesta en producción
   4.3 Documento final y defensa
```

### Cronograma

| Semana | Paquete | Entregable |
|---|---|---|
| 23 al 27 de noviembre de 2026 | 1.1 a 1.4 | Propuesta completa |
| 30 de noviembre al 4 de diciembre de 2026 | 2.1 a 2.4 | Marco teórico y requerimientos |
| 7 al 11 de diciembre de 2026 | 3.1 a 3.3 | Sistema funcionando con base de datos |
| 14 al 18 de diciembre de 2026 | 4.1 a 4.3 | Sistema respaldado y documento final |

## Resumen

La tienda de indumentaria ALESSA KIDS, ubicada en la Ciudad Autónoma de Buenos
Aires, Argentina, recibe encargos mediante Facebook Marketplace, WhatsApp y
TikTok. Los pedidos se redirigen a una cuenta exclusiva de WhatsApp y se
registran manualmente, por lo que no existe una consulta centralizada ni una
copia de respaldo unificada.

Este proyecto desarrolla un sistema web de registro y consulta de pedidos que
integra el catálogo construido previamente con una base de datos relacional
MySQL y una capa lógica en PHP. Permitirá ordenar los encargos por fecha de
entrega y estado, consultar las entregas pendientes y exportar respaldos
periódicos de la información.

El funcionamiento se verificará mediante casos de prueba centrados en el
registro, las validaciones, la consulta, el filtrado y la recuperación de
datos. Se espera que la herramienta reduzca el tiempo dedicado a revisar
conversaciones dispersas y disminuya el riesgo de perder pedidos o repetir
contactos con los clientes.

## Introducción

El presente documento describe el desarrollo de un sistema de gestión de pedidos
para la tienda de indumentaria para niñas y niños ALESSA KIDS, elaborado como
proyecto integrador del módulo Proyecto de Software del Programa Académico
Desconcentrado "Técnico Superior en Informática" de la UMSA, Sede Colquencha.

El proyecto da continuidad al trabajo iniciado en el módulo de Programación Web, donde
se construyó y publicó la interfaz web del catálogo. La primera versión permite
mostrar los productos almacenados en un archivo JSON, pero no registra
operaciones ni conserva los encargos de forma centralizada. El presente módulo
completa el sistema mediante una base de datos relacional en MySQL y la lógica
del servidor necesaria para registrar encargos, consultar pedidos pendientes
según la fecha de entrega y gestionar respaldos.
El documento se encuentra organizado en cinco partes. La primera presenta la
propuesta: el problema, los objetivos, la justificación y el alcance. La segunda
desarrolla el marco teórico y la recopilación de información. La tercera detalla
el desarrollo, los requerimientos, la metodología, la construcción y las pruebas.
La cuarta aborda la puesta en producción y los costos. La quinta presenta las
conclusiones y recomendaciones.

---
