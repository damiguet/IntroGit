# Tarea 4: Fusión de ramas (Merge)

## 🎯 Objetivo
Aprender a integrar el trabajo realizado en una rama secundaria de vuelta a la rama principal (`main`) utilizando el comando `git merge`. Esta es la forma estándar de incorporar nuevas características una vez que han sido probadas y aprobadas.

---

## 🧭 Conceptos clave antes de empezar

* **¿Qué es un Merge (Fusión)?** Es el proceso mediante el cual Git combina el historial y los cambios de dos ramas distintas en una sola.
* **El principio de integración:** Por lo general, te moverás a la rama receptora (por ejemplo, `main`) y le pedirás a Git que traiga y funda los cambios procedentes de tu rama de trabajo (`caracteristica-saludo`).

---

## 📋 Instrucciones paso a paso

### 1. Asegurar que estás en la rama principal (`main`)
Antes de fusionar nada, es una buena práctica verificar que te encuentras situado en la rama que va a recibir los cambios.

Abre tu terminal y ejecuta:
```bash
git switch main
```
> 💡 **Nota importante sobre los nombres de las ramas y mensajes de estado:**
> En muchos proyectos la rama principal se llama `main`, pero en otros (especialmente en repositorios más antiguos o configurados por defecto) se llama `master`.
>
> Si en algún momento al cambiar de rama ves un mensaje como este en tu terminal:
> ```text
> Tu rama está adelantada a 'origin/master' por 1 commit.
>   (usa "git push" para publicar tus commits locales)
> ```
> No te preocupes: significa simplemente que en tu ordenador local has guardado un cambio (`1 commit`) que **todavía no ha sido enviado** al servidor remoto de GitHub. Tu versión local va "un paso por delante" del servidor, pero seguiremos trabajando de forma local por ahora.

Comprueba con `git branch` que el asterisco `*` está efectivamente en `main`.

### 2. Actualizar la rama principal (opcional pero recomendado)
Si estás trabajando en equipo, asegúrate de que tu `main` local está al día. En este ejercicio local, puedes comprobar el estado con `git status`.

### 3. Ejecutar el comando Merge
Para fusionar los cambios que hiciste en la rama `caracteristica-saludo` dentro de tu rama actual (`main`), ejecuta:

```bash
git merge caracteristica-saludo
```

> **¿Qué hace este comando?**
> Git examina la historia de ambas ramas, busca el punto común en el que se separaron y aplica de forma automática los nuevos commits de `caracteristica-saludo` sobre `main`.
> - Si todo va bien, se abrirá un editor de texto pidiéndote confirmar el mensaje del commit de fusión (*merge commit*), o se completará directamente (*Fast-forward* o fusión automática).

### 4. Comprobar el resultado
Verifica que el contenido actualizado de `saludo.txt` ya forma parte de la rama `main`:
```bash
cat saludo.txt
```

### 5. Limpiar y comprobar la eliminación de la rama
Una vez que una rama ha sido completamente integrada en `main`/`master` y ya no la necesitas para seguir desarrollando esa característica, es una buena práctica de limpieza eliminarla:

```bash
git branch -d caracteristica-saludo
```
> **¿Qué hace este comando?**
> Borra la rama local `caracteristica-saludo`. El parámetro `-d` es una medida de seguridad: Git solo te dejará borrarla si sus cambios ya han sido fusionados previamente, evitando que pierdas código por error.

Por último, vuelve a listar las ramas para comprobar que la rama secundaria ha desaparecido y solo queda la principal:
```bash
git branch
```

---

## ✅ Preguntas de autoevaluación para el alumno
1. ¿Sobre qué rama debes estar situado antes de ejecutar el comando `git merge mi-rama`?
2. ¿Qué significa el mensaje o tipo de fusión conocido como *Fast-forward*?
3. ¿Por qué se utiliza el comando `git branch -d` después de hacer un merge exitoso?

---

## 💡 Soluciones / Respuestas a la autoevaluación
* **Respuesta 1:** Debes estar situado en la rama **receptora** (aquella que va a recibir los cambios, normalmente `main`).
* **Respuesta 2:** Significa que la rama principal no había recibido ningún cambio nuevo desde que creaste la rama secundaria, por lo que Git simplemente ha avanzado el puntero de `main` hasta el último commit de la otra rama sin necesidad de crear un commit de fusión complejo.
* **Respuesta 3:** Para mantener el repositorio limpio y ordenado, evitando acumular decenas de ramas antiguas que ya cumplieron su función y dificultarían la lectura del proyecto.
