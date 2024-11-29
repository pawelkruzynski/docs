---
title: "FAQ Web Hosting"
excerpt: "Encuentre las respuestas a las preguntas más frecuentes sobre alojamiento web"
updated: 2024-06-27
---

## Gestión de su producto

### ¿Cómo configurar mi alojamiento?

Conéctese al [área de cliente de OVHcloud](/links/manager) para configurar el alojamiento. Desde la sección `Alojamientos` podrá gestionar sus certificados SSL, la versión PHP, la opción CDN, el multisitio, las bases de datos, etc.

**Trucos y Trucos**: Para ayudarle a configurar su alojamiento, consulte la sección *Primeros pasos* que encontrará [aquí](/products/web-cloud-hosting).

### ¿Cómo administrar mis contraseñas?

Para gestionar sus contraseñas, debe conectarse en primer lugar al [área de cliente de OVHcloud](/links/manager). En caso de olvidar su identificador o su contraseña, haga clic en el `¿No recuerda su ID de cliente o contraseña?`{.action} en la ventana de conexión. Recibirá la información necesaria por correo electrónico.

También puede consultar la guía [Establecer y gestionar la contraseña de su cuenta](/pages/account_and_service_management/account_information/manage-ovh-password).

Una vez que se haya conectado al área de cliente,

- Para cambiar la contraseña de su espacio FTP, siga las indicaciones de [esta guía](/pages/web_cloud/web_hosting/ftp_change_password).
- Para cambiar la contraseña de la base de datos, siga las instrucciones de [esta guía](/pages/web_cloud/web_hosting/sql_change_password).
- Para cambiar la contraseña de una cuenta MX Plan, siga las indicaciones de [esta guía](/pages/web_cloud/email_and_collaborative_solutions/mx_plan/email_change_password).

### ¿Cómo publicar mi sitio web? 

Para publicar su sitio web, debe disponer de un [nombre de dominio](/links/web/domains) que corresponda a la dirección web desde la que estará accesible su sitio web (por ejemplo: *mi dominio.com*). También necesitará un [alojamiento](/links/web/hosting) en el que instalar su sitio web.

Para más información, consulte esta [página](/links/web/hosting-website) y siga las indicaciones de la guía [Publicar un sitio web en internet](/pages/web_cloud/web_hosting/hosting_how_to_get_my_website_online).

**Trucos y Trucos**: Para ayudarle a crear su sitio web, OVHcloud le permite instalar en su alojamiento un programa de soporte para la creación de sitios web (WordPress, PrestaShop, Joomla! y Drupal), gracias a la funcionalidad [Módulos en 1 clic](/pages/web_cloud/web_hosting/cms_install_1_click_modules).

### ¿Cómo transferir sin interrupción del servicio mi sitio web, mi base de datos, mi dominio y mi correo a los servidores de OVHcloud?

Para más información, consulte la guía "[Migrar un sitio web y los servicios asociados a OVHcloud](/pages/web_cloud/web_hosting/hosting_migrating_to_ovh)".

### ¿Cómo alojar varios sitios web en un mismo plan de hosting?

Consulte la guía "[Alojar varios sitios web en un mismo hosting](/pages/web_cloud/web_hosting/multisites_configure_multisite) ".

### ¿Cómo cambiar de plan de alojamiento?

Para contratar el plan de hosting más adecuado para usted, puede consultar nuestros planes en [esta página](/links/web/hosting).

A continuación, siga las indicaciones de nuestra guía ["Mejorar el plan de hosting"](/pages/web_cloud/web_hosting/how_to_upgrade_web_hosting_offer).

### ¿Cómo conservar la solución de correo asociada a mi alojamiento compartido cuando se da de baja el servicio?

Al dar de baja o eliminar el alojamiento compartido, el servicio de correo asociado también se dará de baja. Para conservar sus direcciones de correo, deberá desvincular el servicio de correo antes de dar de baja el alojamiento.<br>

Para ello, acceda a la pestaña `Información general`{.action} del alojamiento. En la sección **Configuración**, haga clic en el botón `...`{.action} situado a la derecha de "**Direcciones de correo**". Haga clic en `Desvincular mi opción de correo`{.action} y siga las instrucciones para contratar una solución de correo independiente que le permitirá conservar sus direcciones de correo ya creadas.

### Al dar de baja un plan de hosting Performance, ¿cómo conservar la solución Web Cloud Databases asociada?

