Fase de Investigación: Comprendiendo el corazón del sistema.

Reto de Investigación 1. 

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

Reto de Investigación 2.




