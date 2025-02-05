# Configuración de la Red en Ubuntu 18.04

### Configuración de red con Netplan

```bash
sudo nano /etc/netplan/00-netcfg.yaml
```

### Configuración del archivo YAML

Asegúrate de que el archivo `00-netcfg.yaml` contenga la configuración adecuada para tu red, como se muestra a continuación:

```yaml
# This is the network config written by 'subiquity'
network:
  ethernets:
    ens33:               # Nombre de la interfaz de red (ajusta si es necesario)
      addresses:
      - 192.168.1.120/24  # Dirección IP estática
      gateway4: 192.168.1.1  # Dirección IP del gateway
      nameservers:
        addresses:
        - 8.8.4.4          # DNS de Google (puedes cambiarlo si prefieres otro)
  version: 2
```

### Aplicar la configuración

Para aplicar la configuración de red:

```bash
sudo netplan apply
```

### Verificar la configuración

Puedes verificar que la configuración se haya aplicado correctamente ejecutando el siguiente comando:

```bash
ip a
``` 

