# Calculador de Margen de Planta — ENAMI

Calculador interactivo de resultado económico de maquila (Planta Delta), con
pestaña de sensibilización y guardado de escenarios en sesión.

Es un sitio 100% estático (un solo `index.html`, sin backend ni build step),
así que se despliega en Vercel tal cual, sin configuración adicional.

## Publicar en Vercel vía GitHub

1. **Crear el repositorio en GitHub**
   - Entra a https://github.com/new
   - Nombre sugerido: `calculador-margen-planta`
   - Puede ser público o privado — Vercel funciona igual con ambos
   - No agregues README/gitignore ahí (ya tienes estos archivos)

2. **Subir este archivo al repo** (desde tu computador, con `git` instalado):
   ```bash
   cd carpeta-donde-descargaste-index.html
   git init
   git add index.html README.md
   git commit -m "Calculador de margen de planta"
   git branch -M main
   git remote add origin https://github.com/TU-USUARIO/calculador-margen-planta.git
   git push -u origin main
   ```

3. **Conectar con Vercel**
   - Entra a https://vercel.com/new
   - Elige "Import Git Repository" y selecciona el repo que acabas de crear
   - Framework Preset: **Other** (o "Static") — no necesita build command
   - Output directory: dejar vacío o `.` (raíz)
   - Click "Deploy"

   En ~30 segundos queda publicado en una URL tipo
   `https://calculador-margen-planta.vercel.app`

4. **Actualizaciones futuras**: cualquier `git push` a `main` vuelve a
   desplegar automáticamente (Vercel queda escuchando el repo).

## Sobre Supabase (para más adelante)

Hoy los "Escenarios Guardados" viven solo en memoria del navegador (se
pierden al cerrar la pestaña). Si más adelante quieres que persistan entre
sesiones o se compartan entre usuarios, se puede agregar Supabase como
base de datos: una tabla `scenarios` (nombre, fecha, json de parámetros,
margen) y reemplazar las funciones `saveScenario`/`loadScenario`/
`deleteScenario` del `index.html` por llamadas a la API de Supabase
(`supabase-js` vía CDN, sin necesidad de build step). Aviso si quieres que
lo arme.
