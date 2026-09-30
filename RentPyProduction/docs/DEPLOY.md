# Despliegue recomendado

## Servidor
- Ubuntu LTS o proveedor cloud administrado.
- Node.js 20+.
- HTTPS obligatorio.
- Reverse proxy (Nginx/Caddy/Cloudflare).
- PostgreSQL administrado para producción.
- Backups automáticos y prueba de restauración.
- Logs centralizados y monitoreo.

## Dominio
Registrar y verificar disponibilidad de `rentpy.com.py`, `rentpy.com` y variantes antes de anunciar la marca.

## Base de datos
La demo usa `data/db.json` para que pueda arrancar sin infraestructura adicional. Para producción migrar usuarios, anuncios, reservas y sesiones a PostgreSQL con migraciones versionadas.

## Imágenes
Usar almacenamiento de objetos con URLs firmadas. Validar extensión y MIME, limitar tamaño y procesar imágenes antes de servirlas.

## Pagos
Solicitar adhesión a Bancard vPOS 2.0/TPago y obtener credenciales de producción. Las credenciales deben ser variables secretas del servidor.
