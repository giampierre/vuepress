# Guía VuePress deploying in Github Pages

Esta es mi guía de como publicar nuestra documentación generada con [VuePress](https://vuepress.vuejs.org/) en [GitHub Pages](https://pages.github.com/).

## ¿Qué es VuePress?

VuePress es un generador de sitios estáticos alimentado por [Vue](https://vuejs.org/) que genera páginas HTML a partir de archivos de [Markdown](https://markdown.es/). Esto le permite centrarse en escribir la documentación en lugar de trabajar en perfeccionar el sitio web.

En esta guía se mostrarán dos maneras de publicar nuestro proyecto en GitHub Pages.

Para esta guía, nos imaginaremos que estamos trabajando con un proyecto llamado **deployvuepress**

## Subir todo nuestro proyecto a GitHub

1. Establecer **base** correcta  **proyecto/.vuepress/config.js**

``` js
module.exports = {
    base: '/deployvuepress/'
}
```
2. Crear una carpeta con el nombre **docs** en la raiz de nuestro proyecto.

::: danger Nota
El nombre de la carpeta tiene que ser **docs**, no otro.
:::

3. Compilar nuestro proyecto para producción con el siguiente comando.

``` bash
$ vuepress build
```
Al ejecutar este comando dentro de nuestro proyecto nos generará una carpeta llamada **dist**
dentro de la carpeta **.vuepress/dist**

Esta carpeta (**dist**) tendrá todo nuestro proyecto listo para ser desplegado a GitHub Pages 

4. copiar todo el contenido de la carpeta **dist** generada a la carpeta **docs** (la que creamos antes)

``` bash
$ cp -r d:/deployvuepress/.vuepress/dist/* d:/deployvuepress/docs
```

5. Eliminar la carpeta dist genereda dentro de .vuepress (opcional)

(dirigirnos dentrode la carpeta .vuepress del proyecto)

``` bash
$ rm -r dist 
```
6. subir todo el proyecto a nuestro repositorio

``` bash
    $ git init
	$ git add .
	$ git commit -m "deploy in github pages with folder docs"
	$ git push -f https://github.com/[usuario]/[repositorio].git master
```

7. Activar GitHub Pages en **github.com/settings**, opcion **folder docs**


## Subir solo la carpeta compilada a GitHub

1. Generar carpeta **dist** con el comando **vuepress build**, como se muestra a continuación.

``` bash
$ vuepress build
```

Esta carpeta (**dist**) tendrá todo nuestro proyecto listo para ser desplegado a GitHub Pages 

2. navegar hasta nuestra carpeta **dist** generada e iniciar git para subir nuestro proyecto al repositorio.

``` bash
    $ git init
	$ git add .
	$ git commit -m "deploy in github pages"
	$ git push -f https://github.com/[usuario]/[repositorio].git master:gh-pages
```
	

6. Activar Github Pages en **github.com/settings**, opcion **gh-pages**

