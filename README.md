# 🧭 Guía paso a paso – Demo Barra de Navegación Responsive

## BEM + OOCSS + Estructura Modular

---

## 1️⃣ Objetivo de la Demo

👉 Construir una barra de navegación responsive desde cero, aplicando:

- **BEM** para el nombrado de clases
- **OOCSS** para separar estructura y apariencia
- **Arquitectura CSS modular** (componentes, skins y utilidades)

La idea no es solo que _“funcione”_, sino mostrar cómo crece un proyecto **ordenadamente**.

---

## 2️⃣ Analizar el componente antes de codear

Antes de escribir código, observamos el componente:

### Elementos que tendrá la barra de navegación

- Logo (marca)
- Lista de enlaces
- Enlace activo
- Botón de acción (por ejemplo: Login / Menú)

📌 **Pregunta clave para el grupo:**

> ¿Qué partes son **estructura** y cuáles son solo **apariencia visual**?

---

## 3️⃣ Definir la estructura de carpetas

Creamos una estructura pensada para **escalar**:

```txt
css/
├── components/
│   └── nav.css
├── skins/
│   └── nav-theme.css
├── utils/
│   └── spacing.css
└── main.css
```

## 4️⃣ Estructura HTML usando BEM

```HTML
<nav class="nav">
  <div class="nav__logo">MiLogo</div>

  <ul class="nav__list">
    <li class="nav__item">
      <a href="#" class="nav__link nav__link--active">Inicio</a>
    </li>
    <li class="nav__item">
      <a href="#" class="nav__link">Servicios</a>
    </li>
    <li class="nav__item">
      <a href="#" class="nav__link">Contacto</a>
    </li>
  </ul>

  <button class="nav__button">Login</button>
</nav>

```

> 💡 Claves didácticas <br/>
> .nav → bloque
> **logo, **list, \_\_item → elementos
> --active → modificador
> Las clases describen función, no apariencia

## 5️⃣ CSS de estructura (OOCSS)

📁 **components/nav.css**

Aquí definimos **cómo se ordenan los elementos**, no cómo se ven.

```css
.nav {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.nav__list {
  display: flex;
  gap: 1rem;
  list-style: none;
}

.nav__link {
  text-decoration: none;
  font-weight: 600;
}

.nav__button {
  border: none;
  cursor: pointer;
}
```

> 👉 Hasta aquí:<br/>
> No hay colores
> No hay sombras
> No hay “branding”

## 6️⃣ Estilos visuales (Skin)

📁 **skins/nav-theme.css**

Ahora sí agregamos **identidad visual**.

```css
.nav {
  background-color: #ffffff;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.nav__link {
  color: #333;
}

.nav__link--active {
  color: #0d6efd;
  border-bottom: 2px solid #0d6efd;
}

.nav__button {
  background-color: #0d6efd;
  color: #fff;
  padding: 0.5rem 1rem;
  border-radius: 6px;
}
```

> 📌 Mensaje clave:
> Podríamos cambiar completamente el diseño sin tocar el HTML ni el componente base.

## 7️⃣ Utilidades reutilizables

📁 utils/spacing.css

```CSS
u-padding-md {
  padding: 1rem;
}

.u-margin-sm {
  margin: 0.5rem;
}
```

Uso en HTML:

```HTML
<nav class="nav u-padding-md">
```

👉 Son clases:

Genéricas

Reutilizables

No dependen del componente

## 8️⃣ Archivo principal

📁 main.css

```CSS
@import "utils/spacing.css";
@import "components/nav.css";
@import "skins/nav-theme.css";

```

📌 Orden lógico:

Utilidades

Estructura

Apariencia

## 9️⃣ Mostrar cómo crece el proyecto

Durante la demo puedes decir:

- “Si mañana agregamos un footer → otro componente”
- “Si cambiamos el branding → solo tocamos `skins/`”
- “Si queremos menos padding → ajustamos utilidades”

👉 El proyecto **escala sin romperse**.

---

## 🔟 Reflexión final (muy importante)

❓ **¿Qué pasaría si todo estuviera en un solo archivo CSS?**

- Clases mezcladas sin orden
- Difícil encontrar errores
- Cambios pequeños rompen cosas grandes
- Código poco mantenible
- Más tiempo → más bugs

✅ **Con esta estructura:**

- Código más legible
- Mejor trabajo en equipo
- Menos miedo a modificar
- Pensamiento profesional

---

## 🎯 Cierre para la clase

> “No se trata solo de que el navbar funcione,  
> sino de que el código pueda vivir y crecer en el tiempo.”

---

### 👉 Si quieres, en el próximo mensaje puedo:

- Adaptar esto a **SCSS**
- Convertir la demo en **responsive con menú hamburguesa**
- Prepararlo como **guión para presentar en clase** 👨‍🏫
