# Instalación y Configuración de ASTRA Cesbo

### Requisitos

- Sistema operativo basado en Linux
- CPU de 64 bits (x86)
- Conexión a internet en el servidor
- Se requiere acceso a internet periódicamente para la validación de licencia por parte de Astra en los servidores: ls1.cesbo.com, ls2.cesbo.com y ls3.cesbo.com

### Dependencias necesarias

Antes de comenzar, actualiza el sistema y asegúrate de tener `curl` instalado:

```bash
sudo apt-get update && sudo apt-get upgrade -y
sudo apt install curl
```

### Instalación de Astra

Para instalar Astra, ejecuta los siguientes comandos desde la consola:

```bash
curl -Lo /usr/bin/astra https://cesbo.com/astra-latest
chmod +x /usr/bin/astra
astra -v
```

### Obtener licencia

Para iniciar Astra en tu servidor, necesitas una licencia válida. Puedes obtener una licencia demo en el siguiente enlace:

```bash
https://app.cesbo.com/orders/software/astra/demo/
```

Una vez registrado con tu correo, recibirás un mensaje con los pasos para instalar la licencia en tu servidor. A continuación, un ejemplo del mensaje recibido:

```bash
Demo License
License ID: 14b442
Expiration date: 2025-03-29
Serial number: 14b442a7fe80aacab27ef6348ebcbbcd
Install license on your server:

Create directory for license and configuration files on your server: mkdir -p /etc/astra
Download license: curl -o /etc/astra/license.txt https://cesbo.com/astra-license/14b442a7fe80aacab27ef6348ebcbbcd
For more information, please check: Quick Start
```

### Iniciar Astra Cesbo

Para iniciar el servicio de Astra Cesbo:

```bash
astra init
systemctl start astra
```

### Habilitar inicio automático

Para que el servicio de Astra se inicie automáticamente al arrancar el sistema:

```bash
systemctl enable astra
```

### Acceder al panel de administración

Una vez que la instalación esté completa, puedes acceder al panel de Astra Cesbo en la siguiente URL:

```http
http://<IP_DE_TU_SERVIDOR>:8000
```

### Iniciar sesión en el panel

El usuario y contraseña por defecto al instalar Astra Cesbo por primera vez son:

- **Usuario**: admin
- **Contraseña**: admin

### Gestión del servicio Astra Cesbo

Puedes gestionar el servicio Astra Cesbo con los siguientes comandos:

```bash
systemctl restart astra       |  Reiniciar el servicio
systemctl start astra         |  Iniciar el servicio
systemctl stop astra          |  Detener el servicio
systemctl status astra        |  Ver el estado del servicio
systemctl enable astra        |  Iniciar el servicio al arrancar el sistema
systemctl disable astra       |  Deshabilitar el inicio automático
journalctl -fu astra          |  Ver los logs del servicio
```

### Configuración básica de Astra Cesbo

Para asegurar un funcionamiento correcto de Astra Cesbo, se recomienda realizar la siguiente configuración (aunque no es obligatoria). Esto ayudará a evitar problemas al agregar y/o reproducir señales dentro del panel de Astra Cesbo.

Esta configuración debe ingresarse en las opciones de configuración que se encuentran en el panel de Astra Cesbo:

```bash
Settings / Edit Config
```

Si no puedes localizar estas opciones en tu panel, puedes usar la siguiente URL que te redirigirá automáticamente al editar la configuración de tu servidor:

```http
http://<IP_DE_TU_SERVIDOR>:8000/#/settings-edit/<IP_DE_TU_SERVIDOR>:8000
```

Dentro de la opción "Edit Config", copia el siguiente código y reemplaza la configuración predeterminada de Astra Cesbo:

```bash
{
    "dvb_tune": [],
    "gid": 466561,
    "users": {
        "admin": {
            "created": 1712863792,
            "cipher": "3fed7a346e430ea4c2aa10250928f4de",
            "comment": "Jeremias",
            "type": 1,
            "enable": true,
            "interface": {
                "arrange": "$dvb",
                "theme": "dark"
            }
        }
    },
    "settings": {
        "http_disable_tls": true,
        "http_keep_active": "-1",
        "http_play_stream": true,
        "udp_threads": true,
        "http_play_hls": true
    }
}
```

**Importante**: Al ingresar esta configuración, tu usuario y contraseña se restablecerán a los valores por defecto:

```bash
Usuario: admin
Contraseña: admin
```

### Reiniciar Astra después de la configuración

Una vez que hayas ingresado la nueva configuración, es necesario reiniciar el servicio de Astra para que los cambios surtan efecto:

```bash
systemctl restart astra
```
