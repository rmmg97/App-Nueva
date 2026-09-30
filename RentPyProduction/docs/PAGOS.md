# Pagos RentPy

La integración productiva debe usar un adquirente contratado por RentPy. La alternativa local prioritaria es Bancard vPOS 2.0/TPago.

Bancard publica que vPOS 2.0 admite tarjetas de crédito/débito, Zimple, tarjetas internacionales, API y 3D Secure. La adhesión requiere documentación comercial y una cuenta a nombre de la empresa. No se deben almacenar números de tarjeta en RentPy.

Flujo seguro:
1. Crear reserva en estado `pending_payment`.
2. Crear orden de pago server-side.
3. Redirigir/embebir el checkout autorizado por el adquirente.
4. Recibir confirmación server-to-server/webhook firmado.
5. Verificar monto, moneda, reserva y estado.
6. Solo entonces cambiar a `confirmed`.
7. Registrar comisión RentPy y saldo del anfitrión.
8. Ejecutar liquidación al anfitrión según contrato y reglas de cancelación.

Nunca confirmar una reserva solamente porque el navegador volvió del checkout.
