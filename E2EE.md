### Safety Number

El Safety Number fue comparado presencialmente con mi compañero mediante los dígitos/QR
mostrados por Signal. Después de confirmar que coincidía en ambos dispositivos, la
conversación quedó marcada como verificada.

Un Safety Number diferente podría indicar un cambio de dispositivo o identidad
criptográfica, pero también podría ser una señal de sustitución de identidad o de un
ataque man-in-the-middle.


# E2EE: Signal, WireGuard y acceso excepcional

La **forward secrecy (FS)** significa que el compromiso de una clave actual no debería permitir descifrar automáticamente las comunicaciones pasadas. En Signal, las claves se actualizan durante la conversación, por lo que una clave comprometida no debería revelar todo el historial anterior. Sin embargo, si el atacante obtiene acceso al teléfono desbloqueado, puede leer el historial que esté almacenado en texto plano dentro del dispositivo.

La **post-compromise security (PCS)** se refiere a la capacidad de recuperar la seguridad después de una intrusión. Si el atacante pierde el acceso y Signal puede continuar actualizando las claves mediante nuevos intercambios, los mensajes futuros pueden volver a estar protegidos. Esto depende de que el dispositivo deje de estar comprometido y de que las identidades puedan verificarse nuevamente mediante el Safety Number. La PCS no borra automáticamente el historial que el atacante ya haya copiado.

WireGuard también utiliza claves de sesión efímeras durante sus handshakes, por lo que el compromiso de una clave no debería revelar todas las sesiones anteriores. No obstante, WireGuard protege principalmente el trayecto entre dos peers. Si uno de los endpoints está comprometido, el atacante puede observar el tráfico después de que sea descifrado en ese dispositivo.

Un mandato de acceso excepcional contra Signal tendría que modificar el protocolo, obligar al proveedor a guardar claves adicionales o introducir una forma especial de descifrar mensajes. Eso debilitaría la separación entre las claves y aumentaría el riesgo de abuso o filtración. El artículo *Keys Under Doormats* explica que este tipo de acceso excepcional agrega complejidad y puede debilitar propiedades como la forward secrecy, afectando potencialmente a todos los usuarios.

En WireGuard, el proveedor del túnel normalmente no puede leer el contenido protegido sin las claves privadas de los peers. Para crear un acceso excepcional tendría que agregar un nuevo peer, obtener una clave privada, modificar la configuración o comprometer uno de los endpoints. En ese caso, el acceso no sería una función transparente del protocolo, sino una modificación de la configuración o una intrusión en un dispositivo.

**Para nuestro venture Pactrail: Tor oculta el origen de red de las partes frente a observadores del escrow, Signal protege la mensajería y acuerdos confidenciales con E2EE frente al servidor, y WireGuard cifra el enlace de transporte entre peers de validación sin brindar anonimato.**

Durante el laboratorio, el estado de WireGuard se comprobó mediante `wg show`, observando un handshake reciente y bytes enviados y recibidos, además de un ping entre las direcciones privadas del túnel. Las claves privadas se mantuvieron fuera del repositorio.

Fuente: [Keys Under Doormats](https://academic.oup.com/cybersecurity/article/1/1/69/2367066)