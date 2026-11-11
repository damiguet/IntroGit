# Tarea 2: Primeros cambios y confirmaciones (Commits)

## 🎯 Objetivo
Ahora que ya tienes el proyecto en tu ordenador, vas a realizar tu primera modificación sobre un archivo existente (`saludo.txt`), a preparar el cambio y a guardarlo de forma permanente en el historial de Git creando tu primer `commit`.

---

## 🧭 Conceptos clave antes de empezar

* **El flujo de trabajo de Git (The Three States):**
  1. **Working Directory (Directorio de trabajo):** Es donde editas tus archivos libremente en tu ordenador.
  2. **Staging Area (Área de preparación o Índice):** Es una zona intermedia donde seleccionas qué cambios específicos quieres incluir en tu siguiente guardado.
  3. **Repository (Repositorio / Historial):** Es donde se guardan de forma permanente e inmutable los cambios (`commits`) junto con un registro de quién los hizo y cuándo.
* **¿Qué es un Commit?** Es como una "fotografía" o punto de control del proyecto en un momento determinado de su historia. Cada commit tiene un código identificador único (un hash largo) y un mensaje descriptivo de lo que se ha hecho.

---

## 📋 Instrucciones paso a paso

### 1. Editar un archivo existente
Dentro de la carpeta `IntroGit` ya existe un archivo llamado `saludo.txt`. 

Dado que utilizas **Linux Mint**, puedes abrir y editar este archivo con el editor de textos por defecto **Xed** (o cualquier otro de tu preferencia, como *Nano*, *Gedit*, *VS Code*, etc.). Abre tu terminal y ejecuta:

```bash
xed saludo.txt
```
*(O si prefieres editarlo directamente desde la terminal sin abrir una interfaz gráfica:* `nano saludo.txt`*)*

Añade una línea nueva con tu nombre o un breve mensaje de saludo dentro del archivo, guarda los cambios y cierra el editor.

### 2. Comprobar el estado del proyecto
Abre tu terminal dentro de la carpeta del proyecto y ejecuta:
```bash
git status
```
> **¿Qué observarás?**
> Git detectará que el archivo `saludo.txt` ha sido modificado y aparecerá destacado en **rojo**. Esto significa que Git sabe que el archivo cambió, pero aún **no** está incluido en la siguiente foto (`commit`).

### 3. Preparar el cambio (Staging)
Para decirle a Git que quieres incluir la modificación de ese archivo en el próximo guardado, utiliza el comando `git add`:

```bash
git add saludo.txt
```
*(También puedes usar `git add .` para preparar todos los cambios modificados en el proyecto de golpe)*

Vuelve a comprobar el estado:
```bash
git status
```
> **¿Qué observas ahora?**
> El archivo habrá pasado a color **verde**. Esto significa que ya está en el *Staging Area* (preparado y listo para ser guardado en el historial).

### 4. Guardar el cambio permanentemente (Commit)
Una vez que tus cambios están preparados en verde, creas el commit utilizando el comando `git commit` acompañado de un mensaje descriptivo entre comillas (`-m`):

```bash
git commit -m "Añadido mi saludo personal en saludo.txt"
```

> **¿Qué hace este comando?**
> Toma todos los archivos que estaban en el área de preparación (*staging area*) y los sella en el historial del repositorio con el mensaje que le has indicado. Tu directorio de trabajo vuelve a quedar limpio.

### 5. Ver el historial del proyecto
Para comprobar que tu commit se ha guardado correctamente en la historia del proyecto, utiliza el comando `git log`:

```bash
git log
```
> **¿Qué verás?**
> Una lista con los commits realizados hasta la fecha, mostrando el autor, la fecha, el código hash único del commit y el mensaje que escribiste. (Para salir de la vista de log, presiona la tecla `q`).

---

## ✅ Preguntas de autoevaluación para el alumno
1. ¿Por qué es necesario pasar por el comando `git add` antes de hacer un `git commit`?
2. ¿Por qué se recomienda que los mensajes de los commits (`-m "..."`) sean claros y descriptivos?
3. Si modificas un archivo después de haber hecho un `git add` de ese mismo archivo, ¿el cambio posterior se incluye automáticamente en el commit? ¿Por qué?

---

## 💡 Soluciones / Respuestas a la autoevaluación
* **Respuesta 1:** Porque `git add` añade los archivos al área de preparación (*staging area*). Esto te da flexibilidad para elegir exactamente qué cambios quieres guardar en el commit y cuáles prefieres dejar para más adelante.
* **Respuesta 2:** Para que cualquier miembro del equipo (o tú mismo en el futuro) pueda leer el historial (`git log`) y entender rápidamente qué cambios se introdujeron en ese punto sin necesidad de abrir y revisar todo el código línea por línea.
* **Respuesta 3:** **No.** El comando `git add` hace una "fotografía" del estado del archivo en el momento exacto en que se ejecutó. Si vuelves a modificar el archivo después, esa última modificación existirá solo en tu directorio de trabajo (en rojo) y tendrás que volver a hacer `git add` si quieres incluirla en el commit.
