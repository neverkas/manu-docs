# Integrando GIT con MAGIT

## 1. Traer cambios de un branch al master

Si hicimos cambios y los guardamos en **branches** y queremos traerlos al **branch master** (suele ser la ultima version, la que ira a produccion)

1. Cambiamos al **branch master**
>Presionamos **SPC g s** para acceder al menu de Magit, 
>luego **b b** y elegimos el **master branch** (no es lo mismo que origin/master)

2. Hacemos **merge** con el branch que queremos (Ej. hotfix branch o testing branch)
>Presionamos **SPC g s** luego **m m** y elegimos el **branch** para traer los cambios al **master branch**

3. Hacemos **push** del **merge**
>Presionamos con **SPC g s** luego **p p**

- - -

## 2. Diferencia entre master y origin/master

Del ejemplo anterior quizas puede aparecer esto, y pueden surgir dudas.

Cuando se dice **master** se refiere al **local branch** (el entorno local),
mientras que **origin/master** hace referencia al **remote branch** (el que esta en el servidor github**

**Observacion:** Lo mismo aplica con los **branches**
Ej. origin/hotfix y hotfix, origin/testing y testing, etc..

#### 2.2 Referencias

- Referencia #1 - Stackify.com - [Ver Pagina](https://stackify.com/git-checkout-remote-branch/)
- Referencia #2 - Stackoverfow - [Ver Pagina](https://stackoverflow.com/questions/48596045/git-difference-between-origin-master-and-origin-master)

- - -

## 3. Guardar cambios de forma temporal (Stash)

Si hicimos cambios en archivos de nuestro ordenador (se dice que es local, y se guarda en **unstage**),
para guardar esos cambios en otro lugar de "forma temporal" (se guarda en **stash**) antes de hacer un **pull** 

1. Antes de hacer **commit** de los cambios, separamos el codigo con **stash**
> Los cambios que se hicimos en los archivos del entorno local estan en **unstage** sino hicimos commit,
> seleccionamos ese bloque de codigo y presionamos **zz RET** (no le asignamos nombre porque es opcional).
> **Nota:** Cuando volvamos al archivo, no apareceran lo cambios, quedaron separados en **stash**

2. Creamos un **branch** para las nuevas caracteristicas que nos pidieron de improviso
> Al crear el **branch** nos aseguramos de separar las nuevas caracteristicas
> del **commit** que hariamos con las funcionalidades que estabamos desarrollando.

3. Volvemos a traer el codigo que reservamos con **stash**
> Seleccionamos los cambios que teniamos **stashes** y presionamos **a** (add/agregar)
> y volvera a aparecer esos cambios en el archivo, por tanto estara en **unstage** 
> donde quedan las modificaciones que aun no se hizo **commit** (si lo hicieramos quedarian
> en **stage**)

#### 3.2 Referencias

- Referencia #1 - Code Tutsplus [Ver Pagina](https://code.tutsplus.com/es/tutorials/quick-tip-leveraging-the-power-of-git-stash--cms-22988)
- Referencia #2 - RunRoom -  [Ver Pagina](https://www.runroom.com/realworld/git-stash)

- - -

## 4. Listar historial de commits de un archivo

Corremos el comando **blame** presionando **SPC g b** y nos muestra un log de los cambios
Si presionamos **b** va a los commits anteriores y con **q** los mas recientes

#### 4.2. Referencias

- Referencia #1 - Magit.vc - [Ver Pagina](https://magit.vc/manual/magit/Blaming.html)

- - -

## 5. Atajos 

| Comando     | Descripción                                                                |
| :---------- | :-----------                                                               |
| SPC-g s     | Muestra el estado de cambios                                               |
| Tab         | Expande/Oculta el contenido del bloque donde esta el cursor                |
| s           | Agrega archivos nuevos/Guarda los cambios locales **unstage** en **stage** |
| u           | Pasa los cambios de **stage** al entorno local (unstage)                   |
| x           | Descarta los cambios                                                       |
| c c         | Crear **commit** (luego de escribir el motivo, se debe finalizar)          |
| , ,         | Finalizar **commit**                                                       |
| b c         | Crear un nuevo branch, y hacer checkout de ese branch                      |
| b b         | Cambiar de **branch** (Ej. Ir del master al develop o testing)             |
| t t         | Crear un **tag**                                                           |
| p p         | Hacer **push**                                                             |
| p e         | Hacer *push*** en un repositorio externo                                   |
| F p         | Hacer **pull**                                                             |

- - -

## 6. Posibles Situaciones

#### 6.1 Hacer cambios, subirlos y actualizar

1. Guardamos los cambios de forma local **(unstage)**
> Modificamos los archivos, guardamos con con **SPC f s** o **M-x s**

2. Guardo los cambios en **Stage**
> Presionamos **SPC g s** seleccionamos los cambios que queremos guardar en **stage** 
> con **shift** o **v** y las flechas Down/Up, y presionamos **s**

3. Hacemos **commit** (aplicamos los cambios)
> Presionamos **SPC g s** seguido de **c c**

4. Creomos un **branch** del **commit**
> Presionamos **SPC g s** seguido de **b c** luego **RET** y escribimos
> el nombre del nuevo **branch** donde se guardaran los cambios del **commit**

5. Hacemos **push**
> Presionamos **SPC g s** seguido de **p p**

6. Hacemos **pull** del **branch** nuevo al **master branch**
> Presionamos **SPC g s** seguido de **b b** elegimos el **master branch**
> y terminamos con **F p**

**Observacion:**
> Si ya estamos en el menu de **magit** no es necesario presionar el atajo **SPC g s**

#### 6.2 Resolver conflicto, diferencia entre archivos

Si en el paso 5 del ejemplo anterior hubiesemos tenido un conflicto,
porque alguien modifico el mismo archivo en las mismas lineas.

1. Hacemos **pull**
> Para traer el archivo con el que tenemos conflicto,
> ver las diferencias entre este archivo y el archivo local para resolverlo.

2. Mostramos el conflicto
> Presionamos **SPC g s** y luego **e** , apareciendo tres buffers 
> identificados en la parte inferior izquierda con las letras A, B, C.
>
> A y B son los archivos en conflicto, y C el archivo final, el que tendra los conflictos resuelto.

3. Comparamos las diferencias con **n** y **p**
>Si presionamos **p** o **n** se resaltara los cambios, p de **previous diff** n de **next diff** 

4. Corregimos el conflicto
> Podemos elegir entre elegir que archivo (buffer A o B) sera el correcto como solucion e ira al buffer C, 
> presionando la letra minuscula del buffer que identifica al archivo.
>
> La otra manera, seria si corregimos las diferencias de forma manual escribiendo en el buffer C

5. Guardamos los cambios y salimos
> Presionamos **q** seguido de **y** dos veces para confirmar los cambios realizados.

6. Verificamos que se hizo el **merge**
> Presionamos **SPC g s** y debe decir "Merging origin/nombre del branch"

7. Hacemos **commit** del **merge** y **push**
>Comiteamos con **c c** y **, ,** y por ultimo pusheamos con **P p**

- - -

## 7. Referencias

#### 7.1 Paginas recomendadas

- Referencia #1 - Salty Crane - [Ver Pagina](https://www.saltycrane.com/blog/2018/11/magit-spacemacs-evil-magit-notes/)

#### 7.2 Videos de recomendados

- Referencia #1 - [Ver Video](https://www.youtube.com/watch?v=7ywEgcbaiys)
- Referencia #2 - [Ver Video](https://www.youtube.com/watch?v=qXgGtyjXPiw)
- Referencia #3 - [Ver Video](https://www.youtube.com/watch?v=fFuf3hExF5w)
- Referencia #4 - [Ver Video](https://www.youtube.com/watch?v=NDP91RNgT4A)
- Referencia #5 - [Ver Video](https://www.youtube.com/watch?v=1IYsiHXR620)