Los alojamientos compartidos **Performance** incluyen una solución Web Cloud Databases que se puede activar gratuitamente.
Al dar de baja o eliminar el alojamiento compartido **Performance**, la solución Web Cloud Databases asociada también se dará de baja. Para conservar su Cloud Databases, deberá desvincularlo antes de dar de baja el alojamiento.<br>

Para ello, abra la pestaña `Información general`{.action} del alojamiento. En la sección **Configuración**, haga clic en el botón `...`{.action} a la derecha de "**Web Cloud Databases**". Haga clic en `Desvincular`{.action} y siga las instrucciones para contratar una solución Cloud Databases independiente, lo que le permitirá conservar su Cloud Databases ya creado.

### ¿Cómo aumentar la RAM de un plan de hosting Cloud Databases asociado a un alojamiento compartido "Performance"?

Para aumentar la RAM de un plan de hosting Cloud Databases asociado a un alojamiento compartido **Performance**, deberá eliminar obligatoria y previamente el plan de hosting Cloud Databases del alojamiento **Performance** para migrar a un plan superior.

Para ello, conéctese al [área de cliente de OVHcloud](/links/manager). Acceda a la sección `Web Cloud`{.action} y seleccione el alojamiento correspondiente en la pestaña `Alojamientos`{.action}. 

En la página Información general{.action}, encontrará un recuadro titulado `Configuración`{.action} en el centro de la página. Haga clic en el botón `...`{.action} a la derecha de la mención `Web Cloud Databases`{.action} y luego en `Desvincular`{.action}. Seleccione la duración de renovación más corta y continúe hasta la validación del pedido.

