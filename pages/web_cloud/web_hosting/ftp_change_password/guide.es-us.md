---
title: "Cambiar la contraseña de un usuario FTP"
excerpt: "Descubra cómo cambiar la contraseña de un usuario FTP en un alojamiento de OVHcloud"
updated: 2024-02-29
---

## Objetivo

Los planes de hosting de OVHcloud permiten acceder a un espacio de almacenamiento de archivos en la nube que puede utilizarse a través del protocolo **FTP**: el espacio de almacenamiento FTP.

Para acceder a este espacio de almacenamiento, puede utilizar un **usuario FTP** y su contraseña asociada.

Este acceso permite, entre otras cosas, [publicar el sitio web](/pages/web_cloud/web_hosting/hosting_how_to_get_my_website_online).

**Descubra cómo cambiar la contraseña de un usuario FTP en un alojamiento de OVHcloud.**

> [!warning]
>
La configuración, la gestión y la responsabilidad de los servicios que OVHcloud pone a su disposición recaen sobre usted. Por lo tanto, usted deberá asegurarse de que estos funcionan correctamente.
>
> Ponemos a su disposición esta guía para ayudarle a realizar las tareas más habituales. No obstante, si tiene alguna duda, le recomendamos que contacte con un [proveedor especializado](/links/partner). Nosotros no podremos asistirle. Más información en la sección ["Más información"](#go-further) de esta guía.
>

## Requisitos

- Tener contratado un plan de [hosting de OVHcloud](/links/web/hosting).
- Haber iniciado sesión en el [área de cliente de OVHcloud](/links/manager).

## Procedimiento

### Etapa 1: Acceder a la gestión de los usuarios FTP

Conéctese al [área de cliente de OVHcloud](/links/manager), acceda a la sección `Web Cloud`{.action}, haga clic en `Alojamientos`{.action} y seleccione el alojamiento correspondiente. Seleccione la pestaña `FTP-SSH`{.action}.

Se mostrará una tabla con los *usuarios FTP* creados en su alojamiento web. Estos usuarios le permiten acceder a su espacio de almacenamiento FTP para publicar los archivos de su sitio web. Al instalar el alojamiento web, se crea un usuario automáticamente.

### Etapa 2: Cambiar la contraseña de un usuario FTP

> [!primary]
>
> Para más información sobre las buenas prácticas de gestión de contraseñas, consulte esta [guía](/pages/account_and_service_management/account_information/manage-ovh-password).
>

Según el plan de [hosting de OVHcloud](/links/web/hosting), la modificación de la contraseña del usuario FTP a través de la pestaña `FTP-SSH`{.action} se realizará por dos caminos diferentes:

- **productos que no permiten crear un segundo usuario FTP** (*Personal*): haga clic en el *pictograma con forma de lápiz* en la columna `Contraseña`{.action} de la tabla que aparece, introduzca la nueva contraseña **respetando la política de contraseñas** y luego confirme el cambio haciendo clic en *botón verde* de validación.

![change-ftp-password-step1-perso](/pages/assets/screens/control_panel/product-selection/web-cloud/web-hosting/ftp-ssh/change-password-perso.png){.thumbnail}

- **Planes que permiten crear varios usuarios FTP** (planes *Pro* y *Performance*): pulse el botón `...`{.action} a la derecha del usuario FTP correspondiente y luego `Cambiar la contraseña`{.action}. Se abrirá una ventana en la que deberá introducir la nueva contraseña **respetando la política de contraseñas**, confirmarla introduciéndola por segunda vez y haciendo clic en el botón `Aceptar`{.action}.

![change-ftp-password-pro](/pages/assets/screens/control_panel/product-selection/web-cloud/web-hosting/ftp-ssh/change-password-pro.png){.thumbnail}

> [!primary]
>
> La nueva contraseña debe respetar la **política de las siguientes contraseñas** :
>
>- Mínimo 8 caracteres;
>- Máximo 30 caracteres;
>- Al menos una letra mayúscula;
>- Al menos una letra minúscula;
>- Al menos una cifra.
>- Estar compuesto únicamente por números y letras.

Por último, abra la pestaña `Tareas en curso`{.action} y vuelva a actualizar la página periódicamente. El cambio de contraseña tarda unos minutos en aplicarse.

### Etapa 3: Acceder al espacio de almacenamiento

Para acceder a su espacio de almacenamiento FTP, consulte nuestra guía ["Conectarse al espacio de almacenamiento de un alojamiento web"](/pages/web_cloud/web_hosting/ftp_connection).

## Más información <a name="go-further"></a>

[Establecer y gestionar la contraseña de su cuenta](/pages/account_and_service_management/account_information/manage-ovh-password)

[Conectarse al espacio de almacenamiento de un alojamiento web](/pages/web_cloud/web_hosting/ftp_connection)

[Publicar el sitio web](/pages/web_cloud/web_hosting/hosting_how_to_get_my_website_online)

Para servicios especializados (posicionamiento, desarrollo, etc.), contacte con [partners de OVHcloud](/links/partner).

Si quiere disfrutar de ayuda para utilizar y configurar sus soluciones de OVHcloud, puede consultar nuestras distintas soluciones [pestañas de soporte](/links/support).

Interactúe con nuestra [comunidad de usuarios](/links/community).