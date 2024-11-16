# Guía de uso básico: Brick-CFCMC

El objetivo de este repositorio es explicar de manera breve y explicativa lo necesario para comenzar a realizar simulaciones moleculares (**MS**) utilizando el paquete de *software* Brick-CFCMC. Este paquete pertenece a la universidad tecnológica de Delft y está pensado para ser utilizado en el sistema operativo **GNU/Linux**.

Este tutorial, al igual que toda la documentación oficial del paquete (en <a href="https://gitlab.com/ETh_TU_Delft/Brick-CFCMC/-/tree/master?ref_type=heads">GitLab</a> o en <a href="https://thijsvlugt.github.io/website/Brick-CFCMC/Brick-CFCMC.pdf">PDF</a>), asume que *bash* es el intérprete de comandos (shell). Este es el intérprete por default de distribuciones basadas en Devian (*Mint* o *Ubuntu*) o de Fedora.

### Contenidos:
1. [Recomendaciones preliminares](#c1)
2. [Instalación básica](#c2)
    1. [Brick-CFCMC para servidores](#c2_1)
3. [Simluación y comandos básicos](#c3)
    1. [Entradas (Inputs)](#c3_1)
    2. [Salidas (Outputs)](#c3_2)

<br></br>

## Recomendaciones preliminares <a name="c1"></a>
Antes de utilizar este paquete de *software* se recomienda encarecidamente manejar **comandos básicos desde el terminal bash** (*cambiar/crear directorios, manejo de archivos y editores de texto básicos*). Lo mismo aplica para comandos básicos de Git, el cual viene instalado por default en distribuciones de Linux como Ubuntu.
* La distribución de **Ubuntu** es recomendada para aprender a utilizar Linux. Ubuntu cuenta con una excelente documentación y con una <a href="https://ubuntu.com/tutorials/command-line-for-beginners#1-overview">guía para principiantes con los comandos básicos del terminal</a>.
* Por otro lado, **GitHub** es una herramienta útil para manejar archivos y colaborar en proyectos computacionales. Además, contiene en su estructura los comandos de Git que serán necesarios en este tutorial. <a href="https://docs.github.com/es">Documentación en español</a>.

<br></br>

## Instalación básica <a name="c2"></a>
La instalación de **Brick-CFCMC** es sencilla y consta de dos pasos: instalar **Fortran** y descargar el *software*.

Se puede trabajar con el <a href="https://www.intel.com/content/www/us/en/developer/tools/oneapi/fortran-compiler.html">compilador de Fortran de Intel</a>, este funciona únicamente con procesadores Intel, y sus versiones están optimizadas para funcionar con las tecnologías de cómputo ofrecidas por esta compañía.

Otra alternativa es utilizar <a href="https://gcc.gnu.org/fortran/">GNU Fortran</a>, este compilador se encuentra disponible en varias distribuciones de Linux, el listado se puede encontrar <a href="https://gcc.gnu.org/wiki/GFortranDistros">aquí</a>. Sin embargo, también se puede revisar los paquetes disponibles en la documentación de algunas distribuciones (<a href="https://packages.ubuntu.com/search?keywords=gfortran">Ejemplo con Ubuntu</a>).

Para instalar **GFortran** desde el terminal en distribuciones de Devian:

```
sudo apt-get install gfortran
```

Luego de instalar el compilador de Fortran, se debe descargar el *software*. Es recomendado descargarlo utilizando git desde el <a href="https://gitlab.com/ETh_TU_Delft/Brick-CFCMC/-/tree/master?ref_type=heads">repositorio oficial</a>. Para descargar Brick-CFCMC localmente desde git, se debe ingresar el siguiente comando desde el terminal

```
git clone https://gitlab.com/ETh_TU_Delft/Brick-CFCMC.git brick
```

Este comando crea una carpeta llamada `brick` en el directorio indicado. Se debe descargar el software en el directorio **HOME** (`cd ~`) por los pasos que siguen a continuación.

Después de la descarga, debemos indicarle a `bash` que ejecute comandos del *software* desde el terminal. Desde el directorio **HOME** debemos abrir el archivo oculto `.bashrc`. Se puede verificar que este archivo se encuentra en **HOME** escribiendo:

```
ls -a
```

Luego, se abre el archivo con un editor de texto (vi, Vim, nano, entre otros). Por ejemplo, para nano:

```
nano .bashrc
```

A continuación, al final del documento (`Crtl+W+V` con nano) se ingresan las siguientes lineas de texto:

```
export BRICK_DIR=${HOME}/brick
. ${BRICK_DIR}/.brick.sh
. ${BRICK_DIR}/.autocompletion
```

Se guardan los cambios y se actualiza `bash` con,

```
source .bashrc
```

O simplemente saliendo y entrando nuevamente al terminal.

Finalmente, el *software* puede ser compilado desde el terminal utilizando:

```
brick compile
```

Si se utiliza **GFortran**, se recomienda agregar el argumento `-g` o `--gfortran` luego de `compile`.


### Brick-CFCMC para servidores <a name="c2_1"></a>

La gran mayoría de los servidores en el mundo utilizan alguna distribución de Linux, por este motivo se asume que este es el caso. En específico, este tutorial considera el uso de los <a href="https://dt.ing.uc.cl/recursos/cluster/">clústers de la UC</a>. El uso de servidores es casi obligatorio para trabajar con simulaciones de este estilo, en especial por el tiempo necesario para computar resultados.

Para conectarse a los clústers de ingeniería, se debe pedir un usuario y luego estrablecer conección desde el terminal.

```
ssh [usuario]@[nombre-host]
```

En servidores, la instalación de **Fortran** debe ser hecha por el administrador de dicho servidor. En el caso de los clústers UC, este viene instalado.

Los pasos son los mismos para la instalación de **Brick-CFCMC** de manera local. No obstante, si se tiene una copia local ya instalada, es análogo copiar los documentos locales al servidor que, descargarlos con `git`. Esto se puede hacer con `scp` desde el terminal local.

```
scp -r ~/brick [usuario]@[nombre-host]:brick
```

Es imporante cambiar el archivo `.bashrc`. El cual se debería encontrar siempre en el directorio **HOME** del usuario.

<br></br>

## Simluación y comandos básicos <a name="c3"></a>

Para comenzar cualquier simulación, el comando:

```
brick new [nombre_simulacion]
```

Crea un directorio de simulación con el nombre entregado con el subdirectorio `INPUT` y un ejecutable `run`. 

### Entradas (Inputs) <a name="c3_1"></a>

El directorio `INPUT` debe contener 3 archivos, `settings.in`, `forcefield.in` y `topology.in`. El primer documento se agrega automáticamente con `brick new`, los últimos dos se pueden crear manualmente o, lo más recomendado, crear ambos documentos utilizando:

```
brick input
```

Con este comando también se podrá acceder a la base de datos de algunos compuestos básicos. Opcionalmente, brick cuenta con directorios `TEMPLATES` y `EXAMPLES`, donde se pueden copiar (`cp`) los archivos correspondientes y después modificarlos con algún editor de texto.

- `settings.in` contiene información sobre la simulación: Número de subsistemas, temperatura, presión, ciclos de iteración, métodos de cálculo para propiedades termodinámicas, esquemas, entre otros conceptos de simulación molecular.
- `forcefield.in` contine información sobre parámetros de interacción, atracción/repulsión (Lennard-Jones) y torsión, para el cálculo de las **energías** y **fuerzas** en el sistema. Además de incluir métodos (*Wolf, FG o Edwald*), y otros parámetros asociados a los métodos y simulación.
- `topology.in` define el número inicial de moléculas en el sistema, así como opciones específicas según el *ensemble*<sup>[1](#q1)</sup> y parámetros asociados a los *grupos fraccionales*<sup>[2](#q2)</sup>. También, puede incluir información sobre las reacciones químicas del sistema.

En `INPUT`, también es necesario crear documentos con parámetros de interacciones de Lennard-Jones y electroestáticas, geometría molecular, enlaces, torsión molecular y angulación (*bending*) molecular, **para cada molécula en el sistema**. En `${BRICK_DIR}/MOLECULES` o en `${BRICK_DIR}/EXAMPLES` se pueden encontrar archivos con la información correspondiente para algunas moléculas en específico.

### Salidas (Outputs) <a name="c3_2"></a>

En esta sección se utilizará el ejemplo `${BRICK_DIR}/EXAMPLES/Ionic_Liquids/Example_2_Solubility_NPT` como apoyo para discutir conceptos importantes sobre los resultados de la simulación.

> [!WARNING]
> La simulación puede extenderse durante varios días. Se puede cambiar el número de iteraciones desde el archivo `settings.in`. Sin embargo, los resultados en `OUTPUT` serán diferentes.

WIP

<br></br>

> <a name="q1">[1]</a> Ensemble: **Es la colección de todas las configuraciones o microestados (subsistemas) de un sistema físico que son gobernados por un mismo conjunto de parámetros de control**. Por ejemplo, en un sistema isotérmico, todos sus subespacios o conjuntos moleculares deben tener la misma temperatura. En simulación molecular, los *ensembles* son llamados según los parámetros que permanecen constantes.<br></br>
> <a name="q2">[2]</a> Grupos fraccionales: En **Brick-CFCMC**, CFC significa *Continuous Fractional Component*. Esta técnica permite separar una molécula en "moleculas fraccionales" (definidas por un parámetro fraccional $\lambda\in\left[0,1\right]$), de esta manera se regulan las fuerzas de interacción con otras moléculas adyacentes. **Los grupos fraccionales entonces, son grupos de moléculas que comparten parámetros fraccionales**.