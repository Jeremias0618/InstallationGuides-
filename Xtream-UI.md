# XTREAM-UI


## Entorno de prueba

### Configuración del entorno

```
SO: Ubuntu Server 18.04.6 LTS (Bionic Beaver)
SSH: Habilitado
NAT: Habilitado
```

### Detalles importantes

El entorno de prueba está configurado en un servidor con **Ubuntu Server 18.04.6 LTS**. Además, se ha habilitado **SSH** para permitir conexiones remotas y **NAT** (Network Address Translation) para la gestión de direcciones IP.

### Guía de instalación de Xtream-UI

```
apt-get update ; apt-get install libxslt1-dev libcurl3 libgeoip-dev python -y ; wget https://lofertech.com/xui/install.py ; sudo python install.py
```

### Iniciar Xtream-UI manualmente

```
/home/xtreamcodes/iptv_xtream_codes/start_services.sh
```

### Borrar registros de Xtream-UI

Los registros a veces pueden ocupar demasiado espacio. Puede borrar los registros si se queda sin espacio en disco. Puedes hacerlo así:

```
sudo mysql -u root -h localhost -D xtream_iptvpro -e "TRUNCATE TABLE client_logs;"
sudo mysql -u root -h localhost -D xtream_iptvpro -e "TRUNCATE TABLE user_activity;"
sudo mysql -u root -h localhost -D xtream_iptvpro -e "TRUNCATE TABLE mag_logs;"
sudo mysql -u root -h localhost -D xtream_iptvpro -e "CREATE TABLE stream_logs_new LIKE stream_logs; RENAME TABLE stream_logs TO stream_logs_old, stream_logs_new TO stream_logs; DROP TABLE stream_logs_old;"
sudo echo > /home/xtreamcodes/iptv_xtream_codes/logs/access.log
sudo echo > /home/xtreamcodes/iptv_xtream_codes/logs/error.log
```

### BACKUPS DIRECTORY

El directorio donde se almacenan las copias de seguridad de Xtream-UI es:

```
/home/xtreamcodes/iptv_xtream_codes/adtools/backups
```

### Screenshots

![image](https://minio1.vsys.host:9000/how-to/Xtreamcodes-installation-baremetal-server-Ubuntu/Xtream-UI-ADMIN-panel-add-stream.webp)
