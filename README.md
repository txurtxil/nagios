# Instalar Docker Nagios
sudo docker-compose -p nagios up -d    (Nagios es el nombre que le damos al contenedor)
# Parar contenedor Docker Nagios
 sudo docker-compose down
# Eliminar Docker Nagios
sudo docker rmi  71c4992638a2 (poner Image ID: sudo docker image ls)
# Entrar en la Bash shel de docker Nagios
sudo docker exec -it nagios /bin/bash
## Reiniciar Nagios (para aplicar cambios, etc)
sudo docker restart  nagios_nagios_1
