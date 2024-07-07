# Instalar Docker Nagios

   cd /opt

   git clone https://github.com/txurtxil/nagios/
   
   sudo docker-compose -p nagios up -d    (nagios es el nombre que le damos al contenedor)
   
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

1.Instalar el agente en los hosts Windows a monitorizar, en nuestro caso instalaremos “NSClient++” 

    (1.Generic,2.Complete 3. IP equipo a monitorizar y activar las casillas Enable check plugins, Enable nsclient server, Enable NRPE server y insecure legacy)

2. Editamos el fichero de configuración de nagios:

    nano /etc/nagios/nagios.cfg

3. Creamos una carpeta donde alojaremos el fichero .cfg de maquina a monitorzar

   mkdir /opt/nagios/etc/objects/equipos
   cd /opt/nagios/etc/objects/equipos

4. copiamos la plantilla  el fichero /opt/nagios/etc/objects/windows.cfg del equipo a minitorizar:
   
    cp /opt/nagios/etc/objects/windows.cfg /opt/nagios/etc/objects/equipos/win01.cfg
   
   Lo editamos y en  el apartado "define host" poner la direccion IP del equipo a monitorizar

5.Editamos el fichero de configuración de nagios:

    nano /etc/nagios/nagios.cfg
    
Añadimos la línea que especifica el fichero de configuración el equipo windows que vamos a monitorizar
debajo de la seccion "Definitions for monitoring a Windows machine":

        cfg_file=/opt/nagios/etc/objects/equipos/win01.cfg
        
6.Editamos el fichero donde se definen los comandos para nagios:

nano /etc/nagios/objects/commands.cfg

En la definición del comando para “check_nt” es donde se situa la comunicacion con el equipo y lleva la passwd generada dirante la instalacion de “NSClient++” 
, comentamos el que viene por defecto y agregamos el siguiente:

command_line $USER1$/check_nt -H $HOSTADDRESS$ -p 12489 -s YPg7gMkLOOne49PB -v $ARG1$ $ARG2$

Con este procedimiento ya deberiamos tener monitorizado el primer equipo windows

## Comandos utiles para tranajar ocn el doquer nagios
### Reiniciar Ngios para aplicar cambios: 

     sudo docker restart  nagios

### Entrar en la Shell del volumen Nagios para poder trabajar con los ficheros de configuracion Nagios

    sudo docker exec -it nagios /bin/bash


   


 
