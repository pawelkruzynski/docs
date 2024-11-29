---
title: 'Web Cloud Databases - Como gerir os logs?'
excerpt: 'Saiba como gerir os logs das suas bases de dados alojadas no seu servidor Web Cloud Databases'
updated: 2024-11-25
---

## Objetivo

Um log corresponde a um evento ocorrido num sistema informático (servidor, computador, aplicação, website, base de dados, rede informática, etc.).
Por exemplo, um log pode registar e conter um ou vários dos seguintes elementos:

- O carimbo temporal (data, hora, minuto, segundo, etc.) do evento.
- A natureza do evento (ligação, encerramento de sessão, erro, download, upload, alerta, etc.).
- Informações adicionais sobre o evento (página ou arquivo acessado, aplicativo iniciado, servidor remoto chamado, nome do arquivo carregado ou baixado etc.)
- A origem do evento (ID do utilizador, endereço IP de origem, programa de origem, etc.).
- O estado do sistema onde o evento está a ocorrer (recursos disponíveis, memória restante, utilização da CPU, etc.).

Na maior parte dos casos, os logs são gerados diretamente pelos sistemas informáticos onde os eventos se realizam.
São armazenados e analisados em ficheiros de texto também chamados ficheiros de logs.

Por este motivo, os ficheiros de logs permitem efetuar as seguintes ações:

- Analisar o comportamento do sistema informático que gera os logs.
- Identificar os erros ocorridos no sistema informático.
- Resolver erros encontrados no sistema de computador.
- Otimizar e melhorar o desempenho do sistema informático.

Assim, o seu serviço [Web Cloud Databases](/links/web/databases) gera os seus próprios logs.

Em certas situações, poderá ter de consultar / recuperar os logs:

- do seu servidor Web Cloud Databases;
- para uma das bases de dados alojadas no seu servidor Web Cloud Databases.

**Descubra como visualizar e gerir os logs do seu serviço Web Cloud Databases.**

## Requisitos

- Ter uma solução [Web Cloud Databases](/links/web/databases).
- Ter acesso à [Área de Cliente OVHcloud](/links/manager).

## Instruções

> [!warning]
>
> Nós disponibilizamos-lhe este tutorial a fim de o acompanhar nas tarefas mais comuns. No entanto, se encontrar dificuldades, recomendamos que recorra a um [fornecedor especializado](/links/partner). Não poderemos proporcionar-lhe assistência na interpretação dos logs disponíveis com a sua solução Web Cloud Databases. Mais informações na secção "[Quer saber mais?](#go-further)" deste tutorial.
>

### Visualizar os logs em tempo real do seu Web Cloud Databases

Para verificar em tempo real os logs da sua solução Web Cloud Databases, execute as seguintes ações:

1. Aceda à [Área de Cliente OVHcloud](/links/manager).
2. Na linha situada no topo da Área de Cliente, clique no separador `Web Cloud`{.action}.
3. Na coluna da esquerda, clique no menu pendente `Web Cloud Databases`{.action}.
4. Selecione a instância Web Cloud Databases em causa.
5. Na página que vai aparecer, clique no separador `Logs (registos)`{.action}.

![Web Cloud Databases](/pages/assets/screens/control_panel/product-selection/web-cloud/web-cloud-databases/logs/tab.png){.thumbnail}

É nesta consola integrada que encontrará, em tempo real, os logs da sua solução Web Cloud Databases.

> [!primary]
>
> Como já indicado, os logs só estão disponíveis aqui em tempo real. Isto significa que estes logs apenas aparecerão se forem gerados no momento em que se encontrar no separador `Logs (registos)`{.action}. 
>
> Se sair do separador `Logs (registos)`{.action} e voltar a abri-lo mais tarde, o histórico anteriormente apresentado desaparecerá.
>

### Obter o histórico dos logs da sua solução Web Cloud Databases

Para recuperar o histórico dos logs da sua solução Web Cloud Databases deverá ligar-se em SFTP.

