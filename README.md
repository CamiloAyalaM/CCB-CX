# Ruta CX

Cuaderno de trabajo en línea del taller **Customer Experience: analítica y gestión de datos para startups** (Innovalab, Cámara de Comercio de Bogotá).

Cada startup construye en cuatro pasos su Ruta de Experiencia y Datos del Cliente, recibe retroalimentación inmediata y la descarga en PDF. El facilitador ve el avance del grupo en un tablero en vivo.

## Enlaces

| Para | Dirección |
|---|---|
| Participantes | `https://camiloayalam.github.io/CCB-CX/` |
| Tablero del facilitador | `https://camiloayalam.github.io/CCB-CX/?facilitador` |
| Demostración sin guardar | `https://camiloayalam.github.io/CCB-CX/?demo` |

El grupo se asigna por fecha (antes del 17 de octubre de 2026, grupo del 14; después, grupo del 20). Se puede forzar con `?g=1` o `?g=2`.

## Cómo está hecho

- `index.html`: toda la aplicación, sin compilación. Usa `supabase-js` desde CDN.
- `privacidad.html`: política de tratamiento de datos.
- Base de datos: proyecto de Supabase `CCB-CX`, migración `ruta_cx_schema`. Las tablas tienen RLS sin políticas; todo el acceso pasa por funciones `cx_*`.
- `supabase/functions/feedback/`: función que pide la revisión a Claude Haiku 5.5.

## Configuración

- La revisión con IA necesita el secreto `ANTHROPIC_API_KEY` en Supabase (Edge Functions → Secrets). Sin él, la app ofrece copiar la instrucción para usarla en otra IA.
- Límites: dos revisiones por paso y por equipo, y un tope global en `config.ai_cap`.
- La clave del tablero se guarda como hash SHA-256 en `config.fac_hash`.
