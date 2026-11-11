# 📚 Ruta de Aprendizaje de Git y GitHub

¡Bienvenido/a al repositorio de la guía práctica de Git y GitHub! Esta ruta de aprendizaje está diseñada paso a paso para alumnos que buscan dominar el control de versiones desde la terminal, desde los comandos más básicos hasta flujos de trabajo avanzados en equipo y resolución de conflictos.

---

## 🗺️ Estructura del Curso

El contenido está dividido en 5 módulos progresivos. Cada tarea incluye explicaciones detalladas del propósito de los comandos, ejemplos prácticos en la terminal y preguntas de autoevaluación con sus respectivas respuestas.

### Módulo 1: Fundamentos y Exploración
* **[Tarea 1: Clonar y explorar un proyecto](./01-clonar-y-explorar.md)**
  * *Comandos:* `git clone`, `cd`, `git status`, `git remote -v`.
* **[Tarea 2: Primeros cambios y confirmaciones (Commits)](./02-primeros-cambios-y-commits.md)**
  * *Objetivo:* Editar el archivo `saludo.txt` (usando editores de Linux Mint como *Xed* o *Nano*).
  * *Comandos:* `git add`, `git commit`, `git log`.

### Módulo 2: Trabajo con Ramas (Branches)
* **[Tarea 3: Creación y navegación entre ramas](./03-creacion-y-navegacion-de-ramas.md)**
  * *Objetivo:* Aislar nuevas funcionalidades creando ramas y entendiendo los mensajes de estado local/remoto (`master`/`main`).
  * *Comandos:* `git branch`, `git switch` / `git checkout`.
* **[Tarea 4: Fusión de ramas (Merge)](./04-fusion-de-ramas-merge.md)**
  * *Objetivo:* Integrar ramas secundarias en la principal y limpiar ramas obsoletas.
  * *Comandos:* `git merge`, `git branch -d`.

### Módulo 3: Sincronización con el Remoto
* **[Tarea 5: Sincronización, Forks y Repositorios Remotos](./05-sincronizacion-remota-push-pull.md)**
  * *Objetivo:* Adaptar el remoto al repositorio personal de cada alumno y enviar cambios (`push`) autenticándose con un *Personal Access Token*.
  * *Comandos:* `git remote set-url`, `git push -u origin master`.
* **[Tarea 6: Sincronización avanzada: Inspección y Pull](./06-sincronizacion-fetch-pull.md)**
  * *Objetivo:* Detectar cambios en GitHub (`remoto.txt`) sin alterar el entorno local usando `fetch` y `status`, antes de bajarlos con `pull`.
  * *Comandos:* `git fetch`, `git status`, `git pull`.

### Módulo 4: Resolución de Conflictos y Escenarios Reales
* **[Tarea 7: Simulación y resolución de conflictos](./07-resolucion-de-conflictos.md)**
  * *Objetivo:* Provocar un conflicto de edición en la misma línea de un archivo, interpretar las marcas de conflicto y resolverlo manualmente paso a paso.
* **[Tarea 8: Flujo de trabajo en equipo: Ramas paralelas y actualización](./08-ramas-paralelas-y-actualizacion.md)**
  * *Objetivo:* Gestionar dos ramas paralelas (`rama-A` y `rama-B`), fusionar una en la principal y actualizar la otra rama pendiente tras su segunda modificación para mantenerla al día.

### Módulo 5: Herramientas de Emergencia y Control Avanzado
* **[Tarea 9: Guardar temporalmente y deshacer cambios (Stash y Restore)](./09-stash-y-deshacer-cambios.md)**
  * *Objetivo:* Aprender a aparcar cambios a medias con `git stash` y a descartar modificaciones locales erróneas de forma segura con `git restore`.


