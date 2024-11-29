---
title: "Resolver los errores recurrentes durante el uso de un programa FTP"
excerpt: "Encuentre aquí las anomalías más frecuentes asociadas a su programa FTP"
updated: 2022-01-05
---

## Objetivo

El uso de software FTP durante la conexión a su [hosting Web Cloud](/links/web/hosting) puede provocar diferentes anomalías. Esta guía explica cómo solucionar los problemas más comunes.

**Esta guía explica cómo solucionar los errores relacionados con el software FTP.**

> [!warning]
>
> La configuración, la gestión y la responsabilidad de los servicios que OVHcloud pone a su disposición recaen sobre usted. Por lo tanto, usted deberá asegurarse de que estos funcionen correctamente.
>
> Esta guía le ayudará a realizar las operaciones más habituales. No obstante, si tiene alguna duda le recomendamos que contacte con un proveedor de servicios especializado o con el editor del servicio. Nosotros no podremos asistirle al respecto. Para más información, consulte el apartado [Más información](#go-further) de esta guía.
>

## Requisitos

- Tener contratado un plan de [hosting Web Cloud](/links/web/hosting).
- Haber iniciado sesión en el [área de cliente de OVHcloud](/links/manager).

## Procedimiento

### "Este servidor no soporta FTP en TLS" (FileZilla)

![doesnt-support-ftp-on-tls](/pages/assets/screens/other/web-tools/filezilla/doesnt-support-ftp-on-tls.png){.thumbnail}

Este mensaje en el programa [FileZilla](/pages/web_cloud/web_hosting/ftp_filezilla_user_guide) indica que no ha activado la opción SFTP o SSH desde el [área de cliente de OVHcloud](/links/manager). Por ese motivo, la información intercambiada entre el servidor de hosting de OVHcloud y su ordenador no se cifrará.

Si los datos que desea intercambiar por este medio no son confidenciales, haga clic en `Aceptar`{.action}.

En caso contrario, acceda al [área de cliente de OVHcloud](/links/manager), en la sección `Web Cloud`{.action} y, seguidamente, `Alojamientos`{.action}. Seleccione el alojamiento correspondiente y abra la pestaña `FTP-SSH`{.action}.

Si dispone de un alojamiento [Personal](/links/web/hosting-personal-offer), marque la casilla `Desactivado`{.action} en la columna `SFTP`{.action} y espere unos minutos.

Si dispone de un alojamiento [Pro](/links/web/hosting-professional-offer) o [Performance](/links/web/hosting-performance-offer), haga clic en el botón `...`{.action} a la derecha del usuario FTP correspondiente y seleccione `Editar`{.action}.

Seleccione `SFTP`{.action} o `Activado`{.action} (para activar el protocolo SSH en su alojamiento), haga clic en `Siguiente`{.action} y luego en `Aceptar`{.action}. Espere unos minutos.

> [!primary]
>
> Para más información sobre los errores, consulte la sección `Diagnóstico` de nuestras guías de [Hosting](/products/web-cloud-hosting).
>

### He transferido mis archivos con un programa FTP, pero mi sitio web no aparece.

En primer lugar, compruebe que los archivos y carpetas del sitio web estén presentes en la [carpeta raíz](/pages/web_cloud/web_hosting/hosting_how_to_get_my_website_online#23-cargar-los-archivos-en-el-espacio-de-almacenamiento) del alojamiento.

Si ha realizado algún cambio en sus [servidores DNS](/pages/web_cloud/domains/dns_server_edit) o en su [zona DNS](/pages/web_cloud/domains/dns_zone_edit) hace menos de 48 horas, espere y reinicie periódicamente sus dispositivos para vaciar su caché.

### Mis claves FTP no funcionan.

Si no puede autenticarse, modifique su contraseña FTP siguiendo las instrucciones de esta [guía](/pages/web_cloud/web_hosting/ftp_change_password).

### Encuentro errores aleatorios en mi sitio web.

La falta de espacio en su alojamiento compartido puede provocar fallos de funcionamiento en su sitio web al intentar modificarlo o actualizarlo.

Para comprobar el espacio de almacenamiento restante del alojamiento, conéctese al [área de cliente de OVHcloud](/links/manager). Haga clic en `Web Cloud`{.action} y, seguidamente, en `Alojamientos`{.action}. Seleccione el alojamiento correspondiente.

La cantidad de datos almacenados en el servidor de alojamiento (excluyendo las bases de datos) se muestra en la sección `Información general`{.action} > `Espacio en disco`.

![disk_space](/pages/assets/screens/control_panel/product-selection/web-cloud/web-hosting/general-information/find-disk-space.png){.thumbnail}

### No puedo transferir mis archivos al servidor FTP.

Compruebe que su programa FTP esté conectado en "Modo Pasivo" (Modo de configuración de un servidor FTP en el que el servidor determina el puerto de conexión).

Por ejemplo, en [Filezilla](/pages/web_cloud/web_hosting/ftp_filezilla_user_guide), haga clic en `Edición`{.action}, `Opciones`{.action}, `FTP`{.action} y seleccione `Pasivo (recomendado)`{.action}.

Limite también el tamaño de sus transferencias de datos (no podrá enviar más de **5.000 archivos y carpetas** a los servidores compartidos de OVHcloud en una sola transferencia). Realice sus importaciones varias veces si es necesario utilizando carpetas comprimidas.

Si dispone de una [fórmula Pro](/links/web/hosting-professional-offer) o [Performance](/links/web/hosting-performance-offer), utilice preferentemente el [protocolo SSH](/pages/web_cloud/web_hosting/ssh_on_webhosting) para importar los archivos en el espacio de almacenamiento de los archivos del alojamiento.

### No puedo eliminar el enlace simbólico "index.html" en mi espacio FTP.

Este enlace se instala por defecto en los alojamientos compartidos de OVHcloud. El cartel dice:

![site-under-construction](/pages/assets/screens/other/browsers/errors/site-under-construction.png){.thumbnail}

Si no ha utilizado la funcionalidad "[Módulo en 1 clic](/pages/web_cloud/web_hosting/cms_install_1_click_modules)" para crear su sitio web, deberá utilizar el programa [Net2FTP](/pages/web_cloud/web_hosting/ftp_connection#21-conexion-mediante-un-explorador-ftp) accesible desde el [área de cliente de OVHcloud](/links/manager) para eliminar manualmente la página "Sitio en construcción".

## Más información <a name="go-further"></a>

[Uso de FileZilla con el alojamiento](/pages/web_cloud/web_hosting/ftp_filezilla_user_guide)

Para servicios especializados (posicionamiento, desarrollo, etc.), contacte con los [partners de OVHcloud](/links/partner).

Si quiere disfrutar de ayuda para utilizar y configurar sus soluciones de OVHcloud, consulte nuestros distintos [servicios de soporte](/links/support).

Interactúe con nuestra [comunidad de usuarios](/links/community).