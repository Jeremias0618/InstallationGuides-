# Instalación y Configuración de Webmin/Virtualmin en Ubuntu 18.04

### Actualización del sistema
Asegúrate de que tu sistema esté actualizado.
```
sudo apt update && sudo apt upgrade -y
```

### Configuración del hostname
Configura un nombre de host (hostname) para tu servidor, lo cual es requerido por Virtualmin.
```
sudo hostnamectl set-hostname <tu-hostname>
```

### Descarga y ejecución del script de instalación
Descarga el script automatizado que facilita la instalación de Webmin/Virtualmin.
```
wget http://software.virtualmin.com/gpl/scripts/install.sh
```

### Dar permisos de ejecución al script
Asegúrate de que el script sea ejecutable.
```
chmod +x install.sh
```

### Ejecución del script de instalación
Ejecuta el script para instalar Webmin/Virtualmin.
```
sudo ./install.sh
```

### Acceso a Webmin/Virtualmin
Una vez completada la instalación, accede al panel a través de la siguiente URL:
```
https://<IP_DE_TU_SERVIDOR>:10000
```
Nota: Usa `https` y no `http`.

### Inicio de sesión en Webmin/Virtualmin
Inicia sesión con el usuario `root` y la contraseña de root de tu servidor.

### Configuración inicial
Sigue las instrucciones para completar la configuración, que incluyen la configuración de MySQL y DNS, así como opciones opcionales como cuotas de disco.

### Creación de un nuevo dominio (Virtual Server)
Ve a "Create Virtual Server" en el menú principal y completa los campos requeridos.
```
Domain name: <nombre_de_dominio>
Description: <opcional>
Administration Password: <contraseña_para_el_dominio>
```

### Gestión de bases de datos
Para crear una base de datos, ve a "Edit Databases" bajo el dominio seleccionado y haz clic en "Create a new database".

### Configuración de correo electrónico
Si configuraste un servidor de correo, puedes gestionar cuentas de correo:
```
Ve a Edit Users y agrega un nuevo usuario con acceso al correo electrónico.
```

### Administración de archivos
Usa el administrador de archivos integrado para gestionar los archivos de tu dominio:
```
Ve a File Manager y gestiona los archivos directamente desde el panel.
```

### Instalación de certificados SSL
Para instalar un certificado SSL gratuito con Let’s Encrypt, ve a:
```
Server Configuration > SSL Certificate > Let’s Encrypt.
```

### Comandos útiles

### Reiniciar Webmin/Virtualmin
Para reiniciar Webmin/Virtualmin, usa el siguiente comando:
```
sudo systemctl restart webmin
```

### Ver el estado de Webmin/Virtualmin
Para verificar el estado de Webmin/Virtualmin:
```
sudo systemctl status webmin
```

### Ver logs del sistema
Para ver los logs de Webmin/Virtualmin en tiempo real:
```
tail -f /var/webmin/miniserv.error
```