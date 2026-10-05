# Web de David Puig — conexión con n8n

## 1) Publicar gratis
Recomendación: Cloudflare Pages.

Opción sencilla:
1. Crea una cuenta gratuita en Cloudflare.
2. Ve a Workers & Pages.
3. Crea un proyecto de Pages.
4. Sube esta carpeta como sitio estático (o usa un repositorio Git).
5. El archivo principal debe llamarse `index.html`.
6. Cloudflare te dará una dirección `*.pages.dev`.

## 2) Crear el Webhook en n8n
1. En n8n crea un workflow.
2. Añade un nodo **Webhook**.
3. Method: `POST`.
4. Path: `solicitud-fotografia`.
5. Response: responde inmediatamente con un JSON simple, por ejemplo:
   `{"ok": true}`
6. Activa el workflow.
7. Copia la **Production URL** del Webhook.

## 3) Conectar la web
Abre `index.html`, busca:

`const N8N_WEBHOOK_URL = "https://TU-N8N/webhook/solicitud-fotografia";`

y sustituye la URL por la Production URL real de n8n.

## 4) Datos que recibe n8n
La web enviará JSON con:
- nombre
- email
- telefono
- servicio
- fecha
- ubicacion
- duracion
- personas
- descripcion
- presupuesto
- extras
- comentarios
- origen
- enviado_en

A partir del Webhook puedes conectar:
Webhook → AI Agent/OpenAI → cálculo → Google Sheets/Airtable → email a David.

## 5) Cambiar las fotos
Dentro de `/images`, sustituye:
- hero.jpg
- gallery-1.jpg
- gallery-2.jpg
- gallery-3.jpg
- gallery-4.jpg
- gallery-5.jpg
- gallery-6.jpg

Mantén los mismos nombres para no tocar el HTML.

## 6) Antes de publicar
- Cambia el texto "Sobre mí" por la bio real de David.
- Añade su Instagram y email reales.
- Añade aviso de privacidad/consentimiento antes de usar el formulario con clientes reales.
- Prueba el Webhook con la URL de producción, no solo la URL de test de n8n.
