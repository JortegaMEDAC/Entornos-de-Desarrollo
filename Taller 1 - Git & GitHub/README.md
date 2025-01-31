# Introducción a Git y GitHub: Ejercicios

Este repositorio contiene ejercicios para un taller introductorio a Git y GitHub. El taller cubre los contenidos de [Unidad 1].

Cada ejercicio que involucra crear un commit contiene una ilustración de cómo debe verse el árbol de commits del repo al final del ejercicio.

**En las ilustraciones, el número dentro de cada commit hace referencia al ejercicio en el que se creó.**

## #1 Configuración inicial

¡**Configura** tu nombre, correo electrónico y editor de texto!

Ejemplo de configuración:

```bash
git config --global user.name "Jose Ortega"
git config --global user.email joseortega.prof@stemgranada.com
```

Tras la configuración puedes ejecutar `git config --global --list` para ver en la terminal toda tu configuración global.

❓ ¿Para qué sirve establecer el parámetro --global? ¿Funcionaría si no lo ponemos?

## #2 Primer repositorio local

Crea un nuevo repositorio en un directorio llamado `git-workshop`.

Crea los archivos `README.md` y `Jose.txt`. Actualmente los archivos no requieren tener contenido.

Agrega esos dos archivos al staging area y realiza el **primer commit** del repo.

<p align="center">
  <img width=100px src="./images/2.png" />
</p>

## #3 Correcciones básicas

¿Tu nombre no es Jose? Vamos a cambiar el nombre del archivo Hernán.txt para que coincida con el tuyo.

De tal forma que **reescribas** el commit realizado en el paso anterior, renombra el archivo `Jose.txt` a `<tu-nombre>.txt`, p. ej. `Pablo.txt` o `Teresa.txt`.

<p align="center">
  <img width=100px src="./images/3.png" />
</p>

## #4 Crear ramas

Crea la rama `yo++` y cámbiate a esa rama. Ahora que estás en la rama `yo++`, escriba una o dos oraciones acerca de ti en el archivo `.txt` con tu nombre.

Cuando hayas concluido de redactar, agrega tus cambios al staging area y realiza un commit.

Ahora regresa al primer commit del repo usando `git checkout master`. Crea otra rama: `taller-info`, y cámbiate a la rama. En el `README.md`, escribe una o dos oraciones acerca del taller, agrega los cambios al staging area y realiza un commit.

<p align="center">
  <img width=280px src="./images/4.png" />
</p>


| ℹ | Inspecciona el estado actual del repositorio con:<br> `git log --oneline --all --graph`<br>Observa que el repo ahora contiene tres commits, uno apuntado por `master`, otro por `taller-info` y el tercero apuntado por `yo++`.
|---|---|

❓ ¿Desde la rama `taller-info`, el archivo `.txt` con tu nombre tiene contenido o está vacío? ¿Por qué crees que es así?

## #5 Merge fast-forward de ramas

Colócate en la rama `master`, e incorpora los cambios de `yo++` a `master` mediante un merge.

## #6 Merge recursive de ramas

Ahora, permaneciendo en `master` incorpora los cambios de `taller-info` en `master` mediante un merge.

<p align="center">
  <img width=350px src="./images/6.png" />
</p>

## #7 Aparición de conflictos al realizar merge

En `master`, modifica la primera línea del archivo `README.md`, agrega los cambios al staging area y realiza un commit.

Ahora colócate en la rama `taller-info`, modifica la primera línea de `README.md` (de manera distinta a como la modificaste previamente), agrega los cambios al staging area y realiza un commit.

Regresa a `master`, e incorpora los cambios de `taller-info` mediante un merge. Git te debería reportar que ha ocurrido un conflicto que requiere ser solucionado manualmente.

<p align="center">
  <img width=380px src="./images/7.png" />
</p>

❓ ¿Por qué ocurrió un conflicto en este caso?


## #8 Resolución de conflictos de merge

En tu editor de texto preferido, abre el archivo con el conflicto (`README.md`), elimina los marcadores de conflicto y edita el contenido de acuerdo a cómo deseas preservar el archivo.

Una vez terminada la edición en el editor de texto, agrega los cambios al staging area y ejecuta `git merge --continue` o como se indica en vuestro manual, puedes hacer simplemente un nuevo commit con `git commit -m "Resolución del conflicto"`.

<p align="center">
  <img width=550px src="./images/8.png" />
</p>

## #9 Primer repositorio de GitHub

Crea un repositorio público en GitHub, con el nombre de `<tu-nombre>-intro-git`, p. ej. `pablo-intro-git`.

❓ ¿Cómo o en qué es GitHub diferente a Git?

## #10 Sube tus cambios a GitHub

Empuja (push) los cambios de tu rama `master` a GitHub, para que los demás también puedan ver tu repo.

❓ Tras realizar push de `master`, ¿puedes también ver en GitHub tus ramas `taller-info` y `yo++`?