> [!warning]
>
> Antes de se ligar, verifique se o endereço IP público do posto que utiliza é autorizado no seu servidor Web Cloud Databases, com a opção `SFTP` selecionada.
>
> Para verificar esta informação, obtenha o endereço IP público do seu ponto de acesso à Internet e consulte **Permitir um endereço IP** de [este manual](/pages/web_cloud/web_cloud_databases/starting_with_clouddb).
>

Para encontrar as informações de ligação em SFTP à sua solução Web Cloud Databases, realize as seguintes ações:

1. Aceda à [Área de Cliente OVHcloud](/links/manager).
2. Na linha situada no topo da Área de Cliente, clique no separador `Web Cloud`{.action}.
3. Na coluna da esquerda, clique no menu pendente `Web Cloud Databases`{.action}.
4. Selecione a solução Web Cloud Databases correspondente.
5. Na página que é apresentada, permaneça no separador `Informações gerais`{.action} e posicione-se no quadro intitulado `Informações da ligação`{.action}.
6. Abaixo da menção `SFTP`{.action}, encontrará todas as informações necessárias para se ligar em SFTP.

> [!primary]
>
> Se não souber qual será a `Palavra-passe do servidor`{.action}, clique no botão `...`{.action} à direita para a alterar.
>

![Web Cloud Databases](/pages/assets/screens/control_panel/product-selection/web-cloud/web-cloud-databases/general-information/sftp-login.png){.thumbnail}

Quando tiver recuperado as credenciais de acesso SFTP, ligue-se através de um cliente FTP (FileZilla, Cyberduck, WinSCP, etc.).

Para o FileZilla, aceda ao menu em cima à esquerda `File`{.action} e clique em `Site Manager`{.action}.

Clique em `New site`{.action} e introduza os parâmetros indicados anteriormente.

![Web Cloud Databases](/pages/assets/screens/other/web-tools/filezilla/site-manager.png){.thumbnail}

O ficheiro de logs, chamado `stdout.log`, encontra-se na raiz.

Poderá descarregá-lo para o seu computador para o consultar.

> [!primary]
>
> Na raiz SFTP do servidor Web Cloud Databases, poderá aparecer um ficheiro adicional de logs intitulado `slow-query.log`.
> Este ficheiro contém o histórico dos pedidos lentos que foram executados no servidor Web Cloud Databases. 
> 
> O valor predefinido é de 1 segundo nas soluções Web Cloud Databases na variável **long_query_time**.
> 
> Graças a este ficheiro, poderá otimizar os seus scripts e o conteúdo da(s) sua(s) base(s) de dados a fim de melhorar as performances dos seus diferentes serviços associados.
>

### Subscrever os logs da sua solução Web Cloud Databases no Logs Data Platform <a name="wcdb-ldp"></a>

[Logs Data Platform](/links/manage-operate/ldp) é uma plataforma que permite gerir os seus logs. Pode ser útil se dispõe de uma infraestrutura muito grande ou se os seus serviços geram inúmeros logs. De facto, esta plataforma foi concebida para facilitar a agregação e a gestão dos logs.

Ela funciona recuperando os logs gerados pela sua infraestrutura / os seus websites ou ainda as suas aplicações para, por exemplo:

- armazená-los;
- visualizá-los em painéis em tempo real;
- permitir que os utilizadores efetuem pedidos complexos;
- filtrá-los por data, aplicação, tipo ou conteúdo;

Para mais detalhes sobre o Logs Data Platform, consulte o guia de [introdução ao Logs Data Platform](/pages/manage_and_operate/observability/logs_data_platform/getting_started_introduction_to_LDP) (EN).

Uma vez que as soluções [Web Cloud Databases](/links/web/databases) podem ser utilizadas com numerosos serviços (alojamentos partilhados, VPS, servidores dedicados, etc.), estas podem, em complemento dos logs em tempo real já disponíveis, ser subscritas por fluxo de dados para o Logs Data Platform.

Para subscrever a solução Web Cloud Databases a um fluxo de dados no Logs Data Platform, execute as seguintes ações:

