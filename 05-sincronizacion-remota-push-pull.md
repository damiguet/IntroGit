# Tarea 5 (Alternativa para Clase): Sincronización, Forks y Repositorios Remotos

## 🎯 Objetivo
Aprender a sincronizar tu repositorio local con repositorios remotos en GitHub, entendiendo cómo funciona el envío (`git push`) y la descarga (`git pull`), y cómo lidiar con los permisos cuando trabajas con repositorios ajenos (como el del profesor).

---

## 🧭 Conceptos clave antes de empezar

* **¿Por qué da error al hacer `git push` en el repositorio del profesor?** 
  Cuando clonaste el repositorio del profesor (`https://github.com/damiguet/IntroGit`), descargaste una copia, pero GitHub protege los repositorios ajenos para que nadie que no sea el propietario pueda modificarlos. Si intentas hacer `git push` directamente allí, Git te devolverá un error de permisos (por ejemplo, *Permission to damiguet/IntroGit denied*).
* **La solución en entornos educativos (El Fork y Repositorio Personal):**
  Para poder practicar el `push`, cada alumno necesita su **propia copia remota** en su cuenta personal de GitHub, o bien configurar su propio repositorio remoto de prácticas.

---

## 📋 Instrucciones paso a paso

### 1. Entender el bloqueo del `push` original
Si estás situado en tu carpeta clonada y ejecutas:
```bash
git push
```
Verás que GitHub rechaza la operación debido a que no tienes permisos de escritura en el repositorio del profesor. Esto es completamente normal y de seguridad.

### 2. Cambiar la URL del remoto a tu propio repositorio (o clonar tu Fork)
Para poder practicar el envío de cambios (`push`) a un servidor donde **sí** tengas permisos:
1. Crea un repositorio vacío en tu propia cuenta de GitHub (por ejemplo, llamado `PracticaIntroGit`).
2. En tu terminal, dentro de la carpeta del proyecto, cambia la dirección del remoto `origin` para que apunte a tu nuevo repositorio personal:
   ```bash
   git remote set-url origin https://github.com/TU-USUARIO/tu-repositorio.git
   ```
3. Comprueba que el cambio se ha aplicado correctamente:
   ```bash
   git remote -v
   ```

### 3. Enviar tus cambios a tu propio repositorio remoto (git push)
Ahora que `origin` apunta a tu repositorio personal, ya puedes publicar tus commits:
```bash
git push -u origin master
```
> **⚠️ Autenticación en GitHub:**
> Al ejecutar el `push`, Git te pedirá que te identifiques. Ten en cuenta lo siguiente:
> - Como **Username**, introduce tu nombre de usuario de GitHub.
> - Como **Password**, **no** debes introducir tu contraseña habitual de la cuenta, sino el **Personal Access Token (PAT)** que hayas generado previamente en tu perfil de GitHub (Settings > Developer settings > Personal access tokens).

> **¿Qué hace el comando `-u`?**
> El parámetro `-u` (*upstream*) vincula tu rama local con la remota para que en el futuro te baste con escribir `git push` o `git pull` sin necesidad de volver a escribir los argumentos.

### 4. Descargar y actualizar cambios (git pull)
Imagina que haces cambios desde la web de GitHub o desde otro ordenador. Para bajarlos a tu equipo local, utilizas:
```bash
git pull
```

---

## ✅ Preguntas de autoevaluación para el alumno
1. ¿Por qué aparece un error de permisos (*permission denied*) al intentar hacer `git push` en el repositorio original del profesor?
2. ¿Qué comando se utiliza para cambiar la dirección URL del servidor remoto (`origin`) en tu repositorio local?
3. ¿Para qué sirve el parámetro `-u` al hacer `git push -u origin master` por primera vez?

---

## 💡 Soluciones / Respuestas a la autoevaluación
* **Respuesta 1:** Porque el repositorio pertenece al profesor y GitHub bloquea los permisos de escritura a usuarios ajenos para proteger el código original de modificaciones no autorizadas.
* **Respuesta 2:** El comando `git remote set-url origin <nueva-url>`.
* **Respuesta 3:** Sirve para asociar (vincular) tu rama local con la rama remota, de modo que en el futuro Git recuerde dónde debe enviar o recibir los cambios automáticamente con un simple `git push` o `git pull`.
