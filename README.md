# Fase de Investigación: Comprendiendo el corazón del sistema.

## Reto de Investigación 1. 

Syslog es una estándar de facto para el envío de mensaje de registro (log) en una red IP. Syslog funciona como un protocolo de capa de aplicación que permite a diversos dispositivos como servidores o routers enviar sus registros a un receptor centralizado.

La anatomía de un mensaje Syslog se divide en 3 partes.

    PRI(prioridad) -> Es la primera parte y esta encerrada entre ángulos < >. Es un valor numérico calculado a partir de Facility ( Indica el tipo de sistema o proceso que generó el mensaje) y Severity ( indica la importancia del mensaje). La fórmula para calcular la prioridad es Facility * 8 + Severity.

    HEADER(cabecera): Contiene información identificativa. La fecha y hora  en la que se generó el mensaje y el nombre o dirección IP del dispositivo que envió el mensaje.

    MSG(mensaje): Contenido real del log con un TAG que nos indica que programa o proceso lo generó y el CONTENT que nos indica la descripción detallada del evento.

El estándar de Syslog es la piedra angular de la gestión de logs en sistemas Linux y als redes IP. Nos permite separar la aplicación que genera el log , el sistema que lo almacena y el software que lo analiza.

El sistema mediante Severity clasifica el evento indicando la importancia del mensaje siendo la escala:
        0-Emergencia
        1-Alerta
        2-Crítico
        3-Error
        4-Advertencia
        5-Notificación
        6-informativo
        7-Depuración

Por ejemplo que el archivo /var/log/auth.log tenga permisos de lectura para usuarios no privilegiados es una negligencia grave , debido a la exposición de información sensible sobre la autenticación que este archivo contiene. Se verían expuestos nombres de usuario , intento fallido de auth , detalle de privilegios , fugas de credenciales involuntarias ,etc...

La principal diferencia entre un intento fallido de conexión remota SSH y una fallo de contraseña local radica en la presencia de las direcciones IP de origen , el nombre del proceso , el uso de los puertos de red y la ausencia de una terminal física(TTY).

## Reto de Investigación 2.

La protección de la información es un factor esencial para la sostenibilidad de las organizaciones. En este escenario, cobra gran importancia las acciones encaminadas a garantizar la auditoría de los sistemas con el objetivo de prevenir o detectar violaciones que afecten la integridad, disponibilidad y confidencialidad de los datos.

El alto costo que ha implicado históricamente la ausencia o errores asociados a la generación de registros de auditoría
han provocado que surjan múltiples marcos de referencia con diversidad de estructura, procesos y términos, lo cual
afecta la integración, disminución de la complejidad y aplicación pertinente en las organizaciones de dichos marcos.

La información que contienen los registros, de los sistemas y la red, es sensible, por lo cual es necesario
que se garantice la integridad y confidencialidad de los mismos. La falta de protección de los registros puede causar
que se modifiquen o eliminen, lo cual puede permitir que una actividad maliciosa pase desapercibida[1]

Importancia de la Centralización y Custodia Externa de Registros
La gestión de logs no debe limitarse a una recolección pasiva en el host local. Mantener los registros dispersos en las máquinas que los generan las deja "indefensas" ante un compromiso del sistema; un atacante con privilegios elevados puede manipular o eliminar los archivos de auditoría para ocultar sus huellas. Por el contrario, el envío de registros en tiempo real a un servidor externo seguro garantiza la integridad de la evidencia y facilita el análisis forense post-mortem, ya que los datos permanecen fuera del alcance del atacante. Además, esta centralización es la base para la implementación de sistemas de correlación de eventos, que permiten detectar patrones de ataque complejos que serían invisibles al analizar máquinas de forma aislada [2].La adopción de modelos de madurez en la gestión de registros es, por tanto, una pieza clave para garantizar la resiliencia y la disponibilidad de los servicios en infraestructuras críticas [3].

## REFERENCIAS

[1] G. E. González Hidalgo, H. R. González Brito, y M. Peña Casanova, "Marcos de referencia para gestión de registros de auditoría", Serie Científica de la Universidad de las Ciencias Informáticas, vol. 14, no. 2, pp. 36-50, feb. 2021. [En línea]. Disponible en: https://dialnet.unirioja.es/servlet/articulo?codigo=8590410

[2] J. Arizaga Gamboa, E. Alvarado Unamuno, y J. Chicala Arroyave, "Sistemas SIEM aplicados a sistemas de salud: Caso de estudio TEMONET", Serie Científica de la Universidad de las Ciencias Informáticas, vol. 14, no. 11, pp. 206-232, nov. 2021. [En línea]. Disponible en: https://dialnet.unirioja.es/servlet/articulo?codigo=8590578

[3] A. V. Padrón Guerra, "Modelo de madurez para la gestión de logs en centros de datos: automatización y buenas prácticas", Revista Científica de Ingeniería Electrónica, Automática y Comunicaciones, vol. 46, no. 0, 2025. [En línea]. Disponible en: https://dialnet.unirioja.es/servlet/articulo?codigo=10398407