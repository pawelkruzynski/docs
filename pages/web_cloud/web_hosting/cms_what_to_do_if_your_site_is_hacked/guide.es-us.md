---
title: "Casos de uso - Asesoramiento sobre la piratería de su sitio web"
excerpt: "Descubra nuestros consejos para reparar su sitio web pirateado"
updated: 2022-11-15
---
  
## Objetivo

Este tutorial le ayudará cuando vea que su sitio web ha sido pirateado. A continuación puede consultar **los cuatro pasos que debe seguir** para corregir esta situación.

La piratería informática puede manifestarse de varias maneras (lista no exhaustiva):

- su sitio web ya no se muestra correctamente o ya no, sin ningún cambio (FTP, SQL o DNS) por su parte;
- el sitio web será redirigido a otro sitio web.
- su sitio web genera "anuncios" intempestivos (pop-ups, ventanas de error, etc.).
- la base de datos del sitio web se rellena de repente.
- usted recibe SPAM generados por scripts infectados desde su alojamiento.

**Descubra nuestros consejos para reparar su sitio web pirateado.**

> [!warning]
>
La configuración, la gestión y la responsabilidad de los servicios que OVHcloud pone a su disposición recaen sobre usted. Por lo tanto, usted deberá asegurarse de que estos funcionan correctamente.
> 
> Ponemos a su disposición este tutorial para ayudarle lo mejor posible en tareas habituales. No obstante, si tiene alguna duda, le recomendamos que contacte con un [proveedor especializado](/links/partner). Nosotros no podremos asistirle. Más información en la sección ["Más información"](#go-further) de esta guía.
>

## Requisitos

- Disponer de un [plan de hosting Cloud](/links/web/hosting) con su sitio web alojado en él.
- Estar conectado a su [área de cliente de OVHcloud](/links/manager).

## Procedimiento

La piratería de un sitio web siempre está vinculada a **al menos** uno de los siguientes puntos:

- falta de actualizaciones del sitio web;
- un programa espía presente en uno de los dispositivos que utiliza para administrar su sitio web;
- el uso de un plugin o un tema "no oficial", especialmente si utiliza un content managment system (CMS) como WordPress, Joomla, PrestaShop o Drupal.
- contraseñas (FTP, SQL, "back-office" para los CMS, etc.) demasiado cortas o fáciles de encontrar, especialmente cuando nunca se han cambiado;
- un script de su sitio web que abre deliberadamente puertos al nivel de su alojamiento web **sin** verificar lo que reciben estos puertos;
- los permisos de acceso FTP CHMOD son demasiado permisivos.

**La piratería de un sitio web no se debe a un fallo de seguridad del alojamiento web.** Solo los scripts o archivos alojados en él pueden dar órdenes al alojamiento. Pueden pedirle o no que abra algunos puertos de acceso cerrados por defecto o que ejecute o no ciertas acciones.<br>
Los scripts ordenan, el alojamiento ejecuta.

### Etapa 1 - escanear todos sus dispositivos

Realice un análisis antivirus y antispyware de todos los dispositivos (PC, Mac, smartphone/Iphone, tableta...) desde los que gestione la administración o la gestión de su sitio web.

> [!warning]
>
Si utiliza dispositivos que funcionan en *Linux*, *Mac OS* u otros sistemas operativos para los que se especifica comúnmente que no hay riesgo de tener un virus o un programa "espía", **realice de todos modos este análisis**.
>
> **Ningún sistema operativo es inmune al software/virus maliciosos.**
>

> [!success]
>
> Le recomendamos que utilice varios antivirus/antispywares (gratuitos o de pago) para cada uno de sus dispositivos.
> Efectivamente, algunos virus o spywares pueden persistir en función del programa antivirus utilizado.
> Existen versiones antivirus/antispywares que puede instalar "en local" en su dispositivo o utilizar directamente "en línea" en internet.
>

Si se encuentra un virus o un programa espía, deberá eliminarlo del software anti-virus/antispyware **antes** para pasar a la siguiente etapa.

### Etape 2 - modificar sus contraseñas <a name="step2"></a>

Una vez que haya pirateado un sitio web, modifique todas las contraseñas relacionadas con él por motivos de precaución.

En cuanto a OVHcloud, utilice nuestra documentación para:

- [Cambiar la contraseña de acceso a su ID de cliente de OVHcloud](/pages/account_and_service_management/account_information/manage-ovh-password).
- [Proteger el acceso a su área de cliente de OVHcloud con doble autenticación](/pages/account_and_service_management/account_information/secure-ovhcloud-account-with-2fa).
- [Cambiar la contraseña de acceso al espacio de almacenamiento FTP de su alojamiento web](/pages/web_cloud/web_hosting/ftp_change_password).
- [Cambiar la contraseña de acceso a la base de datos](/pages/web_cloud/web_hosting/sql_change_password).

También le recomendamos que utilice un [gestor de contraseñas](/pages/account_and_service_management/account_information/manage-ovh-password#utilizar-un-gestor-de-contrasenas).

> [!warning]
> 
> Cambiando la contraseña de la base de datos, no olvide actualizar también la contraseña en el archivo de configuración de su sitio web. En caso contrario, se interrumpirá el enlace entre la base de datos y los archivos presentes en el espacio de almacenamiento FTP de su alojamiento web y su sitio web mostrará un "error al conectarse a la base de datos".
>

> [!primary]
>
Si utiliza un CMS como WordPress, Joomla, PrestaShop o Drupal, consulte la documentación oficial de su CMS para cambiar la contraseña de acceso al área de administración del CMS ("backup").
>

### Etapa 3 - buscar los archivos maliciosos y los fallos de seguridad

> [!warning]
>
Si tiene dificultades para realizar las acciones que se describen a continuación, contacte con un [proveedor especializado](/links/partner) en ciberseguridad.
>

Utilice nuestra guía sobre [las estadísticas y logs de su alojamiento web](/pages/web_cloud/web_hosting/logs_and_statistics) para buscar los elementos maliciosos introducidos en su sitio web. Puede consultar la información en los logs "web". 

Comience a buscar a partir de la fecha en la que haya detectado la piratería y vuelva al historial de sus logs.

Identifique las peticiones POST que salen de lo normal. Por lo general, los archivos maliciosos tienen nombres alfanuméricos sin ningún significado especial (**ejemplos** : az78e4jFn.txt, oij8bh4.html, udh73hd45.php, mlkjc23d.js...).

Identifique la dirección IP que ha realizado la solicitud maliciosa. A continuación, busque la dirección en sus logs para ver todas las acciones que la IP solicita en su sitio web.

> [!primary]
>
> Generalmente, varias direcciones IP maliciosas denominan, durante el mismo período, los scripts maliciosos presentes como consecuencia de la piratería.
> An [OVHcloud web hosting plan]alice todos los logs de su alojamiento.
>

Suba los fallos de seguridad en su sitio web y, al mismo tiempo, enumere los archivos maliciosos que encontrará.

> [!success]
>
> Varios sitios web (no gestionados por OVHcloud) le permiten obtener información sobre las IP maliciosas. Puede utilizar uno de ellos para recuperar información como el proveedor de la IP, su geolocalización, el gestor, etc.
>
> Si está absolutamente seguro de que se trata de una IP maliciosa, puede bloquearle el acceso a su alojamiento siguiendo nuestra documentación sobre las [restricciones de acceso a través del archivo ".htaccess"](/pages/web_cloud/web_hosting/htaccess_how_to_block_a_specific_ip_address_from_accessing_your_website).
> 

### Etapa 4 - eliminar los elementos maliciosos y corregir los fallos de seguridad

Para ello, se pueden realizar tres acciones: 

> [!alert]
>
> **Importante**: En cualquier caso, si elimina los códigos maliciosos sin corregir los fallos de seguridad, el pirata informático podría volver a utilizarlos para volver a introducir código malicioso en su alojamiento. Incluso podría crear una nueva puerta trasera.
>
> La restauración a una fecha anterior a la piratería requiere una actualización **inmediata** y la realización indispensable de una **auditoría de seguridad**, para identificar todos los fallos de seguridad.
>

#### Caso n°1 - OVHcloud dispone de una copia de seguridad de su sitio web (espacio de almacenamiento FTP y base de datos)

En función de la fecha de hackeo de su sitio web (menos de 14 días), OVHcloud puede ofrecerle una copia de seguridad (no contractual).

Para ello, consulte nuestras 3 guías sobre el tema:

- [Restaurar el espacio de almacenamiento FTP de su alojamiento web](/pages/web_cloud/web_hosting/ftp_save_and_backup)
- [Descargar la copia de seguridad SQL de su base de datos](/pages/web_cloud/web_hosting/sql_database_export)
- [Importar la copia de seguridad SQL en la base de datos](/pages/web_cloud/web_hosting/sql_importing_mysql_database)

Ajuste al máximo las fechas de restauración de su espacio de almacenamiento FTP y su base de datos SQL.

>[!warning]
>
> OVHcloud dispone de robots de seguridad que pueden detectar acciones maliciosas realizadas desde su alojamiento. que desactivan el alojamiento y le informan por correo electrónico de que el alojamiento ha sido desactivado.
> Para completar el email, la página "403 Forbidden" aparece por lo general cuando intenta acceder al sitio web.
>
Si el alojamiento está "desactivado", también se desactivarán los robots de restauración automática disponibles desde el [área de cliente de OVHcloud](/links/manager).
> Deberá restaurar el sitio web "manualmente", eliminar los elementos maliciosos residuales y corregir todos los fallos de seguridad presentes en el snapshot. Realice esta acción **antes** de reactivar el alojamiento.
>
> Para reactivar el alojamiento web, siga las indicaciones del apartado 4 de esta [guía](/pages/web_cloud/web_hosting/diagnostic_403_forbidden).
>

Su sitio web debería reaparecer si estas acciones se han realizado correctamente.

#### Caso n°2 - dispone de su propia copia de seguridad anterior al pirateo

Para ello, consulte nuestras 2 guías:

- [Restaurar el espacio de almacenamiento FTP de su alojamiento web](/pages/web_cloud/web_hosting/ftp_save_and_backup)
- [Importar la copia de seguridad SQL en la base de datos](/pages/web_cloud/web_hosting/sql_importing_mysql_database)

>[!warning]
>
> OVHcloud dispone de robots de seguridad que pueden detectar acciones maliciosas realizadas desde su alojamiento. que desactivan el alojamiento y le informan por correo electrónico de que el alojamiento ha sido desactivado.
> Para completar el email, la página "403 Forbidden" aparece por lo general cuando intenta acceder al sitio web.
>
Si el alojamiento está en estado "desactivado", realice una restauración "manual" del sitio web, elimine los elementos maliciosos residuales y corrija todos los fallos de seguridad presentes en el backup. Realice esta acción **antes** de reactivar el alojamiento..
>
> Para reactivar el alojamiento web, siga las indicaciones del apartado 4 de esta [guía](/pages/web_cloud/web_hosting/diagnostic_403_forbidden).
>

Su sitio web debería reaparecer si estas acciones se han realizado correctamente.

#### Caso n°3 - No hay ninguna copia de seguridad disponible para su sitio web

Deberá eliminar manualmente los archivos y códigos maliciosos detectados anteriormente en [el paso 2](#step2) de esta guía y corregir los fallos de seguridad de su sitio web.

Para conectarse al espacio de almacenamiento de su alojamiento, consulte [nuestra guía](/pages/web_cloud/web_hosting/ftp_connection) sobre el asunto.

> [!warning]
>
> OVHcloud dispone de robots de seguridad que pueden detectar acciones maliciosas realizadas desde su alojamiento. que desactivan el alojamiento y le informan por correo electrónico de que el alojamiento ha sido desactivado.
> Para completar el email, la página "403 Forbidden" aparece por lo general cuando intenta acceder al sitio web.
>
Si su alojamiento está en estado "desactivado", elimine los elementos maliciosos residuales y corrija todos los fallos de seguridad presentes en la copia de seguridad **antes** de reactivar el alojamiento.
>
> Para reactivar el alojamiento web, siga las indicaciones del apartado 4 de esta [guía](/pages/web_cloud/web_hosting/diagnostic_403_forbidden).
>

Su sitio web debería reaparecer si estas acciones se han realizado correctamente.

### Etapa 5 - Actualizar el sitio web

Actualice su sitio web al nivel de su código fuente, de los parámetros de seguridad de que dispone, de las versiones de lenguaje que utiliza (especialmente PHP).

Compruebe los permisos de acceso FTP CHMOD para cada una de sus carpetas y archivos alojados en su espacio de almacenamiento.
Por defecto, le recomendamos que utilice al máximo los permisos "CHMOD" **705** para las carpetas y **604** para los archivos.
Para más información sobre los permisos CHMOD, consulte la sección "Información útil" de nuestro [tutorial sobre el uso del cliente FTP Filezilla](/pages/web_cloud/web_hosting/ftp_filezilla_user_guide#useful-information).

Si utiliza un CMS (WordPress, Joomla, PrestaShop, Drupal...), actualice sus plugins, su tema y el CMS en sí mismo.
Apueste por utilizar plugins o temas "oficiales" y mantenga actualizado su sitio web con la mayor regularidad posible y de forma completa.

Proteja sus formularios de contacto al menos con un sistema de tipo "Captcha", para evitar que robots maliciosos emitan spam por este medio. Si la función "mail()" de PHP también ha sido bloqueada en su alojamiento, consulte [nuestra guía](/pages/web_cloud/web_hosting/mail_function_script_records) sobre este asunto para solucionar el bloqueo.

Consulte nuestra guía sobre cómo proteger su sitio web (/pages/web_cloud/web_hosting/secure_your_website) para reducir al mínimo el riesgo de que se produzca una nueva piratería.

## ## Más información <a name="go-further"></a>

[Conectarse al espacio de almacenamiento de un alojamiento web](/pages/web_cloud/web_hosting/ftp_connection)

[Modificar la configuración de un alojamiento web](/pages/web_cloud/web_hosting/configure_your_web_hosting)

[Activar el firewall de aplicación](/pages/web_cloud/web_hosting/multisites_activating_application_firewall)

[Optimizar el rendimiento de su sitio web](/pages/web_cloud/web_hosting/optimise_your_website_performance)

Para servicios especializados (posicionamiento, desarrollo, etc.), contacte con [partners de OVHcloud](/links/partner).

Si quiere disfrutar de ayuda para utilizar y configurar sus soluciones de OVHcloud, puede consultar nuestras distintas soluciones (pestañas de soporte)(/links/support).

Interactúe con nuestra [comunidad de usuarios](/links/community).