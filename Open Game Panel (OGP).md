# INSTALACION DEL PANEL Open Game Panel (OGP) EN UBUNTU 18.04

### Nota: 
Si encuentras algún problema con alguno de los comandos presentados en esta guía (como en el caso de que no se pueda encontrar un paquete), NO te preocupes y continúa con la siguiente línea o comando. La instalación tendrá éxito incluso si algunos paquetes no se instalan. Esto ocurre porque los nombres de los paquetes cambian en diferentes versiones del sistema operativo y estas instrucciones están agrupadas de forma genérica.

### Requisitos previos para Ubuntu 18.04

Si estás utilizando Ubuntu 18.04, ejecuta los siguientes comandos en una terminal:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install libxml-parser-perl libpath-class-perl perl-modules screen rsync sudo e2fsprogs unzip subversion libarchive-extract-perl pure-ftpd libarchive-zip-perl libc6 libgcc1 git curl
sudo apt-get install libc6-i386
sudo apt-get install libgcc1:i386
sudo apt-get install lib32gcc1
sudo apt-get install lib32gcc-s1
sudo apt-get install libhttp-daemon-perl
```

```
sudo apt-get install apache2 curl subversion php7.2 php7.2-gd php7.2-zip libapache2-mod-php7.2 php7.2-curl php7.2-mysql php7.2-xmlrpc php-pear mysql-server php7.2-mbstring php-gettext git php-bcmath
```

### Configuración de la base de datos para Ubuntu 18.04

Después de instalar los requisitos previos, asegúrate de que la cuenta de root en MySQL esté configurada ejecutando este comando (esto puede no aplicar a versiones anteriores de Debian / Ubuntu):

```
sudo mysql_secure_installation
```

Al instalar MySQL / MariaDB, asegúrate de responder las siguientes preguntas de esta manera:

```
Switch to unix_socket authentication [Y/n] n (no, no lo hagas)
Change the root password? [Y/n] y (sí, hazlo y escribe la contraseña que uses)
```

Durante este proceso, se te pedirá que configures una contraseña para el usuario root. Por favor, elige algo seguro y anótalo, ya que el instalador te lo pedirá más tarde para crear la base de datos inicial de OGP.

¡Asegúrate de escribir la contraseña de root en algún lugar, ya que se utilizará en el siguiente paso!

Después de instalar y configurar la contraseña de root para el servidor MySQL / MariaDB, puedes instalar el paquete phpmyadmin y configurarlo (opcional):

```
sudo apt-get install phpmyadmin
```

### Instalación del paquete del panel para Ubuntu 18.04

Ahora, podemos descargar e instalar el último paquete DEB del panel OGP:

```
wget -N "https://github.com/OpenGamePanel/Easy-Installers/raw/master/Linux/Debian-Ubuntu/ogp-panel-latest.deb" -O "ogp-panel-latest.deb"
sudo dpkg -i "ogp-panel-latest.deb"
```

Una vez hecho esto, abre el navegador y ve a `http://{IP_DEL_SERVIDOR_O_localhost}/index.php`

Prueba `http://127.0.0.1/index.php` si localhost no funciona.

Se te pedirá que completes la instalación del panel OGP. Cuando se te solicite la información de la base de datos, utiliza lo siguiente:

```
MySQL Host = "localhost"
MySQL User = "ogpuser"
MySQL Database Name = "ogp_panel"
```

También necesitarás la contraseña de tu base de datos, la cual puedes encontrar ejecutando el siguiente comando:

```
sudo cat /root/ogp_panel_mysql_info
```

La contraseña es lo que sigue después de `OGPDBPass=`, como se muestra a continuación:

```
OGPDBPass=SampleDBPass
```

Una vez que hayas completado la instalación del panel web, necesitas agregar el servidor que ejecutará los servidores de juegos al software del panel web. Necesitarás la dirección IP del servidor que ejecuta el agente (127.0.0.1 si está en la misma máquina), y la clave de cifrado para esa máquina, la cual puedes obtener ejecutando el siguiente comando en ese servidor:

```
sudo cat /root/ogp_user_password
```

La clave de cifrado es lo que sigue después de `ogpEnc=`, como se muestra a continuación:

```
ogpEnc=sampl13eKey
```

Una vez instalado el panel, por favor ejecuta la funcionalidad de actualización del panel iniciando sesión con la cuenta de administrador creada durante la instalación.

Coloca el cursor sobre la pestaña "Administración" y luego haz clic en "Actualizar Panel" en el menú desplegable. Después haz clic en el botón "Actualizar".

### Tema Obsidian para Open Game Panel (OGP)

```
cd /var/www/html/themes/
git clone https://github.com/hmrserver/Obsidian.git
mv Obsidian/themes/Obsidian/* Obsidian/
rm -r Obsidian/themes
```

