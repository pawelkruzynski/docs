---
title: "Tutorial - ¿Cómo bloquear el acceso a mi sitio web para determinadas direcciones IP a través de un archivo .htaccess?"
excerpt: "Descubra las posibles acciones a través de un archivo .htaccess para bloquear el acceso a su sitio web a determinadas direcciones IP."
updated: 2024-03-14
---

## Objetivo

Este tutorial le ayudará a proteger el acceso a sus sitios web de la red exterior, a prevenir o corregir posibles intrusiones o intentos de ataques DDoS (ataques de denegación de servicio).

Esto se puede lograr a través de un archivo ".htaccess", un archivo de texto en particular detectado por el servidor web (Apache), que permite establecer reglas especiales para un directorio y todos sus subdirectorios.

Puede crear varios archivos ".htaccess" en [el espacio FTP](/pages/web_cloud/web_hosting/ftp_connection) de su alojamiento, pero **un solo** por directorio o subdirectorio para evitar conflictos entre diferentes ficheros ".htaccess".

**Descubra cómo bloquear el acceso a su sitio web para algunas direcciones IP a través de un archivo ".htaccess".**

> [!warning]
>
La configuración, la gestión y la responsabilidad de los servicios que OVHcloud pone a su disposición recaen sobre usted. Por lo tanto, usted deberá asegurarse de que estos funcionan correctamente.
> 
> Ponemos a su disposición esta guía para ayudarle a realizar las tareas más habituales. No obstante, si tiene alguna duda, le recomendamos que contacte con un [proveedor especializado](/links/partner). Nosotros no podremos asistirle. Más información en la sección ["Más información"](#go-further) de esta guía.
>

## Requisitos

- Disponer de un [hosting OVHcloud](/links/web/hosting)

## Procedimiento

> [!primary]
>
> El archivo ".htaccess" puede estar situado en varias carpetas diferentes, pero respetando la regla de un **solo** fichero ".htaccess" por carpeta o subcarpeta.
>
> La configuración de un archivo ".htaccess" se aplica al directorio en el que está instalado y a todos sus subdirectorios.
>
> Para editar (o crear) estos directorios, conéctese al espacio FTP de su alojamiento. Si lo necesita, consulte la guía "Acceder a mi espacio de almacenamiento" (/pages/web_cloud/web_hosting/ftp_connection).
>

### Bloquear una IP, un rango de IP, un dominio o todas las IP de un país 

Hay varias reglas disponibles para bloquear los accesos al alojamiento a través del ".htaccess".<br>
Preste especial atención a la sintaxis y a los parámetros que bloquee para evitar que se bloquee usted mismo durante la consulta de sus sitios web y/o scripts alojados.<br>
En caso de error, puede conectarse a [el espacio FTP](/pages/web_cloud/web_hosting/ftp_connection) de su alojamiento para corregir la situación. 

> [!primary]
>
> Los alojamientos compartidos funcionan actualmente con **Apache 2.4**. Desde la versión **Apache 2.3**, se han implementado variables y la sintaxis de redacción de las restricciones/autorizaciones de acceso ha cambiado.
>
> Debido a que la sintaxis antigua es muy utilizada, esta sigue activa en nuestras infraestructuras. Sin embargo, *Apache* la considera obsoleta y podría no estar disponible en breve. En este tutorial encontrará ejemplos que detallan ambas sintaxis.
>
> Para más información sobre la nueva sintaxis, puede consultar las siguientes páginas oficiales:
>
> - [Documentación sobre el control de acceso Apache 2.4](https://httpd.apache.org/docs/2.4/en/howto/access.html) {.external}
> - [Documentación sobre el módulo mod_authz_core Apache 2.4](https://httpd.apache.org/docs/2.4/mod/mod_authz_core.html) {.external}
>

#### Bloquear una IP

Para bloquear una dirección IP específica, introduzca uno de los siguientes códigos en el archivo ".htaccess":

> [!tabs]
> Sintaxis histórica
>>
>> ```bash
>> Deny from IP_address
>> ```
>>
> Sintaxis de Apache 2.3
>>
>> ```bash
>> <RequireAll>
>> Require all granted
>> Require not ip IP_address
>> </RequireAll>
>> ```
>>

- **Ejemplo** : si desea bloquear la dirección IP 203.0.113.0, deberá escribir uno de los siguientes códigos:

> [!tabs]
> Sintaxis histórica
>>
>> ```bash
>> Deny from 203.0.113.0
>> ```
>>
> Sintaxis de Apache 2.3
>>
>> ```bash
>> <RequireAll>
>> Require all granted
>> Require not ip 203.0.113.0
>> </RequireAll>
>> ```
>>

#### Bloquear un rango de IP

Para bloquear un rango de direcciones IP, introduzca uno de los siguientes códigos en su archivo ".htaccess":

> [!tabs]
> Sintaxis histórica
>>
>> ```bash
>> Deny from IP_range
>> ```
>>
> Sintaxis de Apache 2.3
>>
>> ```bash
>> <RequireAll>
>> Require all granted
>> Require not ip IP_range
>> </RequireAll>
>> ```
>>

- **Ejemplo** : si desea bloquear todas las IP en 203.0.113.x, deberá escribir uno de los dos códigos siguientes:

> [!tabs]
> Sintaxis histórica
>>
>> ```bash
>> Deny from 203.0.113
>> ```
>>
> Sintaxis de Apache 2.3
>>
>> ```bash
>> <RequireAll>
>> Require all granted
>> Require not ip 203.0.113
>> </RequireAll>
>> ```
>>

#### Bloquear un dominio

Algunos dominios pueden acceder al alojamiento a través de redirecciones o peticiones.

Para bloquear un dominio, introduzca uno de los dos códigos siguientes en el archivo ".htaccess":

> [!tabs]
> Sintaxis histórica
>>
>> ```bash
>> Deny from domain
>> ```
>>
> Sintaxis de Apache 2.3
>>
>> ```bash
>> <RequireAll>
>> Require not host domain
>> </RequireAll>
>> ```
>>

- **Ejemplo** : si desea bloquear el dominio.tld, deberá escribir uno de los dos códigos siguientes:

> [!tabs]
> Sintaxis histórica
>>
>> ```bash
>> Deny from domain.tld
>> ```
>>
> Sintaxis de Apache 2.3
>>
>> ```bash
>> <RequireAll>
>> Require not host domain.tld
>> </RequireAll>
>> ```
>>

#### Bloquear las IP de un país

> [!primary]
>
> Todas las direcciones IP (especialmente las IP públicas) disponen de una geolocalización a escala de país. Esto permite tener una idea de la procedencia de los flujos de una IP y localizar físicamente la IP. 
>
> El ".htaccess" permite, gracias a este elemento, bloquear el conjunto de IP geolocalizadas en un país. 
> En otras palabras, todas las personas que intenten visitar su sitio desde este país serán bloqueadas (a menos que utilicen una conexión VPN con una IP geolocalizada en otro país).
>
> Los bloqueos a través del ".htaccess" se realizan a través de los "Country Codes" de dos letras (Norma ISO 3166-1 alpha2) de los países.
>
> Varios sitios web enumeran los países y sus respectivos "Country Codes", de los que [https://www.iban.com/country-codes](https://www.iban.com/country-codes) {.external} (independiente de OVHcloud).
>

Para bloquear todas las IP de un país, introduzca uno de los siguientes códigos en su archivo ".htaccess":

> [!tabs]
> Sintaxis histórica
>>
>> ```bash
>> SetEnvIf GEOIP_COUNTRY_CODE Country_Code BlockCountry
>> Deny from env=BlockCountry
>> ```
>>
> Sintaxis de Apache 2.3
>> Poner todo en la parte superior de su ".htaccess"
>>
>> ```bash
>> RewriteCond %{ENV:GEOIP_COUNTRY_CODE} ^(Country_Code)$
>> RewriteRule ^(.*)$ - [F,L]
>> ```
>>

- **Ejemplo** : si desea bloquear las direcciones IP geolocalizadas en Fiyi (FJ) y Groenlandia (GR), deberá escribir uno de los siguientes códigos:

> [!tabs]
> Sintaxis histórica
>>
>> ```bash
>> SetEnvIf GEOIP_COUNTRY_CODE FJ BlockCountry
>> SetEnvIf GEOIP_COUNTRY_CODE GR BlockCountry
>> Deny from env=BlockCountry
>> ```
>>
> Sintaxis de Apache 2.3
>> Poner todo en la parte superior de su ".htaccess"
>>
>> ```bash
>> RewriteCond %{ENV:GEOIP_COUNTRY_CODE} ^(FJ|GR)$
>> RewriteRule ^(.*)$ - [F,L]
>> ```
>>

### Para autorizar solo algunas IP, un rango de IP o el conjunto de IP de un país

En lugar de restringir el acceso a una o más IP y dejar que el resto acceda al alojamiento, puede hacer lo contrario bloqueando todas las IP y permitiendo el acceso a su servicio a una o más IP.

#### Autorizar una o más IP

Para autorizar solo una IP a acceder al servicio, introduzca uno de los siguientes códigos en el archivo ".htaccess":

> [!tabs]
> Sintaxis histórica
>>
>> ```bash
>> order deny,allow
>> deny from all
>> Allow from IP_address
>> ```
>>
> Sintaxis de Apache 2.3
>>
>> ```bash
>> Require ip IP_address
>> ```
>>

- **Ejemplo** : si solo quiere autorizar a las IPs 203.0.113.0 y 203.0.113.1 a acceder a su alojamiento, deberá escribir uno de los siguientes códigos:

> [!tabs]
> Sintaxis histórica
>>
>> ```bash
>> order deny,allow
>> deny from all
>> Allow from 203.0.113.0
>> Allow from 203.0.113.1
>> ```
>>
> Sintaxis de Apache 2.3
>>
>> ```bash
>> Require ip 203.0.113.0 203.0.113.1
>> ```
>>

#### Autorizar un rango de IP

Para autorizar a un rango de IP a acceder al servicio, introduzca uno de los siguientes códigos en su archivo ".htaccess":

> [!tabs]
> Sintaxis histórica
>>
>> ```bash
>> order deny,allow
>> deny from all
>> Allow from IP_range
>> ```
>>
> Sintaxis de Apache 2.3
>> Poner todo en la parte superior de su ".htaccess"
>>
>> ```bash
>> Require ip IP_range
>> ```
>>

- **Ejemplo** : si solo desea autorizar el acceso al alojamiento al rango de IPs 203.0.113.x, deberá escribir uno de los siguientes códigos:

> [!tabs]
> Sintaxis histórica
>>
>> ```bash
>> order deny,allow
>> deny from all
>> Allow from 203.0.113
>> ```
>>
> Sintaxis de Apache 2.3
>> Poner todo en la parte superior de su ".htaccess"
>>
>> ```bash
>> Require ip 203.0.113
>> ```
>>

#### Autorizar el conjunto de IP de un país

Para autorizar a todas las IP de un país a acceder al servicio, introduzca uno de los siguientes códigos en el archivo ".htaccess":

> [!tabs]
> Sintaxis histórica
>>
>> ```bash
>> order deny,allow
>> deny from all
>> SetEnvIf GEOIP_COUNTRY_CODE Country_Code AllowCountry
>> Allow from env=AllowCountry
>> ```
>>
> Sintaxis de Apache 2.3
>> Poner todo en la parte superior de su ".htaccess"
>>
>> ```bash
>> RewriteCond %{ENV:GEOIP_COUNTRY_CODE} !^(Country_Code)$
>> RewriteRule ^(.*)$ - [F,L]
>> ```
>>

- **Ejemplo** : si únicamente desea autorizar a las islas Fiyi (FJ) y Groenlandia (GR) a acceder a su alojamiento, deberá escribir uno de los siguientes códigos:

> [!tabs]
> Sintaxis histórica
>>
>> ```bash
>> order deny,allow
>> deny from all
>> SetEnvIf GEOIP_COUNTRY_CODE FJ AllowCountry
>> SetEnvIf GEOIP_COUNTRY_CODE GR AllowCountry
>> Allow from env=AllowCountry
>> ```
>>
> Sintaxis de Apache 2.3
>> Poner todo en la parte superior de su ".htaccess"
>>
>> ```bash
>> RewriteCond %{ENV:GEOIP_COUNTRY_CODE} !^(FJ|GR)$
>> RewriteRule ^(.*)$ - [F,L]
>> ```
>>

### Complementos en el archivo ".htaccess"

Independientemente de la seguridad en el acceso general al alojamiento, el archivo ".htaccess" permite realizar otras acciones. A continuación encontrará otros tres tutoriales de OVHcloud sobre el tema:

- [Proteger la interfaz de administración de su sitio web a través del ".htaccess"](/pages/web_cloud/web_hosting/htaccess_protect_directory_by_password).
- [Reescribir sus URLs gracias al "mod_rewrite"](/pages/web_cloud/web_hosting/htaccess_url_rewriting_using_mod_rewrite).

## Más información <a name="go-further"></a>

Para servicios especializados (posicionamiento, desarrollo, etc.), contacte con [partners de OVHcloud](/links/partner).

Si quiere disfrutar de ayuda para utilizar y configurar sus soluciones de OVHcloud, puede consultar nuestras distintas soluciones [pestañas de soporte](/links/support).

Interactúe con nuestra [comunidad de usuarios](/links/community).