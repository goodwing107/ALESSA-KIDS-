<!-- ═══════════════════════════════════════════════════════════════════════
     Propuesta de proyecto - documento de ejemplo

     ⚠️ Este es el proyecto de ejemplo del módulo, no el tuyo.

     Se sigue el caso de la Panadería del Barrio, que es el cliente que se usó
     en Programación Web, para poder mostrar un documento completo y coherente.
     Tú escribes el mismo documento sobre tu cliente, el que elegiste el mes
     pasado.

     El documento crece día a día:
       Día 1  se elige el tipo de proyecto y se encuadra
       Día 2  formulación del problema
       Día 3  objetivos y justificación
       Día 4  factibilidad, alcances y límites
       Día 5  cronograma, resumen e introducción  -> se entrega el Lab 1

     Los comentarios como este explican por qué cada sección dice lo que dice.
     En un documento real no van: aquí están para aprender.
     ═══════════════════════════════════════════════════════════════════════ -->

# Sistema de gestión de pedidos para tienda de ropa 

**Propuesta de Proyecto Integrador**
Programa Académico Desconcentrado "Técnico Superior en Informática"
UMSA · Sede Colquencha

Autor: [Calani Mamani Ludwing]
Fecha: noviembre de 2026

---

<!-- ── Qué tipo de proyecto es este (subtemas 1.1 a 1.5) ────────────────
     Antes de escribir una línea hay que saber qué se está escribiendo. Los
     cuatro tipos no se diferencian por el tema, sino por lo que producen y
     por cómo se los evalúa:

       Monografía            estudia un tema y lo expone. No construye nada.
                             Producto: un documento.

       Proyecto integrador   resuelve un problema real construyendo algo.
                             Producto: el software Y su documentación.
                             ← este es el de este módulo

       Proyecto de grado     igual, pero con exigencia de aporte original y
                             defensa formal ante tribunal.

       Investigación         responde una pregunta que nadie respondió antes,
                             con método y datos. Producto: conocimiento nuevo.

     La diferencia práctica: en una monografía se pregunta "¿qué se sabe de
     X?"; en un proyecto integrador, "¿qué le falta a este cliente y cómo se
     lo construyo?".

     Confundirlos es el error del Día 1: escribir una monografía sobre
     sistemas de pedidos, en vez de construir uno.                        -->

## Tipo de proyecto

**Proyecto integrador.** Se resuelve un problema concreto de un cliente real
construyendo un producto de software funcional, acompañado de la documentación
de ingeniería que respalda las decisiones tomadas.

No es una monografía: no se estudia el estado del arte de los sistemas de
pedidos, ssi no que se construye una solución aplicada. Tampoco constituye una investigación, dado que no se responde a una pregunta teorica abierta, si no que se resuelve una problrmática operativa conocida en un negocio familiar.


---

## El punto de partida

Este proyecto continúa el trabajo del módulo de Programación Web, en el que se
construyó el frontend: una página funcional, publicada, con los datos del
cliente en un archivo JSON.

Para completar el proyecto falta lo siguiente:

| Ya existe | Se construye este módulo |
            |---|---|
| el interfaz  funcionando y publicado | la propuesta que lo justifica |
| los datos en un archivo JSON         | una base de datos real |
| "funciona en mi máquina"             | requerimientos, pruebas, costos y *deploy* (puesta en
                                          producción) |
|catalogo de prendas en un archivo JSON| Base de datos relacional real en MySQL |
|Funcionamiento en entorno local       | Requerimientos, pruebas, costos y puesta en produción  
                                         (*deploy*)|

<!-- ── El cliente ───────────────────────────────────────────────────────
     Todo lo que viene depende de esta sección. Un cliente vago produce un
     problema vago, objetivos vagos y requerimientos imposibles de verificar.

     Tres datos que no pueden faltar, y que hay que poder responder sin
     inventar:
       quién es (nombre, rubro, tamaño)
       qué hace hoy para resolver lo que se le va a resolver
       cómo se sabe (de dónde salió esa información)

     El tercero es el que separa un proyecto real de uno imaginado.         -->

## El cliente

**Alain Calani Mamamni**, Av. Emilio Castro 4771 
Teléfono: 1130923280, Argentina-Ciudad Autónoma de Buenos Aires. 
Es un negocio familiar dos personas, en funcionamiento desde 2018 sin registro de patente hasta el año 2021 con registro de marca registrada. Vende indumentaria para niñ@s, temporada de ivierno y verano tanto para venta directa al público como por encargo.

