# Iperftester

Iperftester es una distribución liveCD basada en [**Debian**](https://www.debian.org/) para medir el ancho de banda (throughput) y calidad de enlaces de red mediante [**iperf**](https://sourceforge.net/projects/iperf2/) / [**iperf3**](https://github.com/esnet/iperf#iperf3--a-tcp-udp-and-sctp-network-bandwidth-measurement-tool) 

El enlace a examinar se delimita por dos equipos ejecutando `iperftester` donde uno actua como cliente y otro como servidor.

```
Un equipo ejecutanto `iperftester` puede actuar como cliente o servidor.
```

![](https://github.com/fmbrieva/iperftester/blob/master/use_case/iperftester_version_00r04.png?raw=true)

```
Tip: Pueden realizarse tests de forma automática donde solamente es necesario introducir ip/mascara/gateway
```

Al iniciar el LiveCd se arrancan 4 servidores:

 1. iperf3 TCP/UDP/STCP puerto 5201
 2. iperf TCP puerto 5001
 3. iperf UDP puerto 5002
 4. ssh puerto 22
 
Los servidores **iperf/iperf3** se utilizan para realizar los tests  y el servidor **ssh** para poder controlar remotamente los equipos.

## Perfiles de uso:

### usuario: iperf

Permite realizar tests de forma interactiva, controlar parametros de ejecución (puertos, tiempo, intervalo, etc.), consultar resultados y exportarlos a unidades externas (pendrive).

```
Tip: Comprobar que no existen filtros intermedios (firewall) que impidan la conectividad entre un servidor y un cliente ejecutando tests cambiando el puerto del servidor iperf/iperf3, por ejemplo cambiando el puerto TCP a 3306 puede comprobarse la conectividad con un servidor Mysql.
```

### usuario: root
Accede a un terminal con permisos de administrador en el cual tiene disponible herramientas como:

    ping iperf iperf3 ssh ftp lftp speedtest-cli iproute2 net-tools bridge-utils
    lshw iproute2 net-tools  iputils-arping iputils-ping iputils-tracepath  zip
    unzip bridge-utils vi vim traceroute ethtool lshw ntfs-3g netcat            

Si necesita instalar nuevas herramientas puede utilizar el comando **apt-get install programa_a_instalar**

```
Tip: Para acceder mediante un proxy necesita exportar la variables http_proxy y https_proxy:
- export http_proxy="http://usuario:password@ip_del_proxy:puerto_del_proxy"  
- export https_proxy="http://usuario:password@ip_del_proxy:puerto_del_proxy" 
```
## Caso de uso ##
### Escenario 

Se desea medir el throughput y calidad de enlaces entre dos sedes:

- Sede A: Red 10.10.10.1 Máscara 255.255.255.0 Gateway: 10.10.10.1 a 1Gbps/1000Mbps con conexión Macrolan 100Mbps 
- Sede B: Red 10.10.20.1 Máscara 255.255.255.0 Gateway: 10.10.20.1 a 1Gbps/1000Mbps con conexión Macrolan 150Mbps  

![](https://github.com/fmbrieva/iperftester/blob/master/use_case/iperftester_macrolan_100M_escenario_00r01.png?raw=true)

### Solución basada en iperftester

El throughput máximo en este escenario será en del enlace con menor ancho de banda (Macrolan de 100Mbps)
Para realizar los tests es necesario iniciar el LiveCd en un equipo de la Sede A y otro de la Sede B:

1. Iniciar **iperftester** en la Sede A con el usuario **iperf** (IP 10.10.10.10 Máscara: 255.255.255.0 Gateway:10.10.10.1)
2. Iniciar **iperftester** en la Sede B con el usuario **iperf** (IP 10.10.20.20 Máscara: 255.255.255.0 Gateway:10.10.20.1)
3. Ejecutar la opción **Auto** en cualquiera de las sedes para realizar los test sde forma automática
4. Consultar los resultados con la opción **Ver** o exportar a una unidad externa con la opción **Pendrive**

La opción `Auto` ejecuta los siguientes comandos:

| Commando | Detalle |
| --- | --- |
| `ping` | Desde Sede A a Sede B |
| `traceroute` | Desde Sede A a Sede B |
| `iperf3` | Inyectar tráfico TCP desde Sede A a Sede B (Tráfico de color azul) |
| `iperf3` | Inyectar tráfico TCP desde Sede B a Sede A  (Tráfico de color rojo) |
| `iperf3` | Inyectar tráfico UDP desde Sede A a Sede B (Tráfico de color azul) |
| `iperf3` | Inyectar tráfico UDP desde Sede B a Sede A  (Tráfico de color rojo) |

1. First list item
   - First nested list item
     - Second nested list item
     
Ejemplo fichero de log con los resultados de la prueba [**20180223_1212_Macrolan_100M.log**](https://www.debian.org/)

![](https://github.com/fmbrieva/iperftester/blob/master/use_case/iperftester_macrolan_100M_00r01.png?raw=true)


## Roadmap

### Version 0 (febrero 2018):

- Iperftester LiveCD
   - Medir ancho de banda y calidad de enlaces
   - Automatizar pruebas y crear ficheros de log con los resultados.

### Versión 1:

- Programación horaria de pruebas iperf / iperf3
- APIRest
   - Descarga resultados iperf / iperf3 (Json)
   - Consultar tráfico E/S (mirror / sflow) 
   - Documentación Swagger
- Facilitar despliegue (Contenedores LXD)

### Versión 2 - 3:
- Modo sonda / colector
- Colector Sflow para visualizar tráfico E/S en tiempo real 
- Monitorizar sondas mediante (Icinga/Nagios)
- Paneles con tráfico E/S (Grafana y Mediawiki) https://github.com/fmbrieva/mediawiki-grafana
- Herramienta Web para centralizar resultados y controlar sondas
- Facilitar despliegue de sondas (Docker)

## Créditos

### Version 0:
- [**Debian**](https://www.debian.org/)
- [**iperf**](https://sourceforge.net/projects/iperf2/)
- [**iperf3**](https://github.com/esnet/iperf#iperf3--a-tcp-udp-and-sctp-network-bandwidth-measurement-tool)

### Versión 1:
- [**Swagger**](https://swagger.io/)
- [**LXD - Linux container**](https://linuxcontainers.org/lxd/)

### Versión 2 - 3:
- [**Grafana**](https://grafana.com/)
- [**Mediawiki**](https://www.mediawiki.org/wiki/MediaWiki)
- [**Icinga**](https://www.icinga.com/)
- [**Docker**](https://www.docker.com/)
