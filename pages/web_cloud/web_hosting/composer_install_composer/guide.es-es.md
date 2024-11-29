---
title: "Instalar Composer en un alojamiento web"
excerpt: "Descubra cómo instalar y dar los primeros pasos en Composer"
updated: 2023-02-24
---

## Objetivo

[Composer](https://getcomposer.org/){.external} es un gestor de dependencias creado para el lenguaje PHP. Permite a los desarrolladores de PHP incluir librerías externas en sus programas. "Composer" ha permitido a los proyectos PHP facilitar la distribución de librerías y el mantenimiento de su código. Además, desde la creación de esta herramienta, se han propuesto numerosas buenas prácticas de desarrollo en el seno de la comunidad PHP y han mejorado las librerías de la comunidad PHP. Estas buenas prácticas se documentan en forma de [PSR](http://www.php-fig.org/){.external}.

**Cómo instalar y dar los primeros pasos en Composer**

> [!warning]
>
La configuración, la gestión y la responsabilidad de los servicios que OVHcloud pone a su disposición recaen sobre usted. Por lo tanto, usted deberá asegurarse de que estos funcionan correctamente.
> 
> Ponemos a su disposición esta guía para ayudarle a realizar las tareas más habituales. No obstante, si necesita ayuda, le recomendamos que contacte con un [proveedor especializado](/links/partner) o con el editor del servicio. Nosotros no podremos asistirle. Más información en la sección ["Más información"](#go-further) de este tutorial.
> 

## Requisitos

- Tener contratado un [plan de hosting](/links/web/hosting){.external} con acceso SSH.
- Haber iniciado sesión en el [área de cliente de OVHcloud](/links/manager){.external}.

## Procedimiento

Conéctese a su alojamiento compartido por SSH con ayuda de nuestra guía sobre [el uso del SSH con su alojamiento web de OVHcloud](/pages/web_cloud/web_hosting/ssh_on_webhosting).

Compruebe que utiliza una versión de PHP compatible en línea de comandos:

```bash
php —version
```

Si no es la versión correcta, puede configurar un alias:

```bash
alias php='/usr/local/php8.0/bin/php'
```

Le recomendamos que permanezca en la carpeta raíz de su alojamiento para no hacer públicos los archivos de Composer. Ejecute el siguiente comando:

```bash
curl -sS https://getcomposer.org/installer | php
```

"Composer" ya está disponible en su alojamiento compartido.

### Ejemplos de uso

Si desea instalar **Symfony 2**, puede por ejemplo ejecutar el siguiente comando:

```bash
php composer.phar create-project symfony/framework-standard-edition my_project_name "2.7.*"
```

También puede utilizar la API de OVHcloud desde su alojamiento utilizando el wrapper oficial. Para ello, añada un archivo llamado *composer.json* que contiene la lista de dependencias que necesite. Este es un ejemplo de este archivo con el wrapper de la API de OVHcloud:

```json
1. {
2.     "name": "Ejemplo Application",
3.     "description": "This is an ejemplo of OVHcloud APIs wrapper usage",
4.     "require": {
5.         "ovh/ovh": "1.1.*"
6.     }
7. }
```

Para instalarlo, ejecute el siguiente comando en la misma carpeta:

```bash
php composer.phar install
```

Para utilizar esta librería, consulte la documentación y el código, disponibles en [GitHub](https://github.com/ovh/php-ovh){.external}

## Más información <a name="go-further"></a>

Para servicios especializados (posicionamiento, desarrollo, etc.), contacte con [partners de OVHcloud](/links/partner).

Si quiere disfrutar de ayuda para utilizar y configurar sus soluciones de OVHcloud, puede consultar nuestras distintas soluciones [pestañas de soporte](/links/support).

Interactúe con nuestra [comunidad de usuarios](/links/community).