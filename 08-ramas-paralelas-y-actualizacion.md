# Tarea 8: Flujo de trabajo en equipo: Ramas paralelas y actualización

## 🎯 Objetivo
Simular un escenario de trabajo real en equipo donde conviven dos ramas secundarias independientes (`rama-A` y `rama-B`). Aprenderás a fusionar una de ellas en la principal (`master`/`main`) y a actualizar la otra rama pendiente para que esté al día antes de continuar trabajando o fusionarla también.

---

## 🧭 Conceptos clave antes de empezar

* **Trabajo en paralelo:** Es muy común que distintos desarrolladores creen ramas al mismo tiempo para tareas diferentes.
* **Mantenerse al día (*Keep up to date*):** Cuando una rama principal recibe cambios nuevos, las demás ramas secundarias que siguen abiertas se quedan "obsoletas". Actualizarlas a tiempo evita futuros dolores de cabeza y conflictos complejos.

---

## 📋 Instrucciones paso a paso

### 1. Crear dos ramas secundarias independientes
Partiendo de tu rama principal (`master` o `main`) limpia y al día:
1. Crea y cámbiate a la **`rama-A`**:
   ```bash
   git switch -c rama-A
   ```
   Abre `saludo.txt`, añade una línea (por ejemplo: `Línea añadida por Rama A`), guarda el archivo y haz commit:
   ```bash
   git add saludo.txt
   git commit -m "Commit en rama-A"
   ```

2. Vuelve a la rama principal (`master`) y asegúrate de que partes de ella para crear la **`rama-B`**:
   ```bash
   git switch master
   git switch -c rama-B
   ```
   Abre `saludo.txt`, modifica la primera líena (por ejemplo: `Línea añadida por Rama B`), guarda el archivo y haz commit:
   ```bash
   git add saludo.txt
   git commit -m "Commit en rama-B"
   ```

---

### 2. Fusionar la primera rama (`rama-A`) en la principal
1. Vuelve a la rama principal:
   ```bash
   git switch master
   ```
2. Fusiona los cambios de la `rama-A`:
   ```bash
   git merge rama-A
   ```
   *(Como modificaron zonas distintas o `master` no se movió, se fusionará limpiamente).*
3. Elimina la `rama-A` ya integrada:
   ```bash
   git branch -d rama-A
   ```

*En este momento, la rama principal (`master`) ha avanzado e incorporado el trabajo de la `rama-A`, pero la **`rama-B`** (en la que trabajaba otro compañero, o tú mismo) sigue en su propio mundo y no sabe que `master` ha cambiado.*

---

### 3. Actualizar la rama pendiente (`rama-B`) para ponerla al día
Imagina que ahora quieres seguir trabajando en la `rama-B`, pero necesitas que tenga los últimos cambios que ya están en `master` (es decir, el trabajo de la `rama-A`).

1. Cámbiate a la `rama-B`:
   ```bash
   git switch rama-B
   ```
2. Trae e integra los cambios actuales de `master` hacia tu rama actual:
   ```bash
   git merge master
   ```
   *(Git combinará los cambios limpios de `master` dentro de tu rama).*

---

### 4. Segunda modificación, commit y fusión final hacia la principal
Ahora que tu `rama-B` está totalmente al día y sincronizada con los cambios de la `rama-A`:

1. Abre el archivo `saludo.txt` con tu editor (por ejemplo, `xed saludo.txt`): verás que **los cambios de la `rama-A` ya han llegado a tu documento**.
2. Añade una nueva línea con tus propias modificaciones correspondientes a la `rama-B`, guarda el archivo y ciérralo.
3. Prepara y guarda este cambio haciendo un commit en la `rama-B`:
   ```bash
   git add saludo.txt
   git commit -m "Segunda modificación en rama-B tras actualizarse"
   ```
4. Finalmente, ya puedes fusionar la `rama-B` de vuelta a la rama principal (`master`):
   ```bash
   git switch master
   git merge rama-B
   ```
5. Limpia borrando la `rama-B`:
   ```bash
   git branch -d rama-B
   ```

---

## ✅ Preguntas de autoevaluación para el alumno
1. ¿Por qué es importante actualizar una rama secundaria (`rama-B`) cuando la rama principal (`master`) ha recibido fusiones de otras ramas?
2. Si estás situado en la `rama-B`, ¿qué comando debes ejecutar para incorporar los cambios recientes que hay en `master`?
3. ¿Por qué tras actualizar la `rama-B` con `master` puedes seguir editando el archivo, hacer commit y fusionarlo a `master` sin problemas?

---

## 💡 Soluciones / Respuestas a la autoevaluación
* **Respuesta 1:** Para evitar trabajar sobre una base de código antigua y asegurar que tu nueva característica es compatible con lo que otros ya han integrado.
* **Respuesta 2:** Debes situarte en la `rama-B` (`git switch rama-B`) y ejecutar `git merge master`.
* **Respuesta 3:** Porque al actualizar la rama te aseguras de que tu versión local contiene el estado más reciente del proyecto, permitiendo que Git integre tus nuevos commits de forma limpia y fluida sobre la rama principal.
