---
title: 'Transferir un dominio .uk a OVHcloud'
excerpt: 'En esta guía encontrará información relativa a la transferencia de un dominio .uk o asociado a OVHcloud'
updated: 2024-06-28
---

## Objetivo

La transferencia de un dominio .uk (o asimilado) debe respetar un procedimiento específico.

> [!warning]
>
> La configuración, la gestión y la responsabilidad de los servicios que OVHcloud pone a su disposición recaen sobre usted. Por lo tanto, usted deberá asegurarse de que estos funcionen correctamente.
>
> Esta guía le ayudará a realizar las operaciones más habituales. No obstante, si tiene alguna duda le recomendamos que contacte con un proveedor de servicios especializado o con el editor del servicio. Nosotros no podremos asistirle al respecto. Para más información, consulte el apartado [Más información](#go-further) de esta guía.
>

**Cómo transferir un dominio .uk (o asimilado) a OVHcloud**

> [!warning]
>
> Si el dominio que está siendo modificado se encuentra registrado en OVHcloud, la transferencia entrante de dominio no es el procedimiento adecuado. Este procedimiento solo se aplica al cambio de dominio registrado (OVHcloud).
>
> Para transferir la gestión de su dominio a otra cuenta de cliente de OVHcloud, el método adecuado es un *cambio de contactos*. El procedimiento se describe en [esta guía](/pages/account_and_service_management/account_information/managing_contacts).
>
Si también debe cambiar el **propietario** del dominio, debe hacerlo **antes** de cambiar los contactos del dominio. Para ello, siga las indicaciones que le indicamos en la guía sobre el [cambio de propietario de los dominios](/pages/web_cloud/domains/trade_domain).
>
> Si, además de la transferencia del dominio, quiere migrar los servicios asociados al mismo (sitio web, correo electrónico...), consulte en primer lugar nuestra guía "[Migrar un sitio web y los servicios asociados a OVHcloud](/pages/web_cloud/web_hosting/hosting_migrating_to_ovh)" antes de continuar.
> Esta guía explica en detalle cómo migrar todos sus servicios sin cortes del servicio.
>
> Si solo va a transferir su dominio sin trasladar los demás servicios, deberá obtener los servidores DNS activos para su dominio de su actual **registrar** para informarlos directamente en el paso 3 de la guía "[Transferir su dominio a OVHcloud](/pages/web_cloud/domains/transfer_incoming_generic_domain)".
> De este modo, no tendrá que interrumpir la asociación entre su dominio y los servicios externos asociados.
>

## Requisitos

- El dominio no debe estar en período de **redención** o de eliminación.
- El dominio no debe ser bloqueado en su registrador.
- Los datos del propietario deben estar bien actualizados en el [Whois](https://www.nominet.uk/whois/){.external} del dominio.
- Deberá obtener el código de autorización que se enviará a la dirección de correo electrónico del propietario.

> [!primary]
>
> El período de **redención** será de un máximo de 90 días a partir del día de expiración del dominio. En el caso de una transferencia, este período permite restaurar el dominio y así desbloquear la posibilidad de transferirlo.

## Extensiones afectadas

- .uk
- .co.uk
- .ac.uk
- .gov.uk
- .me.uk
- .net.uk
- .org.uk
- .plc.uk
- .sch.uk

## Procedimiento

### Procedimiento de transferencia

#### Etapa 1: Modificación del TAG del dominio

Para poder transferir su dominio a OVHcloud, es necesario indicar previamente el TAG de OVHcloud a su registrador actual. El TAG de OVHcloud es "OVH-FR". La lista de TAGS de los diferentes registradores está disponible en el sitio oficial del Registro [Nominet](https://registrars.nominet.uk/uk-namespace/registrar-agreement/list-of-registrars/){.external}.

> [!primary]
>
> Si no consigue cambiar el Tag del dominio a través de
> su actual agente registrador, puede enviar una solicitud al Registro.
> Nombre para que este último realice los cambios.
> Por favor, vuelva a esta página del sitio web del Registro: "Manage your domain - Change registrar".
> Atención: Esta operación es facturada por Nominet.
>

#### Etapa 2: Obtener el código de autorización de transferencia

Una vez que haya modificado el TAG, el propietario del dominio recibirá al cabo de unos minutos un código de autorización (código auténtico) por correo electrónico. Dicho registro, válido durante 5 días, permitirá realizar el pedido (gratuito) del dominio en OVHcloud.

#### Etapa 3: Solicitar la transferencia gratuita

Una vez que disponga del código de autorización, puede consultar e iniciar el pedido de transferencia del dominio en el sitio web de OVHcloud. El pedido es similar al de cualquier otro dominio genérico.

El dominio aparecerá en el [área de cliente de OVHcloud](/links/manager) en unas horas.

### Información útil

#### Transferencia de un dominio en .uk (o asimilado)

El traslado es gratuito.

#### Validez del código de autorización

El código de autorización se genera automáticamente al modificar el TAG. Si el pedido no se realiza en un plazo de 5 días, la transferencia se anulará ante el Registro.

#### Renovación del dominio tras una transferencia

La transferencia es gratuita, por lo que la fecha de expiración del dominio tras su transferencia será la misma que antes de su transferencia. Para renovarlo tras la transferencia, acceda a la [web de OVHcloud](https://www.ovh.co.uk/cgi-bin/order/renew.cgi).

## Más información <a name="go-further"></a>

[Transferir un dominio a OVHcloud](/pages/web_cloud/domains/transfer_incoming_generic_domain)

Interactúe con nuestra [comunidad de usuarios](/links/community).