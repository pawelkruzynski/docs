---
title: 'Transferir um domínio .uk para a OVHcloud'
excerpt: 'Neste guia encontrará diferentes informações relativas à transferência de um nome de domínio .uk ou equiparado para a OVHcloud'
updated: 2024-06-28
---

## Objetivo

A transferência de um nome de domínio .uk (ou equiparado) requer uma abordagem específica.

> [!warning]
>
> A responsabilidade sobre a configuração e a gestão dos serviços que a OVHcloud disponibiliza recai sobre o utilizador. Assim, deverá certificar-se de que estes funcionam corretamente.
>
> Este manual fornece as instruções necessárias para realizar as operações mais habituais. No entanto, se encontrar dificuldades, recomendamos que recorra a um [prestador de serviços especializado](/links/partner) e/ou que contacte o editor do serviço. Não poderemos proporcionar-lhe assistência técnica. Para mais informações, aceda à secção [Quer saber mais?](#go-further)?
>

***Descubra como transferir um domínio .uk (ou equiparado) para a OVHcloud**

> [!warning]
>
> Se o domínio em curso de modificação está atualmente registado na OVHcloud, a transferência de entrada de domínio não é o procedimento adequado. Este procedimento aplica-se apenas à alteração do nome de domínio registado (OVHcloud).
>
> Para transferir a gestão do seu domínio para outra conta de cliente OVHcloud, o método adequado é *uma alteração de contactos*. O procedimento está descrito no [guia](/pages/account_and_service_management/account_information/managing_contacts).
>
> Se também tem de mudar o **proprietário** do nome de domínio, deve fazê-lo **antes** de alterar os contactos do nome de domínio. Para isso, siga as instruções descritas na nossa documentação sobre a [alteração de proprietário dos nomes de domínio](/pages/web_cloud/domains/trade_domain).
>
> Se, para além da transferência do seu domínio, pretender migrar os serviços que lhe estão associados (site, e-mail, etc.), consulte primeiro o guia "[Migrar o site e os serviços associados para a OVHcloud](/pages/web_cloud/web_hosting/hosting_migrating_to_ovh)" antes de prosseguir.
> Este guia explica em detalhe como migrar o conjunto dos seus serviços sem interrupções.
>
> Se apenas transferir o domínio sem mudar de serviço, certifique-se de que recupera os servidores DNS ativos para o domínio junto do seu **agente de registo** atual para os introduzir diretamente na etapa 3 do guia "[Transferir domínio para a OVHcloud](/pages/web_cloud/domains/transfer_incoming_generic_domain)".
> Isto evitará que interrompa a associação entre o seu nome de domínio e os seus serviços externos associados.
>

## Requisitos

- O seu domínio não deve estar em período de **redenção** ou de eliminação.
- O domínio não deve ser bloqueado no seu registar. 
- Os dados de contacto do proprietário devem estar bem atualizados no [Whois](https://www.nominet.uk/whois/){.external} do domínio.
- Deverá obter o código de autorização que será enviado para o endereço de e-mail do proprietário.

> [!primary]
>
> O período de **redenção** é de 90 dias, no máximo, a contar da data de expiração do nome de domínio. No caso de uma transferência, este período permite restaurar o domínio e assim desbloquear a possibilidade de o transferir.

## Extensões em causa

- .uk
- .co.uk
- .ac.uk
- .gov.uk
- .me.uk
- .net.uk
- .org.uk
- .plc.uk
- .sch.uk

## Instruções

### Procedimento de transferência

#### Etapa 1: Modificação do TAG do seu domínio

Para poder transferir o seu domínio para a OVHcloud, deve indicar previamente o TAG OVHcloud no seu registar atual. A TAG OVHcloud é "OVH-FR". A lista dos TAGS dos diferentes registrars está disponível no site oficial do registo [Nominet](https://registrars.nominet.uk/uk-namespace/registrar-agreement/list-of-registrars/){.external}.

> [!primary]
>
> Se não consegue efetuar a modificação do Tag do seu domínio através
> o seu Registar atual, pode efetuar um pedido junto do Registry
> Nominet para que efetue a modificação por si.
> Reencaminhe-se para esta página do site do Registry: "Manage your domain - Change registar".
> Atenção, esta operação é faturada por Nominet.
>

#### Etapa 2: Obtenção do código de autorização de transferência

Depois de alterar a TAG, o proprietário do nome de domínio receberá após alguns minutos um código de autorização (authcode) por e-mail. Este, válido por 5 dias, permitirá iniciar a encomenda (gratuita) do domínio na OVHcloud.

#### Etapa 3: Encomenda da transferência gratuita

Uma vez na posse do seu código de autorização, pode procurar e iniciar a encomenda de transferência do seu nome de domínio para o site OVHcloud. A encomenda é semelhante à de qualquer outro domínio genérico.

O seu domínio estará de seguida presente na sua [Área de Cliente OVHcloud](/links/manager) dentro de algumas horas.

### Informações úteis

#### Custo de uma transferência de domínio em .uk (ou equiparado)

A transferência é gratuita.

#### Validade do código de autorização

O código de autorização é gerado automaticamente após a modificação da TAG. Se a encomenda não for realizada dentro de 5 dias, a transferência será anulada no registry.

#### Renovação do domínio na sequência de uma transferência

Como a transferência é gratuita, a data de expiração do domínio após a transferência será a mesma que antes da transferência. Para o renovar após a transferência, aceda ao [site OVHcloud](https://www.ovh.co.uk/cgi-bin/order/renew.cgi).

## Quer saber mais? <a name="go-further"></a>

[Transferir o nome de domínio para a OVHcloud)[/pages/web_cloud/domains/transfer_incoming_generic_domain]

Fale com nossa [comunidade de utilizadores](/links/community).