1. Aceda à [Área de Cliente OVHcloud](/links/manager).
2. Na linha situada no topo da Área de Cliente, clique no separador `Web Cloud`{.action}.
3. Na coluna da esquerda, clique no menu pendente `Web Cloud Databases`{.action}.
4. Selecione a instância Web Cloud Databases em causa.
5. Na página que vai aparecer, clique no separador `Logs (registos)`{.action}.
6. À direita da caixa onde são apresentados os logs em tempo real, clique no botão `Subscrever`{.action}.

![Web Cloud Databases](/pages/assets/screens/control_panel/product-selection/web-cloud/web-cloud-databases/logs/tab-subscribe.png){.thumbnail}

Na nova página que se abrir, e se dispuser de várias soluções Logs Data Platform na sua [Área de Cliente OVHcloud](/links/manager), selecione, na lista pendente situada imediatamente abaixo do botão intitulado `Adicionar um fluxo de dados`, a referência do Logs Data Platform com a qual deseja subscrever.

![Web Cloud Databases](/pages/assets/screens/control_panel/product-selection/web-cloud/web-cloud-databases/logs/data-stream.png){.thumbnail}

Ocorrem dois casos para subscrever a solução Web Cloud Databases.

#### Caso n°1 - Subscrever a um fluxo já existente na sua solução Logs Data Platform <a name="wcdb-ldp-case1"></a>

Se o fluxo em causa já existir, este aparecerá sob a forma de uma linha na tabela situada na parte inferior da página.
Neste caso preciso, e para subscrever a sua solução Web Cloud Databases a este fluxo existente, basta clicar no botão `Subscrever`{.action} à direita da linha correspondente ao fluxo em causa.

Após alguns segundos e se permanecer na mesma página, será apresentada uma mensagem na Área de Cliente a indicar que a subscrição foi criada com sucesso.

#### Caso n°2 - Subscrever um novo fluxo de dados na sua solução Logs Data Platform

Se o fluxo em causa ainda não existir, clique no botão `Adicionar um fluxo de dados`{.action}.
Será então reencaminhado para uma nova página da sua Área de Cliente OVHcloud que lhe permitirá criar e adicionar um novo fluxo de dados na sua solução Logs Data Platform.

![Web Cloud Databases](/pages/assets/screens/control_panel/product-selection/bare-metal-cloud/logs-data-platform/data-stream/add-data-stream.png){.thumbnail}

Caso seja necessário, consulte os nossos manuais "[Introdução ao Logs Data Platform](/pages/manage_and_operate/observability/logs_data_platform/getting_started_introduction_to_LDP)" (EN) e "[Iniciar rapidamente com Logs Data Platform](/pages/manage_and_operate/observability/logs_data_platform/getting_started_quick_start)" (EN) para realizar estas ações.

Depois de preencher os diferentes formulários e informações, clique no botão `Guardar`{.action}.

De seguida, será redirecionado para o separador `Fluxo de dados` da sua solução Logs Data Platform.

Só precisa de subscrever a solução Web Cloud Databases com o fluxo recentemente criado na solução Logs Data Platform.

Para isso, e tal como explicado [anteriormente](#wcdb-ldp), volte ao separador `Logs (registos)`{.action} da sua solução Web Cloud Databases para subscrever este novo fluxo de dados. Desta vez siga [Caso nº 1](#wcdb-ldp-case1) descrito acima.


## Quer saber mais? <a name="go-further"></a>

[Primeiros passos com o seu Web Cloud Databases](/pages/web_cloud/web_cloud_databases/starting_with_clouddb)

[Introdução ao Logs Data Platform](/pages/manage_and_operate/observability/logs_data_platform/getting_started_introduction_to_LDP) (EN)

[Iniciar rapidamente com Logs Data Platform](/pages/manage_and_operate/observability/logs_data_platform/getting_started_quick_start) (EN)
 
Para serviços especializados (referenciamento, desenvolvimento, etc), contacte os [parceiros OVHcloud](/links/partner).
 
Fale com nossa [comunidade de utilizadores](/links/community).