**Cómo trabaja hoy:** Los pedidos llegan por los tres canales, cada uno con su
propio formato. En WhatsApp quedan en el historial de chats; en Facebook
Marketplace en la mensajería de la publicación; en TikTok en los comentarios y
mensajes directos, pero todos se direcionan a un numero de watsapp que tienen uso exclusivo para ventas y envios. El propietario anota los encargos y controla el stock de forma manual
sobre esas dichas conversaciones. Actualmente no exxiste un registro unificado ni una vista centralizada que permita visualizar que prendas estan disponibles, que pedidos se encuentran oendientes y que debe entregarse cada día. Aasi mismo el negocio carece de copias de respaldos  centralizados de esta información.
**Fuente de esta información:** entrevista con la propietario, el 15 de noviembre de 2026, on line ya que se encuentra en otro pais. Se registró en notas y se validó con ella al día siguiente.

---

<!-- ── Formulación del problema (subtema 2.3) ──────────────────────────
     esta sección responde una sola pregunta:
     ¿qué está mal hoy, y cómo se sabe?

     Las tres reglas, y las tres se rompen todo el tiempo:

     1. No se menciona la solución. Ni una vez. En cuanto aparece "falta un
        sistema", ya no se está describiendo un problema: se está describiendo
        la ausencia de tu solución, que no es lo mismo.

     2. Se mide. "Se pierden pedidos" es una queja. "Se perdieron 12 pedidos
        en marzo, según el conteo de la dueña" es un problema. Si no hay
        número, hay que ir a buscarlo.

     3. Se dice de dónde sale. Cada dato con su fuente. Sin eso, el tribunal
        pregunta "¿y usted cómo sabe?" y no hay respuesta.

     La prueba para saber si está bien escrito: dárselo a leer a alguien que
     no conoce el proyecto. Si al terminar puede decir qué está mal hoy, sin
     saber todavía qué vas a construir, está bien.                        -->

## Formulación del problema
El negocio de indumentaria para niñ@s de Alain Calani y sra. vende por tres canales
virtuales (Facebook Marketplace, WhatsApp y TikTok), pero los productos no se
pueden visualizar en una sola página y los registros de pedidos y de stock se
manejan de manera manual, y todos los pedidos y encargos son redirigidos a una cuenta 
de watsapp y el registro queda en dicho chat.

Este flujo operativo presenta  dificultades críticas documentadas durante la entrevista
realizada con los propietarios:

**Imposibilidad de consulta.** Las plataformas virtuales utilizadas operan principalmete desde telefonos inteligentes y no ofrecen una visualizacion adecuadad en computadora ni un catálogo unificado. Para saber qué pedidos están pendientes para un día determinado hay que recorrer la mensajería de cada aplicación por separado, lo que consume tiempo diario del propietario.

**Ausencia de respaldo.** El cuaderno físico  y los historiale de chat son los únicos medios de almacenamineto. No existe una copia unificada ni centralizada, ante el extavio del dispoditivo móvil  el borrado accidental de conversaciones o el deterioro del cuaderno, se pierde la informacion de los encargos y resulta necesario recontruirla contctando nuevamente a cada cliente.
 
<!-- ── El árbol de problemas ────────────────────────────────────────────
     Herramienta para no confundir el problema con sus causas ni con sus
     efectos. Se dibuja así:

              Efectos        ← lo que se ve, lo que duele
                 ↑
          problema central   ← una sola frase
                 ↑
              causas         ← por qué ocurre

     El error más común es poner un efecto como problema central. "Los
     clientes se quejan" es un efecto; el problema es lo que lo produce.

     Y el segundo error: poner como causa "no tienen un sistema". Eso es,
     otra vez, la ausencia de la solución.                                -->

### Árbol de problemas

```
   EFECTOS      Clientes insatisfechos que no que no concretan futuras compras 
                Pérdida de ingresos por pedidos no concretados 
                Tiempo del personal dedicado a reconstruir información dispersa
                          ↑
   PROBLEMA     El registro manual de pedidos por encargo  de LESSA KIDS no permite consultar
   CENTRAL      de forma confiable qué debe prepararse cada día
                          ↑
   CAUSAS       Los pedidos se anotan en orden de llegada, no por fecha
                El registro es único y no tiene copia
                La revisión diaria depende de exclusivamente de un historial de chat
```

### Problema central

> El registro de pedidos por encargo de la Tienda de ropa ALESSA  KIDS no permite
> visualisar de forma correcta ya que su uso se limita al uso de celulares, lo que ocasiona
> pedidos no cocretados por escasa informacion que se le brinda al cliente  y tambien tiempo dedicado a revisar información dispersa.

---

