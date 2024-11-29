---
title: "Instalar Composer num alojamento web"
excerpt: "Saiba como instalar e dar os primeiros passos em Composer"
updated: 2023-02-24
---

## Objetivo

[Composer](https://getcomposer.org/){.external} é um gestor de dependências criado para a linguagem PHP. Permite aos programadores PHP incluir bibliotecas externas nos seus programas. "Composer" permitiu aos projetos PHP facilitar a distribuição de livrarias e a manutenção do seu código. Aliás, desde a criação desta ferramenta, foram propostas numerosas boas práticas de desenvolvimento no seio da comunidade PHP e melhoraram as livrarias da comunidade PHP. Estas boas práticas são documentadas sob a forma de [PSR](http://www.php-fig.org/){.external}.

**Descruba como instalar e dar os primeiros passos em Composer**

> [!warning]
>
> A OVHcloud disponibiliza serviços cuja configuração, gestão e responsabilidade lhe incumbem. Assim, deverá certificar-se de que estes funcionam corretamente.
> 
> Este manual fornece as instruções necessárias para realizar as operações mais habituais. No entanto, se encontrar dificuldades, recomendamos que recorra a um [fornecedor especializado](/links/partner) e/ou que contacte o editor do serviço. Não poderemos proporcionar-lhe assistência técnica. Para mais informações, aceda à secção [Quer saber mais?](#go-further) deste tutorial.
> 

## Requisitos

- Ter um [serviço de alojamento web](/links/web/hosting){.external} com acesso SSH.
- Ter acesso à [Área de Cliente OVHcloud](/links/manager){.external}.

## Instruções

Ligue-se ao seu alojamento partilhado através de SSH através do nosso manual sobre [a utilização do SSH com o seu alojamento web partilhado OVHcloud](/pages/web_cloud/web_hosting/ssh_on_webhosting).

Verifique se utiliza uma versão de PHP compatível em linha de comandos:

```bash
php — versão
```

Se esta não é a versão correta, pode configurar um alias:

```bash
alias php='/usr/local/php8.0/bin/php'
```

Recomendamos que permaneça na pasta raiz do seu alojamento para não tornar acessíveis ao público os ficheiros de "Composer". De seguida, execute este comando:

```bash
curl -sS https://getcomposer.org/installer | php
```

"Composer" está agora disponível no seu alojamento partilhado.

### Exemplos de utilização

Se deseja instalar **Symfony 2**, pode, por exemplo, executar o seguinte comando:

```bash
php comer.phar create-project symfony/framework-standard-edition my_project_name "2.7*"
```

Também pode utilizar a API da OVHcloud a partir do seu alojamento, utilizando o wrapper oficial. Para isso, adicione um ficheiro designado *composer.json* contendo a lista das dependências de que precisa. Eis um exemplo deste ficheiro com o wrapper da API OVHcloud:

```json
1. {
2.     "name": "Exemplo De Aplicação",
3.     "Descrição": "This is an example of OVHcloud APIs wrapper use",
4.     "tubarão": {
5.         "ovh/ovh": "1.1.*"
6.     }
7. }
```

Para o instalar, execute o seguinte comando na mesma pasta:

```bash
php composer.phar install
```

Para utilizar esta livraria, consulte a documentação, bem como o código, disponíveis em [GitHub](https://github.com/ovh/php-ovh){.external}

## Quer saber mais? <a name="go-further"></a>

Para serviços especializados (referenciamento, desenvolvimento, etc), contacte os [parceiros OVHcloud](/links/partner).

Se pretender usufruir de uma assistência na utilização e na configuração das suas soluções OVHcloud, consulte as nossas diferentes [ofertas de suporte](/links/support).

Fale com nossa [comunidade de utilizadores](/links/community).