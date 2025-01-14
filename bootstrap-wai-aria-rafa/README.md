<div align='right'>

### **Rafael Martín Mayor**

</div>

# Mejora de Accesibilidad en Elementos de Bootstrap con WAI-ARIA

Este proyecto demuestra cómo implementar atributos WAI-ARIA en elementos comunes de Bootstrap para mejorar su accesibilidad. Incluye ejemplos antes y después de la mejora, siguiendo las prácticas recomendadas de WAI-ARIA.

## Tabla de Contenidos

1. [Introducción](#introducción)  
2. [Elementos Mejorados](#elementos-mejorados)  
3. [Implementación de las mejoras](#implementación-de-las-mejoras)  

---

## Introducción

WAI-ARIA (Web Accessibility Initiative – Accessible Rich Internet Applications) es un conjunto de especificaciones diseñadas para mejorar la accesibilidad de aplicaciones web dinámicas. Al integrar los atributos WAI-ARIA en elementos de Bootstrap, hacemos que las interfaces sean más inclusivas, permitiendo que personas con discapacidades naveguen y usen los elementos de forma efectiva.

---

## Elementos Mejorados

En este proyecto se trabajaron los siguientes cinco elementos de Bootstrap:  

1. **Botón (Button)**  
2. **Barra de Navegación (Navbar)**  
3. **Menú desplegable (Dropdown)**  
4. **Alerta (Alert)**  
5. **Pestañas (Tabs)**  

Cada uno fue mejorado con los atributos `role`, `aria-*` y `tabindex` para garantizar su compatibilidad con tecnologías asistivas como lectores de pantalla.

---

## Implementación de las mejoras

#### **Botón**
##### Código original:
```html
<button class="btn btn-primary">Enviar</button>
```

##### Código mejorado:
```html
<button class="btn btn-primary" aria-pressed="false">Enviar</button>
```

- **Atributo WAI-ARIA:**
  - `aria-pressed`: Indica si el botón está activado (`true`) o no (`false`).
- **Mejora:** Añade información sobre el estado del botón para usuarios con lectores de pantalla.

---

#### **Navbar**
##### Código original:
```html
<nav class="navbar navbar-expand-lg navbar-light bg-light">
  <a class="navbar-brand" href="#">Mi Sitio</a>
  <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav">
    <span class="navbar-toggler-icon"></span>
  </button>
  <div class="collapse navbar-collapse" id="navbarNav">
    <ul class="navbar-nav">
      <li class="nav-item"><a class="nav-link active" href="#">Inicio</a></li>
    </ul>
  </div>
</nav>
```

##### Código mejorado:
```html
<nav class="navbar navbar-expand-lg navbar-light bg-light" role="navigation">
  <a class="navbar-brand" href="#">Mi Sitio</a>
  <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Abrir menú de navegación">
    <span class="navbar-toggler-icon"></span>
  </button>
  <div class="collapse navbar-collapse" id="navbarNav">
    <ul class="navbar-nav">
      <li class="nav-item">
        <a class="nav-link active" href="#" role="menuitem" aria-current="page">Inicio</a>
      </li>
    </ul>
  </div>
</nav>
```

- **Atributos WAI-ARIA:**
  - `role="navigation"`: Identifica el elemento como una barra de navegación.  
  - `aria-expanded`: Informa si el menú de navegación está expandido o colapsado.  
  - `aria-controls` y `aria-label`: Proporcionan más contexto sobre la funcionalidad del botón de la barra de navegación.  
- **Mejora:** Clarifica el propósito y estado del navbar para tecnologías asistivas.

---

#### **Menú desplegable**
##### Código original:
```html
<div class="dropdown">
  <button class="btn btn-secondary dropdown-toggle" type="button" data-bs-toggle="dropdown">
    Opciones
  </button>
  <ul class="dropdown-menu">
    <li><a class="dropdown-item" href="#">Acción</a></li>
  </ul>
</div>
```

##### Código mejorado:
```html
<div class="dropdown">
  <button class="btn btn-secondary dropdown-toggle" type="button" data-bs-toggle="dropdown" aria-expanded="false">
    Opciones
  </button>
  <ul class="dropdown-menu" role="menu" aria-labelledby="dropdownMenuButton">
    <li role="menuitem"><a class="dropdown-item" href="#">Acción</a></li>
  </ul>
</div>
```

- **Atributos WAI-ARIA:**
  - `aria-expanded`: Indica si el menú está abierto.
  - `role="menu"`: Define el contenedor como menú.
  - `role="menuitem"`: Indica que cada opción es un ítem del menú.
- **Mejora:** Clarifica el propósito y estado del menú para tecnologías asistivas.

---

#### **Alerta**
##### Código original:
```html
<div class="alert alert-warning">¡Advertencia!</div>
```

##### Código mejorado:
```html
<div class="alert alert-warning" role="alert">¡Advertencia!</div>
```

- **Atributo WAI-ARIA:**
  - `role="alert"`: Notifica al lector de pantalla sobre el mensaje automáticamente.
- **Mejora:** Permite que el mensaje sea leído inmediatamente, garantizando que no pase desapercibido.

---

#### **Pestañas**
##### Código original:
```html
<ul class="nav nav-tabs">
  <li class="nav-item"><a class="nav-link active" href="#">Inicio</a></li>
  <li class="nav-item"><a class="nav-link" href="#">Perfil</a></li>
</ul>
```

##### Código mejorado:
```html
<ul class="nav nav-tabs" role="tablist">
  <li class="nav-item">
    <a class="nav-link active" href="#" role="tab" aria-selected="true" aria-controls="inicio">Inicio</a>
  </li>
  <li class="nav-item">
    <a class="nav-link" href="#" role="tab" aria-selected="false" aria-controls="perfil" tabindex="-1">Perfil</a>
  </li>
</ul>
```

- **Atributos WAI-ARIA:**
  - `role="tablist"`: Define la lista como un conjunto de pestañas.
  - `role="tab"`: Indica que cada ítem es una pestaña.
  - `aria-selected`: Indica cuál pestaña está activa.
  - `aria-controls`: Relaciona la pestaña con su contenido.
- **Mejora:** Estructura la navegación por pestañas para usuarios con dispositivos de asistencia.