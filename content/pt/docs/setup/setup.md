---
weight: 200
title: "Configurar"
icon: "rocket_launch"
date: "2024-03-20T18:19:36Z"
lastmod: "2024-04-20T18:19:36Z"
description: "A quick start guide to get started in Lotus Doc and how this page was made"
draft: false 
toc: true
tags: ["Beginners"]
author: "Paulo Rodrigues"
---

## Requisitos do Sistema

- git
- Go ≥ v1.19
- Hugo ≥ v0.117.0 (Versão Estendida)

## Instalação

### Instalação Automática
Instale a [Hugo CLI](https://github.com/gohugoio/hugo/releases/tag/v0.124.1), seguindo as instruções específicas para o seu sistema operativo abaixo:

{{< tabs tabTotal="4">}}
{{% tab tabName="Linux" %}}

O gestor de pacotes da sua distribuição Linux pode incluir o Hugo. Se for o caso, instale-o diretamente usando o gestor de pacotes da sua distribuição - por exemplo, no Ubuntu, execute o seguinte comando. Isto irá instalar a edição estendida do Hugo:

```shell
sudo apt install hugo
```

{{% /tab %}}

{{% tab tabName="Homebrew (macOS)"%}}

Se utiliza o gestor de pacotes [Homebrew](https://brew.sh/), execute o comando brew install no terminal para instalar o Hugo:


```shell
brew install hugo
```

{{% /tab %}}

{{% tab tabName="Windows (Chocolatey)"%}}

Se utiliza o gestor de pacotes [Chocolatey](https://chocolatey.org/), execute o comando ``choco install`` no terminal para instalar o Hugo:

```shell
choco install hugo --confirm
```

{{% /tab %}}


{{% tab tabName="Windows (Scoop)"%}}

Se utiliza o gestor de pacotes [Scoop](https://scoop.sh/), execute o comando ``scoop install`` no terminal para instalar o Hugo:

```shell
scoop install hugo
```

{{% /tab %}}

{{< /tabs >}}

### Instalação Manual

O repositório GitHub do Hugo contém versões pré-compiladas da ferramenta de linha de comando do Hugo para vários sistemas operativos, que podem ser encontradas na [página de Releases](https://github.com/gohugoio/hugo/releases/tag/v0.124.1)

Para mais instruções sobre como instalar estas versões, consulte a [documentação do Hugo](https://gohugo.io/installation/)

## Criar um Novo Site de Documentação Lotus

(Explicar como criar novas páginas e com as configurações iniciais)

Com o Hugo instalado, crie um novo projeto Hugo usando o comando ``hugo new``:

```shell
hugo new site my-docs-site && cd my-docs-site
```

Agora utilize o comando ``hugo mod init`` para inicializar o seu projeto como um Módulo Hugo:

```shell
hugo mod init my-docs-site
```

{{< alert context="info" text="Nota: Pode inicializar o seu site utilizando o caminho para o seu repositório git, por exemplo, ``hugo mod init github.com/<user>/<my-docs-site>/``, se já tiver um."/>}}

Das opções abaixo, selecione o seu método preferido para aplicar o tema Lotus Docs ao seu novo site recém-criado:

{{< tabs tabTotal="3">}}
{{% tab tabName="Adicionar como um Módulo Hugo" %}}

As linhas de ``5 a 11`` abaixo precisam ser editadas para adicionar o módulo Bootstrap do Hugo e o tema Lotus Docs ao ficheiro de configuração ``hugo.toml``:

```shell
baseURL = 'http://example.org/'
languageCode = 'en-us'
title = 'My New Hugo Site'

[module]
    [[module.imports]]
        path = "github.com/colinwilson/lotusdocs"
        disable = false
    [[module.imports]]
        path = "github.com/gohugoio/hugo-mod-bootstrap-scss/v5"
        disable = false
```

{{% /tab %}}

{{% tab tabName="Adicionar como um submódulo Git" %}}
Configure o Git e crie um submódulo clonando o repositório do tema Lotus Docs:

```shell
git init
git submodule add https://github.com/colinwilson/lotusdocs themes/lotusdocs
```

Substitua a configuração no seu ficheiro de configuração ``hugo.toml`` atual com o seguinte:
```shell
baseURL = 'http://example.org/'
languageCode = 'en-us'
title = 'My New Hugo Site'

[module]
    # uncomment line below for temporary local development of module
    # or when using a 'theme' as a git submodule
    replacements = "github.com/colinwilson/lotusdocs -> lotusdocs"
    [[module.imports]]
        path = "github.com/colinwilson/lotusdocs"
        disable = false
    [[module.imports]]
        path = "github.com/gohugoio/hugo-mod-bootstrap-scss/v5"
        disable = false
```

{{% /tab %}}

{{% tab tabName="Clonar os ficheiros do tema" %}}
Pode clonar o tema Lotus Docs na subpasta ``themes`` do seu projeto se preferir modificar e atualizar o tema por conta própria.

Para clonar o tema Lotus Docs na sua subpasta ``themes``, utilize o seguinte comando a partir do diretório raiz do seu projeto:

```shell
git clone https://github.com/colinwilson/lotusdocs themes/lotusdocs
```

As linhas de ``5 a 14`` abaixo precisam ser editadas para incluir o módulo Bootstrap do Hugo e o tema Lotus Docs ao ficheiro de configuração ``hugo.toml``:

```shell
baseURL = 'http://example.org/'
languageCode = 'en-us'
title = 'My New Hugo Site'

[module]
    # uncomment line below for temporary local development of module,
    # when using a 'theme' as a git submodule or git cloned files
    replacements = "github.com/colinwilson/lotusdocs -> lotusdocs"
    [[module.imports]]
        path = "github.com/colinwilson/lotusdocs"
        disable = false
    [[module.imports]]
        path = "github.com/gohugoio/hugo-mod-bootstrap-scss/v5"
        disable = false
```


{{% /tab %}}

{{< alert context="info" text="Hugo ≥ v0.110.0 introduziu ``hugo.toml`` como o nome de ficheiro de configuração padrão. Considere renomear o seu ficheiro ``config.toml`` para ``hugo.toml`` se estiver a usar uma versão anterior do Hugo."/>}}
{{< /tabs >}}

## Criar Novo Conteúdo

Crie um ficheiro no diretório ``content/docs`` navegando até à raiz do seu projeto Hugo e utilizando o comando ``hugo new``:

```shell
hugo new docs/nova-pagina.md
```

Isto irá produzir o ficheiro markdown ``nova-pagina.md`` com o front matter padrão como segue:

```shell
---
weight: 999
title: "Nova Página"
icon: "article"
date: "2024-04-17T18:19:36Z"
lastmod: "2024-04-17T18:19:36Z"
description: "Esta nova página tem o tema Lotus Documents"
draft: true 
toc: true
---
```

O código do front matter que foi usado para gerar esta página é exibido no código abaixo, juntamente com algum markdown do corpo:

{{< prism lang="md" >}}
---
weight: 200
title: "Nova Página"
icon: "article"
date: "2024-04-17T18:19:36Z"
lastmod: "2024-04-17T18:19:36Z"
description: "Esta nova página tem o tema Lotus Documents"
draft: true 
toc: true
publishdate: "2023-05-03T22:37:22+01:00"
tags: ["Iniciantes"]
---

## Criar Novo Conteúdo

Navegue até à raiz do seu projeto Hugo e utilize o comando `hugo new` para criar um ficheiro no diretório `content/docs`:

```shell
hugo new docs/paginadeexemplo.md
```
...
{{< /prism >}}

## Pré-visualizar o seu Site

Utilizando o comando ``hugo server -D``, pode agora examinar o seu novo website Lotus Documents depois de criar algum conteúdo de exemplo:

```shell
hugo server -D
```

Quando aceder a localhost:1313/docs/, deverá aparecer um link de cartão para a página Nova Página gerada anteriormente:
![Criar Conteúdo](https://paulorodrigues-isep.sirv.com/TECAA/create_content.png)

### Configurar Conteúdo

### Ordenar Conteúdo

Para ordenação de conteúdo e criação de menu, o Lotus Docs utiliza um sistema de ponderação simples.

Todo o conteúdo é organizado numa determinada sequência e a estrutura do menu (que inclui o menu lateral e os botões de navegação da página) é gerada automaticamente utilizando a variável ``weight`` do front matter. Maior prioridade é atribuída a valores de peso mais baixos. Itens com peso mais baixo são priorizados e organizados desta forma no menu.

Por exemplo:

Nova Página:

```shell
---
weight: 200
title: "Nova Página"
icon: "article"
date: "2024-04-17T18:19:36Z"
lastmod: "2024-04-17T18:19:36Z"
description: "Esta nova página tem o tema Lotus Documents"
draft: true 
toc: true
tags: ["Iniciantes"]
publishdate: "2023-05-03T22:37:22+01:00"
---
```

Nova Página 2:

```shell
---
weight: 100
title: "Nova Página 2"
icon: "article"
date: "2024-04-17T18:19:36Z"
lastmod: "2024-04-17T18:19:36Z"
description: "Esta nova página tem o tema Lotus Documents"
draft: true 
toc: true
tags: ["Iniciantes"]
publishdate: "2023-05-03T22:37:22+01:00"
---
```

Resultado: 
![Ordenar Conteúdo](https://paulorodrigues-isep.sirv.com/TECAA/Ordering_Content.png)

### Descrição do Conteúdo

É imperativo que o site forneça aos leitores um resumo compreensível do seu conteúdo, completo com um título educacional e uma explicação sucinta. As variáveis 'title' e 'description' podem ser alteradas para fazer isso com base no tema do seu website. Por exemplo, o site pode parecer algo assim se o seu objetivo for demonstrar como usar o Lotus Docs para construir uma configuração básica para documentação:

```shell
---
weight: 300
title: "Configuração"
icon: "article"
date: "2024-03-20T18:19:36Z"
lastmod: "2024-03-20T18:19:36Z"
description: "Um guia rápido para começar no Lotus Doc e como esta página foi criada"
draft: true 
toc: true
---
```

E este seria o resultado:
![Descrição do Conteúdo](https://paulorodrigues-isep.sirv.com/TECAA/Content_description.png)

Se quiseres ver mais sobre os iconés no Lotus Docs, pode consultar a pagina de [Customização](docs/customisation/customisation.md)

### Ícone do Conteúdo

Pode alterar o símbolo que aparece no layout da sua página para destacá-la das restantes e tornar as páginas mais fáceis de distinguir entre si.

```shell
---
weight: 300
title: "Configuração"
icon: "rocket_launch"
date: "2024-03-20T18:19:36Z"
lastmod: "2024-03-20T18:19:36Z"
description: "Um guia rápido para começar no Lotus Doc e como esta página foi criada"
draft: true 
toc: true
---
```

E este seria o resultado:
![Ícone do Conteúdo](https://paulorodrigues-isep.sirv.com/TECAA/Content_Icon.png)

## Título do Documento

Pode criar um ficheiro chamado "_index.md" se precisar de renomear o título do seu documento do padrão "Docs" para algo mais pertinente:

```shell
hugo new docs/_index.md
```

E agora tudo o que precisa de fazer é aceder ao ficheiro ``_index.md`` e alterar o título:

```shell
---
weight: 999
title: "Novo Título dos Docs"
description: ""
icon: "article"
date: "2024-04-19T16:14:44+01:00"
lastmod: "2024-04-19T16:14:44+01:00"
draft: true
toc: true
---
```

E é assim que aparece visualmente:
![Novo Título dos Docs](https://paulorodrigues-isep.sirv.com/TECAA/Docs_Title.png)


{{< alert context="info" text="Tenha em mente que os ficheiros _index.md são apenas destinados a serem usados para modificar definições de cabeçalho. Não fará diferença se adicionar algum material que não esteja entre as variáveis permitidas no cabeçalho."/>}}

## Itens de Menu de Segundo Nível

### Criar Segundo Nível

Para construir itens de menu de segundo nível, primeiro crie um diretório chamado **"parent"** que tenha um ficheiro chamado ``_index.md``. Por exemplo:

```shell
hugo new docs/diretorio-pai/_index.md
```

Um ficheiro ``_index.md`` é criado pelo comando mencionado anteriormente dentro do diretório ``content/docs/diretorio-pai``:

```treeview
content/
└── docs/
    ├── diretorio-pai/
    │   └── _index.md
    ├── nova-pagina.md
    ├── nova-pagina-2.md
    ├── configuracao.md
    └── _index.md
```

### Adicionar nova página ao segundo nível

Como antes, os itens de segundo nível podem agora ser criados dentro do diretório pai. Para criar uma postagem dentro do recém-estabelecido ``diretorio-pai``, utilize novamente o comando ``hugo new``:

```shell
hugo new docs/diretorio-pai/nova-pagina-3.md
```

A sua estrutura de diretórios/ficheiros agora deve parecer assim:

```treeview
content/
└── docs/
    ├── diretorio-pai/
    │   ├── _index.md
    │   └── nova-pagina-3.md
    ├── nova-pagina.md
    ├── nova-pagina-2.md
    ├── configuracao.md
    └── _index.md
```

E visualmente parecerá assim:

No geral:
![Geral](https://paulorodrigues-isep.sirv.com/TECAA/overall.png)

No diretório `diretorio-pai`:
![Diretório Pai](https://paulorodrigues-isep.sirv.com/TECAA/Parent_Directory.png)

### Configurar conteúdo de segundo nível

Para configurar o conteúdo para o segundo nível, o processo é semelhante ao do primeiro nível. Basta aceder ao ficheiro _index.md do segundo nível e ajustar o título e a descrição para fornecer mais informações sobre o conteúdo específico presente nesse nível, ajudando o utilizador na navegação e localização.

```shell
---
weight: 999
title: "Novo Diretório Pai"
description: "Este é um exemplo de como criar um segundo nível"
icon: "article"
date: "2024-04-19T15:22:56+01:00"
lastmod: "2024-04-19T15:22:56+01:00"
draft: true
toc: true
---
```

E o resultado é assim:
![Descrição do Diretório Pai](https://paulorodrigues-isep.sirv.com/TECAA/New_Parent_Directory.png)

E para ordenar os itens de menu do segundo nível é da mesma forma que para os outros conteúdos, basta alterar o ``weight`` do ficheiro ``_index.md``:
```shell
---
weight: 150
title: "Novo Diretório Pai"
description: "Este é um exemplo de como criar um segundo nível"
icon: "article"
date: "2024-04-19T15:22:56+01:00"
lastmod: "2024-04-19T15:22:56+01:00"
draft: true
toc: true
---
```

E com isso, muda a posição nos itens do menu
![Nova Ordem de Segundo Nível](https://paulorodrigues-isep.sirv.com/TECAA/Secund_Level_New_Order.png)

## Publicar páginas

Durante as fases anteriores do processo, trabalhámos com páginas de rascunho. No entanto, assim que uma página estiver concluída, precisa de transformá-la de um rascunho numa versão pronta para publicar. Este processo é simples: basta modificar a variável ``draft`` para ``false`` ou, alternativamente, ``remover completamente esta variável``. Isso garante que a página está pronta para ser publicada.

Mostrando um exemplo com a página de Configuração:
```shell
---
weight: 300
title: "Configuração"
icon: "rocket_launch"
date: "2024-03-20T18:19:36Z"
lastmod: "2024-03-20T18:19:36Z"
description: "Um guia rápido para começar no Lotus Doc e como esta página foi criada"
draft: false 
toc: true
---
```

A partir deste momento, a página será considerada publicada. Isso significa que ao visualizar a pré-visualização do site, já não será necessário utilizar o comando ``hugo server -D``. Agora, pode utilizar o comando ``hugo server`` para ver todas as páginas publicadas, excluindo aquelas que estão em rascunho.

Antes de prosseguir, é importante confirmar que fez alterações ao ficheiro ``_index.md`` do primeiro nível. Se o tiver alterado, certifique-se de que a variável ``draft`` está definida como ``false``. No nosso exemplo, como alterámos o título e o ``draft`` está marcado como ``true``, também precisaremos de modificar esta variável.

```shell
---
weight: 999
title: "Novo Título dos Docs"
description: ""
icon: "article"
date: "2024-04-19T16:14:44+01:00"
lastmod: "2024-04-19T16:14:44+01:00"
draft: false
toc: true
---
```

{{< alert context="info" text="Nota: Se não criou um ficheiro _index.md para o primeiro nível porque não precisava de modificar nenhuma informação, não precisa de o criar para definir o rascunho como falso, pois este já é o valor padrão se _index.md não foi criado."/>}}

**Mostrando como fica a pré-visualização da página:**

Quando se faz ``hugo server -D``:
![Pré-visualização do Site Rascunho](https://paulorodrigues-isep.sirv.com/TECAA/preview_site_draft.png)

Aqui pode ver que ``DRAFT`` já desapareceu do conteúdo da página de configuração, assim como do título do documento.

Quando se faz ``hugo server``:
![Pré-visualização do Site Publicado](https://paulorodrigues-isep.sirv.com/TECAA/Preview_Site_Publish.png)

Este é um passo muito importante para mais tarde ser possível [Implantar](/docs/deployment.md) o seu documento.

## Licença

O Lotus Docs é distribuído sob a licença MIT, que é uma licença de software extremamente flexível e permissiva. Colin Wilson, o inventor do Lotus Docs, oferece liberdade irrestrita a qualquer pessoa para usar, modificar e distribuir o programa, desde que o aviso de direitos autorais e a licença sejam incluídos com todas as cópias. Os utilizadores podem utilizar o programa para qualquer fim, incluindo a venda, sem incorrer em custos ou royalties. Não existem promessas específicas de que o programa funcionará, e os autores não são responsáveis por qualquer dano causado pelo seu uso. Em resumo, a Licença MIT dá aos utilizadores total liberdade para usar o programa como desejarem, com poucas obrigações ou limites.

## Recursos Adicionais

- [Lotus Docs](https://lotusdocs.dev/docs/overview/)
- [GitHub do Lotus Docs](https://github.com/colinwilson/lotusdocs)

**1. Pergunta:** Como instalo o Lotus Docs?

**Resposta:** Pode instalar o Lotus Docs seguindo as instruções fornecidas na secção de instalação da documentação. Certifique-se de cumprir os requisitos do sistema e siga o método de instalação apropriado para o seu sistema operativo.

**2. Pergunta:** Como crio um novo site usando o Lotus Docs?

**Resposta:** O processo de criação de um novo site com o Lotus Docs está detalhado na secção "Criar um Novo Site Lotus Docs". Siga os passos fornecidos, incluindo a instalação do Hugo, inicialização do projeto e aplicação do tema Lotus Docs.

**3. Pergunta:** Como adiciono novo conteúdo ao meu site Lotus Docs?

**Resposta:** Pode adicionar novo conteúdo ao seu site Lotus Docs criando novos ficheiros Markdown na pasta content/docs. Utilize o comando hugo new seguido do caminho do ficheiro para criar novo conteúdo.

**4. Pergunta:** Como posso personalizar a aparência do meu site Lotus Docs?

**Resposta:** Esta pergunta pode ser respondida visualizando a página de [Customização](docs/customisation/customisation.md).

**5. Pergunta:** Como publico uma página no meu site Lotus Docs?

**Resposta:** Uma vez que uma página esteja pronta para ser publicada, precisa de alterar a variável ``draft`` para ``false`` no ficheiro Markdown correspondente. Isso marca a página como pronta para publicação e está detalhado na secção "Publicar páginas" da documentação.

**6. Pergunta:** Como foi feita esta página?

**Resposta:** Pode ver como esta página foi feita ativando a página: [Processo de criação Configuração](docs/setup/setup-explanation.md)