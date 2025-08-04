# 🧱 Web Frontend Architecture

This document outlines the folder structure and architecture used in the **web** frontend of this project. It follows a modular, scalable, and domain-driven design to ensure clean separation of concerns and long-term maintainability.

## 📁 Folder Structure Overview

```
project-root/
│
├── public/               # Static files (HTML, images, etc.)
├── src/                  # Application source code
│   ├── features/         # Domain-driven features of the app
│   │   ├── auth/         # Authentication-specific feature
│   │   │   ├── components/   # Auth-specific UI components
│   │   │   ├── hooks/        # Custom hooks for auth logic
│   │   │   ├── services/     # API services related to auth
│   │   │   ├── slices/       # Redux slices (if using Redux Toolkit)
│   │   │   └── pages/        # Pages/views related to auth
│   │   ├── dashboard/    # Dashboard-specific functionality
│   │   │   ├── components/
│   │   │   ├── hooks/
│   │   │   ├── services/
│   │   │   ├── slices/
│   │   │   └── pages/
│   │   └── ...           # Other domain features (e.g. products, users, etc.)
│   │
│   ├── shared/           # Shared reusable logic/components
│   │   ├── components/   # Common UI (buttons, modals, etc.)
│   │   ├── hooks/        # Reusable hooks
│   │   ├── services/     # Global services (e.g. API base)
│   │   ├── utils/        # Helpers and utilities
│   │   ├── styles/       # Global styles (Tailwind, SCSS, etc.)
│   │   └── contexts/     # Global React contexts (Auth, Theme, etc.)
│   │
│   ├── App.js            # Root component with providers and layout
│   ├── index.js          # React entry point
│   └── routes.js         # App routing configuration (React Router)
│
├── .env                  # Environment variables
├── .gitignore            # Git ignored files
├── package.json          # Project metadata, scripts, dependencies
└── README.md             # Project documentation
```

---

## 📂 Folder Descriptions

### `public/`

Contains static files served as-is:

* `index.html`
* Images, icons, logos
* Manifest or favicon

### `src/features/`

Each subfolder under `features` corresponds to a **feature/domain** of the application (e.g., auth, dashboard, orders). Internally, a feature is broken into:

* `components/`: Feature-specific UI elements
* `hooks/`: Feature-specific logic encapsulated in custom hooks
* `services/`: API clients or service logic
* `slices/`: Redux slices (only if using Redux Toolkit)
* `pages/`: Pages related to this feature, used in routing

This structure allows encapsulation and ownership of logic within a feature.

### `src/shared/`

Holds **reusable and shared logic** across the app:

* `components/`: UI elements shared across features (e.g., Button, Modal)
* `hooks/`: Common custom hooks like `useDebounce`, `useWindowSize`
* `services/`: Shared services like base Axios instance
* `utils/`: Utility functions, constants, validators
* `styles/`: Global styles, Tailwind config, themes
* `contexts/`: Shared app-wide contexts like AuthContext, ThemeContext

### `src/App.js`

Sets up high-level structure of the app: layout, context providers, routing.

### `src/index.js`

Mounts the React app to the DOM (`ReactDOM.createRoot`).

### `src/routes.js`

Holds routing config using `react-router-dom`. Includes public/private routes and guards.

---

## ⚙️ Configuration Files

### `.env`

Used for environment variables like:

```
REACT_APP_API_URL=https://api.example.com
```

### `package.json`

Defines:

* Dependencies and devDependencies
* Project scripts (`start`, `build`, `lint`, etc.)

---

## ✅ Best Practices

* Apply **domain-driven structure** using `features/`
* Isolate logic inside `hooks` and `services`
* Favor reusable components in `shared/components`
* Use environment variables for config
* Follow component-driven development and write unit tests for logic-heavy parts
* Apply responsiveness and accessibility from the beginning

---

## 📦 Future Enhancements

* Lazy-load feature pages with `React.lazy` and `Suspense`
* Add tests using Jest + React Testing Library
* Add i18n with `react-i18next`
* Setup error tracking (e.g. Sentry)
* Add PWA support or offline cache if needed

---

## 📣 Contribution Guide

When adding new features:

1. Create a new folder under `features/`.
2. Follow the subfolder convention (`components`, `hooks`, `pages`, etc.).
3. Reuse components and logic from `shared/` wherever possible.
4. Update `routes.js` to register new pages.
5. Write docs in `README.md` if applicable.

For questions, consult the frontend lead or check the documentation in the project root.

Claro, aquí tienes la versión en español del documento **Web Frontend Architecture**:

---

# 🧱 Arquitectura del Frontend Web

Este documento describe la estructura de carpetas y la arquitectura utilizada en el **frontend web** de este proyecto. Sigue un diseño modular, escalable y orientado al dominio para garantizar una separación clara de responsabilidades y mantenibilidad a largo plazo.

## 📁 Vista General de la Estructura de Carpetas

