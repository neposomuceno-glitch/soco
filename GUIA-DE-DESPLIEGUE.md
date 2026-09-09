# Guía de Despliegue

Dos formas de publicar este proyecto en español: como un sitio web estático real (GitHub Pages — gratuito, la forma más fácil de conservar el diseño exacto), o pegado página por página en WordPress.

---

## Opción 1: GitHub Pages (recomendado — conserva el sitio exactamente como fue diseñado)

1. **Cree una cuenta de GitHub** si no tiene una: [github.com/join](https://github.com/join) (gratis).
2. **Cree un nuevo repositorio**: haga clic en el "+" arriba a la derecha → "New repository." Póngale el nombre que quiera (p. ej. `sociologia-proyecto`). Márquelo como **Public**. No lo inicialice con un README.
3. **Suba los archivos**: en la página del nuevo repositorio, haga clic en "uploading an existing file," y arrastre los 12 archivos `.html` del `sociology-project-espanol-sitio-web.zip` que ya tiene (descomprímalo primero). Confirme la subida (commit).
4. **Active Pages**: vaya a la pestaña **Settings** del repositorio → **Pages** (barra lateral izquierda) → en "Build and deployment," fije **Source** en "Deploy from a branch," rama **main**, carpeta **/ (root)**. Guarde.
5. **Espere alrededor de un minuto**, luego actualice esa pantalla de Settings → Pages — mostrará su URL en vivo, algo como `https://suusuario.github.io/sociologia-proyecto/`.
6. Listo — el sitio está en línea, `index-es.html` se carga automáticamente en esa URL raíz (puede que necesite ajustar el nombre del archivo de inicio a `index.html` si prefiere que cargue sin especificar el nombre; véase la nota abajo), y todos los enlaces internos entre páginas ya funcionan, pues se construyeron como enlaces `.html` relativos que coinciden exactamente con esta estructura de archivos.

**Nota sobre el archivo de inicio:** GitHub Pages carga automáticamente un archivo llamado `index.html` en la URL raíz. Nuestro archivo se llama `index-es.html`. Tiene dos opciones: (a) renombrar `index-es.html` a `index.html` al subirlo (y ajustar cualquier enlace que apunte a `index-es.html` para que apunte a `index.html`), o (b) dejarlo como está y compartir el enlace directo a `index-es.html` (p. ej. `https://suusuario.github.io/sociologia-proyecto/index-es.html`) en lugar de la URL raíz.

**Para actualizar después:** edite o vuelva a subir cualquier archivo en el repositorio (mediante el editor web de GitHub o subiéndolo de nuevo), y el sitio en vivo se actualiza en uno o dos minutos automáticamente. No hay un paso de "publicar" aparte.

**Dominio personalizado (opcional):** si tiene un dominio propio, agregue un archivo `CNAME` con su nombre de dominio al repositorio, y apunte el DNS de su dominio a los servidores de GitHub — la propia documentación de GitHub Pages explica esto paso a paso si lo desea.

---

## Opción 2: WordPress (página por página, usando los archivos de fragmento)

WordPress no puede tomar los 12 archivos HTML tal cual — necesita que el contenido de cada página se pegue en una Página de WordPress, no que se suban como archivos. Use los archivos de fragmento en la carpeta `wordpress-fragments` — cada uno tiene solo el `<style>` y el contenido del cuerpo (sin `<html>`/`<head>`/barra de navegación, ya que WordPress aporta su propia estructura de página y menú de navegación).

**Para cada uno de los 11 archivos de fragmento:**

1. En el administrador de WordPress, vaya a **Páginas → Añadir nueva**.
2. Póngale a la página un título que coincida con el contenido (p. ej. "Directorio de Sitios de Sociología").
3. Cambie el editor de bloques a un **bloque de HTML personalizado**: añada un bloque nuevo, busque "HTML personalizado," y selecciónelo.
4. Abra el archivo de fragmento correspondiente en un editor de texto, copie todo su contenido, y péguelo en el bloque de HTML personalizado.
5. Haga clic en **Vista previa** para verificar que se ve bien, luego **Publicar**.
6. Anote el slug de URL final que WordPress asigna a la página (se muestra debajo del título, p. ej. `susitio.com/directorio-de-sociologia`).

**Después de publicar las 9 páginas, corrija los enlaces cruzados:** cada fragmento todavía tiene enlaces internos que apuntan a `algo.html` (p. ej. `href="sociology-websites-directory-es.html"`), coincidiendo con la estructura de archivos de GitHub Pages — las URL de páginas de WordPress no terminarán en `.html`. Una vez que todas las páginas estén publicadas y conozca sus slugs reales, use el bloque de HTML personalizado de cada página nuevamente para buscar y reemplazar esos enlaces `.html` por las URL reales de WordPress (p. ej. cambiar `href="sociology-websites-directory-es.html"` a `href="/directorio-de-sociologia/"`, según la estructura real de permalinks de su sitio).

**Una nota sobre los dos mapas interactivos:** `social-instability-heat-map-es-wp-fragment.html` y `social-instability-maps-by-type-es-wp-fragment.html` incluyen una etiqueta `<script>` (la lógica de cambio de pestañas del mapa por tipo). Algunos planes de WordPress (especialmente los planes gratuitos/básicos de WordPress.com) eliminan las etiquetas `<script>` de los bloques de HTML personalizado por razones de seguridad. Si las pestañas no cambian después de publicar:
- En **WordPress autoalojado** (WordPress.org, su propio hosting): esto debería funcionar tal cual, o instale un plugin como "Insert Headers and Footers" o "WPCode" para autorizar scripts personalizados si están bloqueados.
- En **WordPress.com**: puede que necesite un plan Business o superior (que permite HTML/JS personalizado mediante un plugin), o en su lugar incruste la página vía un iframe que apunte a la versión alojada en GitHub Pages — las dos opciones pueden coexistir: aloje los dos mapas interactivos en GitHub Pages, e incruste solo esos dos en WordPress mediante un bloque de iframe apuntando a la URL de GitHub Pages.

---

## ¿Cuál usar?

- **Quiere que esté en línea lo antes posible, exactamente como fue diseñado, gratis, con la navegación funcionando de inmediato:** GitHub Pages.
- **Quiere que viva dentro de un sitio de WordPress ya existente** (que combine con su tema, menú de navegación, etc.) **y no le importa corregir algunos enlaces manualmente:** los fragmentos de WordPress.
- **Quiere ambos:** aloje los dos mapas interactivos en GitHub Pages (ya que su JavaScript de cambio de pestañas es lo más propenso a tener problemas de compatibilidad con WordPress) e incruste esos dos mediante iframe en WordPress, mientras pega el resto como páginas nativas de WordPress.
