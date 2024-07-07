# Instalar Docker Nagios
sudo docker-compose -p nagios up -d    (Nagios es el nombre que le damos al contenedor)
## Parar contenedor Docker Nagios
 sudo docker-compose down
## Eliminar Docker Nagios
sudo docker rmi  71c4992638a2 (poner Image ID: sudo docker image ls)
## Entrar en la Bash shell de docker Nagios
sudo docker exec -it nagios /bin/bash
## Reiniciar Nagios (para aplicar cambios, etc)
sudo docker restart nagios
# Configurar Nagios

Hubicacion nagios:
/opt/nagios
/opt/nagios/libexdec ---> scripts
/opt/nagios/etc ----> Ficheros configuracion
•localhost.cfg: Plantilla de configuración para monitorizar los servicios del propio servidor Nagios.
• hypervisor.cfg: Plantilla de configuración para monitorizar los servicios de las plataformas de virtualización.
• linux.cfg: Plantilla de configuración para monitorizar los servicios de los hosts Linux.
• windows.cfg: Plantilla de configuración para monitorizar los servicios de los hosts Windows.
• netdev.cfg: Plantilla de configuración para monitorizar los servicios de los dispositivos de red.

# Monitorizar Servidor Windows en Nagios

1.
 
