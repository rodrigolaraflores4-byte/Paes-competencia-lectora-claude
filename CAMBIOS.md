# Cambios de esta versión

## Guardado automático en Supabase (los datos ya no se pierden)
- `server/db.ts`: al arrancar (o tras un reinicio de Vercel) carga todo desde Supabase; cada cambio se sube solo
  (solo las filas modificadas, con borrados incluidos). Ahora también se guardan las **respuestas por pregunta**
  (`attempt_answers`), la **racha** y los **puntos de vocabulario**.
- `server/app.ts`: en Vercel espera a que el cambio llegue a Supabase antes de responder.
- Indicador "Guardado en la nube" en el encabezado docente y panel de estado en "Persistencia Supabase".

## Para dejarlo funcionando (una sola vez)
1. Supabase → SQL Editor → ejecutar `supabase-migration.sql`.
2. Vercel → Settings → Environment Variables: `SUPABASE_URL` y `SUPABASE_ANON_KEY` (ver `.env.example`). Volver a desplegar.

## Vocabulario
- Nueva pestaña docente **Vocabulario**: crear, editar y eliminar palabras; resultados por palabra y por estudiante.
- El estudiante lee el banco desde el servidor; sus respuestas se corrigen y guardan en el servidor.

## Diseño e interactividad
- Animaciones, barra de progreso, atajos de teclado (A-D, Enter, flechas) y retroalimentación en el taller de vocabulario.
- Transiciones entre pestañas docentes, estilos globales y foco accesible.
