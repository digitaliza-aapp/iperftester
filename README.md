# Iperftester

Iperftester es una distribución live basada en [**Debian**](https://www.debian.org/) para medir el ancho de banda (throughtput) y calidad de enlaces de red mediante [**iperf**](https://sourceforge.net/projects/iperf2/) / [**iperf3**](https://github.com/esnet/iperf#iperf3--a-tcp-udp-and-sctp-network-bandwidth-measurement-tool) 

El enlace a examinar se delimita por dos equipos ejecutando **iperftester** donde uno actua como cliente y otro como servidor.

## Roadmap

### Version 0 (febrero 2018):

- Iperftester LiveCD
   - Medir troughtput en tramos de red (iperf / iperf3)			            (usuario iperf)
   - Mirror para visualizar tráfico de entrada y salida 		               (usuario mirror)
   - Modo experto - Herramientas tcpdump tshark ngrep iptraf-ng etc. 	   (usuario root)

### Versión 1:

- Programación horaria de pruebas iperf / iperf3
- APIRest
   - Descarga resultados iperf / iperf3 (Json)
   - Consultar tráfico E/S (mirror / sflow) 
   - Documentación con Swagger

### Versión 2 - 3:
- Modo sonda / colector
- Colector Sflow para visualizar tráfico E/S en tiempo real 
- Monitorizar sondas mediante (Icinga/Nagios)
- Paneles con tráfico E/S (Grafana y Mediawiki)
  https://github.com/fmbrieva/mediawiki-grafana
- Herramienta Web para centralizar resultados y controlar sondas
- Facilitar despliegue de sondas (Docker y contenedores LXD)

## Casos de uso

### Medir ancho de banda (throughtput) y calidad de enlaces
![](http://www.delegacionprovincial.com/mediawiki/upload_files/lxd_images/images/lxd_x2go_scenario.png)

```
Bandwidth tester (Versión 0)
```


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



