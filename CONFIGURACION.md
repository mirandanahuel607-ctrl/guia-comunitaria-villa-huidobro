# Explora Villa Huidobro — configuración

La página ya está publicada en GitHub Pages. El juego funciona sin configurar Supabase, pero en ese modo los resultados quedan guardados únicamente en el navegador donde se jugó. Para que el panel administrador pueda ver resultados enviados desde otros celulares o computadoras, hay que configurar Supabase.

## Activar resultados compartidos

1. Crear un proyecto en https://supabase.com/.
2. En el panel de Supabase, abrir **SQL Editor**, crear una consulta nueva, copiar el contenido de `supabase_schema.sql` y ejecutarlo.
3. En **Project Settings → API** (o **Connect**), copiar la **Project URL** y la clave pública/anon/publishable.
4. En GitHub, abrir `index.html`, tocar el lápiz para editar y buscar estas dos líneas:
   `const SUPABASE_URL = "PEGAR_URL_DE_SUPABASE";`
   `const SUPABASE_ANON_KEY = "PEGAR_CLAVE_PUBLICA_ANON_DE_SUPABASE";`
   Reemplazar los textos entre comillas por la URL y la clave pública del proyecto, guardar y confirmar el cambio.
5. En Supabase, ir a **Authentication → Users** y crear el usuario administrador con tu correo y contraseña.
6. Copiar el UUID/ID de ese usuario.
7. Volver al **SQL Editor** y ejecutar, cambiando el UUID por el de tu usuario:
   `insert into public.quiz_admins (user_id) values ('PEGAR-UUID-DEL-USUARIO');`
8. Esperar un poco a que GitHub Pages actualice la web. Abrir la página, entrar a **Panel privado** e iniciar sesión con el correo y contraseña del usuario creado.

**Importante:** nunca pegues una clave `service_role` en `index.html` ni la compartas. Solo usá la clave pública/anon/publishable. Como participan menores, conviene que usen apodos y no nombres completos.

## Página
https://mirandanahuel607-ctrl.github.io/guia-comunitaria-villa-huidobro/
