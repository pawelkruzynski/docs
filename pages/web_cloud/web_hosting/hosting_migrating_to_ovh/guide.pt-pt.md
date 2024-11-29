---
title: "Migrar o seu website e os seus serviços associados para a OVHcloud"
excerpt: "Descubra como migrar o seu website, o seu nome de domínio, a sua base de dados e os seus e-mails para a OVHcloud sem interrupção de serviços"
updated: 2024-06-24
---

## Objetivo

Este guia apresenta-lhe as diferentes ações a realizar para migrar o conjunto do seu website, as suas pastas, o seu nome de domínio, a sua base de dados e os seus endereços de e-mail para a OVHcloud, sem interrupção de serviços.

> [!warning]
>
> A OVHcloud disponibiliza serviços cuja configuração, gestão e responsabilidade lhe incumbem. Assim, deverá certificar-se de que estes funcionam corretamente.
> 
> Este manual fornece as instruções necessárias para realizar as operações mais habituais. No entanto, se encontrar dificuldades, recomendamos que recorra a um [fornecedor especializado](/links/partner). Não poderemos proporcionar-lhe assistência técnica. Para mais informações, aceda à secção ["Quer saber mais?"](#go-further) deste manual.
>

## Requisitos

- Ter acesso à gestão do nome de domínio do seu website (este deve existir há mais de 60 dias).
- Ter acesso à zona DNS (Domain Name System) ativa do seu domínio.
- Ter acesso aos ficheiros e à base de dados do seu website no seu alojamento atual.
- Dispor de dados de acesso (utilizador, palavra-passe, servidor) aos seus endereços de e-mail atuais.
- Ter acesso à [Área de Cliente OVHcloud](/links/manager).

## Instruções

> [!success]
>
> As instruções deste guia referem-se a vários produtos do universo Web Cloud, recomendamos que leia todos os passos em baixo **antes** de começar a migração dos seus serviços.
>

A migração do site e dos e-mails para a OVHcloud **sem interrupção do serviço** requer um procedimento preciso em 10 etapas:

- [Etapa 1: encomendar o alojamento e os endereços de e-mail na OVHcloud](#step1)
- [Etapa 2: criar e pré-configurar uma zona DNS para o seu domínio na OVHcloud](#step2)
- [Etapa 3: recuperar um backup completo do seu website](#step3)
- [Etapa 4: importar o backup do seu website para a sua oferta de alojamento OVHcloud](#step4)
- [Etapa 5: recriar os seus endereços de e-mail para a OVHcloud](#step5)
- [Etapa 6: declarar os servidores de e-mail OVHcloud na zona DNS ativa do seu domínio](#step6)
- [Etapa 7: transferir o conteúdo dos endereços de e-mail antigos para os novos endereços na OVHcloud](#step7)
- [Etapa 8: reconfigurar o software de e-mail](#step8)
- [Etapa 9: substituir os servidores DNS ativos do seu domínio pelos da OVHcloud](#step9)
- [Etapa 10: transferir o domínio para a OVHcloud](#step10)

Ao seguir estes 10 Etapas **por ordem**, não terá nenhuma interrupção do serviço para aceder ao seu website e receber os seus novos e-mails.

No entanto, dependendo do seu agente de registo, do seu fornecedor de alojamento ou do seu prestador de serviços de e-mail, é possível que estes últimos cortem o acesso aos seus antigos serviços se verificarem que o seu nome de domínio já não está configurado através das suas infraestruturas.<br>
Neste caso, pode ocorrer uma interrupção do serviço.

Se tal interrupção ocorrer, este guia será construído de forma a minimizar a sua duração.

### Etapa 1: encomendar o alojamento e os endereços de e-mail na OVHcloud <a name="step1"></a>

Várias ofertas de [alojamento partilhado OVHcloud](/links/web/hosting) incluem uma oferta de e-mail "[MX Plan](/pages/web_cloud/email_and_collaborative_solutions/mx_plan/email_generalities)". Esta oferta de e-mail permite criar endereços de e-mail com um espaço de armazenamento de 5 GB no máximo para cada endereço. Escolha a seguir as ofertas de alojamento em função da versão PHP, da versão SQL, do número de endereços de e-mail que precisa e do tamanho do seu site a migrar:

- O alojamento [Perso](/links/web/hosting-personal-offer) com **10 endereços de e-mail** "MX Plan"
- O alojamento [Pro](/links/web/hosting-professional-offer) com **100 endereços de e-mail** "MX Plan"
- O alojamento [Performance](/links/web/hosting-performance-offer) com **1000 endereços de e-mail** "MX Plan". Esta oferta é indicada em 4 "subofertas".
- O alojamento [Cloud Web](/links/web/hosting-cloud-web-offer) com **200 endereços de e-mail** "MX Plan". Esta oferta é utilizada pelos programadores de aplicações.

Depois de escolher a oferta de alojamento, se ainda não é cliente da OVHcloud, clique no botão `Encomendar`{.action} presente nas páginas comerciais acima. Siga os passos da encomenda **sem solicitar a transferência do seu nome de domínio** (esta ação será realizada na etapa 10 deste manual).

Também pode efetuar a encomenda a partir da sua [Área de Cliente OVHcloud](/links/manager). Uma vez ligado, siga as instruções seguintes:

- Aceda ao separador `Web Cloud`{.action}.
- No canto superior esquerdo da interface, clique no botão `Encomendar`{.action} e, a seguir, em `Alojamento`{.action}.
- Prossiga com a encomenda **sem solicitar a transferência do domínio** (a transferência será efetuada na etapa 10 deste manual).

Depois de validar o pagamento, a instalação do alojamento vai iniciar. Um e-mail será enviado para o seu endereço de e-mail de contacto. Este último conterá as credenciais de acesso ao espaço de armazenamento FTP (File Transfer Protocol) do seu alojamento Web.

> [!primary]
>
> A OVHcloud oferece outras ofertas de e-mail para além da oferta "MX Plan". Por exemplo, pode combinar endereços de e-mail "MX Plan" de endereços ["Email-Pro"](/links/web/email-pro) e/ou contas ["Exchange"](/links/web/emails-hosted-exchange).
>

### Etapa 2 : criar e pré-configurar uma zona DNS para o seu domínio na OVHcloud <a name="step2"></a>

Se o seu domínio se encontrar noutro prestador e pretender transferi-lo para a OVHcloud, deve num primeiro tempo criar e pré-configurar uma zona DNS antes de iniciar a transferência, a fim de evitar uma interrupção de serviços.

Quando o alojamento estiver criado, aceda à [Área de Cliente OVHcloud](/links/manager) e crie uma zona DNS para o seu domínio **sem "www"**. Para mais informações, consulte o nosso manual sobre a [criação de uma zona DNS na OVHcloud](/pages/web_cloud/domains/dns_zone_create).

Depois de criar a zona DNS, aceda à sua gestão através do nosso guia "[Editar uma zona DNS da OVHcloud](/pages/web_cloud/domains/dns_zone_edit)".

Se não estiverem presentes, preencha as seguintes entradas:

**Exemplo** (para o nome de domínio "domain.tld"):

|Domínio|Tipo de registo|Prioridade|Destino|
|---|---|---|---|
|domain.tld.|MX|1|mx1.mail.ovh.net.|
|domain.tld.|MX|5|mx2.mail.ovh.net.|
|domain.tld.|MX|100|mx3.mail.ovh.net.|
|www.domain.tld.|CNAME|-|domain.tld.|
|domain.tld.|A|-|`endereço_IP_de_destino`|

Para obter o endereço IP certo de destino do seu alojamento OVHcloud, consulte o guia que apresenta os [endereços IP dos diferentes clusters de alojamento partilhados](/pages/web_cloud/web_hosting/clusters_and_shared_hosting_IP).

**Exemplo** : Para o nome de domínio "domain.tld", a rendição das entradas do seu nome de domínio deve ser a seguinte:

![hosting](/pages/assets/screens/control_panel/product-selection/web-cloud/domain-dns/dns-zone/dashboard-mx-a-cname.png){.thumbnail}

> [!success]
>
> Anote os dois valores alvo que têm como tipo de registo "NS". Estes valores, do tipo `dnsXX.ovh.net` e `nsXX.ovh.net` (ou `dns200.anycast.me` e `ns200.anycast.me`), correspondem aos servidores DNS associados a esta zona DNS para o seu domínio. Estas instruções serão utilizadas na [etapa 9](#step9) deste manual.
>

### Etapa 3 : recuperar um backup completo do seu website <a name="step3"></a>

Obtenha o conteúdo do espaço de armazenamento FTP do seu alojamento atual, assim como um backup da sua base de dados caso o seu site utilize um.

Estas operações são realizadas exclusivamente junto do seu alojador atual. Contacte-o se tiver dificuldades em recuperar um backup completo do seu website.

#### Etapa 4 : importar o backup do seu website para a sua oferta de alojamento OVHcloud <a name="step4"></a>

Para importar o backup do espaço de armazenamento FTP do antigo fornecedor, [aceda ao espaço de armazenamento FTP do seu alojamento OVHcloud](/pages/web_cloud/web_hosting/ftp_connection) e elimine o backup da pasta raiz "www" (ou de outra pasta raiz que tenha criado).

Recomendamos que utilize o software [FileZilla](/pages/web_cloud/web_hosting/ftp_filezilla_user_guide) para transferir o seu backup FTP para o seu alojamento.

Se o seu ficheiro de backup estiver comprimido (zipado), descomprima-o numa pasta vazia no seu computador antes de transferir os seus ficheiros para o alojamento OVHcloud.

Para o backup da sua base de dados, [crie uma nova base de dados](/pages/web_cloud/web_hosting/sql_create_database) e depois [importe o seu backup para a sua nova base de dados](/pages/web_cloud/web_hosting/sql_importing_mysql_database).

> [!primary]
>
> A OVHcloud oferece servidores de base de dados Web Cloud Databases. Se pretender utilizar esta oferta com o seu website, consulte toda a nossa documentação sobre este produto na [nossa página dedicada](/products/web-cloud-clouddb).
>

De seguida, associe a sua base de dados OVHcloud ao ficheiro de configuração do seu site presente no espaço de armazenamento FTP do seu alojamento OVHcloud.
Para isso, substitua as informações de ligação da sua antiga base de dados pelas da sua nova base de dados OVHcloud. Estas informações estão disponíveis no ficheiro de configuração/ligação à base de dados do seu website.

> [!success]
>
> Para ligar a sua nova base de dados se utiliza um Content Management System (CMS) como WordPress, Joomla!, Drupal ou PrestaShop, encontre as informações sobre os seus ficheiros de configuração a partir do **etapa 2** do guia "[modificação da palavra-passe de uma base de dados](/pages/web_cloud/web_hosting/sql_change_password)".
>

Declare/autorize o seu domínio externo no seu alojamento web da OVHcloud através do nosso guia "[gestão dos multi-sites de um alojamento web da OVHcloud](/pages/web_cloud/web_hosting/multisites_configure_multisite)". Declare o "nome" da pasta raiz que escolheu no início da [etapa 4](#step4). Relembramos que esta é a pasta na qual colocou os seus ficheiros no seu espaço de armazenamento FTP.

> [!warning]
>
> **A realização desta operação é crucial**, o seu website não será apresentado enquanto não tiver indicado os elementos corretos. Respeite em especial a sintaxe da entrada DNS "TXT".
>
> Uma vez que o seu domínio ainda não está na OVHcloud, deverá adicionar uma entrada DNS do tipo "TXT" ao "token OVHcontrol" e alterar o apontamento do tipo "A" do seu domínio. Isto diretamente na zona DNS ativa o seu nome de domínio no seu fornecedor atual.
>
> Faça o mesmo para o seu subdomínio em "www".
>
> Se necessário, entre em contacto com o atual gestor da zona DNS para efetuar esta operação.
>

**Exemplo**: para o domínio "domain.tld":

![hosting](/pages/assets/screens/control_panel/product-selection/web-cloud/domain-dns/dns-zone/dashboard-a-txt-cname.png){.thumbnail}

**A alteração das entradas DNS "A", "CNAME" e "TXT" deve ser efetuada junto do atual fornecedor DNS do seu domínio e requer um tempo de propagação de 4 a 24 horas, no máximo, antes de ficar totalmente efetivo.**

Após a propagação DNS, o site que irá aparecer com o seu domínio será o alojado na OVHcloud.

### Etapa 5 : recriar os seus endereços de e-mail para os mesmos na OVHcloud <a name="step5"></a>

Recrie de forma idêntica os endereços de e-mail presentes no seu fornecedor de e-mail através do nosso guia sobre a [criação de endereços de e-mail "MX Plan"](/pages/web_cloud/email_and_collaborative_solutions/mx_plan/email_creation).

Se optou por uma solução "Email Pro" ou "Exchange", consulte o nosso manual para criar os seus endereços de e-mail:

- Para [Email-Pro](/pages/web_cloud/email_and_collaborative_solutions/email_pro/first_config)
- Para [Exchange](/pages/web_cloud/email_and_collaborative_solutions/microsoft_exchange/exchange_starting_hosted)

### Etapa 6 : declarar os servidores de e-mail OVHcloud na zona DNS ativa do seu nome de domínio <a name="step6"></a>

Esta etapa consiste em efetuar a alteração dos servidores de e-mail "MX" na zona DNS ativa do seu domínio.
Isto irá permitir que receba novos e-mails nos novos endereços de e-mail da OVHcloud.

Substitua (sem deixar as antigas entradas) as suas antigas entradas "MX" pelo seguinte:

- O seu domínio (sem "www") para o destino do tipo "MX": mx1.mail.ovh.net ".
- O seu domínio (sem "www") para o destino do tipo "MX": mx2.mail.ovh.net ".
- O seu domínio (sem "www") para o destino do tipo "MX": mx3.mail.ovh.net ".

A alteração dos servidores "MX" efetua-se junto do fornecedor DNS atual do seu nome de domínio e requer um tempo de **propagação de 4 a 24 horas**, no máximo, antes de ser totalmente efetivo.<br>
Isto significa que, durante a propagação DNS da modificação, os seus e-mails serão recebidos cada vez menos nos seus antigos endereços de e-mail e cada vez mais nos seus novos endereços de e-mail OVHcloud.<br>
Depois de finalizar a propagação, todos os novos e-mails recebidos serão recebidos nos seus endereços de e-mail OVHcloud.

Recomendamos que altere as entradas "MX" **antes** de efetuar a migração do conteúdo dos seus antigos endereços de e-mail.
Este método permite evitar uma migração adicional para os poucos e-mails recebidos nos endereços de e-mail antigos durante a propagação do DNS.

### Etapa 7 : transferir o conteúdo dos endereços de e-mail antigos para os novos endereços OVHcloud <a name="step7"></a>

Após a propagação DNS, os seus novos e-mails são agora todos recebidos nos seus novos endereços de e-mail. Mas os e-mails antigos ainda estão a ser guardados no servidor de e-mail antigo.

Para migrar o conteúdo dos seus antigos endereços de e-mail, tem duas opções à sua disposição.

**Opção 1**: utilize a nossa ferramenta [OVH Mail Migrator (OMM)](https://omm.ovh.net/){.external} que permite copiar o conteúdo dos endereços de e-mail registados no seu antigo fornecedor para os criados na OVHcloud. Para mais informações, consulte o nosso manual "[Migrar contas de e-mail via OVH Mail Migrator](/pages/web_cloud/email_and_collaborative_solutions/migrating/migration_omm)".

Sugerimos que não utilize o `Tipo de servidor`{.action} **POP** na parte `Conta source`{.action}. Este protocolo apaga os e-mails do seu antigo servidor para os enviar para o servidor OVHcloud de destino. Neste caso, já não será possível comparar o conteúdo do endereço de e-mail antigo e novo.

Para a parte `Conta de destino`{.action}, introduza apenas o endereço de e-mail OVHcloud em questão e a respetiva palavra-passe. Isto permitindo o `Tipo de serviço`{.action} em `Hosted by OVH (Autodetect)`{.action}.

Terminada a migração, aceda ao endereço de e-mail da OVHcloud usando o [webmail OVHcloud](/links/web/email) para verificar que todos os seus e-mails estão presentes na nova conta.

Repita a operação para o conjunto das suas contas de e-mail.

> [!primary]
>
> Deve possuir os dados de acesso de todas as contas de e-mail antigas bem como o nome do servidor de e-mail do seu antigo prestador de serviços para realizar esta ação.
>
> Se os seus endereços de e-mail foram configurados em POP sem conservar cópias dos e-mails no seu antigo servidor de e-mail, ou se dispõe dos e-mails registados "localmente" nos seus dispositivos, só poderá realizar a **opção 2**.
>

**Opção 2**: faça um backup do conteúdo dos seus endereços de e-mail com a ajuda de um software de mensagens (Outlook, Mail para Mac,...), reconfigure o seu software de e-mail e depois importe o backup para o seu novo endereço de e-mail OVHcloud.

### Etapa 8 : reconfigurar os seus softwares de e-mail <a name="step8"></a>

Depois de migrar os seus antigos endereços de e-mail para a OVHcloud, reconfigure os seus softwares de e-mail com a ajuda de todos os nossos guias sobre o assumpto.

#### Para as contas de e-mail "MX Plan": 

- Encontre os parâmetros de configuração no nosso guia "[Generalidades sobre os e-mails MX Plan](/pages/web_cloud/email_and_collaborative_solutions/mx_plan/email_generalities#2-utilizar-o-software-a-sua-escolha)". Além disso, poderá encontrar links para os guias de configuração personalizados para os principais softwares de e-mail.

#### Para as contas "Email-Pro"

- Encontre os nossos guias de ajuda à configuração nas secções `Configuration on computador` e `Configuration no smartphone` de [o nosso manual na oferta Email-Pro](/products/web-cloud-email-collaborative-solutions-email-pro).

#### Para as contas de e-mail "Exchange" :

- Encontre os nossos guias de ajuda à configuração nas secções `Configuration Exchange no computador` e `Configuration Exchange no smartphone` de [a nossa documentação sobre a oferta Exchange](/products/web-cloud-email-collaborative-solutions-microsoft-exchange).

### Etapa 9: substituir os servidores DNS ativos do seu domínio pelos da OVHcloud <a name="step9"></a>

A zona DNS pré-configurada durante a [etapa 2](#step2) não é ainda aplicada ao seu domínio. Atualmente, o seu domínio utiliza sempre os servidores DNS do seu fornecedor de origem.

Substitua os servidores DNS atuais (do registar de origem) pelos dois servidores DNS declarados na zona DNS da OVHcloud (de tipo `dnsXX.ovh.net` e `nsXX.ovh.net` ou `dns200.anycast.me` e `ns200.anycast.me`). Esta operação faz-se na interface de gestão do registar de origem.

> [!warning]
>
> A alteração dos servidores DNS deve ser efetuada a partir do agente de registo atual do seu nome de domínio e requer um tempo de **propagação de 24 a 48 horas**, no máximo, antes de ficar totalmente efetivo.
>

### Etapa 10 : transferir o domínio para a OVHcloud <a name="step10"></a>

Uma vez a propagação DNS terminada, verifique que o conjunto do seu website está funcional. Navegue no seu site para verificar se todas as páginas são apresentadas corretamente e se não foi reenviado nenhum erro 404. Verifique também o envio e a receção dos e-mails a partir dos seus endereços de e-mail.

Se tudo estiver em ordem, desbloqueie o seu nome de domínio e recupere o seu "código de transferência", "EPP" ou "AuthCode" a partir do seu agente de registo atual.

De seguida, transfira o domínio para a OVHcloud através do nosso manual sobre a [transferência de um domínio](/pages/web_cloud/domains/transfer_incoming_generic_domain).

Uma vez concluída a transferência dos seus dados e serviços, só precisa de rescindir os seus antigos serviços no(s) seu(s) antigo(s) fornecedor(es).

### Conclusão

Após ter seguido as dez etapas em ordem, todo o seu website é agora migrado para a OVHcloud, tudo sem interrupção de serviço.

## Quer saber mais? <a name="go-further"></a>

[Generalidades sobre os e-mails partilhados](/pages/web_cloud/email_and_collaborative_solutions/mx_plan/email_generalities).

[Generalidades sobre os servidores DNS](/pages/web_cloud/domains/dns_server_general_information).

[Criar um endereço de e-mail partilhado](/pages/web_cloud/email_and_collaborative_solutions/mx_plan/email_creation).

[Importação de uma base de dados MySQL](/pages/web_cloud/web_hosting/sql_importing_mysql_database).

[Gestão de uma base de dados a partir de um alojamento partilhado](/pages/web_cloud/web_hosting/sql_create_database).

Para serviços especializados (referenciamento, desenvolvimento, etc), contacte os [parceiros OVHcloud](/links/partner).

Se pretender usufruir de uma assistência na utilização e na configuração das suas soluções OVHcloud, consulte as nossas diferentes [ofertas de suporte](/links/support).

Fale com nossa [comunidade de utilizadores](/links/community).