# Tarea 9: Guardar temporalmente y deshacer cambios (Stash y Reset)

## 🎯 Objetivo
Aprender herramientas de emergencia para situaciones cotidianas en Git: guardar cambios a medias de forma temporal sin hacer commit (`git stash`), y deshacer cambios o descartar modificaciones locales cuando te equivocas (`git restore` / `git reset`).

---

## 🧭 Conceptos clave antes de empezar

* **`git stash` (El "aparcamiento"):** Imagina que estás editando un archivo en tu rama pero de repente te piden cambiarte urgentemente a otra rama. Git no te dejará moverte si tienes cambios sin guardar. `git stash` guarda tus modificaciones actuales en un "cajón desastre" temporal y deja tu directorio limpio para que puedas moverte libremente.
* **`git restore` (Descartar cambios locales):** Te permite tirar a la basura los cambios que hayas hecho en un archivo antes de hacerle `git add`, volviendo al último estado guardado.

---

## 📋 Instrucciones paso a paso

### 1. Guardar cambios temporalmente con `git stash`
Imagina que estás modificando `saludo.txt` pero aún no has terminado ni quieres hacer un commit todavía:
1. Abre `saludo.txt` y escribe algo provisional.
2. Comprueba el estado con `git status` (verás el archivo modificado en rojo).
3. Imagina que te llaman urgentemente para cambiar de rama. Ejecuta:
   ```bash
   git stash
   ```
   > **¿Qué hace este comando?**
   > "Oculta" tus modificaciones actuales en un almacenamiento temporal y deja tu archivo limpio como si no hubieras tocado nada. Ahora ya puedes cambiar de rama o hacer lo que necesites sin perder tu trabajo.

4. Para recuperar lo que guardaste en el cajón cuando vuelvas a tu rama, ejecuta:
   ```bash
   git stash pop
   ```
   > **¿Qué hace este comando?**
   > Saca los cambios del cajón temporal y los vuelve a aplicar sobre tu archivo en el directorio de trabajo.

---

### 2. Descartar cambios locales por error con `git restore`
Imagina que has modificado el archivo `saludo.txt`, pero te das cuenta de que lo que has escrito es un desastre y prefieres borrarlo todo y volver al estado original del último commit:

1. Modifica `saludo.txt` con cualquier prueba absurda.
2. Ejecuta el siguiente comando para descartar los cambios en ese archivo:
   ```bash
   git restore saludo.txt
   ```
   > **⚠️ ¡Cuidado!** Este comando borra de forma permanente los cambios no guardados en ese archivo. Si ejecutas `git status`, verás que el archivo vuelve a estar limpio como al principio.

---

## ✅ Preguntas de autoevaluación para el alumno
1. ¿Para qué sirve el comando `git stash` y en qué situaciones de emergencia es útil?
2. ¿Qué diferencia hay entre `git stash` y hacer un `git commit` normal?
3. Si utilizas `git restore saludo.txt`, ¿qué ocurre con las modificaciones que habías hecho en ese archivo y que no tenían `git add`?

---

## 💡 Soluciones / Respuestas a la autoevaluación
* **Respuesta 1:** Sirve para "guardar en un cajón" temporalmente los cambios que tienes a medias en tu directorio de trabajo. Es muy útil cuando necesitas cambiarte de rama de urgencia sin tener que hacer un commit incompleto.
* **Respuesta 2:** Un `commit` guarda los cambios de forma permanente en el historial del proyecto con un mensaje descriptivo. Un `stash` es un guardado temporal y rápido en un espacio de almacenamiento auxiliar, pensado para tareas de usar y tirar.
* **Respuesta 3:** Se eliminan de forma irreversible, volviendo el archivo exactamente al estado en el que se encontraba en el último commit realizado.