Para más información, consulte nuestra guía ["Configuración de un plan de hosting Cloud Databases"](/pages/web_cloud/web_cloud_databases/configure-database-server#modify-ram-web-cloud-db)

**Esta acción es irreversible y la solución Web Cloud Databases se facturará a continuación, independientemente de su plan de hosting Performance.**

## Diagnóstico

> [!warning]
>
> Si encuentra una anomalía no indicada en esta FAQ, consulte la página "*Diagnóstico*" de [nuestra documentación](/products/web-cloud-hosting).
>

### ¿Qué hacer si mi sitio web no funciona bien? 

Existen diversos motivos por los que podría haber fallado el funcionamiento del sitio web. Para identificar la causa, compruebe que ninguna de sus suscripciones necesita ser **renovada** conectándose al [área de cliente de OVHcloud](/links/manager).

Consulte a continuación los [eventos en curso en nuestra infraestructura](https://www.status-ovhcloud.com/). Si todos sus servicios están activos y no se ven afectados por ninguna incidencia o mantenimiento, le invitamos a realizar un diagnóstico más detallado.

### ¿Qué hacer si, después de publicar mi sitio web, la página "Sitio en construcción" de OVHcloud sigue apareciendo?

![site-en-construction](/pages/assets/screens/other/browsers/errors/site-en-construction.png){.thumbnail}

Al instalar el alojamiento, OVHcloud coloca esta página de espera como un archivo **index.html** contenido en la carpeta `www` de su servidor FTP.

Este archivo se desactiva automáticamente al crear su [módulo en 1 clic](/pages/web_cloud/web_hosting/cms_install_1_click_modules).

Si ha elegido [Web hosting: Instalar un CMS manualmente](/pages/web_cloud/web_hosting/cms_manual_installation), [conéctese al espacio FTP](/pages/web_cloud/web_hosting/ftp_connection) para renombrarlo como **index.html.old**.

### ¿Qué hacer si mi sitio web aparece en una dirección web de tipo "xxxx.cluster0xx.hosting.ovh.net"?

![url-cluster](/pages/assets/screens/other/browsers/urls/url-cluster.png){.thumbnail}

Dos escenarios son posibles. O bien el sitio web se ha creado con esta dirección, o bien esta ha aparecido como consecuencia de un cambio.

#### Situación 1: su sitio web ha sido creado con una dirección web de tipo "xxxxx.cluster0xx.hosting.ovh.net".

> [!warning]
>
> La eliminación de una base de datos, como la de un módulo en 1 clic, es definitiva. También implica la **supresión de las copias de seguridad** de los datos correspondientes. Antes de eliminar el sitio web del alojamiento de OVHcloud, **asegúrese de poder crearlo de la misma** forma. Si no está seguro de las operaciones a realizar, contacte con su Webmaster o con uno de [nuestros partners](/links/partner).
>

En primer lugar, después de realizar todas las copias de seguridad necesarias, elimine el módulo desde el área de `Alojamientos` de OVHcloud.

![delete-a-module](/pages/assets/screens/control_panel/product-selection/web-cloud/web-hosting/1-click-modules/delete-a-module.png){.thumbnail}

A continuación, elimine la base de datos desde la pestaña con el mismo nombre situada a la derecha de su pantalla, en la sección `Alojamientos`:

![delete_a_database](/pages/assets/screens/control_panel/product-selection/web-cloud/web-hosting/databases/sharedsql-deletion.png){.thumbnail}
 
Por último, reinicie la instalación en el dominio deseado, utilizando la funcionalidad [Módulo en 1 clic](/pages/web_cloud/web_hosting/cms_manage_1_click_module).

#### Situación 2: su sitio web aparece con una dirección web de tipo "xxxxx.cluster0xx.hosting.ovh.net" después de una modificación

Si el sitio web aparece con esta URL debido a una manipulación, vuelva a su estado anterior.

> [!alert]
>
> La restauración del alojamiento de OVHcloud conlleva la restauración **del conjunto de sitios** que contiene.

> Al restaurar un sitio web, el contenido del espacio FTP o el de la base de datos se sustituyen por una copia de seguridad. No podrá recuperar los datos del servidor FTP ni los de la base de datos antes de restaurarlos.
>

Para restaurar el código fuente del sitio web, consulte nuestra guía [Restaurar el espacio de almacenamiento de un alojamiento web](/pages/web_cloud/web_hosting/ftp_save_and_backup).

Si su sitio web incluye una base de datos, consulte nuestra guía [Restaurar una copia de seguridad de la base de datos](/pages/web_cloud/web_hosting/sql_importing_mysql_database#restaurar-una-copia-de-seguridad-desde-el-area-de-cliente).

### ¿Qué hacer si mi sitio web redirige al webmail-login-interface de OVHcloud?

![webmail-login-interface](/pages/assets/screens/website/webmail/webmail-login-interface.png){.thumbnail}

Esta anomalía indica una configuración errónea a nivel de los [servidores DNS](/pages/web_cloud/domains/dns_server_edit) o de la [zona DNS](/pages/web_cloud/domains/dns_zone_edit) asociada a su dominio.

El caso más común es el siguiente: usted ha contratado por separado su dominio y su alojamiento, por lo que no están conectados entre sí a través de su zona DNS.

Acceda a la sección `Dominios`{.action} del [área de cliente de OVHcloud](/links/manager). Haga clic en el dominio correspondiente y, seguidamente, en la pestaña `Servidores DNS`{.action}.

Anote los servidores DNS indicados y acceda a la pestaña `Zona DNS`{.action}.

Compare los `Objetivos` de las entradas de tipo `NS` indicadas en la pestaña `Zona DNS`{.action} con los `servidores DNS` indicados en la pestaña del mismo nombre:

- Si los elementos son idénticos, sustituya el objetivo `213.186.33.5` por el código de cuatro cifras indicado en la pestaña `Información general` con la mención `IPv4` (para más información sobre las operaciones a realizar, consulte las instrucciones de [esta guía](/pages/web_cloud/domains/dns_zone_edit)).

- Si los elementos no son idénticos, pero los `servidores DNS` indicados en la pestaña del mismo nombre aparecen en [esta lista](/pages/web_cloud/web_hosting/clusters_and_shared_hosting_IP), siga las instrucciones de [esta guía](/pages/web_cloud/domains/dns_server_edit) para restaurarlos.

- Si los elementos no son idénticos y los `servidores DNS` indicados en la pestaña del mismo nombre no aparecen en [esta lista](/pages/web_cloud/web_hosting/clusters_and_shared_hosting_IP), contacte con su Webmaster o busque un [proveedor especializado](/links/partner) a través de la página de [partners de OVHcloud](/links/partner).

### ¿Qué hacer si mi sitio web muestra un error "La página no se redirige correctamente"?

![the-page-isnt-redirecting-properly](/pages/assets/screens/other/browsers/errors/the-page-isnt-redirecting-properly.png){.thumbnail}

> [!alert]
>
> La restauración del alojamiento de OVHcloud conlleva la restauración del conjunto de sitios que contiene.
>
> Al restaurar un sitio web, el contenido del espacio FTP o el de la base de datos se sustituyen por una copia de seguridad. No podrá recuperar los datos del servidor FTP ni los de la base de datos justo antes de restaurarlos.
>

Restaure su sitio web a su estado anterior:

- Para restaurar el código fuente del sitio web, consulte nuestra guía [Restaurar el espacio de almacenamiento de un alojamiento web](/pages/web_cloud/web_hosting/ftp_save_and_backup).

- Si su sitio web incluye una base de datos, consulte nuestra guía [Importar una copia de seguridad en la base de datos de un alojamiento web](/pages/web_cloud/web_hosting/sql_importing_mysql_database#restaurar-una-copia-de-seguridad-desde-el-area-de-cliente).

Si las restauraciones no le permiten restablecer el acceso a su sitio web, contacte con su Webmaster o busque un [proveedor especializado](/links/partner) en la web de los [partners de OVHcloud](/links/partner).

### ¿Qué hacer si mi sitio web muestra un error "503 error Backend fetch failed"?

![503_varnish](/pages/assets/screens/other/browsers/errors/http-503-backend-varnish.png){.thumbnail}

Si ha activado la [opción CDN](/pages/web_cloud/web_hosting/cdn_how_to_use_cdn) del alojamiento, desactive el modo de *mantenimiento* en su sitio web WordPress o PrestaShop.

Si no ha activado esta opción ni ha utilizado el modo de *mantenimiento*, póngase en contacto con su Webmaster o busque un [proveedor especializado](/links/partner) en el sitio web de los [partners de OVHcloud](/links/partner).

### ¿Qué hacer si mi sitio web muestra un error "Your request has been blocked"?

![your-request-has-been-blocked](/pages/assets/screens/other/browsers/errors/your-request-has-been-blocked.png){.thumbnail}

Este mensaje indica que el tipo de petición HTTP que intenta realizar en su sitio web está prohibido durante un tiempo limitado. En ese caso, [consulte los logs](/pages/web_cloud/web_hosting/logs_and_statistics) de su sitio web para ver qué peticiones han provocado el bloqueo.

Para ayudarle a corregir estas anomalías, contacte con su Webmaster o con uno de nuestros [partners](/links/partner).

### ¿Qué hacer si mi sitio web muestra un error "Your IP has been banned"?

![your-ip-has-been-banned](/pages/assets/screens/other/browsers/errors/your-ip-has-been-banned.png){.thumbnail}

Este mensaje indica que la dirección IP que utiliza para conectarse a su sitio web está bloqueada durante un tiempo limitado. 

En ese caso, [compruebe los logs](/pages/web_cloud/web_hosting/logs_and_statistics) de su sitio web para determinar qué peticiones han provocado el bloqueo.<br>
Compruebe también que su equipo informático no esté infectado por un virus.<br>
Por último, puede contactar con uno de nuestros partners (/links/partner) para que verifique el código informático de su sitio web.

### He contratado un dominio con acentos que aparece escrito de forma extraña en mi área de cliente. ¿Qué debo hacer?

![idn-notation](/pages/assets/screens/control_panel/product-selection/web-cloud/domain-dns/general-information/idn-notation.png){.thumbnail}

No tiene que hacer nada al respecto. Aunque su dominio se muestre en [notación internacionalizada (IDN)](https://es.wikipedia.org/wiki/Nombre_de_dominio_internacionalizado){.external} en su área de cliente, funcionará y se mostrará de forma totalmente normal en otro lugar. La dirección web del sitio web se mostrará tal y como usted lo haya solicitado. Sus direcciones de correo también se mostrarán como desee con sus interlocutores.

> [!warning]
>
> No es recomendable utilizar una dirección de correo electrónico con un dominio IDN en un cliente de correo (Outlook, Mail de macOS, etc.), ya que puede causar incompatibilidad.
>

## Más información <a name="go-further"></a>

[FAQ - Correo en alojamiento compartido MX Plan](/pages/web_cloud/email_and_collaborative_solutions/mx_plan/faq-emails)

Si quiere disfrutar de ayuda para utilizar y configurar sus soluciones de OVHcloud, puede consultar nuestros distintos [servicios de soporte](/links/support).

Interactúe con nuestra [comunidad de usuarios](/links/community).