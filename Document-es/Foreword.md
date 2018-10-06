
![OWASP LOGO](images/OWASP_logo.png)

# Estándar de Verificación de Seguridad en Aplicaciones Móviles - Liberación 1.1

05.08.2018

## Prefacio por Bernhard Mueller, lider del proyecto móvil de OWASP

Las revoluciones tecnológicas pueden suceder rápidamente. Hace menos de una década los celulares eran dispositivos torpes con pequeños teclados - juguetes caros para usuarios empresariales expertos en tecnología. Hoy los celulares son una parte esencial de nuestras vidas. Hemos llegado a confiar en ellos para la búsqueda de información, la navegación y la comunicación y están presentes tanto en los negocios como en nuestra vida social.

Cada nueva tecnología introduce nuevos riesgos de seguridad, y mantenerse al día con estos cambios es uno de los principales retos a los que se enfrenta la industria de la seguridad. El bando defensivo está siempre unos pasos detrás. Por ejemplo, el modo predeterminado para muchos fue aplicar viejas formas de hacer las cosas: los celulares son como pequeños ordenadores y las aplicaciones móviles son como el software clásico, así que seguramente los requerimientos de seguridad son similares, ¿no? Pero no funciona así. Los sistemas operativos para teléfonos inteligentes son diferentes a los sistemas operativos de escritorio, y las aplicaciones móviles son diferentes a las aplicaciones web. Por ejemplo, el método clásico de escaneo de virus basado en firmas no tiene sentido en los sistemas operativos móviles modernos: no sólo es incompatible con el modelo de distribución de aplicaciones móviles, sino que también es técnicamente imposible debido a las restricciones del aislamiento. Además, algunos tipos de vulnerabilidades, como los desbordamientos de búfer y los problemas XSS, son menos relevantes en el contexto de las aplicaciones móviles que, por ejemplo, en las aplicaciones de escritorio y las aplicaciones web (con excepciones).

Con el tiempo, la industria ha conseguido un mejor control del panorama de amenazas móviles. Resulta que la seguridad móvil tiene que ver con la protección de los datos: las aplicaciones almacenan nuestra información personal, imágenes, grabaciones, notas, datos de cuentas, información empresarial, ubicación y mucho más. Actúan como clientes que nos conectan con los servicios que utilizamos a diario, y como centros de comunicación que procesan todos y cada uno de los mensajes que intercambiamos con otros. Comprometer el celular de una persona, es obtener acceso sin filtros a su vida. Cuando consideramos que los dispositivos móviles se pierden o roban más fácilmente y que el malware para dispositivos móviles está aumentando, la necesidad de protección de datos se hace aún más evidente.

Por lo tanto, un estándar de seguridad para aplicaciones móviles debe centrarse en la forma en que las aplicaciones móviles manejan, almacenan y protegen la información sensible. A pesar de que los sistemas operativos móviles modernos como iOS y Android ofrecen buenas APIs para el almacenamiento y la comunicación de datos seguros, éstas deben ser incluidas en las aplicaciones y usadas correctamente para ser efectivas. El almacenamiento de datos, la comunicación entre aplicaciones, el uso apropiado de las API criptográficas y la comunicación segura a través de la red son sólo algunos de los aspectos que requieren una cuidadosa consideración.

Una cuestión importante que requiere el consenso de la industria es hasta dónde se debe llegar exactamente para proteger la confidencialidad e integridad de los datos. Por ejemplo, la mayoría de nosotros estaríamos de acuerdo en que una aplicación móvil debería verificar el certificado del servidor en una conexión TLS. Pero ¿qué ocurre con la fijación de certificados SSL? ¿No resulta en una vulnerabilidad? ¿Debería ser este un requerimiento si una aplicación maneja datos sensibles, o es contraproducente? ¿Necesitamos cifrar los datos almacenados en bases de datos SQLite, a pesar de que el sistema operativo aísla la aplicación? Lo que es apropiado para una aplicación puede ser poco realista para otra. El MASVS es un intento de estandarizar estos requerimientos utilizando distintos niveles de verificación que se ajustan a los diferentes escenarios de amenaza.

Además, la aparición del malware y las herramientas de administración remota han creado conciencia de que los propios sistemas operativos móviles tienen fallas, por lo que las estrategias de aislamiento se utilizan cada vez más para proporcionar protección adicional a los datos confidenciales y evitar la manipulación del lado del cliente. Aquí es donde las cosas se complican. Las características de seguridad por hardware y las soluciones de aislamiento a nivel de sistema operativo, como Android for Work y Samsung Knox, existen, pero no siempre están disponibles en diferentes dispositivos. Como una curita, es posible implementar medidas de protección basadas en software - pero desafortunadamente, no hay estándares o procesos de prueba para verificar este tipo de protecciones.

Como resultado, los reportes de pruebas de seguridad de aplicaciones móviles están por todas partes: por ejemplo, algunos testers reportan una falta de ofuscación o detección de root en una aplicación Android como "falla de seguridad". Por otra parte, las medidas como el cifrado de palabras, la detección de depuradores o la ofuscación del flujo de control no se consideran obligatorias. Sin embargo, esta forma binaria de ver las cosas no tiene sentido porque la resistencia no es una proposición binaria: depende de las amenazas particulares en el dispositivo contra las que se quiere defender. Las protecciones de software no son inútiles, pero en última instancia pueden ser eludidas, por lo que nunca deben utilizarse como sustituto de los controles de seguridad.

El objetivo general del MASVS es ofrecer una línea de base para la seguridad de las aplicaciones móviles (MASVS-L1), mientras que también permite la inclusión de medidas de defensa en profundidad (MASVS-L2) y protecciones contra las amenazas del lado del cliente (MASVS-R). El MASVS está pensado para lograr lo siguiente:

- Proveer requerimientos para arquitectos y desarrolladores de software que buscan desarrollar aplicaciones móviles seguras;
- Ofrecer un estándar para que la industria pueda utilizar en las revisiones de seguridad de aplicaciones móviles;
- Clarificar el rol de los mecanismos de protección de software en la seguridad móvil y proporcionar requerimientos para verificar su efectividad;
- Proporcionar recomendaciones específicas sobre el nivel de seguridad que se recomienda para los diferentes casos de uso.

Somos conscientes de que es imposible lograr un consenso del 100% en la industria. No obstante, esperamos que el MASVS sea útil para proporcionar orientación en las fases de desarrollo y prueba de aplicaciones móviles. Como estándar de código abierto, el MASVS evolucionará con el tiempo, y acogemos con agrado cualquier contribución o sugerencia.