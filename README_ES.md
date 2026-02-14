# 8311 WAS-110 Creador de Firmware

## fwenvs Personalizados
```
8311_fix_vlans=1
8311_internet_vlan=0
8311_services_vlan=36

8311_ipaddr=192.168.11.1
8311_netmask=255.255.255.0
8311_gateway=192.168.11.254
8311_ping_ip=192.168.11.2

8311_console_en=1
8311_ethtool_speed=speed 2500 autoneg off duplex full
8311_failsafe_delay=30
8311_persist_root=0
8311_root_pwhash=$1$BghTQV7M$ZhWWiCgQptC1hpUdIfa0e.
8311_rx_los=0

8311_cp_hw_ver_sync=1
8311_device_sn=DM222XXXXXXXXXX
8311_equipment_id=5690
8311_gpon_sn=SMBSXXXXXXXX
8311_hw_ver=Fast5689EBell
8311_mib_file=/etc/mibs/prx300_1V.ini
8311_reg_id_hex=00
8311_sw_verA=SGC830007C
8311_sw_verB=SGC830006E
8311_vendor_id=SMBS
```


### fwenvs de Corrección de ISP
`8311_fix_vlans` - **Corregir VLANs**  
Establecer en `0` para deshabilitar las correcciones automáticas que se aplican a las VLANs.  

`8311_internet_vlan` - **VLAN de Internet**  
Establecer el ID de VLAN local para usar en Internet o `0` para hacer que Internet no esté etiquetado (y también eliminar VLAN 0) (0 a 4095). Por defecto es `0` (sin etiquetar).  

`8311_services_vlan` - **VLAN de Servicios**  
Establecer el ID de VLAN local para usar en Servicios (ej. TV/Teléfono fijo) (1 a 4095). Esto corrige el multi-servicio en Bell.  


### fwenvs de Gestión
`8311_ipaddr` - **Dirección IP**  
Establecer la dirección IP de gestión. Por defecto es `192.168.11.1`  

`8311_netmask` - **Máscara de Subred**  
Establecer la máscara de subred de gestión. Por defecto es `255.255.255.0`  

`8311_gateway` - **Puerta de Enlace**  
Establecer la puerta de enlace de gestión. Por defecto es la dirección IP (es decir, sin puerta de enlace predeterminada)  

`8311_ping_ip` - **IP de Ping**  
Establece una dirección IP para hacer ping cada 5 segundos, esto puede ayudar a acceder al dispositivo. Por defecto es la segunda dirección IP en la red de gestión configurada (ej. 192.168.11.2).  


### fwenvs del Dispositivo
`8311_console_en` - **Consola Serial**  
Establecer en `1` para habilitar la consola serial, esto causará que TX_FAULT se active ya que comparte el mismo pin SFP.  

`8311_ethtool_speed` - **Configuración de Velocidad Ethtool**  
Establecer la configuración de velocidad ethtool en la interfaz eth0_0 (ethtool -s).  

`8311_factory_mode` - **Modo de Fábrica**  
Establecer en 1 para habilitar el modo de fábrica, de lo contrario el modo de fábrica se deshabilitará automáticamente al iniciar.  

`8311_failsafe_delay` - **Retardo de Seguridad**  
Establece el número de segundos que retrasaremos el inicio de omcid en el arranque (30 a 300). Por defecto es 30 segundos.  

`8311_lct_mac` - **Dirección MAC LCT**  
Establecer la dirección MAC en la interfaz de gestión LCT.  

`8311_persist_root` - **Sistema de Archivos Raíz Persistente**  
Establecer en `1` para permitir que el sistema de archivos raíz permanezca persistente (también requeriría modificar el fwenv bootcmd). Esto no es recomendado y solo debe usarse para propósitos de depuración/pruebas.  

`8311_root_pwhash` - **Hash de Contraseña Root**  
Permite establecer una contraseña root personalizada configurando el hash.  

`8311_rx_los` - **Solución Alternativa RX_LOS**  
Establecer en `0` para monitorear el estado del pin RX_LOS y deshabilitarlo cada vez que se habilite. Esto permitirá que el dispositivo sea accesible en dispositivos que deshabilitan el acceso al puerto si RX_LOS está siendo activado.  


### fwenvs PON
`8311_cp_hw_ver_sync` - **Sincronizar Versión del Paquete de Circuitos**  
Cuando se establece en `1` y `8311_hw_ver` también está establecido, modificará el archivo mib configurado para establecer el campo Versión de cualquier ME de Paquete de Circuitos para que coincida con la versión de Hardware.  

`8311_device_sn` - **Número de Serie del Dispositivo**  
Establece el número de serie del dispositivo físico, esto es más o menos solo para visualización.  

`8311_equipment_id` - **ID de Equipo**  
Establece el campo ID de Equipo PON en el ONU2-G ME (257).  

`8311_gpon_sn` - **Número de Serie GPON / ID ONT**  
Establece el Número de Serie GPON enviado al OLT en varios MEs (4 letras, seguidas de 8 dígitos hexadecimales).  

`8311_hw_ver` - **Versión de Hardware**  
Establece la cadena de versión de hardware enviada al OLT en varios MEs (hasta 14 caracteres).  

`8311_iphost_domain` - **Nombre de Dominio del Host IP**  
Establece el nombre de dominio enviado al OLT en ME 134 (hasta 25 caracteres).  

