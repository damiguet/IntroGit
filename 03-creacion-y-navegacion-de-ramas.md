# Tarea 3: Creación y navegación entre ramas (Branches)

## 🎯 Objetivo
Aprender a trabajar con **ramas** (*branches*) en Git. Las ramas son fundamentales para aislar tu trabajo: te permiten desarrollar una nueva funcionalidad, probar ideas o corregir un error sin alterar ni poner en riesgo el código estable de la rama principal (`main`).

---

## 🧭 Conceptos clave antes de empezar

* **¿Qué es una rama?** Imagina que es una línea temporal independiente de tu proyecto. Por defecto trabajas en la rama principal (`main`). Cuando creas una rama nueva, Git hace una copia exacta del estado actual del proyecto en ese momento para que puedas experimentar en ella de forma aislada.
* **HEAD:** Es un puntero especial que indica en qué rama o commit te encuentras posicionado en este preciso instante.
* **¿Por qué usar ramas?** Permite que varios programadores trabajen en paralelo en distintas tareas sin pisarse el código unos a otros.

---

## 📋 Instrucciones paso a paso

### 1. Ver en qué rama estás actualmente
Antes de crear nada, comprueba en qué rama te encuentras ejecutando:

```bash
git branch
```
> **¿Qué hace este comando?**
> Lista todas las ramas locales que existen en tu repositorio. La rama activa y actual aparecerá marcada con un asterisco (`*`) y normalmente resaltada en verde (por ejemplo, `main` o `master`).



### 2. Crear una nueva rama
Crea una rama nueva llamada `caracteristica-saludo` para añadir mejoras al archivo `saludo.txt`:

```bash
git branch caracteristica-saludo
```
> **¿Qué hace este comando?**
> Crea la nueva rama basada en el estado actual de tu rama principal, pero **todavía no te cambia a ella** (sigues situado en `main`).

### 3. Cambiar de rama (Moverse a la nueva rama)
Para empezar a trabajar en la nueva rama que acabas de crear, debes cambiarte a ella utilizando el comando `git switch` (o el clásico `git checkout`):

```bash
git switch caracteristica-saludo
```
*(O alternativamente con el comando clásico:* `git checkout caracteristica-saludo`*)*

Vuelve a comprobar con `git branch`: verás que el asterisco `*` ahora está al lado de `caracteristica-saludo`.

> *💡 **Truco útil:** Puedes crear una rama y cambiarte a ella de golpe en un solo comando escribiendo:*
> ```bash
> git switch -c nombre-de-rama
> ```

### 4. Realizar un cambio en la nueva rama
Abre el archivo `saludo.txt` con tu editor habitual (por ejemplo, `xed saludo.txt` en Linux Mint), añade una línea nueva "Bienvenido a GIT". (Esta linea solo existe) esta rama, guarda los cambios y ciérralo.

Prepara y guarda el cambio con un commit:
```bash
git add saludo.txt
git commit -m "Añadido mensaje exclusivo de bienvenida"
```

### 5. Comprobar el aislamiento de las ramas
* Si te cambias de vuelta a la rama principal (`git switch main`) y abres el archivo (por ejemplo, ejecutando `cat saludo.txt` en la terminal o abriéndolo con `xed saludo.txt`), verás que **no** aparece lo que acabas de escribir en la otra rama.
* Si vuelves a tu rama de características (`git switch caracteristica-saludo`), el cambio volverá a aparecer. Esto demuestra cómo las ramas mantienen los mundos separados.

---

## ✅ Preguntas de autoevaluación para el alumno
1. ¿Qué indica el asterisco (`*`) cuando ejecutas el comando `git branch`?
2. ¿Cuál es la diferencia principal entre `git branch nombre-rama` y `git switch -c nombre-rama`?
3. Si estás escribiendo código en una rama secundaria y cambias a `main` sin hacer un commit previo, ¿qué suele ocurrir con tus cambios no guardados?

---

## 💡 Soluciones / Respuestas a la autoevaluación
* **Respuesta 1:** Indica la rama activa o actual en la que se encuentra posicionado tu directorio de trabajo en ese momento (*HEAD*).
* **Respuesta 2:** `git branch nombre-rama` solamente crea la rama nueva pero te deja en la rama en la que estabas. En cambio, `git switch -c nombre-rama` crea la rama **y** te cambia automáticamente a ella en un solo paso.
* **Respuesta 3:** Depende de si los archivos entran en conflicto con la otra rama; si no hay conflicto, Git suele arrastrar los cambios contigo a la otra rama, pero es una muy mala práctica. Lo correcto es siempre hacer `commit` o `stash` antes de cambiar de rama para evitar mezclas indeseadas.
