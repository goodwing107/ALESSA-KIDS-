
# Marco teórico

## Sistema de gestión de pedidos para ALESSA KIDS, indumentaria para niñas y niños

---

## Introducción

El registro de encargos y la consulta de disponibilidad en comercios de indumentaria infantil que operan mediante redes sociales y mensajería suelen depender de anotaciones manuales y conversaciones dispersas en las plataformas virtuales donde se publican los productos. Este apartado evalúa las alternativas existentes frente al entorno operativo de ALESSA KIDS, un negocio familiar de dos personas con un catálogo previo en JSON y ventas y encargos canalizados a través de WhatsApp y un cuaderno. Asimismo, fundamenta el desarrollo de un módulo web con una base de datos relacional y respaldos periódicos.


## Estado del arte

### Alternativas existentes

| Solución | Costo | Sin internet | Desde celular | Consulta por fecha |
|---|---|---|---|---|
| **Cuaderno de papel y chat** *(actual)* | Bs 0 | sí | no aplica | **no** |
| **Planilla de cálculo compartida** | Bs 0 | no | difícil de usar | sí, con filtros |
| **Software de gestión comercial** *(genérico)* | desde Bs 200/mes | según el producto | sí | sí, entre muchas funciones |
| **Sistema a medida para comercios** | desde USD 400 iniciales | sí | sí | sí |
| **Solución propuesta** | Bs 600/año | no *(requiere conexión)* | sí | sí |

### Análisis

**El cuaderno** es gratuito, no requiere electricidad ni conexión a internet. Su
límite es exactamente el problema formulado: no permite consultar por fecha de
entrega. Se mantiene como respaldo de contingencia.

**La planilla compartida** resuelve la consulta y no cuesta nada, pero exige
conexión permanente y su uso en un celular, en el mostrador y con prisa, es
impracticable: la observación del 18 de noviembre registró que el registro de un
pedido debe hacerse en menos de un minuto mientras se atiende a dos clientes.

**El software de gestión comercial** resuelve el problema y mucho más:
inventario, facturación, proveedores. Ese "mucho más" es su desventaja aquí. El
costo mensual no se justifica para un negocio que necesita una de sus veinte
funciones, y la curva de aprendizaje es desproporcionada.

**El sistema a medida** es la alternativa más cercana. Se descarta por costo:
USD 400 iniciales representan aproximadamente el margen de un mes del negocio,
según la estimación de la propietaria.

### Conclusión del estado del arte

Ninguna alternativa disponible combina las cuatro condiciones que impone el
caso: costo compatible con un negocio de dos personas, uso desde el celular en
el mostrador, consulta por fecha de entrega y alcance limitado a lo que el
cliente necesita.

La solución propuesta acepta una desventaja frente al cuaderno actual: requiere
conexión a internet. Se mitiga manteniendo el cuaderno como respaldo de
contingencia, y se declara como una limitación del proyecto.



## Metodología de desarrollo
Se aplicará el modelo incremental de desarrollo de software, complementado con prácticas adaptadas de Personal Extreme Programming (PXP) para un desarrollador individual.

El sistema web de gestión de pedidos para ALESSA KIDS se construirá mediante incrementos funcionales, comenzando por la administración del catálogo y el registro de pedidos. En cada incremento se desarrollará, probará y corregirá una funcionalidad específica antes de pasar a la siguiente etapa.

Este método permite reducir riesgos, detectar errores de manera temprana, incorporar cambios según las necesidades de la tienda y entregar versiones utilizables antes de finalizar el proyecto.


| Herramienta | Uso | Por qué |
|---|---|---|
| Git y GitHub | Control de versiones | Ya en uso desde el módulo anterior |
| XAMPP | Entorno local | Funciona sin internet, requisito del aula |
| PHP 8 y MySQL | Backend y datos | Funcionan en hosting compartido de bajo costo |
| Matriz de casos de prueba | Verificación | Trazable con los requerimientos |

---
## Referencias bibliográficas

Hernández Sampieri, R., Fernández Collado, C., y Baptista Lucio, P. (2014).
*Metodología de la investigación* (6ª ed.). McGraw-Hill.

IEEE. (1998). *IEEE Recommended Practice for Software Requirements
Specifications* (IEEE Std 830-1998). Institute of Electrical and Electronics
Engineers.

ISO/IEC/IEEE. (2018). *Systems and software engineering - Life cycle processes
- Requirements engineering* (ISO/IEC/IEEE 29148:2018). ISO.

Nixon, R. (2024). *Learning PHP, MySQL & JavaScript* (7ª ed.). O'Reilly Media.

Patton, J. (2014). *User Story Mapping: Discover the Whole Story, Build the
Right Product*. O'Reilly Media

### Fuentes no bibliográficas

La información sobre el proceso actual de la tienda proviene de:

- entrevista con la propietaria, 13 de noviembre de 2026
- observación directa en el local, 18 de noviembre de 2026, 09:00 a 11:00
- revisión del cuaderno de pedidos de marzo de 2026

Estas fuentes se citan en el texto como comunicación personal y no se listan en
las referencias bibliográficas, conforme a la norma APA.


## Nota sobre integridad académica

Este documento se apoya en fuentes externas, que están citadas donde
corresponde. Las decisiones de diseño, la formulación del problema y el
análisis del caso son propios y se fundamentan en la información recogida
directamente del cliente.

---

*(El marco teórico está completo. El documento continúa el día 9 con los requerimientos.)*
