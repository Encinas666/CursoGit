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