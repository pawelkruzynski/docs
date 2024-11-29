---
title: "Encomendar um projeto Public Cloud através da API OVHcloud"
excerpt: "Saiba como encomendar o seu projeto Public Cloud com a API OVHcloud"
updated: 2020-12-09
---

## Objetivo

A criação de um projeto é a primeira etapa da implantação de [instâncias Public Cloud](https://www.ovhcloud.com/pt/public-cloud/).

**Este guia explica como encomendar um projeto Public Cloud através da APIv6 OVHcloud.**

## Requisitos

- Dispor de identificadores OVHcloud válidos
- Dispor de um [método de pagamento](/pages/account_and_service_management/managing_billing_payments_and_services/manage-payment-methods) válido e registado na sua conta OVHcloud
- Estar familiarizado com o [funcionamento da APIv6 OVHcloud](/pages/manage_and_operate/api/first-steps)

## Instruções

Ligue-se à [interface API OVHcloud](https://api.ovh.com/) e siga os passos abaixo.

### 1 - construir o carrinho

A primeira etapa de uma encomenda consiste em criar um "carrinho" (cart). De seguida, poderá adicionar um projeto Public Cloud.

#### Criar o carrinho

Utilize esta chamada para criar o carrinho:

> [!api]
>
> @api {v1} /order POST /order/cart
>

Queira escolher a sua filial da API OVHcloud. Na resposta, tome nota do número do carrinho ("cartId"); será necessário identificar este carrinho.

De seguida, deverá adicionar um projeto Public Cloud como um artigo. Utilize esta chamada com o seu "cartId" para verificar a disponibilidade do serviço:

> [!api]
>
> @api {v1} /order GET /order/cart/{cartId}/cloud
>

Na resposta, pode verificar os parâmetros relativos a um projeto Public Cloud:

>
>**código_plan**: "Projeto.2018"
>
>**productName**: "Projeto Public Cloud"
>

#### Adicionar um projeto ao carrinho

Utilize esta chamada para adicionar o artigo ao seu carrinho:

> [!api]
>
> @api {v1} /order POST /order/cart/{cartId}/cloud
>

Devem ser fornecidas as seguintes informações, extraídas nas etapas anteriores:

|Campo|Valor|
|---|---|
|CartId|*ID do seu carrinho*|
|duração|P1M|
|planCode|Projeto.2018|
|priceMode|default|
|quantidade|1|

A resposta incluirá um itemId que pode ser utilizado (juntamente com o "cartId") para identificar o artigo do cabaz:

> [!api]
>
> @api {v1} /order GET /order/cart/{cartId}/item/{itemId}
>

Pode verificar a lista dos parâmetros de configuração disponíveis para este artigo com esta chamada:

> [!api]
>
> @api {v1} /order GET /order/cart/{cartId}/item/{itemId}/requredConfiguração
>

Utilize o seguinte endpoint para nomear o seu projeto (`label: "descrição"`):

> [!api]
>
> @api {v1} /order POST /order/cart/{cartId}/item/{itemId}/configuração
>

|Campo|Valor|
|---|---|
|CartId|*ID do seu carrinho*|
|itemId|*ID do artigo*|
|rótulo|descrição|
|valor|*Nome do seu projeto*|

Para aplicar uma nota de compra, utilize a mesma chamada com a etiqueta "voucher", etc.

As respostas incluem uma "configuraçãoId" que pode ser utilizada (juntamente com "cartId" e "itemId") para recuperar a configuração (GET) ou para a eliminar, por exemplo:

> [!api]
>
> @api {v1} /order DELETE /order/cart/{cartId}/item/{itemId}/configuração/{configuraçãoId}
>

### Etapa 2: validar o carrinho

Pode verificar o conteúdo do seu carrinho através do "CartId":

> [!api]
>
> @api {v1} /order GET /order/cart/{cartId}/checkout
>

A seguinte chamada permite-lhe criar um link para a sua encomenda. A casa correspondente deve ser assinalada em primeiro lugar, a fim de renunciar ao direito de retratação.

> [!api]
>
> @api {v1} /order POST /order/cart/{cartId}/checkout
>

## Quer saber mais?

Fale com nossa [comunidade de utilizadores](/links/community).