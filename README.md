# Crucigramas VS

Duelo de crucigramas en tiempo real para dos jugadores. Es un solo archivo (`index.html`), sin backend propio: los navegadores se conectan directo entre sí con [PeerJS](https://peerjs.com), usando su servidor público gratuito solo para presentarse.

## Cómo publicarlo

Sirve cualquier hosting de archivos estáticos con HTTPS.

### GitHub Pages (se puede hacer desde el celu)
1. En github.com: **New repository** → nombre `crucigramas-vs` → público → **Create**.
2. **Add file → Upload files** → subí `index.html` → **Commit changes**.
3. **Settings → Pages** → Source: *Deploy from a branch* → Branch `main`, carpeta `/ (root)` → **Save**.
4. En uno o dos minutos queda en `https://TU-USUARIO.github.io/crucigramas-vs/`.

### Vercel o Netlify
Importá el repo de GitHub, o en la compu arrastrá la carpeta a https://app.netlify.com/drop. No hace falta configurar build.

## Cómo se juega
1. Uno toca **Crear sala de duelo** y después **Invitar con link** (en el celu abre el menú para compartir por WhatsApp).
2. El otro abre el link, pone su nombre y toca **Unirme**.
3. El anfitrión elige 5, 10 o 15 minutos y toca **Empezar duelo**.

## Cosas a saber
- El anfitrión es el árbitro: si cierra la pestaña o bloquea el celu mucho rato, la sala se cae. Mientras espera, conviene dejar la pantalla abierta.
- Si el invitado se desconecta, puede volver con el mismo link y conserva sus palabras.
- En algunas redes muy cerradas (wifi corporativo, algunos datos móviles) la conexión directa puede fallar. Para producción conviene pasar a un servidor propio (Supabase Realtime o un servidor PeerJS propio).
- El banco tiene 200 palabras con pistas en `BANK`, al principio del script. Para sumar más, agregá líneas `PALABRA|Pista` (solo mayúsculas, sin tildes, Ñ permitida, 3 a 11 letras).
