---
title: "Restaurar o espaço de armazenamento do alojamento web"
excerpt: "Saiba como restaurar um ficheiro ou a totalidade do espaço de armazenamento do seu alojamento web"
updated: 2023-12-04
---

## Objetivo

A sua solução de alojamento web da OVHcloud dá-lhe acesso a um espaço de armazenamento no qual pode alojar os seus websites. Por várias razões (para eliminar ou alterar um ficheiro que torna o seu site inacessível, por exemplo), poderá ter de restaurar os dados do seu espaço de armazenamento ou simplesmente um ficheiro guardado nesse mesmo espaço.

> [!primary]
> 
> Os backups propostos pela OVHcloud para os alojamentos partilhados são extracontratuais. Oferecemos-lhe estas informações em complemento dos seus serviços, de forma a ajudá-lo em situações urgentes. Recomendamos que efetue regularmente as suas próprias cópias de segurança para corrigir eventuais perdas de dados.
> 
> Quando efetuar um backup de segurança para o seu site e utilizar uma base de dados, faça também um backup da sua base de dados. Não hesite em consultar o nosso guia para [recuperar a cópia de segurança da base de dados de um alojamento web](/pages/web_cloud/web_hosting/sql_database_export).
>

**Saiba como restaurar um ficheiro ou a totalidade do espaço de armazenamento do seu alojamento web.**

## Requisitos

- Ter um [alojamento web](/links/web/hosting){.external} (não funciona com um alojamento [Cloud Web](/links/web/hosting-cloud-web-offer)).
- Consoante o método utilizado, ter acesso à gestão do alojamento web a partir da [Área de Cliente OVHcloud](/links/manager){.external} ou dispor da palavra-passe do utilizador FTP que lhe permite aceder ao seu espaço de armazenamento. 

## Instruções

Antes de começar, certifique-se de que as datas de restauração propostas permitem-lhe restaurar o espaço de armazenamento do seu alojamento web à data pretendida:

- no mesmo dia, às 00h01 da manhã;
- no dia anterior, às 00h01 da manhã;
- dois dias antes, às 00h01 da manhã;
- no domingo anterior, à 01h00 da manhã;
- no domingo, duas semanas antes, à 01h00 da manhã.

A OVHcloud não poderá fornecer uma cópia de segurança mais antiga. Nesse caso, deverá utilizar uma cópia de segurança do website que realizou no passado. 

Da mesma forma, deverá definir o método de restauração que vai utilizar:

|Método de restauração|Descrição|
|---|---|
|Restauração a partir da Área de Cliente|Restaura na íntegra o conteúdo do espaço de armazenamento. O conteúdo atual será totalmente substituído pelo da cópia de segurança selecionada.|
|Restauração a partir de um programa ou uma interface|Permite-lhe aceder em modo só de leitura a uma cópia de segurança do espaço de armazenamento. Este método, embora mais técnico, permite restaurar um ou vários ficheiros numa data anterior sem apagar todo o conteúdo do espaço de armazenamento.|

> [!warning]
>
> Relativamente ao método de **restauro a partir da Área de Cliente OVHcloud**, verifique que pelo menos **metade do espaço de armazenamento FTP total** incluído com o seu plano de alojamento ainda está disponível.
> Por exemplo, se dispõe de uma oferta de alojamento **Performance**, 250GB ainda estão disponíveis nos 500GB disponibilizados.
>
> De facto, os nossos robôs instalam o backup no seu alojamento antes de eliminar o conteúdo FTP que será substituído pelo restauro.
>
> Para verificar o limite utilizado no seu alojamento web, aceda à [Área de Cliente OVHcloud](/links/manager). Aceda à secção `Web Cloud`{.action} e clique em `Alojamentos`{.action}. De seguida, selecione o nome do alojamento correspondente. 
>
> A quota utilizada aparece na página que aparece:
>
>![ftp quota](/pages/assets/screens/control_panel/product-selection/web-cloud/web-hosting/general-information/find-disk-space.png){.thumbnail}
>
> Se o espaço de armazenamento FTP utilizado for superior a metade do espaço de armazenamento FTP total do seu plano de alojamento, recupere localmente determinados elementos volumosos do seu website (para isso, pode utilizar [Filezilla](/pages/web_cloud/web_hosting/ftp_filezilla_user_guide)). De seguida, elimine-os do seu espaço de armazenamento FTP. Isto diminuirá o tamanho do espaço de armazenamento FTP que utiliza e poderá então lançar o seu restauro a partir da Área de Cliente OVHcloud.
>

Aceda à informação correspondente ao método de restauração escolhido.

