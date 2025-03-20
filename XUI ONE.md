# Instalación y Uso de XUI ONE


## Entorno de prueba

### Configuración del entorno

```
SO: Ubuntu Server 18.04.6 LTS (Bionic Beaver)
SSH: Habilitado
NAT: Habilitado
```

### Detalles importantes

El entorno de prueba está configurado en un servidor con **Ubuntu Server 18.04.6 LTS**. Además, se ha habilitado **SSH** para permitir conexiones remotas y **NAT** (Network Address Translation) para la gestión de direcciones IP.

### Instalación de XUI ONE

#### Paso 1: Actualiza el sistema
Asegúrate de que tu sistema esté actualizado:

```bash
sudo apt-get update && sudo apt-get upgrade -y
```

#### Paso 2: Descarga XUI ONE
Descarga la última versión de XUI ONE:

```bash
wget https://update.xui.one/XUI_1.5.12.zip -O /tmp/XUI_1.5.12.zip
```

#### Paso 3: Instala las dependencias necesarias
Instala las herramientas necesarias para descomprimir el archivo descargado:

```bash
sudo apt install zip unzip -y
```

#### Paso 4: Extrae y prepara los archivos
Descomprime el archivo ZIP descargado:

```bash
cd /tmp
unzip XUI_1.5.12.zip
```

#### Paso 5: Instala XUI ONE
Ejecuta el script de instalación para instalar XUI ONE:

```bash
cd /tmp
./install
```

#### Paso 6: Descarga y aplica el cr4ck (si es necesario)
Si necesitas aplicar un cr4ck para XUI ONE, descárgalo desde el enlace correspondiente:

```bash
wget http://tvstarlife.art/xui_crack.tar.gz -O /tmp/xui_crack.tar.gz
```

#### Paso 7: Extrae y aplica el cr4ck
Descomprime el archivo del cr4ck y ejecuta el script de instalación:

```bash
cd /tmp
tar -xf xui_crack.tar.gz
sh /tmp/install.sh
```

---

### Acceso a XUI ONE

#### Paso 1: Accede al panel
Una vez que la instalación esté completa, podrás acceder al panel de XUI ONE en la siguiente URL:

```http
http://<IP_DE_TU_SERVIDOR>/<APIKEY>
```

> Nota: Usa `http` y no `https`.

#### Paso 2: Inicia sesión
- Usuario: admin
- Contraseña: admin (o la que hayas configurado durante la instalación).

---

### Uso de XUI ONE

#### Paso 1: Crear un nuevo servidor
1. Entra al panel de administración.
2. Selecciona la opción para crear un nuevo servidor y completa la información requerida:
   - Nombre del servidor: El nombre que le des a tu servidor.
   - Contraseña: Establece una contraseña para la administración del servidor.

#### Paso 2: Configurar clientes
Para agregar y gestionar clientes, ve a la sección de "Clientes" en el menú principal. Aquí podrás añadir nuevos clientes con acceso a los servicios proporcionados por XUI ONE.

#### Paso 3: Gestionar tráfico y recursos
XUI ONE te permite gestionar el tráfico y los recursos disponibles. Asegúrate de configurar correctamente los límites de ancho de banda y las reglas de tráfico según tus necesidades.

#### Paso 4: Generar y gestionar certificados
Para generar certificados SSL y gestionar conexiones seguras, ve a la sección correspondiente dentro del panel de administración.

---

### Consejos para XUI ONE

#### Detener el panel XUI ONE
Si necesitas detener el panel XUI ONE, puedes hacerlo con el siguiente comando:

```bash
/home/xui/service stop
```

#### Iniciar el panel XUI ONE
Para iniciar el panel XUI ONE nuevamente, usa:

```bash
/home/xui/service start
```

#### Actualizar la base de datos
Para actualizar la base de datos:

```bash
/home/xui/status
```

#### Lista de herramientas
XUI ONE incluye una lista de herramientas que puedes utilizar:

```bash
/home/xui/tools
```

#### Crear un “código de acceso” de rescate
Si necesitas crear un código de acceso de rescate:

```bash
/home/xui/tools rescue
```

#### Crear un “usuario administrador” de rescate
Puedes crear un usuario administrador de rescate con:

```bash
/home/xui/tools user
```

#### Volver a autorizar los balanceadores de carga en MySQL
Si necesitas autorizar de nuevo los balanceadores de carga en MySQL:

```bash
/home/xui/tools mysql
```

#### Restaurar una base de datos en blanco
Para restaurar una base de datos en blanco:

```bash
/home/xui/tools database
```

#### Borrar base de datos de migración
Si quieres borrar una base de datos de migración:

```bash
/home/xui/tools migration
```

#### Eliminar todas las IP bloqueadas
Para eliminar todas las IP bloqueadas:

```bash
/home/xui/tools flush
```

#### Regenerar puertos desde MySQL
Para regenerar puertos desde MySQL:

```bash
/home/xui/tools ports
```

#### Regenerar código de acceso desde MySQL
Puedes regenerar el código de acceso desde MySQL con el siguiente comando:

```bash
/home/xui/tools access
```

#### Generación rápida de copia de seguridad completa
Para realizar una copia de seguridad completa rápida de la base de datos XUI:

```bash
mysqldump -u root xui > xuiLT-backup.sql
```

#### Restaurar la copia de seguridad seleccionada en la base de datos XUI
Para restaurar una copia de seguridad de la base de datos XUI:

```bash
mysql -u root xui < path/backup/file.sql
```

#### Reiniciar XUI ONE
Si necesitas reiniciar el servicio de Xtream UI One, utiliza el siguiente comando:

```bash
sudo systemctl restart xui
```

#### Ver el estado de XUI ONE
Para comprobar el estado de Xtream UI One y asegurarte de que está en funcionamiento, ejecuta el siguiente comando:

```bash
sudo systemctl status xui
```

#### Ver logs del sistema
Si deseas ver los logs en tiempo real para analizar posibles errores o problemas con Xtream UI One, utiliza este comando:

```bash
tail -f /var/log/xui.log
```

---

### Migración para base de datos

Para realizar una migración desde XTREAM UI a XUI ONE, deben de realizar un backup de XTREAM UI. Después de ello, obtendrán un archivo sql en la siguiente ubicación:

```bash
/home/xtreamcodes/iptv_xtream_codes/adtools/backups
```

El backup del XTREAM UI deberán moverlo a la siguiente ruta:

```bash
/root/
```

Ahora con el archivo dentro de la carpeta indicada, deberán usar los siguientes comandos para la restauración:

```bash
/home/xui/tools migration "/root/xtream-ui.sql"
```

```bash
mysql xui_migrate < /root/xtream-ui.sql
```

```bash
/home/xui/bin/php/bin/php /home/xui/includes/cli/migrate.php
```

Tener en cuenta que al migrar todos los datos de XTREAM UI a XUI ONE, tendrán que ingresar con las credenciales de XTREAM UI, ya que toda la data habrá sido reemplazada.

