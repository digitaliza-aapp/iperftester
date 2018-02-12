# iperftester

Iperftester es una distribución live basada en [**Debian**](https://www.debian.org/) para medir el ancho de banda (throughtput) y calidad de enlaces de red mediante [**iperf**](https://sourceforge.net/projects/iperf2/) / [**iperf3**](https://github.com/esnet/iperf#iperf3--a-tcp-udp-and-sctp-network-bandwidth-measurement-tool) 

El enlace a examinar se delimita por dos equipos ejecutando **iperftester** donde uno actua como cliente y otro como servidor.

## Roadmap

### Version 0 (febrero 2018):

- Iperftester LiveCD
   - Medir troughtput en tramos de red (iperf / iperf3)			            (usuario iperf)
   - Mirror para visualizar tráfico de entrada y salida 		               (usuario mirror)
   - Modo experto - Herramientas tcpdump tshark ngrep iptraf-ng etc. 	   (usuario root)

### Nuevas funciones para incluir en nuevas versiones:

- Programación horaria de pruebas iperf / iperf3
- APIRest
   - Descarga resultados iperf / iperf3 (Json)
   - Consultar tráfico E/S (mirror / sflow) 
   - Documentación con Swagger
- Modo sonda / colector
- Colector Sflow para visualizar tráfico E/S en tiempo real 
- Monitorizar sondas mediante (Icinga/Nagios)
- Paneles con tráfico E/S (Grafana y Mediawiki)
  https://github.com/fmbrieva/mediawiki-grafana
- Herramienta Web para centralizar resultados y controlar sondas
- Facilitar despliegue de sondas (Docker y contenedores LXD)

## Casos de uso

### Medir ancho de banda (throughtput) y calidad de enlaces


## Créditos

- [**Debian**](https://www.debian.org/
- [**iperf**](https://sourceforge.net/projects/iperf2/)
- [**iperf3**](https://github.com/esnet/iperf#iperf3--a-tcp-udp-and-sctp-network-bandwidth-measurement-tool)


