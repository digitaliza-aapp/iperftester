# Iperftester

Iperftester es una distribución live basada en [**Debian**](https://www.debian.org/) para medir el ancho de banda (throughput) y calidad de enlaces de red mediante [**iperf**](https://sourceforge.net/projects/iperf2/) / [**iperf3**](https://github.com/esnet/iperf#iperf3--a-tcp-udp-and-sctp-network-bandwidth-measurement-tool) 

El enlace a examinar se delimita por dos equipos ejecutando **iperftester** donde uno actua como cliente y otro como servidor.

![](https://github.com/fmbrieva/iperftester/blob/master/use_case/iperftester_version_00r04.png?raw=true)

```
Pueden realizarse pruebas de forma automática donde solamente es necesario introducir ip/mascara/gateway
```

## Caso de uso A ##

Se desea medir el throughput y calidad de enlaces entre dos sedes:

- Sede A: red interna 1Gbps/1000Mbps con conexión Macrolan 100Mbps
- Sede B: red interna 1Gbps/1000Mbps con conexión Macrolan 150Mbps

![](https://github.com/fmbrieva/iperftester/blob/master/use_case/iperftester_macrolan_100M_00r01.png?raw=true)

```
El ancho de banda máximo es el del enlace mas lento **100Mbps
```



Al iniciar el LiveCd **iperftester** se arrancan varios servidores:
 - iperf3 TCP/UDP/STCP puerto 5201
 - iperf TCP puerto 5001
 - iperf UDP puerto 5002
 - ssh puerto 22
 
 El servidor ssh permite controlar remotamente los equipos y extraer los resultados de las pruebas mediante sftp.
 
```
Desde equipos con Windows puede utilizarse el programa WinSCP para descargar los resultados

```

## Perfiles de uso:

### usuario: iperf



### usuario: root




## Roadmap

### Version 0 (febrero 2018):

- Iperftester LiveCD
   - Medir ancho de banda y calidad de enlaces
   - Automatizar pruebas y crear ficheros de log con los resultados.
   - Visualizar tráfico E/S en tiempo real utilizando puertos mirror
  
 
![](https://github.com/fmbrieva/iperftester/blob/master/use_case/iperftester_internet_300M_00r01.png?raw=true)




```
Versión 0: usuario mirror
```




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
- Paneles con tráfico E/S (Grafana y Mediawiki)
  https://github.com/fmbrieva/mediawiki-grafana
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
