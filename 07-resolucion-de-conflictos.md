# Tarea 7: Simulación y resolución de conflictos

## 🎯 Objetivo
Aprender qué es un **conflicto de fusión** (*merge conflict*), por qué se produce cuando dos ramas modifican exactamente la misma línea de un archivo de formas distintas, y cómo solucionarlo manualmente de forma correcta.

---

## 🧭 Conceptos clave antes de empezar

* **¿Por qué ocurre un conflicto?** Ocurre cuando Git intenta fusionar dos ramas que han modificado el **mismo archivo y la misma línea** con contenidos diferentes. Al no poder decidir automáticamente qué versión debe quedarse, se detiene y pide intervención humana.
* **Las marcas de conflicto:** Git inserta en el archivo unas señales especiales (`<<<<<<<`, `=======`, `>>>>>>>`) para delimitar claramente dónde está el choque de código.

---

## 📋 Instrucciones paso a paso

### 1. Crear el escenario de divergencia (El conflicto)
Para provocar un conflicto de forma controlada, seguiremos este orden estricto:

1. **Partir de la rama principal (`master` o `main`):**
   Asegúrate de estar situado en tu rama principal.

2. **Crear una rama secundaria para experimentar:**
   Crea y cámbiate a una nueva rama llamada `rama-conflicto`:
   ```bash
   git switch -c rama-conflicto
   ```

3. **Modificar el archivo en la rama secundaria:**
   Abre el archivo `saludo.txt` (por ejemplo, con `xed saludo.txt` o `nano saludo.txt`), cambia el contenido de la primer línea (por ejemplo, escribe: `Mensaje escrito desde la rama secundaria`), guarda los cambios y haz un commit:
   ```bash
   git add saludo.txt
   git commit -m "Cambio en saludo.txt desde rama-conflicto"
   ```

4. **Volver a la rama principal y modificar la *misma* línea:**
   Cámbiate de vuelta a la rama principal:
   ```bash
   git switch master
   ```
   Abre de nuevo `saludo.txt` y, **en esa misma línea**, escribe un texto diferente (por ejemplo: `Mensaje escrito desde master`), guarda los cambios y haz un commit en `master`:
   ```bash
   git add saludo.txt
   git commit -m "Cambio en saludo.txt desde master"
   ```

> *En este punto, tanto `master` como `rama-conflicto` han avanzado por caminos separados y han modificado la misma línea de formas distintas.*

---

### 2. Intentar la fusión (El conflicto)
Ahora, estando situado en la rama principal (`master`), intenta fusionar la rama conflictiva:
```bash
git merge rama-conflicto
```
> **¿Qué verás en la terminal?**
> Git detectará el choque y te avisará con un mensaje como este:
> `CONFLICT (content): Merge conflict in saludo.txt`
> `Automatic merge failed; fix conflicts and then commit the result.`

---

### 3. Inspeccionar y resolver el conflicto
Abre el archivo `saludo.txt` con tu editor habitual (`xed saludo.txt` o `nano saludo.txt`). Verás que Git ha incluido las marcas de conflicto directamente en el código:

```text
<<<<<<< HEAD
Mensaje escrito desde master
=======
Mensaje escrito desde la rama-conflicto
>>>>>>> rama-conflicto
```

* Lo que está entre `<<<<<<< HEAD` y `=======` es tu versión actual (en `master`).
* Lo que está entre `=======` y `>>>>>>> rama-conflicto` es la versión que intentas fusionar.

**Cómo resolverlo:**
1. Borra todas las líneas de marcado de conflicto (`<<<<<<<`, `=======`, `>>>>>>>`).
2. Deja el texto limpio con la combinación o la frase definitiva que quieras conservar.
3. Guarda el archivo y cierra el editor.

---

### 4. Finalizar la fusión
Una vez corregido el archivo manualmente, debes informar a Git de que el conflicto ha terminado:
1. Prepara el archivo solucionado:
   ```bash
   git add saludo.txt
   ```
2. Completa la fusión creando el commit final:
   ```bash
   git commit -m "Resuelto conflicto en saludo.txt"
   ```
¡Listo! El conflicto habrá quedado solucionado y el historial del proyecto estará fusionado correctamente.

---

## ✅ Preguntas de autoevaluación para el alumno
1. ¿Qué significan los símbolos `<<<<<<<`, `=======` y `>>>>>>>` que aparecen dentro de un archivo con un conflicto?
2. ¿Por qué es necesario crear la rama y modificar el archivo en ella *antes* de modificar esa misma línea en `master` para que salte el conflicto?
3. ¿Cuáles son los dos comandos obligatorios que debes ejecutar después de editar manualmente el archivo en conflicto para finalizar el `merge`?

---

## 💡 Soluciones / Respuestas a la autoevaluación
* **Respuesta 1:** Delimitan las dos versiones enfrentadas: la primera sección corresponde a tu rama actual (`HEAD`), la segunda sección pertenece a la rama que intentas fusionar, y el separador `=======` divide ambas.
* **Respuesta 2:** Porque si modificas `master` primero y luego creas la rama, la rama hereda esos cambios y al fusionar se produce un avance rápido (*Fast-forward*) sin conflicto. Para que haya conflicto, ambas ramas deben divergir modificando la misma zona de forma independiente.
* **Respuesta 3:** Primero `git add <archivo>` para marcar el conflicto como resuelto, y después `git commit` para registrar la resolución en el historial.
