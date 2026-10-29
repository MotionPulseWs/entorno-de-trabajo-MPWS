# motionpulse.xyz — Landing del entorno de trabajo

## Qué hacer
1. Usa este archivo como `index.html` en la raíz del dominio `motionpulse.xyz` (public_html). Es un solo archivo: CSS y JS van dentro; las fuentes vienen de Google Fonts (Lexend Deca).
2. **Logo:** el `<img>` del header apunta a `assets/img/logo-motionpulse-blanco.png`. Pon el logo blanco real de MotionPulse en esa ruta o corrige la ruta. Si la imagen no existe, se muestra el texto "MotionPulse".
3. **WhatsApp:** en el `<script>`, completa `WHATSAPP` (solo dígitos, con el 51) y `WHATSAPP_VISIBLE`. El enlace se arma como `wa.me` y lleva un mensaje predefinido.
4. **Correo de soporte:** `sopporte@motionpulse.net` (es el mismo de la plantilla en construcción).
5. **Enlaces:** web, hosting y dominios van a `https://motionpulse.online/`; producción audiovisual va a `https://motionpulse.net/`.

## Diseño (no cambiar)
- Diseño base de 1920 px y caja de 1200 px (`--box`), con 40 px de margen lateral.
- Breakpoints (`max-width`):
  - 1600 (laptop)
  - 1280 (tablet horizontal)
  - 1024 (tablet vertical)
  - 767 (móvil; desde aquí todo se ve como un celular de 390–430 px)
- La página ocupa una pantalla completa (`min-height: 100vh` / `100svh`). Se verificó sin scroll en 1920×1080, 1600×900, 1280×800, 1024×1366 y 767×1000. En un celular de 390×844 ocupa unos 1.07 pantallas, y las tarjetas se vuelven compactas.
- Colores (Manual MPWS):
  - Fondo `#1a1a1a`, superficies `#202024` / `#23272E` y textos `#E9EEF2` / `#b4b4bf`.
  - Acentos: Motion Blue Light `#2843CA`, Motion Blue Dark `#242A8E` y Orange Pulse `#E94E1B`.
  - El punto naranja que late y la línea superior con degradado son los mismos de la plantilla en construcción.

## Que Google no lo indexe
1. El `<head>` ya trae `<meta name="robots" content="noindex, nofollow, …">`.
2. Agrega el contenido de `htaccess.txt` al `.htaccess` de public_html de motionpulse.xyz. Envía la cabecera `X-Robots-Tag: noindex`, que también cubre los PDF e imágenes.
3. Revisa los subdominios:
   - Si las carpetas de los subdominios (fk., laola., etc.) están dentro de ese public_html, heredan la regla.
   - Si un subdominio tiene su propio `.htaccess` (WordPress), agrega el bloque también ahí.
   - En los WordPress de desarrollo, activa además *Ajustes → Lectura → "Disuade a los motores de búsqueda…"*.
4. **No** pongas `Disallow: /` en `robots.txt`. Si Google no puede rastrear la página, nunca ve el `noindex`, y una URL que ya está indexada seguiría apareciendo.
5. Para que un proyecto en desarrollo no lo pueda ver nadie, protege su carpeta con contraseña (cPanel → Privacidad de directorios).
6. Comprueba la cabecera con `curl -I https://motionpulse.xyz` y busca `X-Robots-Tag`.
