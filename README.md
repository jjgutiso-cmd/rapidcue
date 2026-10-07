# RAPIDCUE

Prototipo de una app personal para encontrar y reproducir el momento clave de una canción: chorus, hook, drop, clímax, motivo o verso.

## Estado actual

- Interfaz interactiva de búsqueda y selección de temas.
- Forma de onda simulada para mover, probar y confirmar un cue point.
- Cue asociado conceptualmente a la versión exacta de Spotify.
- Muestras para canción comercial, BSO e instrumental.
- Todavía no hay conexión real con Spotify ni persistencia de datos.

## Ejecutar localmente

No requiere dependencias:

```bash
python3 -m http.server 8080
```

Abre `http://localhost:8080`.

## Próxima fase: Spotify

La integración personal utilizará OAuth 2.0 con PKCE y pedirá únicamente estos permisos:

- `user-read-playback-state`
- `user-modify-playback-state`
- `user-read-currently-playing`

Será necesario crear una aplicación de prueba en Spotify Developer y registrar la URL de retorno del entorno en el que se despliegue RAPIDCUE. El Client ID es público; el Client Secret no se incorporará al frontend.

## Decisiones de producto

1. Un cue confirmado manualmente debe prevalecer siempre sobre una detección automática.
2. Los cues se guardan por ID de pista/version, no solo por título.
3. El objetivo inicial es escucha personal con Spotify Premium, no una plataforma pública.
