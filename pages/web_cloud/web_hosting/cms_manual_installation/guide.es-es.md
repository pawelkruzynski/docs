---
title: "Tutorial - Instalar manualmente un CMS en mi alojamiento"
excerpt: "Descubra cómo instalar manualmente un CMS en un alojamiento"
updated: 2024-03-28
---

## Objetivo

Esta guía explica cómo instalar manualmente un CMS (del inglés content management system), como WordPress, Joomla!, Drupal, PrestaShop, Pico, Grav, Typo3 o SPIP en pocos pasos.

> [!warning]
>
La configuración, la gestión y la responsabilidad de los servicios que OVHcloud pone a su disposición recaen sobre usted. Por lo tanto, usted deberá asegurarse de que estos funcionan correctamente.
> 
> Ponemos a su disposición este tutorial para ayudarle lo mejor posible en tareas habituales. No obstante, si necesita ayuda, le recomendamos que contacte con un [proveedor especializado](/links/partner) o con el editor del CMS que haya elegido instalar. Nosotros no podremos asistirle. Más información en la sección ["Más información"](#go-further) de este tutorial.
>
> Para contactar con los diferentes editores de los CMS mencionados, consulte los enlaces a sus páginas oficiales respectivas:
>
> - [WordPress](https://wordpress.com/support/){.external}
> - [Joomla!](https://www.joomla.org/){.external}
> - [Drupal](https://www.drupal.org/){.external}
> - [PrestaShop](https://www.prestashop.com/en/support){.external}
> - [Pico](https://picocms.org/){.external}
> - [Grav](https://getgrav.org/){.external}
> - [Typo3](https://typo3.com/){.external}
> - [SPIP](https://www.spip.net/en_rubrique25.html){.external}
>

> [!success]
>
> Para instalar su CMS **automáticamente** desde su [área de cliente de OVHcloud](/links/manager), consulte nuestra documentación sobre la instalación de un módulo en un clic](/pages/web_cloud/web_hosting/cms_install_1_click_modules).
>

**Descubra cómo configurar su sitio web instalando manualmente un CMS.**
  
## Requisitos

- Tener contratado un [plan de hosting de OVHcloud](/links/web/hosting) que contenga al menos una base de datos.
- Disponer de un [dominio](/links/web/domains)
- Estar conectado al [área de cliente de OVHcloud](/links/manager)
  
## Procedimiento

### Presentación de los CMS

Para ayudarle a elegir su CMS, consulte a continuación una breve descripción para cada uno de los CMS anteriores.

#### WordPress

**WordPress** suele utilizarse para crear un sitio web o blog. Está basado en la tecnología PHP y cuenta con una gran variedad de herramientas, como un corrector ortográfico y plugins para el e-commerce, el SEO o la seguridad de su sitio web.

Más información en nuestra página relativa a [módulo WordPress](/links/web/hosting-wordpress)

- Sitio oficial de [WordPress](https://wordpress.com/){.external}

#### Joomla!

**Joomla!** es un CMS que permite crear sitios web y aplicaciones web de alto rendimiento.

La comunidad **Joomla!** es muy grande y puede prestar asistencia y servicios en todos los ámbitos relacionados con este CMS (ayuda, documentación, asistencia técnica, temas, etc.).

Más información en nuestra página relativa a [Joomla!](/links/web/hosting-joomla)

- Sitio oficial de [Joomla!](https://www.joomla.org/){.external}

#### Drupal

**Drupal** es una plataforma open source gratuita con PHP creada en 2000. **Drupal** permite crear rápidamente sitios web dinámicos.

Más información en nuestra página relativa a [Drupal](/links/web/hosting-drupal)

- Sitio oficial de [Drupal](https://www.drupal.org/){.external}

#### PrestaShop

CMS creado en 2005 y dedicado a la creación de sitios web de e-commerce. Fuera de las funcionalidades habituales de las tiendas en linea, este software también puede personalizarse con módulos, temas y modelos. 

Más información en nuestra página relativa a [PrestaShop](/links/web/hosting-prestashop)

- Sitio oficial de [PrestaShop](https://www.prestashop.com/){.external}

#### Pico

**Pico** es un CMS ligero basado en PHP, ideal para crear sitios web o blogs. Sin base de datos, utiliza archivos Markdown para administrar el contenido. Soporta extensiones para personalizar su sitio web.

- Sitio web oficial de [Pico](https://picocms.org/){.external}

#### Grav

**Grav** es un CMS moderno y flexible basado en PHP. Está diseñado sin base de datos y utiliza archivos Markdown para el almacenamiento y la gestión de contenido. Grav se distingue por su sistema de gestión de paquetes que facilita la instalación y la actualización de los plugins y temas para su sitio web.

- Sitio web oficial de [Grav](https://getgrav.org/){.external}

#### Typo3

**Typo3** es un CMS basado en PHP, diseñado para el desarrollo de sitios web de todos los tamaños, desde pequeñas hasta grandes empresas. Se basa en una base de datos para almacenar el contenido. Ofrece una amplia gama de extensiones para ampliar sus funcionalidades y personalizar su sitio web.

- Sitio web oficial de [Typo3](https://typo3.com/){.external}

#### SPIP

**SPIP** es un CMS diseñado principalmente para la publicación y la gestión de sitios web editoriales como periódicos o revistas en línea. Basado en PHP y basado en una base de datos SQL, facilita la creación de sitios web enriquecidos con contenido textual, gráfico y/o multimedia.

- Sitio oficial de [SPIP](https://www.spip.net/en_rubrique25.html){.external}

> [!warning]
>
> No importa cuál sea el CMS que elija, le recordamos que OVHcloud no proporciona soporte sobre el uso de estos CMS. Si necesita ayuda, contacte directamente con el editor del CMS que haya elegido utilizando los enlaces que se indican más arriba en este tutorial.
>

### Etapa 1 - preparar la instalación <a name="step1"></a>

Para instalar un CMS en su [plan de hosting](/links/web/hosting), es necesario realizar algunos preparativos.

#### 1.1 - Comprobar la declaración de la "carpeta raíz"

La carpeta raíz corresponde al directorio en el que se instalará el futuro CMS en el alojamiento. Le recomendamos que elija un directorio vacío para evitar conflictos con otros posibles multisitios.

Consulte nuestra guía sobre [cómo añadir un multisitio a un alojamiento web](/pages/web_cloud/web_hosting/multisites_configure_multisite) para determinar la carpeta raíz que debe utilizar con su CMS.

> [!primary]
>
> Si define un nombre de "carpeta raíz" que no existe en su alojamiento web, se creará automáticamente en el espacio de almacenamiento FTP de su alojamiento web.

#### 1.2 - Comprobar el "puntero" del nombre de dominio

- Asegúrese de que el dominio que utilizará para acceder al CMS y el subdominio en "www" apuntan a la dirección IP de su [plan de hosting](/links/web/hosting).

Para obtener la dirección IP de su plan de hosting, conéctese a su [área de cliente de OVHcloud](/links/manager) en la sección `Web Cloud`{.action} y seleccione su plan de hosting en la sección `Alojamientos`{.action}.<br>
En el recuadro `Información general`{.action}, a su derecha, encontrará la dirección IP de su alojamiento web en el formulario `IPv4`{.action}.

Si la zona DNS activa de su dominio está gestionada en su [área de cliente de OVHcloud](/links/manager), compare la dirección IP de su alojamiento con la presente en la zona DNS de su dominio, ayudándole a nuestra documentación sobre las [zonas DNS de OVHcloud](/pages/web_cloud/domains/dns_zone_edit).

> [!warning]
>
> Si ha activado las opciones `CDN`{.action} o `IP del país`{.action} con su dominio, utilice la dirección IP adecuada con nuestra documentación que recoge [todas las direcciones IP de nuestros alojamientos compartidos](/pages/web_cloud/web_hosting/clusters_and_shared_hosting_IP).

Si no puede realizar estas comprobaciones, póngase en contacto con el proveedor de hosting de su zona DNS activa para actualizar el direccionamiento del dominio.

> [!warning]
>
> Todos los cambios realizados en la zona DNS conllevan un plazo de propagación de entre 4 y 24 horas.
>

- Obtenga [la información necesaria para conectarse al espacio FTP de su alojamiento web](/pages/web_cloud/web_hosting/ftp_connection#1-obtener-los-datos-de-conexion).
- Consulte los accesos a la base de datos de su plan de hosting, si ya existe, o cree una con ayuda de [documentación](/pages/web_cloud/web_hosting/sql_create_database).

#### 1.3 - Instalar el cliente FTP gratuito "FileZilla"

Si todavía no utiliza un cliente FTP, puede utilizar Filezilla. Consulte la página de descarga gratuita y el tutorial sobre su uso en nuestra documentación sobre el [uso de FileZilla en el alojamiento de OVHcloud](/pages/web_cloud/web_hosting/ftp_filezilla_user_guide).

> [!primary]
>
> Existen otros clientes FTP que puede utilizar, por ejemplo, Cyberduck. Para más información, consulte nuestra guía relativa al [uso de Cyberduck con el plan de hosting de OVHcloud](/pages/web_cloud/web_hosting/ftp_cyberduck_user_guide_on_mac).
>

#### 1.4 - Preparar una base de datos <a name="step1-4"></a>

> [!warning]
>
> Algunos CMS funcionan sin bases de datos. Si es el caso del CMS que quiere instalar, omita este paso.
>

La mayoría de los CMS necesitan una base de datos para funcionar. Nuestros [planes de hosting](/links/web/hosting) contienen, a excepción de [Alojamiento gratuito 100M](/links/web/domains-free-hosting).

Utilice nuestra guía para [crear una base de datos desde su plan de hosting](/pages/web_cloud/web_hosting/sql_create_database).

Si tiene un plan Web Cloud Databases en MySQL o MariaDB y quiere utilizarlo para instalar manualmente su CMS, consulte nuestra documentación sobre la [creación de una base de datos en un servicio Web Cloud Databases](/pages/web_cloud/web_cloud_databases/create-db-and-user-on-db-server).

Una vez que haya creado la base de datos, deberá descargar los parámetros de conexión (servidor, nombre de la base de datos, nombre de usuario y contraseña) y conservarlos para [el etapa 3](#step3) de esta guía.

> [!primary]
>
> Si desea instalar su CMS con una base de datos ya existente, recupere los parámetros de conexión a su base de datos directamente en los archivos del sitio web asociados a esta.
>
> Si también se trata de un CMS idéntico al que tiene que instalar, puede utilizar [esta guía](/pages/web_cloud/web_hosting/sql_change_password#etapa-3-cambiar-la-contrasena-de-la-base-de-datos-del-sitio-web-en-el-archivo-de-configuracion) para identificar los archivos de configuración en su [espacio de almacenamiento FTP](/pages/web_cloud/web_hosting/ftp_connection).
>
> Conéctese a la base de datos para identificar los "prefijos" de las tablas que ya están en su interior. para no elegir un "prefijo" de tabla que ya utilice otro sitio web.
>
> - Para conectarse a la base de datos asociada a su plan de hosting, consulte [esta guía](/pages/web_cloud/web_hosting/sql_create_database#acceder-a-la-interfaz-phpmyadmin).
> - Para conectarse a una base de datos en un databases de Web Cloud, consulte [esta guía](/pages/web_cloud/web_cloud_databases/connecting-to-database-on-database-server).
>

### Etapa 2 - iniciar la instalación manual

#### 2.1 - Obtener los archivos de origen de su CMS

Acceda a la web del editor del CMS que haya elegido para descargar los archivos de origen.

A continuación se muestran los enlaces a las páginas de descarga de los CMS que figuran en el presente tutorial:

- [WordPress](https://wordpress.org/download/#download-install){.external}
- [Joomla!](https://downloads.joomla.org/){.external}
- [Drupal](https://www.drupal.org/download){.external}
- [Prestashop](https://www.prestashop.com/en/download){.external}
- [Pico](https://picocms.org/download/){.external}
- [Grav](https://getgrav.org/downloads){.external}
- [Typo3](https://get.typo3.org/#download){.external}
- [SPIP](https://www.spip.net/en_download){.external}

> [!primary]
>
> Recupere la versión PHP y, si su CMS utiliza una base de datos, identifique la versión MySQL o MariaDB necesaria para hacer funcionar su CMS.
>
> Para ello, consulte el enlace a la página oficial del CMS que quiera instalar:

>
> - [WordPress](https://wordpress.org/about/requirements/){.external}
> - [Joomla!](https://downloads.joomla.org/technical-requirements){.external}
> - [Drupal](https://www.drupal.org/docs/getting-started/system-requirements/php-requirements){.external}
> - [Prestashop](https://www.prestashop.com/en/system-requirements){.external}
> - [Pico](https://picocms.org/download/){.external}
> - [Grav](https://learn.getgrav.org/17/basics/requirements){.external}
> - [Typo3](https://docs.typo3.org/m/typo3/tutorial-getting-started/main/en-us/SystemRequirements/Index.html){.external}
> - [SPIP](https://www.spip.net/en_article6659.html){.external}
>
>
> Configure la versión de PHP en su alojamiento web con nuestra guía sobre [el cambio de versión PHP de un alojamiento web](/pages/web_cloud/web_hosting/configure_your_web_hosting).
>
Si ya utiliza una versión de PHP igual o superior a la necesaria, no es necesario realizar ningún cambio.
>

Siga las instrucciones del editor de su CMS hasta que los archivos de origen se carguen a su ordenador y continúe leyendo este tutorial.

> [!warning]
>
> Si tiene otros sitios web alojados en su plan de hosting, compruebe que son compatibles con la versión de PHP que seleccione para su nuevo CMS.
>

#### 2.2 - Descomprimir los archivos fuente descargados en una nueva carpeta

>[!primary]
>
> Para mayor facilidad, sustituya en este paso el nombre de la carpeta "**CMS**" por el nombre del CMS que haya elegido. (**WordPress**, **Joomla!**, **Drupal**, **PrestaShop**, etc.).
>

El archivo descargado está en un formato **comprimido** (zippé). Cree una carpeta llamada "**CMS**" en su ordenador y luego **descomprima** el contenido del archivo descargado en la carpeta "**CMS**".

Para ello, abra la carpeta en la que haya descargado el archivo comprimido, haga clic derecho sobre el archivo en cuestión y seleccione "Extraer todo... ".

Indique la carpeta "**CMS**" en la que quiera descargar los archivos desde esta carpeta.

#### 2.3 - Mover los archivos fuente de la carpeta "CMS" al "directorio raíz" de su alojamiento web

Una vez descomprimidos los archivos en su carpeta "**CMS**", [conéctese por FTP al espacio de almacenamiento](/pages/web_cloud/web_hosting/ftp_connection) utilizando el [cliente FTP FileZilla](/pages/web_cloud/web_hosting/ftp_filezilla_user_guide) y, a continuación, copie los archivos contenidos en la carpeta "**CMS**" en la "carpeta raíz" que haya establecido en su alojamiento durante el [etapa 1](#step1) de esta guía.

A continuación, un ejemplo con el CMS *WordPress*:

![hosting](/pages/assets/screens/other/web-tools/filezilla/ftp-upload-wordpress.png){.thumbnail}

> [!warning]
>
> Le recomendamos encarecidamente que utilice una "carpeta raíz" vacía para evitar conflictos con otro de sus sitios web. Compruebe que la carpeta de destino no contenga ningún elemento antes de mover los archivos.
>

> [!primary]
>
Si la "carpeta raíz" que ha definido no se ha creado automáticamente en las acciones descritas en el [etapa 1](#step1), puede crearla a través de FileZilla.
>
> El almacenamiento de los archivos en el alojamiento puede tardar unos minutos.
>
> Una vez finalizada la transferencia, compruebe que todos los elementos de la carpeta local "**CMS**" se hayan transferido correctamente a la carpeta raíz de su alojamiento web.
>

**Caso Particular**: Si tiene una velocidad de internet limitada y/o un plan de hosting **Pro** o superior, puede utilizar la conexión **SSH** para colocar los archivos de origen de su CMS en el espacio de almacenamiento de su alojamiento web.

Para conectarse a su alojamiento por SSH, consulte nuestra guía sobre la [conexión por SSH desde un alojamiento compartido de OVHcloud](/pages/web_cloud/web_hosting/ssh_on_webhosting).

Una vez que se haya conectado a **SSH**, ejecute los siguientes comandos:

Acceda a la carpeta raíz en la que quiere instalar su CMS en su alojamiento web:

```bash
cd NameOfYourTargetFolder
```

- Consulte los archivos de origen de su CMS directamente desde su "directorio raíz" con el comando correspondiente al CMS que haya elegido:

> [!tabs]
> **WordPress**
>> 
>> ```bash
>> wget http://wordpress.org/latest.tar.gz
>> ```
>>
>> **latest** permite instalar automáticamente la última versión del CMS.
>>
> **Joomla!**
>> 
>> ```bash
>> wget https://downloads.joomla.org/cms/joomla4/4-2-8/Joomla_4-2-8-Stable-Full_Package.tar.gz
>> ```
>> 
>> **Joomla4** y **4-2-8*** coinciden con la última versión de Joomla! disponible.
>> Sustituya estos valores por los valores que desee instalar.
>> 
> **Drupal**
>> 
>> ```bash
>> wget https://ftp.drupal.org/files/projects/admin_toolbar-8.x-2.4.tar.gz
>> ```
>> 
>> **8.x-2.4** corresponde a la última versión de Drupal disponible.
>> Sustituya estos valores por los valores que desee instalar.
>> 
> **PrestaShop**
>> 
>> ```bash
>> wget https://github.com/PrestaShop/PrestaShop/archive/1.7.8.8.tar.gz
>> ```
>> 
>> **1.7.8.8** corresponde a la última versión de PrestaShop disponible.
>> Sustituya estos valores por los valores que desee instalar.
>> 

- Descomprima los archivos de origen de su CMS en la carpeta raíz utilizando el comando correspondiente al CMS que haya elegido:

> [!tabs]
> **WordPress**
>> 
>> ```bash
>> tar xvf latest.tar.gz
>> ```
>> 
> **Joomla!**
>> 
>> ```bash
>> tar xvf Joomla_4-2-8-Stable-Full_Package.tar.gz
>> ```
>> 
> **Drupal**
>> 
>> ```bash
>> tar xvf admin_toolbar-8.x-2.4.tar.gz
>> ```
>> 
> **PrestaShop**
>> 
>> ```bash
>> tar xvf 1.7.8.8.tar.gz
>> ```
>> 

- En la carpeta raíz se crea una carpeta "**CMS**". Mueva su contenido a la base de su carpeta raíz:

```bash
mv CMS/* ./
```

- Elimine la carpeta "**CMS**" ya vacía:

```bash
rmdir ./CMS/
```

- Elimine el archivo comprimido correspondiente al CMS que haya elegido:

> [!tabs]
> **WordPress**
>> ```bash
>> rm -f latest.tar.gz
>> ```
>> 
> **Joomla!**
>> ```bash
>> rm -f Joomla_4-2-8-Stable-Full_Package.tar.gz
>> ```
>> 
> **Drupal**
>> ```bash
>> rm -f admin_toolbar-8.x-2.4.tar.gz
>> ```
>> 
> **PrestaShop**
>> ```bash
>> rm -f 1.7.8.8.tar.gz
>> ```
>> 

### Etapa 3 - Finalizar la instalación manual <a name="step3"></a>

> [!success]
>
> Antes de continuar la instalación, vacíe la caché de su navegador de Internet para evitar cualquier error.
>

A partir de esta etapa, el procedimiento será diferente en función del CMS que haya elegido previamente.

Para continuar con la instalación, siga uno de los siguientes enlaces haciendo clic en la guía correspondiente a su CMS:

- [Finalizar la instalación de WordPress](/pages/web_cloud/web_hosting/cms_manual_installation_wordpress)
- [Finalizar la instalación de Joomla!](/pages/web_cloud/web_hosting/cms_manual_installation_joomla)
- [Finalizar la instalación de Drupal](/pages/web_cloud/web_hosting/cms_manual_installation_drupal)
- [Finalizar la instalación de PrestaShop](/pages/web_cloud/web_hosting/cms_manual_installation_prestashop)
- [Finalizar la instalación de Pico](/pages/web_cloud/web_hosting/cms_manual_installation_pico)
- [Finalizar la instalación de Grav](/pages/web_cloud/web_hosting/cms_manual_installation_grav)
- [Finalizar la instalación de Typo3](/pages/web_cloud/web_hosting/cms_manual_installation_typo3)
- [Finalizar la instalación de SPIP](/pages/web_cloud/web_hosting/cms_manual_installation_spip)

## Más información <a name="go-further"></a>

[Migración de su sitio web y de su correo a OVHcloud](/pages/web_cloud/web_hosting/hosting_migrating_to_ovh)

[Publicar un sitio web en internet en un alojamiento web](/pages/web_cloud/web_hosting/hosting_how_to_get_my_website_online)

[Alojar varios sitios web en un mismo hosting](/pages/web_cloud/web_hosting/multisites_configure_multisite)

Para servicios especializados (posicionamiento, desarrollo, etc.), contacte con [partners de OVHcloud](/links/partner).

Si quiere disfrutar de ayuda para utilizar y configurar sus soluciones de OVHcloud, puede consultar nuestras distintas soluciones [pestañas de soporte](/links/support).

Interactúe con nuestra [comunidad de usuarios](/links/community).