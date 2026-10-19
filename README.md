# Lab 18 — Signal + Safety Number y túnel WireGuard (Sesión 21)

Entregable completo del laboratorio de criptografía de extremo a extremo (E2EE), minimización de metadatos y túneles P2P seguros.

- [`index.html`](./index.html): Dashboard interactivo y reporte web completo con diseño dark cyber, tabla de metadatos, evidencias ampliables y citas.
- [`E2EE.md`](./E2EE.md): Ensayo técnico (489 palabras) sobre Forward Secrecy, Post-Compromise Security, mandatos de acceso excepcional (*Keys Under Doormats*) y contraste para el venture Pactrail.
- `image copy 3.png`: Captura de pantalla de Signal oficial verificando el Safety Number (QR y 60 dígitos) con el compañero, marcado como verificado (sin números de teléfono expuestos).
- `image.png`: Evidencia WireGuard en Windows con `wg show` (handshake reciente, bytes transmitidos > 0 KiB y `ping 10.77.0.2`).
- `image copy.png`: Registro de log en el GUI de WireGuard en Windows (keepalives, handshake initiation, handshake response y keypairs).
- `image copy 2.png`: Registro de log en WireGuard iOS móvil (keepalives y UAPI endpoint update con el peer).

## Cumplimiento de Políticas
- Ninguna clave privada expuesta (`private key: (hidden)`).
- AllowedIPs restringido a `/32` (sin full-tunnel).
- Túnel desactivado al concluir las pruebas.
