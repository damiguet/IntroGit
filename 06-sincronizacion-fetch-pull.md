# Tarea 6: Sincronización avanzada: Conociendo qué hay en el servidor (Fetch, Status y Pull)

## 🎯 Objetivo
Aprender a comprobar si existen cambios nuevos en el repositorio remoto sin modificarlos todavía en tu ordenador (`git fetch`), ver el estado de tu repositorio en comparación con el servidor, y finalmente descargar e integrar esos cambios utilizando `git pull`.

---

## 🧭 Conceptos clave antes de empezar

* **`git fetch` (Buscar / Inspeccionar):** Se conecta al repositorio remoto (GitHub), descarga la información sobre los nuevos commits y ramas que hay en el servidor, pero **no** modifica tus archivos locales ni altera tu código actual. Es como mirar por la ventana para ver si llueve antes de salir.
* **`git pull` (Traer y fusionar):** Es la combinación de dos acciones: un `git fetch` seguido de un `git merge`. Descarga los cambios del servidor y los integra de inmediato en tu carpeta de trabajo.

---

## 📋 Instrucciones paso a paso

### 1. Simular un cambio en el repositorio remoto (GitHub)
Para esta práctica, vamos a simular que un compañero (o tú mismo desde la página web de GitHub) ha añadido contenido nuevo directamente en el servidor:
1. Entra en tu repositorio en la web de GitHub.
2. Crea un archivo nuevo llamado `remoto.txt` con el contenido:
   ```text
   Archivo creado desde GitHub
   ```
3. Guarda el archivo haciendo clic en el botón verde de commit en GitHub.

*En este punto, tu repositorio en GitHub tiene un archivo nuevo que tu ordenador **todavía no conoce**.*

---

### 2. Comprobar novedades sin alterar tu código (`git fetch`)
Para enterarte de si hay cambios en el servidor remoto sin descargarlos ni tocarlos todavía, ejecuta en tu terminal local:
```bash
git fetch
```

> **¿Qué hace este comando?**
> Actualiza la información sobre el estado remoto en segundo plano. Si ejecutas inmediatamente después `git status`:
> ```bash
> git status
> ```
> Verás un mensaje en la terminal que te informa de algo como:
> ```text
> Tu rama está detrás de 'origin/master' por 1 commit, y puede ser fusionada.
> ```
> ¡ Git te está avisando de que el servidor va un paso por delante de ti!

---

### 3. Descargar e integrar los cambios (`git pull`)
Ahora que ya sabes que hay cambios pendientes en el servidor y quieres incorporarlos a tu proyecto local, ejecuta:
```bash
git pull
```

> **¿Qué hace este comando?**
> Descarga el archivo `remoto.txt` que creaste en GitHub y lo fusiona en tu rama local actual.

---

### 4. Comprobar que el archivo ya está en tu equipo
Verifica que el archivo ya se encuentra en tu carpeta local utilizando `ls` (para ver los archivos del directorio) o abriéndolo:
```bash
cat remoto.txt
```

---

## ✅ Preguntas de autoevaluación para el alumno
1. ¿Cuál es la diferencia principal entre `git fetch` y `git pull`?
2. ¿Qué mensaje te muestra el comando `git status` después de ejecutar `git fetch` si el servidor remoto tiene cambios nuevos?
3. ¿Por qué es útil ejecutar `git fetch` antes de hacer un `git pull` en un entorno de trabajo real?

---

## 💡 Soluciones / Respuestas a la autoevaluación
* **Respuesta 1:** `git fetch` solo descarga la información de los cambios del servidor remoto sin alterar tus archivos locales. `git pull` descarga los cambios **y además** los fusiona automáticamente en tu código local.
* **Respuesta 2:** Te indica que tu rama local está "detrás" (*behind*) del servidor remoto por un número determinado de commits y que puede ser fusionada.
* **Respuesta 3:** Permite inspeccionar qué cambios han subido otros compañeros y evaluar si podrían entrar en conflicto con tu código actual antes de fusionarlos a ciegas en tu proyecto.
