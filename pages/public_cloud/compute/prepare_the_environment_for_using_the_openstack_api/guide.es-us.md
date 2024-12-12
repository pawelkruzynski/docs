---
title: 'Preparar el entorno para utilizar la API de OpenStack'
excerpt: 'Cómo instalar el entorno OpenStack para controlar las instancias a través de la API'
updated: 2024-12-05
---

## Objetivo

Después de descargar e instalar los componentes de OpenStack, es posible utilizar la consola del sistema para administrar los servicios de Public Cloud mediante comandos.

Con la API de OpenStack puede generar scripts para automatizar la administración.

> [!primary]
>
> OpenStack requiere Python >=3.8.
> Esta guía describe la instalación del paquete `python-openstackclient`, que agrupa la línea de comandos para la mayoría de los proyectos de OpenStack.
> El proyecto Octavia (que impulsa el `Public Cloud Load Balancer`) no está incluido. Por lo tanto, debe ejecutar `pip3 install python-octaviaclient` además de las instrucciones de instalación que se encuentran a continuación..
> Del mismo modo, si utiliza el proyecto Barbican para gestionar secretos, el comando `pip3 install python-barbicanclient` también debe añadirse al procedimiento que se indica a continuación.

**Esta guía explica cómo instalar estas herramientas de OpenStack.**

## Requisitos

- Tener acceso *root* al entorno que quiera configurar.

## Procedimiento

### En Debian

Abra el terminal o conéctese por SSH al entorno que quiera preparar.

Actualice la caché de los paquetes con el siguiente comando:

```sh
apt update
```

Utilice el siguiente comando para instalar los clientes OpenStack:

```sh
$ apt install python3-pip python3-venv -y
$ python3 -m venv env
$ source env/bin/activate
(env)$ pip3 install --upgrade pip
(env)$ pip3 install python-openstackclient
```

Una vez hecho esto, le recomendamos que cree un usuario específico para no utilizar el usuario *root*.

Para acceder a las herramientas de ayuda, ejecute el siguiente comando:

```sh
openstack --help
```

> [!primary]
> 
> En [esta página](https://docs.openstack.org/python-openstackclient/latest/){.external} encontrará la documentación relativa a la API de OpenStack.
> 

### En CentOS

Abra el terminal o conéctese por SSH al entorno que quiera preparar.

Actualice la caché de los paquetes mediante el siguiente comando:

```sh
yum update -y
```

Utilice el siguiente comando para instalar los clientes OpenStack:

```sh
yum install python3-pip -y
$ python3 -m venv env
$ source env/bin/activate
(env)$ pip3 install --upgrade pip
(env)$ pip3 install python-openstackclient
```

Una vez hecho esto, le recomendamos que cree un usuario específico para no utilizar el usuario *root*.

Para acceder a las herramientas de ayuda, ejecute el siguiente comando:

```sh
openstack --help
```

> [!primary]
> 
> En [esta página](https://docs.openstack.org/python-openstackclient/latest/){.external} encontrará la documentación relativa a la API de OpenStack.
> 

### En Windows

Descargue e instale la versión 3.12.0 de Python. Puede añadir automáticamente el lenguaje de programación Python a Path seleccionando la opción correspondiente en el configurador de la instalación.

![Instalación automática](images/1_preparation_openstack_environment_windows.png){.thumbnail}

Alternativamente, también puede realizar la instalación usted mismo. Para ello, siga las indicaciones que se ofrecen a continuación.

#### 1. Editar las variables de entorno del sistema

Comience a introducir «Editar las variables de entorno del sistema» en el campo de búsqueda y seleccione el menú cuando aparezca. Se abrirá la ventana **Propiedades del sistema**.

![Elección de las variables de entorno](images/2_preparation_openstack_environment_windows.png){.thumbnail}

#### 2. Editar la configuración del sistema

En la pestaña `Opciones avanzadas`{.action}, haga clic en el botón `Variables de entorno`{.action} para editar su configuración.

![Configuración de las variables de entorno](images/3_preparation_openstack_environment_windows.png){.thumbnail}

#### 3. Configurar las variables de entorno 

En el apartado **Variables del sistema**, haga clic en  `Nueva...`{.action}, asígnele el nombre `PYTHON_HOME` y añada la ruta hacia Python.

![Introducción de la ruta de acceso](images/4_edit_system_variables.png){.thumbnail}

#### 4. Introducir la ruta de las variables

Una vez que haya añadido Python, seleccione `Path`{.action} (ruta) en las variables del sistema y haga clic en el botón `Editar...`{.action}. Añada lo siguiente al final de la ruta:

`...;%PYTHON_HOME%\;%PYTHON_HOME%\Script`

#### 5. Reiniciar Windows

Es necesario reiniciar el sistema para que se apliquen los cambios.

#### 6. Instalar el cliente OpenStack

Estando conectado como administrador, escriba «cmd» en el campo de búsqueda y seleccione el símbolo del sistema cuando aparezca. Instale el cliente OpenStack utilizando el siguiente comando:

```sh
pip install python-openstackclient
```

Si la operación se ha realizado correctamente, se mostrará un resumen.

![Instalación automática](images/5_preparation_openstack_environment_windows.png){.thumbnail}

En el símbolo del sistema puede comprobar la versión instalada introduciendo `python-V` (no importa en qué directorio se encuentre).

![Verificación](images/6_preparation_openstack_environment_windows.png){.thumbnail}

### En MacOS

Puede utilizar [HomeBrew](https://brew.sh), un gestor de paquetes para MacOS.

Abra el terminal e ejecute el siguiente comando:

```bash
brew install openstackclient
```

Para acceder a las herramientas de ayuda, ejecute el siguiente comando:

```sh
openstack —-help
nova help
```

## Más información

[Cargar las variables de entorno necesarias para OpenStack](/pages/public_cloud/compute/loading_openstack_environment_variables).

Únase a nuestra comunidad de usuarios en <https://community.ovh.com/en/>.
