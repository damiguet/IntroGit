# Tarea 1: Clonar y explorar un proyecto

## 🎯 Objetivo
Te has unido a un nuevo equipo de desarrollo. Tu primera misión es obtener el código fuente del proyecto en tu propia computadora desde un repositorio remoto en GitHub y aprender a inspeccionar su estado actual utilizando los comandos básicos de Git.

---

## 🧭 Conceptos clave antes de empezar

* **¿Qué es un repositorio remoto?** Es una versión de tu proyecto que está alojada en un servidor en internet (por ejemplo, en GitHub). Permite que varios desarrolladores compartan y sincronicen su trabajo.
* **¿Qué significa clonar?** Es el proceso de descargar una copia completa de un repositorio remoto (incluyendo todo su historial de cambios) a tu ordenador local.

---

## 📋 Instrucciones paso a paso

### 1. Clonar el repositorio
Para traer el proyecto a tu máquina, abre tu terminal (consola) y ejecuta el comando `git clone` seguido de la URL del repositorio:

```bash
git clone https://github.com/damiguet/IntroGit
```

> **¿Qué hace este comando?**
> Crea una nueva carpeta en tu ordenador con el nombre del repositorio (`IntroGit`), descarga todos los archivos del proyecto y configura automáticamente una conexión oculta con el servidor remoto para que Git sepa de dónde vino el código.

---

### 2. Navegar al directorio del proyecto
Una vez clonado, necesitas entrar dentro de la carpeta del proyecto para poder ejecutar comandos de Git sobre él. Utiliza el comando `cd` (Change Directory):

```bash
cd IntroGit
```

> **¿Qué hace este comando?**
> Cambia la ruta actual de tu terminal a la carpeta recién creada. **Importante:** casi todos los comandos de Git que utilices a partir de ahora deben ejecutarse desde el interior de esta carpeta.

---

### 3. Comprobar el estado del proyecto
Para saber en qué situación se encuentra tu copia local del proyecto, utiliza el comando `git status`:

```bash
git status
```

> **¿Qué hace este comando?**
> Es como el panel de control o la "radiografía" de tu proyecto en Git. Te informa de:
> - En qué rama (`branch`) te encuentras actualmente (por ejemplo, `main` o `master`).
> - Si tienes archivos modificados, nuevos o pendientes de guardar.
> - Como acabas de clonar el repositorio y no has tocado nada, te dirá que tu árbol de trabajo está limpio (*working tree clean*).

---

### 4. Ver la configuración remota
Para verificar a qué servidor remoto está vinculado este proyecto en tu ordenador, ejecuta:

```bash
git remote -v
```

> **¿Qué hace este comando?**
> Muestra las direcciones web (*URLs*) asociadas a tu repositorio local. Normalmente verás dos entradas:
> - `origin ... (fetch)`: La dirección desde la cual Git descarga las actualizaciones.
> - `origin ... (push)`: La dirección hacia la cual Git enviará tus propios cambios cuando decidas subirlos.

---

## ✅ Preguntas de autoevaluación para el alumno
1. ¿Cuál es el nombre de la rama principal (`branch`) en la que te encuentras tras clonar?
2. ¿Qué URL muestra el comando `git remote -v`?

---

## 💡 Soluciones / Respuestas a la autoevaluación
* **Respuesta 1:** Por defecto suele ser `main` o `master` (puedes comprobarlo mirando la primera línea que devuelve `git status`).
* **Respuesta 2:** Muestra la URL del repositorio remoto de GitHub (`https://github.com/damiguet/IntroGit`), tanto para `fetch` (descargar) como para `push` (subir).