<!-- ── Objetivos (subtema 2.5) ─────────────────────────────────────────
     Aquí sí aparece la solución, y por primera vez. Pero con una forma muy
     estricta.

     Un objetivo general. Uno solo. Es el problema central en positivo:
     si el problema es "el registro no permite consultar", el objetivo es
     "desarrollar un sistema que permita consultar".

     Empieza con un verbo en infinitivo que describe lo que tú vas a hacer:
     desarrollar, implementar, diseñar. Nunca "mejorar la atención" ni
     "lograr que el cliente esté satisfecho": eso no depende de ti.

     Los específicos son los pasos para llegar al general. Y la prueba que
     los ordena: al terminar el proyecto, ¿se puede decir sí o no a cada uno,
     sin discutir? Si hace falta interpretar, está mal escrito.

     SMART, aplicado a un proyecto de software:
       Specific    dice qué, no "mejorar"
       Measurable  se puede verificar si se cumplió
       Achievable  con el tiempo y los recursos que hay
       Relevant    ataca una causa del árbol del Día 2
       Time-bound  cabe en el cronograma

     El error que hay que detectar: objetivos que son tareas ("instalar XAMPP")
     o que son deseos ("mejorar la eficiencia"). Un objetivo específico es un
     resultado verificable, no una actividad ni una aspiración.            -->

## Objetivos

### Objetivo general

Desarrollar un sistema web de registro y consulta de productos y pedidos para
la tienda de indumentaria ALESSA KIDS , que permita visualizar el catálogo por temporada, filtrar los encargos pendientes y entregados segun su fecha de entrega y grantizar la conservación  de los datos mediante respaldos periódicos.

### Objetivos específicos

1. Modelar una base de datos relacional normalizada que gestione la información de clientes,
 prendas, temporadas y pedidos, indexada por fecha de entrega y estado.
2. Implementar el modulo de registro de nuevos encargos atravez de un interfaz web con 
validaciones de integridad en los campos obligatorios.
3. Desarrollar el módulo de consulta y filtrado dinámico que permita visualizar los pedidos 
pendientes segun su fecha de entrega.
4. Estableces un mecaismo automatizado de respaldo (backup)para garntizar la persistencia y
 recuperacion de los registros historicos.


<!-- Cada específico se puede responder con sí o no al terminar. Ninguno dice
     "mejorar", "optimizar" ni "lograr que". Y el 4 no es relleno: verificar
     es parte del proyecto, no algo que se hace si sobra tiempo.

     Fíjate también en lo que no está: "capacitar al personal", "aumentar las
     ventas". Son deseables y no dependen del software. Van en las
     recomendaciones del Día 18, no aquí.                                  -->

<!-- ── Justificación (subtema 2.4) ─────────────────────────────────────
     Responde: ¿por qué vale la pena hacer esto, y por qué así?

     Tres ángulos, y con dos alcanza:
       práctico   qué mejora concretamente para el cliente
       técnico    por qué esta solución y no otra
       social     a quién más beneficia, si aplica

     La trampa de esta sección: escribir elogios de la tecnología.
     "En la actualidad, los sistemas de información son fundamentales para
     toda organización moderna" no justifica nada: sirve para cualquier
     proyecto del mundo, y por eso no sirve para el tuyo.

     La prueba: si el párrafo se puede copiar tal cual en el proyecto de otro
     compañero, sobra.                                                     -->

## Justificación

**Práctica.** Las dificultades descritas en la formulacion del problemas tienen 
solucion directa con la implementacion de la aplicacion web: ya que los pedidos 
fueron confundidos por distintos articulos ya que se habia hecho el cambio de 
temporada y no se actualizó las plataformas virtuales por donde se vende los
productos. Tambien se soluciona el problema de visualizacion de productos ya que 
las plataformas virtuales no brindan una visualizacion web o computador ya que
 son limitadas a uso de celulares inteligentes.

**Técnica.** Se elige una aplicación web y no una de escritorio porque el
negocio ya tiene el frontend construido y publicado, y porque debe consultarse
desde el celular del mostrador y desde la computadora de la trastienda sin
instalar nada. Se usa PHP y MySQL porque funcionan sobre hosting compartido de
bajo costo, que es lo accesible para un negocio de este tamaño.

**Tecnológica** El proyecto utilizará la metodología Httml y css, lo que permitira realizar futuras modificaciones en en el presente sistema, logrando  la escalabilidad.
Por otro lado, el software y las herramientas que se utilizaron para el desarrollo del proyecto no requeriran de inversion de hardware  especializado y son de libre acceso, por lo cual se adaptara favorablemente a los equipos con los que ya cuenta la tienda 

