# iperftester

Iperftester es una distribución live basada en [**Debian**](https://www.debian.org/) para medir el ancho de banda (throughtput) y calidad de enlaces de red mediante iperf / iperf3.

El enlace a examinar se delimita por dos equipos ejecutando [**iperftester**]  (uno actua como cliente y otro como servidor)

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
- Versión en inglés
- Modo sonda / servidor
- Colector SFLOW para visualizar en tiempo real tráfico E/S
- Monitorizar sondas mediante (Icinga/Nagios)
- Visualizar paneles con tráfico E/S (Grafana y Mediawiki)
  https://github.com/fmbrieva/mediawiki-grafana
- Herramienta Web para centralizar resultados y controlar sondas
- Facilitar despliegue de sondas (Docker y contenedores LXD)


## Créditos

Iperftester utiliza las siguientes herramientas:
- Debian https://www.debian.org/
- iperf https://sourceforge.net/projects/iperf2/ https://sourceforge.net/projects/iperf/
- iperf3 https://github.com/esnet/iperf#iperf3--a-tcp-udp-and-sctp-network-bandwidth-measurement-tool


