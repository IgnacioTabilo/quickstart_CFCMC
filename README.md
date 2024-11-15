# Guía de uso básico: Brick-CMCFC

El objetivo de este repositorio es explicar de manera breve y explicativa lo necesario para comenzar a realizar simulaciones moleculares (**MS**) utilizando el paquete de *software* Brick-CMCFC. Este paquete pertenece a la universidad tecnológica de Delft y está pensado para ser utilizado en el sistema operativo **GNU/Linux**.

Este tutorial, al igual que toda la documentación oficial del paquete (en <a href="https://gitlab.com/ETh_TU_Delft/Brick-CFCMC/-/tree/master?ref_type=heads">GitLab</a> o en <a href="https://thijsvlugt.github.io/website/Brick-CFCMC/Brick-CFCMC.pdf">PDF</a>), asume que *bash* es el intérprete de comandos (shell). Este es el intérprete por default de distribuciones basadas en Devian (*Mint* o *Ubuntu*) o de Fedora.

## Contenidos:
1. [Recomendaciones preliminares](#c1)
2. [Instalación básica](#c2)
    1. [Brick-CMCFC para servidores](#c2_1)
3. [Simluación y comandos básicos](#c3)
    1. [Comentarios y recomendaciones](#c3_1)
4. [Aplicación: Líquidos Iónicos](#c4)
    1. [Entradas (Inputs)](#c4_1)
    2. [Salidas (Outputs)](#c4_2)

## Recomendaciones preliminares <a name="c1"></a>
Antes de utilizar este paquete de *software* se recomienda encarecidamente manejar **comandos básicos desde el terminal bash** (*cambiar/crear directorios, manejo de archivos y editores de texto básicos*). Lo mismo aplica para comandos básicos de Git, el cual viene instalado por default en distribuciones de Linux como Ubuntu.
* La distribución de **Ubuntu** es recomendada para aprender a utilizar Linux. Ubuntu cuenta con una excelente documentación y con una <a href="https://ubuntu.com/tutorials/command-line-for-beginners#1-overview">guía para principiantes con los comandos básicos del terminal</a>.
* Por otro lado, **GitHub** es una herramienta útil para manejar archivos y colaborar en proyectos computacionales. Además, contiene en su estructura los comandos de Git que serán necesarios en este tutorial. <a href="https://docs.github.com/es">Documentación en español</a>.

## Instalación básica <a name="c2"></a>
La instalación de **Brick-CMCFC** es sencilla y consta de dos pasos: instalar **Fortran** y descargar el *software*.

Se puede trabajar con el <a href="https://www.intel.com/content/www/us/en/developer/tools/oneapi/fortran-compiler.html">compilador de Fortran de Intel</a>, este funciona únicamente con procesadores de Intel, y sus versiones están optimizadas para funcionar con las tecnologías de cómputo ofrecidas por esta compañía.

Otra alternativa es utilizar <a href="https://gcc.gnu.org/fortran/">GNU Fortran</a>, este compilador se encuentra disponible en varias distribuciones de Linux, el listado se puede encontrar <a href="https://gcc.gnu.org/wiki/GFortranDistros">aquí</a>. Sin embargo, también se puede revisar los paquetes disponibles en la documentación de algunas distribuciones (<a href="https://packages.ubuntu.com/search?keywords=gfortran">Ejemplo con Ubuntu</a>).

Para instalar **GFortran** desde el terminal:

```
sudo apt-get install gfortran
```

### Brick-CMCFC para servidores <a name="c2_1"></a>
Lorem ipsum

## Simluación y comandos básicos <a name="c3"></a>
Lorem ipsum

### Comentarios y recomendaciones <a name="c3_1"></a>
Lorem ipsum

## Aplicación: Líquidos Iónicos <a name="c4"></a>
Lorem ipsum

### Entradas (Inputs) <a name="c4_1"></a>
Lorem ipsum

### Salidas (Outputs) <a name="c4_2"></a>
Lorem ipsum