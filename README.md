# Mercè Sánchez · Salud Femenina +40

Plataforma de contenidos para los tres programas de Mercè Sánchez:
- **Reset Hormonal** (programa esencial de 6 semanas) — clave: `Merce01`
- **Círculo Equilibrio** (acompañamiento premium) — clave: `Merce02`
- **Programa Mentora** (formación de coaches) — clave: `Merce03`

## Estructura del proyecto

```
/
├── index.html         → Landing pública (sin login)
├── acceso1.html       → Reset Hormonal (Merce01)
├── acceso2.html       → Círculo Equilibrio (Merce02)
├── acceso3.html       → Programa Mentora (Merce03)
├── images/            → Fotos del perfil de Mercè
├── videos/            → (futuro) Vídeos subidos directamente
└── pdfs/              → (futuro) Materiales descargables
```

## Despliegue (GitHub + Vercel)

1. **Crear repo en GitHub:**
   - Nombre sugerido: `merce-sanchez-coach`
   - Subir todos estos archivos.

2. **Conectar a Vercel:**
   - Importar el repo desde Vercel.
   - No requiere configuración: es HTML estático puro.
   - URL sugerida: `mercesanchezcoach.vercel.app` (o dominio propio).

3. **Auto-deploy:**
   - Cada vez que se suba un archivo nuevo (vídeo, PDF, foto), Vercel lo despliega automáticamente.

## Cómo añadir contenido nuevo

### Subir un vídeo

**Opción recomendada (YouTube/Vimeo):**
1. Subir el vídeo a YouTube como "No listado" o a Vimeo.
2. En `acceso1.html` (o el que toque), buscar la tarjeta de la sesión correspondiente.
3. Reemplazar el `<div class="video-thumb">Sesión X — Pendiente</div>` por:
   ```html
   <div class="video-thumb" style="aspect-ratio: 16/9; padding: 0;">
     <iframe src="URL_DEL_VIDEO" style="width:100%;height:100%;border:0;" allowfullscreen></iframe>
   </div>
   ```

**Opción 2 (vídeo en el repo, no recomendado para vídeos largos):**
- Subir el .mp4 a la carpeta `/videos/` y usar `<video src="videos/sesion1.mp4" controls>`.
- ⚠️ Vercel tiene límite de 100MB por archivo. Solo usar para vídeos cortos.

### Subir un PDF

1. Subir el archivo a `/pdfs/` (crear la carpeta si no existe).
2. En el `acceso1.html` correspondiente, en la sección "Materiales descargables", descomentar el bloque template y adaptarlo:
   ```html
   <a class="recurso-item" href="pdfs/guia-semana-1.pdf" target="_blank">
     <div class="recurso-icon">PDF</div>
     <div class="recurso-content">
       <h4>Guía Semana 1 — Tu cuerpo después de los 40</h4>
       <p>Resumen, ejercicios y plantilla de seguimiento</p>
     </div>
   </a>
   ```

### Cambiar contraseñas

En cada `accesoN.html`, al final del archivo, en el bloque `<script>`:
```javascript
const PASSWORD = "Merce01";   // ← cambiar aquí
```

## ⚠️ Aviso importante sobre seguridad

Las contraseñas en el código JavaScript son **visibles para cualquiera** que sepa abrir las herramientas de desarrollador del navegador. Esto sirve para evitar accesos accidentales y para una primera versión, pero **no es seguro** contra alguien decidido.

**Para una segunda versión (Fase 2):**
- Migrar autenticación a Supabase Auth (cuentas individuales por alumna).
- Vídeos protegidos por enlace temporal o privados en Vimeo.
- Esto permitirá saber qué alumna ha visto qué, gestionar bajas, etc.

## Stack técnico

- HTML/CSS/JS vanilla (sin framework).
- Tipografía: Cormorant Garamond + Inter (Google Fonts).
- Sin backend en esta v1 — todo en archivos estáticos.
- Deploy: Vercel.

## Próximos pasos sugeridos

1. **v1 (esta):** publicar y empezar a subir contenido.
2. **v2:** Supabase Auth + cuentas individuales + tracking de progreso.
3. **v3:** integración con WhatsApp Business + agente de IA para preguntas frecuentes.