- “[Restaurar o espaço de armazenamento a partir da Área de Cliente](#viacontrolpanel).
- “[Restaurar um ficheiro a partir de um programa ou uma interface](#viainterface).

### Restaurar o espaço de armazenamento a partir da Área de Cliente <a name="viacontrolpanel"></a>

> [!warning]
>
> Este método de restauro não está disponível se o seu alojamento foi colocado no modo "manutenção" pelos nossos administradores ou se não dispõe das permissões de acesso FTP (permissões `chmod`) na sequência de uma ação da sua parte.
>
> As permissões `chmod` na raiz do seu alojamento devem ser obrigatórias em `705` para que este método funcione.
>

> [!primary]
> **Site em modo de manutenção**
> 
> Para determinar se o seu site foi colocado em modo "manutenção", consulte o nosso manual [O que fazer em caso de página “403 forbidden”?](/pages/web_cloud/web_hosting/diagnostic_403_forbidden). 
> 
> Nesse caso:
>
> - As nossas equipas enviam um e-mail ao [administrador](/pages/account_and_service_management/account_information/managing_contacts#aceder-a-area-de-gestao-dos-contactos) do alojamento. 
> - O estado "manutenção" aparece na sua [Área de Cliente OVHcloud](/links/manager){.external}. Na secção `Web Cloud`{.action}, clique no serviço na secção `Alojamento`{.action} e, a seguir, no separador `Informações gerais`{.action}.
> - O(s) site(s) alojado(s) apresenta(m) uma página "403 Forbidden".
>

Aceda à [Área de Cliente OVHcloud](/links/manager){.external}, clique em `Alojamentos`{.action} e escolha o nome do alojamento correspondente. Aceda à janela `FTP - SSH`{.action} e clique no botão `Restaurar um backup`{.action}.

![backupftp](/pages/assets/screens/control_panel/product-selection/web-cloud/web-hosting/ftp-ssh/restore-backup.png){.thumbnail}

Na janela que vai aparecer, terá de selecionar a data de restauração pretendida no menu pendente:

|Data apresentada|Data técnica da cópia de segurança|
|---|---|
|d-1|No mesmo dia, às 00h01 da manhã.|
|d-2|No dia anterior, às 00h01 da manhã.|
|d-3|Dois dias antes, às 00h01 da manhã.|
|1 semana|No domingo anterior, à 01h00 da manhã.|
|2 semanas|No domingo, duas semanas antes, à 01h00 da manhã.|

Depois de selecionar a data, clique no botão `Seguinte`{.action}. 

![backupftp](/pages/assets/screens/control_panel/product-selection/web-cloud/web-hosting/ftp-ssh/restore-backup-step-1.png){.thumbnail}

Certifique-se de que não perdeu nenhum ficheiro no processo de restauração (por exemplo, qualquer ficheiro que guardou no seu espaço de armazenamento após a data de restauração selecionada). Tal como indicado, a restauração vai apagar todos os dados atuais para os substituir pelos dados da cópia de segurança.

De seguida, clique no botão `Validar`{.action}.

> [!primary]
>
> O restauro automático pode demorar alguns minutos a algumas horas. Se a duração da ação for **mais de 24 horas**, contacte [o suporte da OVHcloud](/links/support).
>

### Restaurar um ficheiro a partir de um programa ou uma interface <a name="viainterface"></a>

Esta operação realiza-se em vários passos. Certifique-se de que tem a palavra-passe do utilizador FTP para aceder ao seu espaço de armazenamento. 

> [!warning]
>
> Para realizar as seguintes ações, deve ter conhecimentos sobre o programa ou a interface que vai utilizar. A seguir, propomos-lhe algumas indicações sobre como realizá-las. No entanto, se encontrar dificuldades, recomendamos que recorra a um [prestador de serviços especializado](/links/partner) e/ou que contacte o editor do programa ou da interface. Não poderemos proporcionar-lhe assistência técnica.
>

#### 1 - Escolher o programa ou a interface que vai utilizar

Em primeiro lugar, deve decidir qual o programa ou interface que vai utilizar para aceder à cópia de segurança do seu espaço de armazenamento. Se já decidiu, passe para o passo 2. Caso contrário, recomendamos que utilize uma destas três soluções:

- **FileZilla**: deverá descarregar este programa no website oficial. Para mais informações, consulte o manual [“Guia de utilização do FileZilla”](/pages/web_cloud/web_hosting/ftp_filezilla_user_guide){.external}. Este manual não substitui a documentação oficial do editor.

- **Cyberduck**: deverá descarregar este programa no website oficial. Para mais informações, consulte o manual [“Guia de utilização do Cyberduck (MAC)”](/pages/web_cloud/web_hosting/ftp_cyberduck_user_guide_on_mac){.external}. Este manual não substitui a documentação oficial do editor.

- **FTP Explorer**: deverá aceder previamente através da [Área de Cliente OVHcloud](/links/manager){.external}. Para aceder, basta iniciar sessão, clicar em `Alojamentos`{.action} na barra à esquerda e, em seguida, selecionar o alojamento correspondente. Aceda à janela `FTP - SSH`{.action} e clique no botão `Explorador FTP`{.action}.

Assim que estiver pronto para continuar a operação, avance para o passo seguinte.

![backupftp](/pages/assets/screens/control_panel/product-selection/web-cloud/web-hosting/ftp-ssh/ftp-explorer.png){.thumbnail}

#### 2 - Ligar-se à cópia de segurança

A partir da interface ou do programa selecionado, deverá ligar-se ao seu espaço de armazenamento para aceder aos dados da cópia de segurança que pretende recuperar. Para isso, deverá ter um nome de utilizador FTP, a respetiva palavra-passe e o nome de host do seu servidor FTP.

Pode consultar estas informações na janela `FTP - SSH`{.action} do seu alojamento. Caso não tenha a palavra-passe do utilizador FTP, consulte o manual [“Modificar a palavra-passe de um utilizador FTP”](/pages/web_cloud/web_hosting/ftp_change_password){.external}.

![backupftp](/pages/assets/screens/control_panel/product-selection/web-cloud/web-hosting/ftp-ssh/login-infos.png){.thumbnail}

Deverá adicionar um sufixo ao seu nome de utilizador (ou “login”) FTP principal, especificando a cópia de segurança à qual quer aceder. A seguir, poderá encontrar alguns exemplos sobre como aceder à cópia de segurança desejada.

|Data da cópia de segurança|Sufixo que deve adicionar|Exemplo de nome de utilizador completo|
|---|---|---|
|No mesmo dia, às 00h01 da manhã.|-snap0|utilizadorftp**-snap0**
|No dia anterior, às 00h01 da manhã.|-snap1|utilizadorftp**-snap1**
|Dois dias antes, às 00h01 da manhã.|-snap2|utilizadorftp**-snap2**
|No domingo anterior, à 01h00 da manhã.|-snap3|utilizadorftp**-snap3**
|No domingo, duas semanas antes, à 01h00 da manhã.|-snap4|utilizadorftp**-snap4**

Substitua a informação genérica “utilizadorftp” pelo seu nome de utilizador FTP principal. Mantenha o sufixo que define a cópia de segurança à qual pretende aceder.

A forma de se ligar ao espaço de armazenamento varia em função da interface ou do programa que utiliza. Abaixo, poderá ver uma imagem da janela de ligação da interface FTP Explorer.

![backupftp](/pages/assets/screens/other/web-tools/net2ftp/login-interface-snap0.png){.thumbnail}

#### 3 - Recuperar os ficheiros

Uma vez ligado, deve descarregar os ficheiros que pretende restaurar. Para isso, navegue pelo conteúdo do seu espaço de armazenamento e descarregue os ficheiros. A operação varia em função da interface ou do programa que utiliza.

Antes de avançar para o passo seguinte, certifique-se de que recuperou todos os ficheiros que pretende restaurar e, em seguida, termine a sessão no seu espaço de armazenamento.

> [!success]
>
> Se utilizar a interface do **FTP Explorer**, não hesite em consultar a [página de ajuda](https://net2ftp.cluster020.hosting.ovh.net/help.html){.external} para realizar corretamente a recuperação dos seus ficheiros. Esta página também está acessível através do botão `Help Guide`{.action} situado na parte inferior da interface de ligação ao **FTP Explorer**.
>
> Se utilizar outro software para aceder ao seu espaço de armazenamento FTP, recomendamos que consulte a documentação oficial do software para efetuar as operações corretas.
>

#### 4 - Restaurar os ficheiros

Depois de descarregar os ficheiros, ligue-se novamente ao seu espaço de armazenamento. Mas desta vez, não adicione nenhum sufixo ao utilizador FTP. Desta forma, acederá ao conteúdo atual do seu espaço de armazenamento e não a uma cópia de segurança anterior.

Uma vez ligado, só precisará de restaurar os ficheiros. Para isso, navegue pelo conteúdo do seu espaço de armazenamento até localizar os ficheiros e descarregue-os substituindo os ficheiros anteriores.

> [!success]
>
> Se utilizar a interface do **FTP Explorer**, não hesite em consultar a [página de ajuda](https://net2ftp.cluster020.hosting.ovh.net/help.html){.external} para realizar corretamente o restauro dos seus ficheiros. Esta página também está acessível através do botão `Help Guide`{.action} situado na parte inferior da interface de ligação ao **FTP Explorer**.
>
> Se utilizar outro software para aceder ao seu espaço de armazenamento FTP, recomendamos que consulte a documentação oficial do software para efetuar as operações corretas.
>

## Quer saber mais?

[Guia de utilização do FileZilla](/pages/web_cloud/web_hosting/ftp_filezilla_user_guide){.external}.

[Guia de utilização do Cyberduck (MAC)](/pages/web_cloud/web_hosting/ftp_cyberduck_user_guide_on_mac){.external}.

[Recuperar a cópia de segurança da base de dados de um alojamento web](/pages/web_cloud/web_hosting/sql_database_export)

Para serviços especializados (referenciamento, desenvolvimento, etc), contacte os [parceiros OVHcloud](/links/partner).

Se pretender usufruir de uma assistência na utilização e na configuração das suas soluções OVHcloud, consulte as nossas diferentes [ofertas de suporte](/links/support).

Fale com nossa [comunidade de utilizadores](/links/community).