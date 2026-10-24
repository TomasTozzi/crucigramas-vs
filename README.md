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
1. Cada jugador elige su nombre y su color en el inicio. Si dos eligen el mismo, a uno se lo ve con otro color.
2. Uno toca **Crear sala** y después **Invitar con link** (en el celu abre el menú para compartir por WhatsApp). Entran hasta 5.
3. Los demás abren el link, ponen su nombre y tocan **Unirme**.
4. En la sala, el anfitrión elige el modo y la duración (5, 10 o 15 minutos) y toca **Empezar**:
   - **Mismo tablero**: todos resuelven el mismo crucigrama; cada palabra es de quien la completa primero.
   - **Rotación**: cada uno arranca con su tablero y cada 90 segundos pasan al siguiente. Las palabras completas quedan fijas, las letras sueltas se borran y, si un tablero se completa entero, llega uno nuevo.
5. Cada palabra suma sus letras multiplicadas por la dificultad de la pista: fácil ×1, media ×1,5, difícil ×2. En empate de puntos gana quien llegó primero a ese puntaje.
6. Al terminar hay un ranking. Cualquiera puede pedir otra partida y arranca cuando aceptan todos los que siguen en la sala; el anfitrión también puede volver a la sala para cambiar el modo.
7. Con **Ver tablero** se ven en rojo las palabras que nadie completó (en Rotación se puede mirar cada tablero).
8. Si alguien se desconecta en plena partida, vuelve con el mismo link y conserva su lugar y sus puntos.

La dificultad de cada pista va como tercer campo en el banco: `PALABRA|Pista|2` (media) o `PALABRA|Pista|3` (difícil); sin número es fácil. Al escribir, la N vale como Ñ.

## Cosas a saber
- El anfitrión es el árbitro: si cierra la pestaña o bloquea el celu mucho rato, la sala se cae. Mientras espera, conviene dejar la pantalla abierta.
- En algunas redes muy cerradas (wifi corporativo, algunos datos móviles) la conexión directa puede fallar. Para producción conviene pasar a un servidor propio (Supabase Realtime o un servidor PeerJS propio).
- Cada partida arma un crucigrama cuadrado de 15×15 con casillas negras y unas 35 a 40 palabras. El tamaño está en `GRID`.
- El banco tiene unas 2.000 palabras con pistas en `BANK`, al principio del script. Para sumar más, agregá líneas `PALABRA|Pista` (solo mayúsculas, sin tildes, Ñ permitida, 3 a 11 letras). Cuantas más palabras cortas haya, más denso sale el tablero.
