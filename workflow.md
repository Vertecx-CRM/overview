# 🌳 GitFlow Workflow — Git Branching Strategy

**GitFlow** is a branching model that organizes software development in a structured way, enabling better collaboration, version control, and continuous delivery.

---

## ⚙️ 1. Initial Setup

Before using GitFlow, initialize it in your repository:

```bash
git flow init
```

This command sets up the main branches (`master` and `develop`) and defines the support branches (`feature`, `release`, `hotfix`). You can accept the default names or customize them.

---

## 🌲 2. Main Branches

### `master` 🏁

* Contains the **stable production code**.
* Do not work directly on this branch.
* Only updated via merges from `release` or `hotfix` branches.

### `develop` 🚧

* Branch for **active development**.
* All new features and enhancements are integrated here before being released.
* Serves as the base for `feature` and `release` branches.

---

## 🛠️ 3. Supporting Branches

### 🔧 `feature/` – New Features

* **Base:** `develop`
* **Merged into:** `develop`
* **Purpose:** Implementing specific tasks or features.

```bash
git flow feature start feature-name
# work and commit
git flow feature finish feature-name
```

---

### 🚀 `release/` – Preparing a Release

* **Base:** `develop`
* **Merged into:** `master` and `develop`
* **Purpose:** Finalizing a version for production. Suitable for QA, minor fixes, and versioning.

```bash
git flow release start 1.0.0
# make adjustments, fixes, updates
git flow release finish 1.0.0
```

---

### 🔥 `hotfix/` – Critical Fixes in Production

* **Base:** `master`
* **Merged into:** `master` and `develop`
* **Purpose:** Fixing urgent bugs directly in production without going through `develop`.

```bash
git flow hotfix start fix-login-error
# fix the issue
git flow hotfix finish fix-login-error
```

---

## 🌐 4. Workflow Diagram

You can see a visual representation here:
👉 [GitFlow Fundamentals](https://github.com/Riwi-io-Medellin/git_gitflow_fundamentals)

---

## 🧩 5. Practical Example

### Scenario: Add a login feature and release version 1.0.0

```bash
# Initialize GitFlow
git flow init

# Create a new feature
git flow feature start login-form
# Add the login form, commit changes
git add .
git commit -m "feat: add login form"
git flow feature finish login-form

# Start preparing the release
git flow release start 1.0.0
# Style adjustments, bug fixes, update README
git add .
git commit -m "docs: update readme for release"
git flow release finish 1.0.0
# This merges into master and develop, and creates a version tag

# Push changes to remote
git push origin develop
git push origin master
git push origin --tags
```

---

## 🔄 6. Syncing with Remote Repository

Keep your local repository up to date before and after working:

```bash
git checkout develop
git pull origin develop
```

After finishing a branch:

```bash
git push origin develop
git push origin master
```

---

## ✅ 7. Best Practices

* 🔁 **Sync frequently** to avoid major merge conflicts.
* 🔍 **Review code before merging.**
* 💬 **Use clear and standardized commit messages.**
* 🧩 **Keep branches small and focused.**
* 🧪 **Write tests before merging into `develop` or `master`.**

---

## 📘 Additional Resources

* [GitFlow Cheatsheet – Atlassian](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow)
* [GitFlow Extension for VSCode](https://marketplace.visualstudio.com/items?itemName=vector-of-bool.gitflow)

---

# 🌳 GitFlow Workflow — Estrategia de Ramas en Git

**GitFlow** es una estrategia de ramificación que organiza el desarrollo de software de forma estructurada, facilitando la colaboración, el control de versiones y la entrega continua.

---

## ⚙️ 1. Configuración Inicial

Antes de comenzar a usar GitFlow, inicialízalo en tu repositorio:

```bash
git flow init
```

Este comando crea las ramas principales (`master` y `develop`) y define las ramas de soporte (`feature`, `release`, `hotfix`). Puedes aceptar los nombres por defecto o personalizarlos.

---

## 🌲 2. Ramas Principales

### `master` 🏁

* Contiene el **código estable** que ya está en producción.
* No se debe trabajar directamente sobre esta rama.
* Se actualiza solo mediante merges desde `release` o `hotfix`.

### `develop` 🚧

* Rama de **desarrollo activo**.
* Todas las nuevas funcionalidades y mejoras se integran aquí antes de ser lanzadas.
* Es la base para crear nuevas ramas `feature` y `release`.

---

## 🛠️ 3. Ramas de Soporte

### 🔧 `feature/` – Nuevas funcionalidades

* **Origen:** `develop`
* **Destino:** `develop`
* **Uso:** Desarrollo de características o tareas específicas.

```bash
git flow feature start nombre-de-la-feature
# trabaja y haz commits
git flow feature finish nombre-de-la-feature
```

---

### 🚀 `release/` – Preparación para producción

* **Origen:** `develop`
* **Destino:** `master` y `develop`
* **Uso:** Estabilización del código antes del despliegue. Ideal para QA, ajustes menores o actualización de versiones.

```bash
git flow release start 1.0.0
# realiza ajustes, fixes, versión
git flow release finish 1.0.0
```

---

### 🔥 `hotfix/` – Corrección urgente en producción

* **Origen:** `master`
* **Destino:** `master` y `develop`
* **Uso:** Solución de errores críticos sin pasar por `develop`.

```bash
git flow hotfix start fix-login-error
# soluciona el bug
git flow hotfix finish fix-login-error
```

---

## 🌐 4. Diagrama del Flujo

Puedes consultar una representación visual aquí:
👉 [GitFlow Fundamentals](https://github.com/Riwi-io-Medellin/git_gitflow_fundamentals)

---

## 🧩 5. Ejemplo Práctico

### Escenario: Agregar funcionalidad de login y lanzar la versión 1.0.0

```bash
# Inicializa GitFlow
git flow init

# Crea una nueva funcionalidad
git flow feature start login-form
# Agrega el formulario, realiza commits
git add .
git commit -m "feat: add login form"
git flow feature finish login-form

# Prepara el lanzamiento
git flow release start 1.0.0
# Ajusta estilos, corrige errores, actualiza README
git add .
git commit -m "docs: update readme for release"
git flow release finish 1.0.0
# Esto hace merge a master y develop, y crea un tag

# Empuja los cambios a remoto
git push origin develop
git push origin master
git push origin --tags
```

---

## 🔄 6. Sincronización con Repositorio Remoto

Mantén tu repositorio local actualizado antes y después de trabajar:

```bash
git checkout develop
git pull origin develop
```

Después de finalizar una rama:

```bash
git push origin develop
git push origin master
```

---

## ✅ 7. Buenas Prácticas

* 🔁 **Sincroniza con frecuencia**: evita conflictos grandes.
* 🔍 **Haz revisiones de código** antes de mergear.
* 💬 **Usa mensajes de commit claros** y estandarizados.
* 🧩 **Mantén tus ramas pequeñas y enfocadas**.
* 🧪 **Integra pruebas antes de fusionar a `develop` o `master`**.

---

## 📘 Recursos Adicionales

* [GitFlow Cheatsheet - Atlassian](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow)
* [Extensión GitFlow para VSCode](https://marketplace.visualstudio.com/items?itemName=vector-of-bool.gitflow)

---

