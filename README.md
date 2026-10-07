# RAPIDCUE

App personal para encontrar y reproducir el momento clave de una canción: chorus, hook, drop, clímax, motivo o verso.

## Qué ya funciona en el código

- Login oficial de Spotify con OAuth 2.0 + PKCE. No usa ni almacena Client Secret.
- Búsqueda real de temas en el catálogo de Spotify.
- Selección de pistas reales y guardado local de cues por **Spotify Track ID**.
- Reproducción en el dispositivo Spotify Connect activo desde el milisegundo del cue.
- Ajuste visual del cue sobre la forma de onda y persistencia en el navegador.
- Estado demo si Spotify todavía no está configurado.

## Probarlo en local

Sirve la carpeta desde un host local que utilice la dirección de loopback:

```bash
python3 -m http.server 8080 --bind 127.0.0.1
```

Abre exactamente `http://127.0.0.1:8080/`.

## Configuración de Spotify Developer

1. Entra en [Spotify Developer Dashboard](https://developer.spotify.com/dashboard) y crea una app de prueba.
2. Añade como **Redirect URI** la URL que muestra el diálogo “Conectar Spotify” de RAPIDCUE. Para la prueba local anterior es:
   `http://127.0.0.1:8080/`
3. Copia únicamente el **Client ID** en RAPIDCUE. El Client Secret no se usa.
4. Pulsa “Continuar con Spotify” y concede los permisos solicitados.
5. Abre Spotify en escritorio, web, móvil o un dispositivo Connect y reproduce algo una vez. RAPIDCUE necesita un dispositivo disponible para iniciar la reproducción.

La aplicación solicita estos permisos mínimos:

- `user-read-playback-state`
- `user-read-currently-playing`
- `user-modify-playback-state`

## Requisitos y límites

- La cuenta debe ser Spotify Premium para controlar la reproducción.
- Spotify no entrega análisis estructural de canciones a integraciones nuevas. El detector automático de chorus/clímax es una fase posterior y deberá basarse en cue points propios, letras sincronizadas donde existan o audio sobre el que haya permiso de análisis.
- Los cues de esta versión se guardan localmente en el navegador. La siguiente fase los llevará a una base de datos privada para que sobrevivan entre dispositivos.

## Principios del producto

1. Un cue confirmado manualmente siempre prevalece sobre cualquier detección automática.
2. Los cues pertenecen a una versión exacta de pista, no solo a título y artista.
3. El objetivo inicial es escucha personal con Spotify Premium, no una plataforma pública.
