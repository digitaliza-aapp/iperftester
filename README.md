# Iperftester

Iperftester es una distribución live basada en [**Debian**](https://www.debian.org/) para medir el ancho de banda (`throughput`) y calidad de enlaces de red mediante [**iperf**](https://sourceforge.net/projects/iperf2/) / [**iperf3**](http://software.es.net/iperf/) 

```
Este repositorio contiene solamente los scripts Bash.

```

Puede descargar una imagen iso [**Iperftester_01r00.iso**](https://www.debian.org/) con los scripts y todas las herramientas necesarias para poder realizar tests desde un DVD, CD o Pendrive.

```
Si utiliza la imagen iso desde un software de virtualización debe configurar la tarjeta de red como bridge (adaptador puente)
``` 
El enlace a examinar se delimita por dos equipos ejecutando `iperftester` donde uno actua como cliente y otro como servidor.

```
Un equipo ejecutanto 'iperftester' puede actuar como cliente o servidor.
```

![](use_case/iperftester_version_00r04.png)

Al iniciar `iperftester` se arrancan 4 programas:
 
| Comando | Programa | Puerto |
| --- | --- | ---- |
| `iperf3` | Programa Cliente-Servidor para crear flujos de datos `TCP/UDP/SCTP` | **5201** |
| `iperf` | Programa Cliente-Servidor para crear flujos de datos  `TCP` | **5001** |
| `iperf` | Programa Cliente-Servidor para crear flujos de datos `UDP` | **5002** |
| `ssh` | Programa Servidor para acceder a maquinas remotas mediante `SSH` | **22** |
 
Los servidores `iperf`/`iperf3` se utilizan para realizar los tests  y el servidor `ssh` para poder controlar remotamente los equipos que están ejecutando `iperftester`.

```
Pueden realizarse tests de forma automática donde solamente es necesario introducir ip/mascara/gateway
```

## Perfiles de uso:

### usuario: iperf

Permite realizar tests de forma interactiva, controlar parametros de ejecución (puertos, tiempo, intervalo, etc.), consultar resultados y exportarlos a unidades externas (pendrive) o remotas (sftp).

### usuario: root     

Si necesita instalar nuevas herramientas y utiliza un proxy para acceder a internet necesita exportar la variables `http_proxy` y `https_proxy`:

- export http_proxy="http://usuario:password@ip_del_proxy:puerto_del_proxy"  
- export https_proxy="http://usuario:password@ip_del_proxy:puerto_del_proxy" 

## Caso de uso ##
### Escenario 

Se desea medir el `throughput` y calidad de enlaces entre dos sedes:

- Sede A: Red interna a 1Gbps/1000Mbps con conexión Macrolan 100Mbps 
- Sede B: Red interna a 1Gbps/1000Mbps con conexión Macrolan 150Mbps  

![](use_case/iperftester_macrolan_100M_escenario_00r01.png)

### Solución basada en iperftester

El `throughput` máximo en este escenario será el del enlace con menor ancho de banda (`Macrolan de 100Mbps`)

Para realizar los tests es necesario iniciar `iperftester` en un equipo de la Sede A y otro de la Sede B:

1. Iniciar **iperftester** en la Sede A con el usuario **iperf** (Configurar Ip/Máscara/Gateway)
2. Iniciar **iperftester** en la Sede B con el usuario **iperf** (Configurar Ip/Máscara/Gateway)
3. Ejecutar la opción **Auto** en cualquiera de las sedes para realizar los tests de forma automática
4. Consultar los resultados con la opción **Ver** o exportar a una unidad externa con la opción **Pendrive**

Si seleccionamos la opción `Auto` en la Sede A se ejecutarán los siguientes comandos:

| Commando | Detalle |
| --- | --- |
| `ping` | Desde Sede A a Sede B |
| `traceroute` | Desde Sede A a Sede B |
| `iperf3` | Inyectar tráfico TCP desde Sede A a Sede B (Tráfico de color azul) |
| `iperf3` | Inyectar tráfico TCP desde Sede B a Sede A  (Tráfico de color rojo) |
| `iperf3` | Inyectar tráfico UDP desde Sede A a Sede B (Tráfico de color azul) |
| `iperf3` | Inyectar tráfico UDP desde Sede B a Sede A  (Tráfico de color rojo) |

     
Ejemplo de un fichero de log con los resultados de la prueba [**20180222_122551_Macrolan_100M.log**](use_case/20180222_122551_Macrolan_100M.log)

![](use_case/iperftester_macrolan_100M_00r01.png)

## Otros usos

### Cambio de puertos

Es posible comprobar la conectividad entre dos puntos mediante un puerto, por ejemplo arrancando un servidor `iperf`/`iperf3` en el puerto `3306` podemos comprobar que no existen filtros intermedios (firewall) entre un equipo y un servidor Mysql.

## Roadmap

### Version 0 (febrero 2018):

- Iperftester Live
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
