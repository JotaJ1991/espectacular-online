# 📻 Espectacular Online — Sitio web (versión mejorada)

Rediseño de la página de la emisora digital **Espectacular Online — "Tú Preferida"**: una sola página (`index.html`), autónoma, rápida y accesible, con reproductor en vivo funcional.

> Reconstruye la versión original (WordPress sobre hosting gratuito `.page.gd`) como un sitio estático ligero, corrigiendo sus principales problemas de SEO, rendimiento, accesibilidad y funcionalidad.

## 🔴 La versión original vs. ✅ esta versión

| Aspecto | Original | Esta versión |
|---|---|---|
| Base | WordPress 6.8.3 + Elementor + ~10 plugins (~99 KB de HTML) | 1 archivo estático, sin dependencias pesadas |
| jQuery | Cargado **dos veces** (WP 3.7.1 + CDN 3.6.0) | No usa jQuery |
| Fuentes | Roboto y Montserrat duplicadas | 1 sola petición (Montserrat, `display=swap`) |
| Meta description | ❌ Ausente | ✅ Presente |
| Open Graph / Twitter | ❌ Ausentes (enlace sin previsualización) | ✅ Completos + imagen social |
| Datos estructurados | ❌ | ✅ JSON-LD `RadioStation` |
| Sección de noticias | ❌ Mostraba "Error cargando noticias" | ✅ "Ahora suena" con mejora progresiva (nunca muestra error) |
| Menú | Enlaces a secciones inexistentes | Anclas reales a la misma página |
| Título | `Espectacular Online  – Tú Preferida` (doble espacio) | Limpio y descriptivo |
| Versión de WP expuesta | ⚠️ Sí | No aplica |
| Accesibilidad | Emojis como íconos, sin semántica | HTML semántico, `aria-*`, salto al contenido, foco visible |
| Email | En texto plano (spam) | Compuesto por JS para dificultar el scraping |

## ✨ Características

- **Reproductor en vivo** conectado al stream de Zeno.fm, con play/pausa, control de volumen, indicador "EN VIVO", ecualizador animado y manejo de errores (reintento) sin mensajes intrusivos.
- **"Ahora suena"** vía `EventSource` a la metadata de Zeno.fm (mejora progresiva: si falla, se mantiene el nombre de la emisora, nunca un error).
- **Diseño responsive** (mobile-first) con menú adaptable.
- **Botón directo de WhatsApp** con mensaje prellenado.
- Respeta `prefers-reduced-motion`.

## 🚀 Cómo verlo

Al ser estático, basta abrir `index.html` en el navegador. Para probar con un servidor local:

```bash
python -m http.server 8000
# luego abre http://localhost:8000
```

## 🌐 Despliegue en GitHub Pages

1. Repositorio → **Settings → Pages**.
2. En **Source**, elige la rama `main` y carpeta `/ (root)`.
3. Guarda: en un minuto tendrás una URL pública `https://<usuario>.github.io/<repo>/`.

## ⚙️ Configuración

- **Stream:** cambia la constante `STREAM` en el `<script>` de `index.html`.
- **Metadata "ahora suena":** constante `META` (endpoint de Zeno.fm).
- **URL del sitio:** reemplaza `__SITE_URL__` (en las meta/canonical/OG) por tu dominio real.

## 🖼️ Imagen (hero + social)

El banner oficial de la emisora (`assets/banner.jpg`, 1200×480) se usa como **imagen principal** de la portada y como **imagen social** (`og:image` / `twitter:image`). Es un **JPEG optimizado (~162 KB)**, por debajo del límite de ~300 KB de WhatsApp, así que la previsualización del enlace sí muestra imagen al compartirlo.

---

Créditos de contenido: **Espectacular Online** · Director General: Matías J. Díazgranados.
