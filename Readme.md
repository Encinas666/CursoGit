# GIT
---
### *Status* ("git status")
---
![Status](/resource/Status.png)

Comando que regresa el estado actual del arbol.

### *Add* ("git add ." o "git add nombre_archivo.extencion")
---
![Add](/resource/Add.png)

Agrega al archivo los cambios 

### *Commit* ("git commit" o "git commit -m mensaje entre comillas")
---
![commit](/resource/commit.png)
  
  Un "commit" es una captura de la instancia  de los cambios preparados en ese momento del proyecto.

*Tipos de commits:*
- git commit -a
- git commit -m "commit message"
- git commit -am "commit message"
- git commit --amend

*Buenas practicas:*
- Usa el verbo imperativo.
- No uses punto final ni puntos suspensivos en tus mensajes.
- tipo detalle: maximo 40 caracteres.
- Añade todo el contexto que sea necesario en el cuerpo del mensaje de commit.
- Uso de orefijos:
  * feat: Una nueva característica para el usuario.
  * fix: Arregla un bug que afecta al usuario.
  * perf: Cambios que mejoran el rendimiento del sitio.
  * build: Cambios en el sistema de build, tareas de despliegue o instalación.
  * ci: Cambios en la integración continua.
  * docs: Cambios en la documentación.
  * refactor: Refactorización del código como cambios de nombre de variables o funciones.
  * style: Cambios de formato, tabulaciones, espacios o puntos y coma, etc; no afectan al usuario.
  * test: Añade tests o refactoriza uno existente.

## ***Ramas***
---
![ramas](/resource/ramas.svg)

 En Git, las ramas son parte del proceso de desarrollo diario. Las ramas de Git son un puntero eficaz para las instantáneas de tus cambios. Cuando quieres añadir una nueva función o solucionar un error, independientemente de su tamaño, generas una nueva rama para alojar estos cambios. Esto hace que resulte más complicado que el código inestable se fusione con el código base principal, y te da la oportunidad de limpiar tu historial futuro antes de fusionarlo con la rama principal.
### Branch (git branch)
* git branch:
Enumera todas las ramas de tu repositorio. Es similar a git branch --list.

* git branch ＜branch＞:
Crea una nueva rama llamada ＜branch＞. Este comando no extrae la nueva rama.

* git branch -d ＜branch＞:
Elimina la rama especificada. Esta es una operación segura, ya que Git evita que elimines la rama si tiene cambios que aún no se han fusionado.

* *it branch -D ＜branch＞:
Fuerza la eliminación de la rama especificada, incluso si tiene cambios sin fusionar. Este comando lo puedes usar si quieres eliminar de forma permanente todas las confirmaciones asociadas con una línea concreta de desarrollo.

* git branch -m ＜branch＞:
Cambia el nombre de la rama actual a ＜branch＞.

* git branch -a:
Enumera todas las ramas remotas.

*Creación de ramas:*
* git branch "nombre de rama": crea una rama.
* git git checkout "Nombre de rama": crea y se mueve a la rama creada.

![branch](/resource/branch.png)

*fucion de ramas:*
+ git merge: une dos o más historias de desarrollo.
```
  git merge [-n] [--stat] [--sin compromiso] [--squash] [--[no-]editar]
	[--no-verify] [-s <estrategia>] [-X <opción-estrategia>] [-S[<keyid>]]
	[--[no-]permitir-historias-no-relacionadas]
	[--[no-]rerere-autoupdate] [-m <mensaje>] [-F <archivo>]
	[--into-name <branch>] [<commit>…​]
git merge (--continuar | --abortar | --salir)
```
![merge](/resource/merge.png)

## Log (git log)
---
>git log [opciones] [<rango de revisión>] [[--] ruta…​]

![log](/resource/log.jpeg)

Muestra los registros de confirmación.

*Algunas Opciones:*
+ git log --oneline: Log en una línea por commit.
+ git log -"#": Ver un número limitado de commits.
+ git log -# -p: Ver información extendida del commit.
+ git log --graph --oneline: Opción --graph para el log con diagrama de las ramas.
+ git show b2c07b2: obtener mayor información de un commit.

## Flow (git flow)

Gitflow es un modelo alternativo de creación de ramas en Git en el que se utilizan ramas de función y varias ramas principales. Fue Vincent Driessen en nvie quien lo publicó por primera vez y quien lo popularizó. En comparación con el desarrollo basado en troncos, Gitflow tiene diversas ramas de más duración y mayores confirmaciones. Según este modelo, los desarrolladores crean una rama de función y retrasan su fusión con la rama principal del tronco hasta que la función está completa. Estas ramas de función de larga duración requieren más colaboración para la fusión y tienen mayor riesgo de desviarse de la rama troncal. También pueden introducir actualizaciones conflictivas.

