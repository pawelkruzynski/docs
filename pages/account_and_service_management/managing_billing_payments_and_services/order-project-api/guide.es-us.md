---
title: Contratar un proyecto de Public Cloud a través de la API de OVHcloud
excerpt: Cómo contratar su proyecto de Public Cloud con la API de OVHcloud
updated: 2020-12-09
---

## Objetivo

La creación de un proyecto es la primera etapa del despliegue de [instancias Public Cloud](https://www.ovhcloud.com/es/public-cloud/).

**Esta guía explica cómo contratar un proyecto de Public Cloud a través de la APIv6 de OVHcloud.**

## Requisitos

- Disponer de las claves de OVHcloud válidas.
- Disponer de una [forma de pago](/pages/account_and_service_management/managing_billing_payments_and_services/manage-payment-methods) válida y registrada en su cuenta de OVHcloud.
- Estar familiarizado con el [funcionamiento de la APIv6 de OVHcloud](/pages/manage_and_operate/api/first-steps).

## Procedimiento

Conéctese a la [API de OVHcloud](https://api.ovh.com/) y siga los pasos que se indican a continuación.

### 1\. construir la canasta

El primer paso de un pedido es crear una cesta. A continuación, podrá añadir un proyecto de Public Cloud.

#### Crear la cesta

Utilice esta llamada para crear la cesta:

> [!api]
>
> @api {v1} /order POST /order/cart
>

Elija su filial de la API de OVHcloud. Anote el número de cesta ("cartId") en la respuesta. será necesario identificar esta cesta.

A continuación, añada un proyecto de Public Cloud como artículo. Utilice esta llamada con su cartId para verificar la disponibilidad del servicio:

> [!api]
>
> @api {v1} /order GET /order/cart/{cartId}/cloud
>

En la respuesta, puede comprobar la configuración de un proyecto de Public Cloud:

>
>**code_plan** : "project.2018"
>
>**productName**: "Proyecto de Public Cloud"
>

#### Añadir un proyecto a la cesta

Utilice esta llamada para añadir el artículo a su cesta:

> [!api]
>
> @api {v1} /order POST /order/cart/{cartId}/cloud
>

Se facilitará la siguiente información, extraída en las etapas anteriores:

|Campo|Valor|
|---|---|
|cartId|*ID de la cesta*|
|duración|P1M|
|planCode|project.2018|
|priceMode|default|
|cuantity|1|

La respuesta incluirá un "itemId" que puede utilizarse (junto con el "cartId") para identificar el artículo de la cesta:

> [!api]
>
> @api {v1} /order GET /order/cart/{cartId}/item/{itemId}
>

Puede consultar la lista de parámetros disponibles para este artículo con la siguiente llamada:

> [!api]
>
> @api {v1} /order GET /order/cart/{cartId}/item/{itemId}/requiredConfiguration
>

Utilice el siguiente punto para nombrar su proyecto (`etiqueta: "description"`):

> [!api]
>
> @api {v1} /order POST /order/cart/{cartId}/item/{itemId}/configuración
>

|Campo|Valor|
|---|---|
|cartId|*ID de la cesta*|
|itemId|*ID del artículo*|
|label|descripción|
|value|*Nombre del proyecto*|

Para aplicar un vale, utilice la misma llamada con el distintivo "código promocional", etc.

Las respuestas incluyen un "configuracionId" que puede utilizarse (junto con "cartId" e "itemId") para recuperar la configuración (GET) o eliminarla, por ejemplo:

> [!api]
>
> @api {v1} /order DELETE /order/cart/{cartId}/item/{itemId}/configuración/{configurationId}
>

### 2\. validar la cesta

Puede comprobar el contenido de su cesta utilizando "cartId" :

> [!api]
>
> @api {v1} /order GET /order/cart/{cartId}/checkout
>

La siguiente llamada le permite crear un enlace hacia su pedido. En primer lugar, hay que marcar la casilla correspondiente para renunciar al derecho de desistimiento.

> [!api]
>
> @api {v1} /order POST /order/cart/{cartId}/checkout
>

## Más información

Interactúe con nuestra [comunidad de usuarios](/links/community).