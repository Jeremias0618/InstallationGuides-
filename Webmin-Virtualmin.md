# Instalación y Uso de Webmin/Virtualmin en Ubuntu 18.04

### Instalación de Webmin/Virtualmin

#### Paso 1: Actualiza el sistema
Asegúrate de que tu sistema esté actualizado.

```bash
sudo apt update && sudo apt upgrade -y
```

#### Paso 2: Configura el hostname
Configura un nombre de host (hostname) para tu servidor. Esto es requerido por Virtualmin.

```bash
sudo hostnamectl set-hostname <tu-hostname>
```
Reemplaza `<tu-hostname>` con un nombre de dominio o un nombre descriptivo.

#### Paso 3: Descarga el script de instalación
Webmin/Virtualmin tiene un script automatizado que facilita la instalación:

```bash
wget http://software.virtualmin.com/gpl/scripts/install.sh
```

#### Paso 4: Da permisos al script
Asegúrate de que el script sea ejecutable:

```bash
chmod +x install.sh
```

#### Paso 5: Ejecuta el script
Ejecuta el script para instalar Webmin/Virtualmin:

```bash
sudo ./install.sh
```

#### Paso 6: Sigue las instrucciones
El script se encargará de instalar y configurar todo lo necesario, incluyendo Apache/Nginx, MySQL/MariaDB, Postfix, y más. Dependiendo de la velocidad de tu servidor, esto puede tomar entre 10 y 20 minutos.

---

### Acceso a Webmin/Virtualmin

#### Paso 1: Accede al panel
Una vez que la instalación esté completa, podrás acceder al panel en la siguiente URL:

```https
https://<IP_DE_TU_SERVIDOR>:10000
```

> Nota: Usa `https` y no `http`.

#### Paso 2: Inicia sesión
- **Usuario:** root
- **Contraseña:** La contraseña de root de tu servidor.

#### Paso 3: Completa la configuración inicial
- **Configuración de MySQL:** Configura una contraseña para el usuario root de MySQL si aún no la tiene.
- **Validación de DNS:** Si estás configurando servidores de nombres (DNS), Virtualmin verificará tu configuración.
- **Opciones opcionales:** Configura quotas en disco o servicios adicionales según sea necesario.

---

### Uso de Webmin/Virtualmin

#### Paso 1: Crear un nuevo dominio (Virtual Server)
1. Ve a **Create Virtual Server** en el menú principal.
2. Rellena los campos requeridos:
   - **Domain name:** El dominio que deseas gestionar.
   - **Description:** (Opcional) Una descripción del dominio.
   - **Administration Password:** Contraseña para este dominio.
3. Haz clic en **Create Server**.

#### Paso 2: Gestión de bases de datos
Para crear una base de datos:
1. Ve a **Edit Databases** bajo el dominio seleccionado.
2. Haz clic en **Create a new database**.

#### Paso 3: Configurar correo electrónico
Si configuraste un servidor de correo (Postfix/Dovecot), puedes gestionar cuentas de correo:
1. Ve a **Edit Users**.
2. Agrega un nuevo usuario con acceso al correo electrónico.

#### Paso 4: Administrar archivos
Accede al administrador de archivos integrado para subir o editar archivos directamente desde el panel:
1. Ve a **File Manager**.
2. Usa la interfaz para gestionar los archivos de tu dominio.

#### Paso 5: Certificados SSL
Virtualmin facilita la instalación de certificados SSL:
1. Ve a **Server Configuration > SSL Certificate**.
2. Selecciona **Let’s Encrypt** y sigue las instrucciones para emitir un certificado gratuito.

---

### Comandos útiles

#### Reiniciar Webmin/Virtualmin

```bash
sudo systemctl restart webmin
```

#### Ver el estado de Webmin/Virtualmin

```bash
sudo systemctl status webmin
```

#### Ver logs del sistema

```bash
tail -f /var/webmin/miniserv.error