*Ramas principales y de desarrollo*

En lugar de una única rama main, este flujo de trabajo utiliza dos ramas para registrar el historial del proyecto. La rama main o principal almacena el historial de publicación oficial y la rama develop o de desarrollo sirve como rama de integración para las funciones. Asimismo, conviene etiquetar todas las confirmaciones de la rama main con un número de versión.

El primer paso es complementar la rama main predeterminada con una rama develop. Una forma sencilla de hacerlo es que un desarrollador cree de forma local una rama develop vacía y la envíe al servidor:
```
 git branch develop 
 git push -u origin develop
```
Esta rama contendrá el historial completo del proyecto, mientras que main contendrá una versión abreviada. A continuación, otros desarrolladores deberían clonar el repositorio central y crear una rama de seguimiento para develop.

A la hora de utilizar la biblioteca de extensiones de git-flow, ejecutar git flow init en un repositorio existente creará la rama develop:
```
$ git flow init

Initialized empty Git repository in ~/project/.git/
No branches exist yet. Base branches must be created now.
Branch name for production releases: [main]
Branch name for "next release" development: [develop]

$ git branch
* develop
 main
```


-*Ramas de función*

Todas las funciones nuevas deben residir en su propia rama, que se puede enviar al repositorio central para copia de seguridad/colaboración. Sin embargo, en lugar de ramificarse de main, las ramas feature utilizan la rama develop como rama primaria. Cuando una función está terminada, se vuelve a fusionar en develop. Las funciones no deben interactuar nunca directamente con main.

![flow](/resource/flow.png)

Ten en cuenta que las ramas feature combinadas con la rama develop conforman, a todos efectos, el flujo de trabajo de ramas de función. Sin embargo, el flujo de trabajo Gitflow no termina aquí.

Las ramas feature suelen crearse a partir de la última rama develop.

El flujo general de Gitflow es el siguiente:

1. Se crea una rama develop a partir de main.
2. Se crea una rama release a partir de la develop.
3. Se crean ramas feature a partir de la develop.
4. Cuando se termina una rama feature, se fusiona en la rama develop.
5. Cuando la rama release está lista, se fusiona en las ramas develop y main.
6. Si se detecta un problema en main, se crea una rama hotfix a partir de main.
7. Una vez terminada la rama hotfix, esta se fusiona tanto en develop como en main.
  
## Reflog (git reflog)
---

it realiza el seguimiento de las actualizaciones en el extremo de las ramas a través de un mecanismo denominado registros de referencias o "reflogs". Muchos de los comandos de Git aceptan un parámetro para especificar una referencia o "ref", que es un puntero a una confirmación. Entre los ejemplos habituales se incluyen los siguientes:

+ git checkout
+ git reset
+ git merge

Los registros de referencias realizan un seguimiento de cuándo se han actualizado las referencias de Git en el repositorio local. Además de los registros de referencias del extremo de la rama, se conserva un registro de referencias especial para "git stash". Los registros de referencias se almacenan en los directorios dentro del directorio .git del repositorio local. Los directorios de git reflog se encuentran en .git/logs/refs/heads/., .git/logs/HEAD y también en .git/logs/refs/stash si se ha usado el comando git stash en el repositorio.

*Uso básico*

El caso de uso más básico de Reflog invoca lo siguiente:

> git reflog

Se trata básicamente de un acceso directo que equivale a:

> git reflog show HEAD

Esto dará como resultado el registro de referencias para HEAD. El resultado debería ser algo parecido a lo siguiente:

>eff544f HEAD@{0}: commit: migrate existing content
>
>bf871fd HEAD@{1}: commit: Add Git Reflog outline
>
>9a4491f HEAD@{2}: checkout: moving from main to >git_reflog
>
>9a4491f HEAD@{3}: checkout: moving from >Git_Config to main
>
>39b159a HEAD@{4}: commit: expand on git context 
>
>9b3aa71 HEAD@{5}: commit: more color >clarification
>
>f34388b HEAD@{6}: commit: expand on color >support 
>
>9962aed HEAD@{7}: commit: a git editor -> the >Git editor

Visita la página Reescritura del historial para ver otro ejemplo de acceso habitual al registro de referencias.

