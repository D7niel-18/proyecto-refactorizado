# Taller Práctico DIW (RA2) - El Refactor

**Módulo:** Diseño de Interfaces Web (DAW)  
**Unidad:** UD2 - Uso de Estilos  
**Resultado de Aprendizaje (RA2):** Crear interfaces Web homogéneas definiendo y aplicando estilos.

---

## 📝 Descripción del Proyecto

Este proyecto consiste en la refactorización completa del código HTML y la arquitectura de estilos de un sitio web personal (portfolio) de 3 páginas: **Inicio (`index.html`)**, **Sobre mí (`sobre.html`)** y **Contacto (`contacto.html`)**. 

El objetivo principal es eliminar malas prácticas de desarrollo (uso de estilos en línea `style="..."` y bloques `<style>` internos en el `<head>`) para transformar el sitio en un proyecto limpio, semántico, mantenible y escalable mediante una arquitectura modular en **SASS (SCSS)**.

---

## 📁 Estructura del Proyecto

```text
proyecto-refactorizado/
├── codigoAntiguo/ --> Contiene el código que da la actividad sin refactorizar
├── css/
    ├── .css 
└── scss/ 
    # Carpeta con el código fuente en SASS
    ├── _base.scss        # Reglas globales y reseteo básico
    ├── _header.scss      # Estilos del header
    ├── _footer.scss      # Estilos del pie de página
    ├── _nav.scss         # Estilos del menú de navegación
    ├── _variables.scss  # Variables de colores, fuentesy medidas
    ├── _componentes.scss # Componentes reutilizables (tarjetas, botones, formulario)
    ├── .css       # Archivo CSS final compilado
    ├── .css.map
    └── .scss      # Archivo SCSS principal u orquestador
├── index.html            # Página principal / Inicio
├── sobre.html            # Página de información
├── contacto.html         # Página de contacto
├── README.md             # Documentación del proyecto

```

---

## 🛠️ Explicación Detallada de los Archivos

### 📄 Páginas HTML (Estructura Semántica)
* **`index.html`**: Presentación general y sección de proyectos destacados.
* **`sobre.html`**: Resumen profesional y lista de habilidades técnicas.
* **`contacto.html`**: Formulario estructurado para envío de mensajes (`<form>`, `<input>`, `<textarea>`, `<button>`).

> **Nota de Refactorización:** Todos los archivos HTML están 100% limpios de atributos de estilo directos y vinculados al único heet externo: `.css`. Se han empleado etiquetas semánticas (`<header>`, `<nav>`, `<main>`, `<section>`, `<footer>`).

---

### 🎨 Arquitectura SASS (`scss/`)

El diseño de  utiliza la metodología de parciales (`_nombre.scss`) para garantizar la modularidad y facilitar el mantenimiento:

1. **`scss/_variables.scss`**
   * **Propósito:** Almacena los valores globales que se reutilizan en toda la web.
   * **Contenido:** Definición de variables Sass (`$color-primario`, `$color-secundario`, `$color-fondo`, `$color-texto`, `$fuente-principal`, etc.). No genera reglas CSS por sí solo.

2. **`scss/_base.scss`**
   * **Propósito:** Define los estilos genéricos y el comportamiento global de las etiquetas HTML.
   * **Contenido:** Reglas para `body`, `main`, párrafos (`p`), y los títulos globales (`h2`, `h3`).

3. **`scss/_header.scss`**
   * **Propósito:** Controla el bloque superior de la interfaz.
   * **Contenido:** Estilos del `<header>`, como el fondo azul, la alineación del texto y los tamaños tipográficos del título `<h1>`.

4. **`scss/_nav.scss`**
   * **Propósito:** Estiliza el sistema de navegación.
   * **Contenido:** Formato de la lista `<ul>` y los enlaces `<a>`, eliminación de subrayados, espaciado entre elementos y el indicador de la página actual (`.activo`).

5. **`scss/_componentes.scss`**
   * **Propósito:** Agrupa elementos visuales específicos y componentes reutilizables.
   * **Contenido:** Estilos de tarjetas (`.caja-contenido`), contenedores secundarios (`.caja-placeholder`), listas personalizadas (`.lista-habilidades`) y todo el maquetado del formulario de contacto (`.form-contacto`).

6. **`scss/_footer.scss`**
   * **Propósito:** Controla el cierre de la interfaz web.
   * **Contenido:** Estilos para el `<footer>`, color de fondo oscuro, tipografía en tonos grises y derechos de autor.

7. **`scss/.scss` (Orquestador)**
   * **Propósito:** Archivo principal que conecta todos los parciales.
   * **Contenido:** Contiene las directivas `@import` para ensamblar todos los parciales en el orden adecuado y generar el archivo final `.css`.

---

## 🚀 Fases de Desarrollo

* [x] **Fase 1: El Refactor (Limpieza total) - Terminada el 13/10/2026**
  * Extracción de estilos en línea en `index.html`.
  * Eliminación del bloque `<style>` en `sobre.html`.
  * Creación e integración de `contacto.html`.
  * Centralización de reglas CSS en la estructura de parciales SASS.
* [ ] **Fase 2: La Evolución (Diseño y Personalización)**
  * Aplicación de una nueva paleta de colores coherente.
    Para esta fase utilizaré una web llamada coolors.co donde puedes generar una paleta de colores completa. En mi caso he generado la siguiente paleta de colores:

    - #004E98;  Azul oscuro (Header, títulos principales)
    - #3A6EA5;  Azul medio (Subtítulos, elementos secundarios)
    - #FF6700;  Naranja (Botones, hovers, elementos interactivos)
    - #EBEBEB;  Gris claro (Fondo general de la web)
    - #C0C0C0;  Gris plateado (Bordes de cajas, inputs)
    - #1A1A1A;  Texto oscuro para legibilidad
    - #FFFFFF;  Blanco para tarjetas y texto sobre azul/naranja


  * Incorporación de tipografías desde Google Fonts.
    Para la incorporación de tipografias debemos buscar en google fonts una fuente que nos guste en mi caso elegí Montserrat y Roboto ambas sans-serif

  * Maquetación mediante Flexbox para el menú `<nav>` y efectos `:hover`.
  * Estilizado del formulario de contacto.
* [ ] **Fase 3: La Verificación**
  * Validación del archivo `.css` compilado mediante el **W3C CSS Validator** garantizando cero errores.

---

## ⚙️ Instrucciones para la Compilación de SASS

1. Abrir la carpeta del proyecto en **Visual Studio Code**.
2. Asegurarse de tener instalada la extensión **Live Sass Compiler** (por Glen Marks).
3. Hacer clic en el botón **"Watch Sass"** ubicado en la barra de estado inferior para activar la compilación automática.
4. Cualquier modificación dentro de la carpeta `scss/` recompilará automáticamente el archivo `.css`.