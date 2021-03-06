# VIDEOS PENDIENTES:
- ubuntu neofetch add image
- https://www.youtube.com/watch?v=QAaT6BTUnPg
- https://www.youtube.com/watch?v=fKmD1Q2-994
- w3m-img https://www.youtube.com/watch?v=R2bMUtCOGko
- cambiar terminal - https://www.youtube.com/watch?v=m8QKK42Hp64
- xterm dropdown - https://www.youtube.com/watch?v=mAUQsNUnk9I
- ubuntu i3wm install
- urxvt - https://www.youtube.com/watch?v=eaBf_yFHps8
- linux i3 setup
- neofetch - https://www.omgubuntu.co.uk/2017/01/neofetch-3-0-released
- https://www.omgubuntu.co.uk/2016/11/neofetch-terminal-system-info-app
- https://lamiradadelreplicante.com/2016/05/15/la-informacion-de-tu-sistema-en-la-terminal-con-neofetch/
- https://github.com/dylanaraps/neofetch/wiki/Image-Backends


## Varios dotfiles
 - https://github.com/notthebee/dotfiles
 - Que es polybar [Ver Página](https://www.youtube.com/watch?v=7RNgpvBMua0)
 - Que es Rofi #1 [Ver Página](https://www.youtube.com/watch?v=wcMyH3o5FMg)
 - Que es Rofi #2 [Ver Página](https://www.youtube.com/watch?v=Sa9SWMvAMIU)
 - Que es Compton [Ver Página](https://www.youtube.com/watch?v=5GpyaSEe0VY)
 - Entendiendo i3 [Ver Pagina](https://github.com/Airblader/i3)
 https://erikdubois.be/how-to-change-the-size-of-the-gaps-between-the-windows-in-i3/
 - Que es i3-gaps [Ver Video](https://www.youtube.com/watch?v=hUe2Tm7u1lI)
 - Instalar i3 gaps https://www.youtube.com/watch?v=94Nhq-qWj98

# gaps sirve para darle separacion a las ventanas

https://gist.github.com/dabroder/813a941218bdb164fb4c178d464d5c23

# Cambiar de Terminal
>Existe una gran variedad de terminales, entre las más conocidas son:
-Rxvt
-Terminator
-Tilix
-Gnome
-Xterm

## 1. Cambiar la terminal a rxvt
https://www.youtube.com/watch?v=_kjbj-Ez1vU

- Rxvt - Configuraciones
    - Referencia #1 por ArchLinux [Ver Pagina](https://wiki.archlinux.org/index.php/Rxvt-unicode_(Espa%C3%B1ol))
    - Referencia #2 por Addy [Ver Pagina](https://addy-dclxvi.github.io/post/configuring-urxvt/)
- Rxvt - Habilitar transparencia a la terminal [Ver Pagina](https://wiki.archlinux.org/index.php/Rxvt-unicode/Tips_and_tricks#Transparency)


### 1. Instalamos la nueva terminal rxvt
>Si queremos cambiar a una terminal más personalizada y sin limitaciones,
>podemos hacer uso de **rxvt** que a diferencia de la predeterminada gnome de ubuntu
```bash
sudo apt install rxvt-unicode
```

### 2. Creamos los directorios y archivos necesarios
>En este archivo podemos aplicar las configuraciones que queremos aplicar a la terminal,
>luego de haberlas agregado ejecutamos el siguiente comando en nuestra terminal predeterminada
> `xrdb ~/.Xresources`
```bash
touch ~/.Xresources # creamos el archivo para las configuraciones
mkdir ~/.rxvt/ext # creamos directorio, donde guardaremos plugins
```

### 3. Algunas configuraciones
https://github.com/bookercodes/dotfiles/tree/arch
!Más info: https://wiki.archlinux.org/index.php/Rxvt-unicode#Font_declaration_methods
!Mas info: https://wiki.gentoo.org/wiki/Rxvt-unicode
!Mas info: https://github.com/muennich/urxvt-perls

```xresources
!Para aplicar cambios ejecutar en la terminal la sig linea de comando
!xrdb ~/.Xresources

!Configuramos la ruta donde agregamos las extensiones
URxvt.perl-lib: ~/.urxvt/ext/

!Configuramos la fuente
URxvt.font: xft:DejaVu Sans Mono:size=11

!! URxvt Appearance
URxvt.letterSpace: 0
URxvt.lineSpace: 0
URxvt.geometry: 92x24
URxvt.internalBorder: 24
URxvt.cursorBlink: true
URxvt.cursorUnderline: false
URxvt.saveline: 2048
URxvt.scrollBar: false
URxvt.scrollBar_right: false
URxvt.urgentOnBell: true
URxvt.depth: 32
URxvt.iso14755: false

!! Common Keybinds for Navigations
URxvt.keysym.Shift-Up: command:\033]720;1\007
URxvt.keysym.Shift-Down: command:\033]721;1\007
URxvt.keysym.Control-Up: \033[1;5A
URxvt.keysym.Control-Down: \033[1;5B
URxvt.keysym.Control-Right: \033[1;5C
URxvt.keysym.Control-Left: \033[1;5D

!! Copy Paste & Other Extensions
!URxvt.perl-ext-common: default,selection-to-clipboard,pasta,matcher,keyboard-select
URxvt.perl-ext-common: default,clipboard,url-select,keyboard-select
URxvt.copyCommand: xclip -i -selection clipboard
URxvt.pasteCommand: xclip -o -selection clipboard
URxvt.keysym.M-c: perl:clipboard:copy
URxvt.keysym.M-v: perl:clipboard:paste
URxvt.keysym.M-C-v: perl:clipboard:paste_escaped
URxvt.keysym.M-Escape: perl:keyboard-select:activate
URxvt.keysym.M-s: perl:keyboard-select:search
URxvt.keysym.M-u: perl:url-select:select_next
URxvt.urlLauncher: firefox
URxvt.underlineURLs: true
URxvt.urlButton: 1

!! Colorscheme
!! Para cambiar a otros diseños podemos elegir en  https://terminal.sexy/
! special
*.foreground: #93a1a1
*.background: #141c21
*.cursorColor: #afbfbf

! black
*.color0: #263640
*.color8: #4a697d

! red
*.color1: #d12f2c
*.color9: #fa3935

! green
*.color2: #819400
*.color10: #a4bd00

! yellow
*.color3: #b08500
*.color11: #d9a400

! blue
*.color4: #2587cc
*.color12: #2ca2f5

! magenta
*.color5: #696ebf
*.color13: #8086e8

! cyan
*.color6: #289c93
*.color14: #33c5ba

! white
*.color7: #bfbaac
*.color15: #fdf6e3
```

### 4. Atajos
- Shift+ArrowUp scroll hacia arriba
- Shift+ArrowDown scroll hacia abajo
- Control+ArrowLeft desplaza el cursor a la izquierda por palabra
- Control+ArrowRight desplaza el cursor a la derecha por palabra
- M-w Copia texto seleccionado al portapapeles
- C-y Pega texto del portapapeles

>*Observaciones:*
- Con *M*  nos referimos a MetaKey, que es la tecla Alt
- Con *C* hacemos referencia a la tecla Control
- Los shortcuts de copiar y pegar, los adapte por costumbre de usar Emacs

- - -

# 2. Instalar WIndows Manager i3wm
>Podemos usar el *i3* que no se refiere al procesador, sino al nombre del
>programa que nos permite manejar las terminales de una manera más eficiente
>mediante atajos (shortcuts)
>Más info en https://i3wm.org/docs/userguide.html
https://ericren.me/posts/2019-01-27-minimal-ubuntu-tiling-wm-setup/
https://www.maketecheasier.com/install-use-i3-window-manager-ubuntu/
https://www.dagorret.com.ar/instalar-utilizar-i3-window-manager-ubuntu/
https://opensource.com/article/18/8/getting-started-i3-window-manager

```
# averiguar por: doas, cmus, qutebrowser, emerge

sudo apt-get install i3 i3status i3lock compton nitrogen
# i3 para manejar las ventanas
# i3status
# i3lock para dar atajos al linux (ej. apagar el ordenador)
# compton para darle transparencia a las imagenes
# nitrogen cambia el aspecto del linux (supongo que el theme)
```

## 1. Instalación
```
sudo apt-get install i3
```
## 2. Configuraciones
>Debemos modificar el archivo `.config/i3/config`

INSTALL https://www.youtube.com/watch?v=CREit-6_IgI&t=928s
ROFI https://www.youtube.com/watch?v=wcMyH3o5FMg

## 3. Atajos
-Super+Ret Abre una terminal
-Super+Shift+e Cerrar sesion de i3
-Super+d Despliega **Rofi** para ejecutar lineas de comando (por default suele abrir el dmenu, yo lo cambié en la configuración)
-Super+Shift+r Reinicia el entorno i3 y mantiene los espacios de trabajo
-Super+Shift+c Recarga archivos de configuración de i3
-Super+Shift+Q Cierra la ventana
-Super+Flecha Cambiar cursor a otra ventana
-Super+Shift+Flecha Mueve la ventana
-Super+n (siendo **n** un numero cualquiera) Cambia el espacio de trabajo
-Super+v Super+Ret Establece que la próxima ventana se abra vertical a la que estamos posicionados (es decir luego de Super+v necesitamos ejecutar Super+Ret que abrirá la nueva ventana como siempre, pero debajo de la actual)
-Super+Shift+n Mueve una ventana a otro espacio de trabajo, suponiendo que **n** es número de la estación de trabajo
-Modo Resize:
>Para cambiar el tamaño de las ventanas
    1. Super+r Activa el modo Resize
		2. ArrowKey (para ajustar el tamaño)
		3. Ret (para aplicar el cambio)
-Modo Widescreen:
>Para agrupar varias pestañas que estan una debajo de la otra en una sola con tantas pestañas como ventanas tuviera debajo
    -Super+w superpone la ventana a las que tenga arriba y debajo
		-Super+ArrowKey para desplazarnos entre las pestañas
		-Super+e Desactiva el modo Widescreen

>**Observaciones**:
- **Super** es la tecla que asignamos al configurar i3 (suele ser Windows ó Alt).
- **Ret** se suele referir a la tecla **Enter**
- **ArrowKey** es cualquiera de las flechas del teclado

- - -

# 3. Usando w3m y w3m-img
>Con el programa `w3m` podemos navegar via internet mediante la terminal de comandos,
>mientras que con `w3m-img` nos permite visualizar imagenes desde la terminal.


- - -

# 4. Rofi 
>Parecido a una terminal? permite ejecutar comandos, diferencia? facilidad?

>Este programa nos despliega un menu (parecido al dmenu) y facilita la ejecución de
>programas mediante lineas de comando, evitando tener que abrir una terminal.

## 1. Instalación
```bash
sudo apt-get install rofi
```

## 2. Ejecutar y configurar
```
rofi -show run 
```

## 3. Cambiar el theme
>Suponiendo que ya esta configurado con i3
1. Presionamos el atajo `Mod+d` 
2. Elegimos rofi-theme-selector (yo prefiero el monokai o solarized)
3. Para ver la lista de themes entramos a `/usr/share/rofi/themes`
4. Configuramos `~/.config/i3/config/ y agregamos la siguiente linea
```
bindsym $mod+d exec rofi -show run -opacity "80" -columns 2 -theme Monokai
```
5. Reiniciamos el ... con `Mod+Shift+R
6. Podemos probar que se aplicó el tema con `Mod+d`

- - - 
## Otras configuraciones
>Si queres encontrar otras configuraciones podes visitar la siguiente página [Ver Reddit Unixporn](https://www.reddit.com/r/unixporn/)

- - -

# 5. Nitrogen agregar wallpapers al sistema
>Si queremos darle un estilo al sistema agregando un fondo de pantalla,
>necesitaremos del programa `Nitrogen` que nos lo facilita.

## 5.1 Instalación
```
sudo apt-get install nitrogen -y
```

## 5.2 Configuramos la ruta de las imágenes
>Para que podamos seleccionar los wallpaper debemos indicar en donde
>estan ubicados, por tanto en la terminal escribimos lo siguiente
```
nitrogen $HOME/Pictures/Wallpapers
```
Luego sólo elegimos la imagen que queramos y seleccionamos en **Apply**

- - -

# 6. Compton - Agregar transparencia a transición entre ventanas
>Con `compton` podemos agregar una animación de transparencia en cada transición
entre ventanas.

## 6.1 Instalación
>Ejecutamos la siguiente linea de comando en la terminal
```bash
sudo apt-get install compton -y
```

## 6.2 Lo configuramos con i3
>Agregamos en el archivo de configuración de i3 la siguiente linea
```
exec_always compton -f # este comando se ejecutará cada vez que inicie i3
```

- - - 

# 7. i3Blocks - Configurar la barra de estado

## 7.1 Instalación
>Ejecutamos la siguiente linea de comando en la terminal
```bash
apt-get install i3blocks -y
```

## 7.2 Configuración de i3
>En el archivo de configuración de i3 buscamos la linea que diga `bar` y la modificamos
>para que quede algo parecido a lo siguiente
```
bar{
		status_command i3blocks # al agregar esto, la barra de estado se modifica
		position top # con esto se posiciona arriba de la pantalla
}
```
## 7.3 Copiamos la configuración y se lo agregamos a la configuración de i3
>Esto es para no perder la configuración original
```
cp /etc/i3blocks.conf ~/.config/i3/

```

>Luego modificamos en `~/.config/i3/i3blocks.conf` lo que queremos o no visualizar en la barra de estado
>y reiniciamos el i3 con `Super+Shift+R`

https://i3wm.org/docs/userguide.html#_configuring_i3bar

- - -

# 8. Terminal File Manager 
>Con `Ranger File Manager` nos ayuda navegar por los directorios, y el manejo de archivos y carpetas,
>como puede ser copiar,mover,borrar, etc..

- Referencias sobre Ranger Terminal File Manager
    -Documentacion Oficial [Ver Pagina](https://github.com/ranger/ranger)
		-Wiki, por ArchLinux [Ver Pagina](https://wiki.archlinux.org/index.php/Ranger)
    -Referencia 1, por Vitux [Ver Pagina](https://vitux.com/how-to-install-ranger-terminal-file-manager-on-linux/)
    -Referencia 2, por Vultr [Ver Pagina](https://www.vultr.com/docs/how-to-install-ranger-terminal-file-manager-on-linux)

## 8.1 Instalacion && Ejecucion
>En la terminal solo ejecutamos la siguiente linea de codigo
```bash
sudo apt-get install ranger -y # para instalar en ubuntu
```

>Para iniciarlo solo escribimos la siguiente linea de comando
```bash
ranger
```

## 8.2 Atajos
>Algunos de ellos son:
- Shift+q Salir de la terminal


- - -

#Agregar color a la terminal
terminal dark-google theme
https://www.linuxuprising.com/2019/07/179-color-schemes-for-your-gtk-based.html

#agregar imagen de fondo a la terminal
https://www.maketecheasier.com/add-wallpaper-linux-terminal/#targetText=Thankfully%2C%20within%20the%20settings%20of,the%20top%20and%20click%20Preferences.


#Fuente para programar
source code pro
https://wesbos.com/programming-fonts/
http://hivelogic.com/articles/top-10-programming-fonts/
https://www.narga.net/top-best-programing-fonts/

https://www.slant.co/topics/7014/~fonts-to-use-in-a-terminal-emulator
https://github.com/adobe-fonts/source-code-pro
https://github.com/adobe-fonts/source-code-pro/releases/tag/variable-fonts

Instalar font manager
https://itsfoss.com/install-fonts-ubuntu/#targetText=To%20install%20several%20fonts%20at,show%20hidden%20files%20in%20Ubuntu.

# neofetch
https://github.com/dylanaraps/neofetch/wiki
https://www.omgubuntu.co.uk/2017/01/neofetch-3-0-released
sudo add-apt-repository ppa:dawidd0811/neofetch

# Referencia
- Informacion del Ordenador con NeoFetch [Ver Página](https://blog.desdelinux.net/neofetch-obten-informacion-de-tu-equipo-y-sistema-en-la-terminal/)
https://www.ostechnix.com/neofetch-display-linux-systems-information/
-Instalar y configurar i3
		-Documentación Oficial [Ver Página](https://i3wm.org/)
    -Configurar la barra de i3 [Ver Página](https://i3wm.org/docs/userguide.html#_configuring_i3bar)
    -Opcion 1 [Ver Video](https://www.youtube.com/watch?v=8-S0cWnLBKg)
		