```
project-root/
│
├── public/               # Archivos estáticos (HTML, imágenes, etc.)
├── src/                  # Código fuente de la aplicación
│   ├── features/         # Funcionalidades orientadas al dominio
│   │   ├── auth/         # Funcionalidad específica de autenticación
│   │   │   ├── components/   # Componentes UI específicos de auth
│   │   │   ├── hooks/        # Hooks personalizados para la lógica de auth
│   │   │   ├── services/     # Servicios API relacionados con auth
│   │   │   ├── slices/       # Slices de Redux (si se usa Redux Toolkit)
│   │   │   └── pages/        # Páginas/vistas relacionadas con auth
│   │   ├── dashboard/    # Funcionalidad específica del dashboard
│   │   │   ├── components/
│   │   │   ├── hooks/
│   │   │   ├── services/
│   │   │   ├── slices/
│   │   │   └── pages/
│   │   └── ...           # Otras funcionalidades (productos, usuarios, etc.)
│   │
│   ├── shared/           # Lógica y componentes reutilizables
│   │   ├── components/   # UI común (botones, modales, etc.)
│   │   ├── hooks/        # Hooks reutilizables
│   │   ├── services/     # Servicios globales (por ejemplo, base API)
│   │   ├── utils/        # Funciones auxiliares y utilidades
│   │   ├── styles/       # Estilos globales (Tailwind, SCSS, etc.)
│   │   └── contexts/     # Contextos globales de React (Auth, Tema, etc.)
│   │
│   ├── App.js            # Componente raíz con providers y layout
│   ├── index.js          # Punto de entrada de React
│   └── routes.js         # Configuración de rutas (React Router)
│
├── .env                  # Variables de entorno
├── .gitignore            # Archivos ignorados por Git
├── package.json          # Metadatos del proyecto, scripts y dependencias
└── README.md             # Documentación del proyecto
```

---

## 📂 Descripción de Carpetas

### `public/`

Contiene archivos estáticos que se sirven tal como están:

* `index.html`
* Imágenes, íconos, logos
* Manifest o favicon

### `src/features/`

Cada subcarpeta dentro de `features` representa una **funcionalidad o dominio** de la aplicación (por ejemplo, auth, dashboard, pedidos). Dentro de cada funcionalidad se organiza así:

* `components/`: Elementos UI específicos de la funcionalidad
* `hooks/`: Lógica encapsulada en hooks personalizados
* `services/`: Clientes de API o lógica de servicios
* `slices/`: Slices de Redux (si se usa Redux Toolkit)
* `pages/`: Páginas relacionadas con la funcionalidad, utilizadas en el enrutamiento

Esta estructura permite encapsular y mantener la lógica dentro de cada funcionalidad.

### `src/shared/`

Contiene **lógica y componentes reutilizables** en toda la app:

* `components/`: Elementos UI usados en múltiples funcionalidades (por ejemplo, Botón, Modal)
* `hooks/`: Hooks personalizados como `useDebounce`, `useWindowSize`
* `services/`: Servicios compartidos como la instancia base de Axios
* `utils/`: Funciones auxiliares, constantes, validadores
* `styles/`: Estilos globales, configuración de Tailwind, temas
* `contexts/`: Contextos globales como `AuthContext`, `ThemeContext`

### `src/App.js`

Define la estructura principal de la aplicación: layout, providers de contexto, enrutamiento.

### `src/index.js`

Monta la app de React al DOM (`ReactDOM.createRoot`).

### `src/routes.js`

Contiene la configuración de rutas usando `react-router-dom`. Incluye rutas públicas/privadas y protecciones.

---

## ⚙️ Archivos de Configuración

### `.env`

Usado para definir variables de entorno como:

```
REACT_APP_API_URL=https://api.example.com
```

### `package.json`

Define:

* Dependencias y dependencias de desarrollo
* Scripts del proyecto (`start`, `build`, `lint`, etc.)

---

## ✅ Buenas Prácticas

* Aplica estructura **orientada al dominio** usando `features/`
* Aísla la lógica dentro de `hooks` y `services`
* Favorece componentes reutilizables en `shared/components`
* Usa variables de entorno para la configuración
* Desarrolla con enfoque en componentes y escribe tests para partes con lógica
* Implementa accesibilidad y diseño responsivo desde el inicio

---

## 📦 Mejoras Futuras

* Carga diferida de páginas con `React.lazy` y `Suspense`
* Añadir pruebas con Jest + React Testing Library
* Soporte de internacionalización (i18n) con `react-i18next`
* Configurar seguimiento de errores (por ejemplo, con Sentry)
* Soporte PWA o caché offline si es necesario

---

## 📣 Guía para Contribuir

Al agregar nuevas funcionalidades:

1. Crea una nueva carpeta dentro de `features/`.
2. Sigue la convención de subcarpetas (`components`, `hooks`, `pages`, etc.).
3. Reutiliza componentes y lógica desde `shared/` siempre que sea posible.
4. Actualiza `routes.js` para registrar las nuevas páginas.
5. Agrega documentación en el `README.md` si aplica.

Para dudas, consulta con el líder frontend o revisa la documentación en la raíz del proyecto.