`8311_iphost_hostname` - **Nombre de Host del Host IP**  
Establece el nombre de host enviado al OLT en ME 134 (hasta 25 caracteres).  

`8311_iphost_mac` - **Dirección MAC del Host IP**  
Establece la dirección MAC enviada al OLT en ME 134.  

`8311_loid` - **ID de ONU Lógico**  
Establece el ID de ONU Lógico presentado al OLT en ME 256 (hasta 24 caracteres).  

`8311_lpwd` - **Contraseña Lógica**  
Establece la Contraseña Lógica presentada al OLT en ME 256 (hasta 12 caracteres).  

`8311_mib_file` - **Archivo MIB**  
Establece el archivo MIB usado por omcid. Por defecto es `/etc/mibs/prx300_1U.ini`  

`8311_pon_slot` - **Ranura PON**  
Establece el número de ranura en la que se presenta el puerto UNI, necesario en algunos ISPs.  

`8311_reg_id_hex` - **ID de Registro**  
Establece el ID de Registro (hasta 36 caracteres [72 hexadecimales]) enviado al OLT en formato hexadecimal. Aquí es donde establecerías una contraseña ploam (que está contenida en los últimos 12 caracteres).  

`8311_sw_verA` / `8311_sw_verB` - **Versiones de Software**  
Establece las versiones de software específicas de la imagen enviadas en los MEs de imagen de Software (7).  

`8311_vendor_id` - **ID de Proveedor**  
Establece el ID de Proveedor PON enviado al OLT, derivado automáticamente del Número de Serie GPON si no está establecido (4 letras).  



## Autenticación
Las claves de host SSH (todas en `/etc/dropbear`) y authorized_keys (todas en `/root/.ssh`) ahora se almacenan de forma persistente.
Las configuraciones UCI anteriores se migrarán automáticamente.

La contraseña root actual (cambiar con `passwd`) puede persistirse usando el comando `8311-persist-root-password.sh`


### SSH Sin Contraseña

Por defecto, esta imagen permite acceso SSH sin contraseña al usuario root. Puedes establecer una contraseña después del primer acceso:

```bash
ssh root@192.168.11.1
passwd  # Establecer nueva contraseña
8311-persist-root-password.sh  # Hacerla persistente
```

Nota: Si estableces la variable fwenv `8311_root_pwhash`, se aplicará la autenticación por contraseña.


## Instalación de Paquetes

Esta imagen incluye soporte completo de opkg para instalar paquetes adicionales:

```bash
opkg update
opkg install <nombre-del-paquete>
```

Los siguientes repositorios de paquetes están preconfigurados para OpenWrt 21.02.3:
- Paquetes Core
- Paquetes Base
- Paquetes LuCI
- Paquetes de la Comunidad
- Paquetes de Routing
- Paquetes de Telefonía

Nota: Los paquetes se instalan en el sistema de archivos overlay, por lo que persistirán entre reinicios cuando `8311_persist_root=1` esté configurado (ver el fwenv `8311_persist_root` en la sección de Gestión arriba).



## Scripts

### build.sh
Herramienta para construir nuevas imágenes de firmware modificadas para WAS-110
```
Uso: ./build.sh [opciones]

Opciones:
-i --image <archivo>            Especificar archivo de imagen de actualización local de stock.
-I --image-dir <dir>            Especificar directorio de imagen de stock (debe contener bootcore.bin, kernel.bin, y rootfs.img).
-o --image-out <archivo>        Especificar imagen de actualización local a generar.
-h --help                       Este texto de ayuda
```

### create.sh
Herramienta para crear nuevas imágenes de actualización local para WAS-110
```
Uso: ./create.sh [opciones]

Opciones:
-i --image <archivo>            Especificar archivo de imagen de actualización local a crear (requerido).
-H --header <archivo>           Especificar nombre de archivo de encabezado de imagen en el que basar la imagen (por defecto: header.bin).
-b --bootcore <archivo>         Especificar nombre de archivo de imagen bootcore a colocar en la imagen creada (por defecto: bootcore.bin).
-k --kernel <archivo>           Especificar nombre de archivo de imagen de kernel a colocar en la imagen creada (por defecto: kernel.bin).
-r --rootfs <archivo>           Especificar nombre de archivo de imagen rootfs a colocar en la imagen creada (por defecto: rootfs.img).
-V --image-version <versión>    Especificar cadena de versión a establecer en la imagen creada (máximo 14 caracteres).
-h --help                       Este texto de ayuda
```


### extract.sh
Herramienta para extraer imágenes de actualización local de stock para WAS-110
```
Uso: ./extract.sh [opciones]

Opciones:
-i --image <archivo>            Especificar archivo de imagen de actualización local a extraer (requerido).
-H --header <archivo>           Especificar nombre de archivo para extraer el encabezado de imagen (por defecto: header.bin).
-b --bootcore <archivo>         Especificar nombre de archivo para extraer la imagen bootcore (por defecto: bootcore.bin).
-k --kernel <archivo>           Especificar nombre de archivo para extraer la imagen de kernel (por defecto: kernel.bin).
-r --rootfs <archivo>           Especificar nombre de archivo para extraer la imagen rootfs (por defecto: rootfs.img).
-h --help                       Este texto de ayuda
```
