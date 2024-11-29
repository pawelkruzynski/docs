---
title: "O que fazer em caso de erro 500 Internal Server Error?"
excerpt: "Diagnosticar os casos mais comuns de erros 500"
updated: 2023-11-22
---

## Objetivo

Os erros 500 "Internal Server Error" podem afetar a totalidade ou parte do seu site, ser aleatórios ou permanentes. Podem também aparecer sob a forma de uma página em branco.

![error500](/pages/assets/screens/other/browsers/errors/http-500.png){.thumbnail}

Por vezes, provêm também de uma atualização efetuada **automaticamente** por um componente do seu site e, portanto, ocorrem sem ação da sua parte.

**Saiba como diagnosticar os casos mais comuns de erros 500.**

> [!warning]
>
> A responsabilidade sobre a configuração e a gestão dos serviços que a OVHcloud disponibiliza recai sobre o utilizador. Assim, deverá certificar-se de que estes funcionam corretamente.
>
> Este manual fornece as instruções necessárias para realizar as operações mais habituais. No entanto, se encontrar dificuldades, recomendamos que recorra a um [prestador de serviços especializado](/links/partner) e/ou que contacte o editor do serviço. Não poderemos proporcionar-lhe assistência técnica. Para mais informações, aceda à secção [Quer saber mais](#go-further) ?
>

## Requisitos

- Dispor de uma [oferta de alojamento partilhado](/links/web/hosting)
- Ter acesso à [Área de Cliente OVHcloud](/links/manager)
- Estar atualizado em [pagamentos](/pages/account_and_service_management/managing_billing_payments_and_services/invoice_management#pay-bills) e [renovações](/pages/account_and_service_management/managing_billing_payments_and_services/how_to_use_automatic_renewal#renewal-management) dos serviços associados (nome de domínio e alojamento web)

## Instruções

Antes de prosseguir, verifique o seu site em vários dispositivos e browsers. Se o erro 500 não aparece em certos casos (por exemplo, num browser diferente do seu), é porque não está relacionado com os seus serviços OVHcloud. Reinicie os seus dispositivos e contacte um técnico informático próximo da sua casa.

Um site é constituído por um **código fonte** (os ficheiros em .php, por exemplo, visíveis durante uma ligação ao seu alojamento em [FTP](/pages/web_cloud/web_hosting/ftp_connection), ao qual se junta frequentemente uma **base de dados**.
<br>Apesar do erro 500, é fortemente aconselhado efetuar um backup local do conjunto dos seus dados antes de qualquer outra manipulação :

- Siga este [guia](/pages/web_cloud/web_hosting/ftp_filezilla_user_guide) para obter uma cópia do código fonte.
- Se o seu site utiliza uma base de dados, consulte também este [documento](/pages/web_cloud/web_hosting/sql_database_export) para obter uma cópia.

No caso de um erro 500, é perfeitamente possível efetuar um [restauro](#restore) do seu site. No entanto, é preferível efetuar um diagnóstico aprofundado para determinar a origem exata do erro.

### Verificar os logs do seu alojamento

Consulte primeiro este [guia](/pages/web_cloud/web_hosting/logs_and_statistics) para procurar a causa do erro 500 nos logs do seu alojamento.

### Passar o seu site em modo de desenvolvimento

Para que apareçam eventuais erros PHP, passe o seu alojamento em modo de `desenvolvimento` graças a estas [indicações](/pages/web_cloud/web_hosting/configure_your_web_hosting#2-alterar-a-configuracao-do-alojamento-web).

### Testar o ficheiro.htaccess

Um erro 500 pode estar associado a uma anomalia num ficheiro `.htaccess`. Este ficheiro está geralmente localizado no primeiro nível da pasta que contém o seu site no seu FTP.

Para o verificar, [ligue-se FTP](/pages/web_cloud/web_hosting/ftp_connection) ao seu alojamento.

De seguida, renomeie este ficheiro em `.htaccess.old` e volte a testar o seu site.

Se este último estiver de novo acessível, então o `.htaccess` está em causa. Por conseguinte, deverá ser alterado. Se desejar, contacte um dos nossos [parceiros](/links/partner) a este respeito.

### Verificar permissões nas pastas e nos ficheiros

Os ficheiros e os dossiers que constituem o seu site possuem um certo nível de "permissões" em leitura, escrita e execução. Isto para as proteger contra qualquer manipulação maliciosa ou incorreta.

Um erro 500 pode estar associado a um nível de direitos de acesso incorreto em alguns dos dossieres ou ficheiros do seu site.

Para aceder a estes ficheiros, ligue-se ao seu alojamento através de FTP, seguindo a nossa [documentação](/pages/web_cloud/web_hosting/ftp_connection).

O guia "[Partilhado : Guia de utilização do FileZilla](/pages/web_cloud/web_hosting/ftp_filezilla_user_guide#permissoes-de-pastas-e-ficheiros)" ajudá-lo-á a verificar os seguintes elementos :

- A **raiz** do seu alojamento (Trata-se do diretório notado `/` ou `.` no seu software FTP) deve ter obrigatoriamente permissões 705 (são permissões padrão). Aconselhamos que não altere este nível de direitos.
- Os dossiers devem estar em permissões 705.
- Os ficheiros devem estar em permissões 604.

### Aceder aos detalhes dos erros nos seus scripts

Por razões de segurança, o seu website oculta eventuais detalhes sobre a origem do erro 500 a qualquer pessoa que se lhe ligue por um browser.

Se pretender ter acesso a estes detalhes, poderá aceder ao seu site através de uma [ligação ssh](/pages/web_cloud/web_hosting/ssh_on_webhosting) a partir da fórmula de alojamento [Pro](/links/web/hosting-professional-offer) ou superior.

### Verificar o estado da base de dados

Para qualquer erro 500 que possa estar relacionado com a base de dados do seu website, consulte o nosso manual ["Resolver os erros mais frequentes associados às bases de dados"](/pages/web_cloud/web_hosting/diagnosis_database_errors).

### Restaurar o seu site para o estado anterior <a name="restore"></a>

> [!warning]
>
> O restauro do código fonte do seu site dirá respeito ao conjunto dos sites do seu alojamento OVHcloud.
>
> Durante o restauro, o conteúdo do seu espaço FTP ou da sua base de dados é substituído por um backup. Assim, não poderá recuperar os dados presentes no servidor imediatamente antes do restauro.
>

Para restaurar o código fonte do seu site, consulte o nosso manual "[Restaurar o espaço de armazenamento do alojamento web](/pages/web_cloud/web_hosting/ftp_save_and_backup)".

Se o seu site tiver uma base de dados, consulte o nosso manual "[Importar um backup para a base de dados de um alojamento web](/pages/web_cloud/web_hosting/sql_importing_mysql_database#restaurar-um-backup-a-partir-da-area-de-cliente)" para a restaurar para um estado anterior.

Por fim, se o erro 500 aparecer após uma atualização da versão PHP do seu alojamento, consulte o nosso guia "[Mudar a versão de PHP do alojamento web](/pages/web_cloud/web_hosting/configure_your_web_hosting)" para voltar à configuração anterior.

## Saiba mais <a name="go-further"></a>

[O que fazer se o meu site está inacessível?](/pages/web_cloud/web_hosting/diagnostic-website-not-accessible)

[O que fazer em caso de erro « Sua conexão não é particular »?](/pages/web_cloud/web_hosting/diagnostic-not-secured)

[O que fazer em caso de página « Index of »?](/pages/web_cloud/web_hosting/diagnostic-index-of)

[O que fazer em caso de página "403 forbidden"?](/pages/web_cloud/web_hosting/diagnostic_403_forbidden)

[Resolver os erros mais frequentes associados às bases de dados](/pages/web_cloud/web_hosting/diagnosis_database_errors)

[O meu site é lento. O que fazer?](/pages/web_cloud/web_hosting/diagnostic_slownesses)

[Resolver o erro “Site não instalado”](/pages/web_cloud/web_hosting/multisites_website_not_installed)

Para serviços especializados (referenciamento, desenvolvimento, etc), contacte os [parceiros OVHcloud](/links/partner).

Fale com nossa [comunidade de utilizadores](/links/community).