**Social.** El registro con respaldo elimina la reconstrucción manual de
pedidos, que en julio de 2025 obligó a llamar uno por uno a los clientes de una
semana.
*(Este documento continúa el Día 4 con la factibilidad, los alcances y los límites.)*

<!-- ── Factibilidad (subtema 2.6) ──────────────────────────────────────
     Responde una pregunta incómoda: ¿esto se puede hacer de verdad?

     Tres dimensiones, y las tres se responden con evidencia, no con
     optimismo:

       Técnica      ¿existe la tecnología, y sabemos usarla?
       Operativa    ¿el cliente va a poder usarlo y mantenerlo?
       Económica    ¿los costos son asumibles para ese cliente?

     La operativa es la que más se subestima y la que más proyectos hace fracasar.
     Un sistema técnicamente perfecto que el cliente no usa es un fracaso.
     Y la pregunta que la resuelve no es "¿le gusta?", sino "¿quién lo va a
     usar todos los días, y sabe hacerlo?".

     Una factibilidad honesta puede decir que no. Si la conclusión es que
     algo no se puede, eso no descalifica el proyecto: se ajusta el alcance.
     Decir que todo es factible sin haberlo mirado es lo que sí descalifica. -->

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

<!-- El último párrafo es el que convierte la factibilidad económica en un
     argumento. Un costo suelto no dice nada; un costo comparado con lo que
     se pierde hoy, sí. El detalle fino de costos es el Día 15.            -->

<!-- ── Alcances y límites (subtema 2.7) ────────────────────────────────
     la sección más corta y la que más problemas evita.

     Alcance  = lo que sí se va a entregar
     Límite   = lo que no, y por qué

     Los límites son una decisión del proyecto, y hay que escribirlos
     antes de programar, no después, porque después se llaman "cosas que no
     me dio tiempo".

     La regla: cada límite dice qué queda fuera y por qué. Un límite sin
     razón parece una excusa; con razón, es una decisión de diseño.

     Y hay algo que se descubre escribiendo esta sección: si el alcance no
     cabe en el cronograma, hay que recortarlo ahora. Ese es el objetivo real
     del ejercicio.                                                        -->
## Alcances y límites

### Alcance

El sistema entregado incluye:
- Registro de pedidos, destinada a registrar cada encargo asociado con los datos del cliente, 
  el producto u ART solicitado y la cantidad y la fecha de entrega establecida.
- Consulta y filtrado,permite visualizar los pedidos pednientes mediante un filtrado dinámico
  segun la fecha de entrega.
- Gestión de entrega, opcion par aactualizar el estado operativo de los pedidos, permitiendo 
  marcarlos como entregados una vez completado el proceso de envío.
- Administración de catalogo y precios, listado de productos, indumentaria y precios, que puede 
  administrar desde la base de datos relacional.
- Respaldo de informción, mecanismo de de respaldo ue facilitará la exportacion de datos para    
  preservar los registtros de todos los pedidos.
- Adaptabilidad estacional, soporte estructural orientado a gestionar el cambio de temporada (de
  verano a invierno o viseversa)en la presentación de los productos.

### Límites

El sistema **no** incluye, y en cada caso se indica por qué:

- **Cobros ni facturación electrónica.** La tienda de ropa ALESSA KIDS realiza sus operacions de facturacion medianate un talonario manual, por lo que la incorporacion de pasarelas de pago o facturacion digital.

- **Gestión de inventario y control de stock.** El problema central identificado se enfoca en la dispersion  y pérdida de pedidos, no en le control, exaustivo de almacen, incrementar esta funcionalidad incrementria  l complegidad técnica sin resolver elproblema principal.

- **Notificaciones automáticas al cliente.** Dicha caracteristica requiere integración con srvicion exterenos demensajeria que implican costos o recursos adicionales, por lo cual queda planteada como una reccomendacion a futuro.

- **Múltiples sucursales.** El negocio opera con un único local físico, de modo que el diseño de la arquitectura de la base datos se limit a una solanubicación, aunque contempla l escalabilidad necesaria en caso de una futur expansión.

<!-- Fíjate en el patrón: cada límite dice qué queda fuera Y por qué. Y las
     razones son de tres tipos: no ataca el problema, excede el tiempo, o
     depende de algo externo. Ninguna dice "no me dio tiempo".             -->

---

*(Este documento continúa el Día 5 con el cronograma, el resumen y la introducción.)*

