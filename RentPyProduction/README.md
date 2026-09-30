# RentPy — Production Foundation v1.0

Marketplace de alojamientos para Paraguay, con roles de huésped/anfitrión, autenticación, publicación moderada, búsqueda, reserva con control de solapamiento y base para pagos.

## Ejecutar
Requiere Node.js 20+.

```bash
npm start
```
Abrir `http://127.0.0.1:8080`.

## Seguridad incluida
- Contraseñas con scrypt (Node crypto).
- Sesiones en cookie HttpOnly + SameSite.
- Validación de entradas básicas.
- Control de roles.
- Protección contra path traversal.
- CSP, X-Frame-Options y nosniff.
- Escritura atómica del almacenamiento.
- Bloqueo de reservas con fechas superpuestas.
- No se almacenan datos de tarjetas.

## Producción real
1. Sustituir `data/db.json` por PostgreSQL/MySQL.
2. Ejecutar detrás de HTTPS y proxy seguro.
3. Configurar backups, logs y monitoreo.
4. Integrar Bancard vPOS/TPago mediante las credenciales y contrato de RentPy. Bancard indica que vPOS 2.0 permite tarjetas, Zimple, tarjetas internacionales, API y 3D Secure; la integración requiere adhesión comercial. No colocar credenciales en frontend.
5. Implementar webhook/firma de pago antes de confirmar una reserva.
6. Incorporar almacenamiento de imágenes (S3-compatible) y antivirus/validación MIME.
7. Implementar KYC/identidad mediante proveedor contratado y revisión legal.
8. Configurar correo/SMS/WhatsApp transaccional.
9. Crear política de privacidad, términos, cancelaciones, reembolsos, cookies y contrato anfitrión.
10. Configurar dominio, HTTPS y publicación de PWA/Android/iOS.

## Flujo de pago recomendado
Reserva -> bloqueo temporal -> checkout Bancard -> confirmación server-to-server/webhook -> reserva confirmada -> liquidación al anfitrión. Nunca marcar una reserva como pagada solo porque el navegador volvió de la página de pago.
