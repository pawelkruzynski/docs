---
title: Object Storage Swift - 'Utilizar o Object Storage com o rClone'
updated: 2021-10-27
---

## Sumário

O Object Storage da OVH pode ser sincronizado via rClone.

**Este guia tem por objetivo apresentar os passos a efetuar para realizar essa sincronização na Área de Cliente OVH.**

O rClone é um software de sincronização externa. Desta forma, os detalhes de utilização desta ferramenta estão disponíveis para consulta na [documentação oficial](https://rclone.org/).

## Requisitos

- Ter criado o seu container *Object Storage* (na Área de Cliente ou no [Horizon - FR](/pages/storage_and_backup/object_storage/pcs_create_container){.external}).
- Ter criado um [utilizador OpenStack - FR](/pages/public_cloud/compute/create_and_delete_a_user).

## Instruções

Quando tiver criado o container e o utilizador OpenStack, já só precisa de fazer duas coisas:

- Obter o arquivo de configuração para o rClone:

Depois de ter criado o seu [utilizador OpenStack - FR](/pages/public_cloud/compute/create_and_delete_a_user){.external}, poderá, na Área de Cliente, obter o arquivo de configuração necessário para o rClone.

Para isso, na página dos utilizadores OpenStack da Área de Cliente, clique no símbolo da chave inglesa, que se encontra à direita do utilizador, e em `Fazer o download de um arquivo de configuração rClone`{.external}.

![Fazer download de um arquivo de configuração rClone](images/download_file.png){.thumbnail}

- Configurar o rClone:

Depois de fazer o download do arquivo, pode executar o comando que se segue, de forma a adicionar o seu novo espaço de armazenamento:

```sh
rclone config
```

Neste momento, será pedido que indique os dados de configuração apresentados no seu arquivo.

> [!primary]
>
> Pode também copiar e colar o conteúdo do seu arquivo no espaço previsto para as configurações do rClone (*.config/rclone/rclone.conf*).
>

Depois de efetuar a configuração, pode testá-la listando, por exemplo, os seus containers:

```sh
rclone lsd BackupStorage
```

*BackupStorage* corresponde ao nome dado ao seu espaço de armazenamento.

Encontrará no site oficial do rClone a documentação que apresenta os procedimentos a efetuar para sincronizar o seu Object Storage e o rClone: [Documentação oficial rClone](https://rclone.org/swift/){.external}.

## Quer saber mais?

Se precisar de formação ou de assistência técnica para implementar as nossas soluções, contacte o seu representante comercial ou clique em [esta ligação](/links/professional-services) para obter um orçamento e solicitar uma análise personalizada do seu projecto aos nossos especialistas da equipa de Serviços Profissionais.

Fale com a nossa comunidade de utilizadores: <https://community.ovh.com/en/>.