<!-- ── Cronograma (subtema 2.8) ────────────────────────────────────────
     Antes del cronograma va la WBS: descomponer el trabajo en pedazos que
     se puedan estimar. La regla práctica es que ningún paquete pase de una
     semana; si pasa, todavía no se entiende bien y hay que partirlo.

     La WBS se arma con sustantivos, no con verbos. No es "hacer la base de
     datos", es "base de datos". Se describe lo que va a existir, no lo que
     se va a hacer. Eso evita que aparezcan actividades sin producto.

     El cronograma sale de la WBS. Si se empieza por el calendario, quedan
     fechas sin un entregable claro.

     La columna que más se olvida: el entregable, es decir, qué queda hecho
     cuando esa fila termina. Una fila sin entregable no produce nada que se
     pueda revisar.                                 -->

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
| 1 | 1.1 a 1.4 | Propuesta completa **(Lab 1)** |
| 2 | 2.1 a 2.4 | Marco teórico y requerimientos **(Lab 2)** |
| 3 | 3.1 a 3.3 | Sistema funcionando con base de datos **(Lab 3)** |
| 4 | 4.1 a 4.3 | Sistema respaldado y documento final |

<!-- Cuatro semanas, cuatro entregables. El cronograma no inventa fechas: usa
     las del módulo, que son las reales. Un cronograma que no coincide con el
     tiempo que existe es una declaración de deseos.                       -->

<!-- ── Resumen e introducción (subtemas 2.1 y 2.2) ─────────────────────
     se escriben al final, aunque vayan al principio. Así pueden
     resumir el documento completo, que al empezar todavía no existe.

     El resumen: entre 150 y 250 palabras, y responde cuatro cosas:
       qué problema · qué se hizo · cómo · qué resultado se espera
     Sin citas, sin secciones, sin "el presente documento tiene por objeto".

     La introducción: presenta el proyecto y anuncia la estructura del
     documento. Es más larga y más suelta que el resumen.

     La prueba del resumen: si alguien lee solo eso, ¿entiende de qué se
     trata el proyecto? Es lo único que muchos van a leer.                -->

## Resumen
La tienda de indumentaria ALESSA KIDS de la Ciudad Autónoma de Buenos Aires (CABA-Argentina)
en funcionamiento desde ---- registra sus pedidos de encango bajo un estricto control en un cuadeno físico ya que la tienda opera en las plataformas virtuales como ser Marketplace de Facebook, Instagram, Tick tok y WatsApp, y todoslos pedidos son concretados mediante WatsApp, y despues se pasa a un cuaderno para llevar el registro.

Para resolver esta problemática este proyecto desarrolla un sistema web de registro y consulta
de pedidosque permite filtrar por fecha de entrega y asegura la persistencia de los datos mediante un reslpaldo que se construye sobre el interfaz del usuario desarollado previamente, incorporado a un abase de datos relacionalen MySQL y una capa lógica en PHP.

El funcionamiento del sistema se valida mediante casos de prueba orientados al registro, 
la consulta y el manejo de errores.
Se espera que la implementacion de esta herramienta elimine la version dispersa de chats 
y tambien el direccionamiento que se hace para concretar un pedido y que garantice un respldo confiable para la gestión diaria de la tienda.


*(163 palabras)*

## Introducción

El presente documento describe el desarrollo de un sistema de gestión de pedidos
para la Tienda de indumentaria para niñ@s ALESSA KIDS, elaborado como proyecto integrador        del módulo
Proyecto de Software del Programa Académico Desconcentrado "Técnico Superior en
Informática" de la UMSA, Sede Colquencha.

El proyecto da continuidad al trabajo iniciado en el módulo de Programación Web, donde
se construyó y publicó la interfaz web de usuario del catálogo. Aquella primera versión 
permite mostrar los productos al público almacenadas en un achivo JSON, pero carece de 
una base de datos y de las herramientas necesarias para registrar y consultar las operaciones  
de forma centralizada. El presente modulo completa el el sitema mediante la incorporación 
de una base de datos relacional en MySQL y lógica del servidor requerida para el
registro de encargos, la consulta de pedidos  pendientes segun la fecha de entrega 
y la gestion del respaldo de la información. 
almacenaba la información en un archivo estático, lo que permitía mostrar los
productos pero no registrar operaciones. Este módulo completa el sistema con una
base de datos y la lógica de servidor necesaria para registrar y consultar
pedidos.


El documento se encuentra organizada en cinco partes. La primera presenta la propuesta: el
problema, los objetivos, la justificación y el alcance. La segunda desarrolla el
marco teórico y la recopilación de información. La tercera detalla el desarrollo:
requerimientos, metodología, construcción y pruebas. La cuarta aborda los
aspectos de puesta en producción y costos. La quinta presenta las conclusiones y
recomendaciones.

---

*(La propuesta está completa. El documento continúa el Día 6 con el marco teórico.)*
