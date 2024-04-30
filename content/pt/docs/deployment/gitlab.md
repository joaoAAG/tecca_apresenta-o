---
weight: 300
title: "Distribuição em páginas gitlab"
description: "Como fazer a distribuição num repositório GitLab"
icon: "code"
date: "2024-03-20T18:20:03Z"
lastmod: "2024-03-20T18:20:03Z"
draft: false
toc: true
---

## Visão Geral

O GitLab fornece uma plataforma DevOps abrangente entregue como uma única aplicação, permitindo que equipes colaborem, gerenciem e acelerem o ciclo de vida do desenvolvimento de software. Com CI/CD integrado, controle de versão e rastreamento de problemas, o GitLab simplifica o processo de desenvolvimento e melhora a produtividade da equipe.

## Pré-requisitos

1. [Uma Conta no GitLab](https://about.gitlab.com/)
2. [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
3. [Crie um site Hugo usando o tema Lotus Docs](https://lotusdocs.dev/docs/quickstart/#create-a-new-lotus-docs-site)

## Procedimento

  1. Crie um novo repositório no GitLab, por exemplo, `[https://gitlab.com/lordcodex/lotustheme_tecaa]`.

     Selecione o GitLab Pages como o destino de implantação do projeto:

      ![GitLab Pages](https://joaoaag.sirv.com/Images/lotus_gitlab.png "Gitlabs blank repository")

  2. Crie um novo projeto Hugo usando o comando hugo new:

      ```bash
      hugo new site collinwilson.github.io
      cd colinwilson.github.io
      ```
      Inicialize seu projeto como um Módulo Hugo usando o comando hugo mod init:

      ```bash
      hugo mod init my-docs-site
      ```

  3.  Atualize o arquivo de configuração do seu site (`hugo.toml` / `hugo.yaml` / `hugo.json`) para incluir os módulos do tema necessários e atualize o seu baseURL para o seu domínio GitLab Pages pretendido, por exemplo, colinwilson.gitlab.io. Você também pode configurar um item `[[menu.primary]]`. Isto cria um link na página inicial para a seção docs/.

      {{< alert context="info" text="Você pode acessar os arquivos do site via interface de linha de comando. Vários editores de código, como <strong>Notepad e VS Code</strong>, estão disponíveis para uso." />}}

      Para abrir, por exemplo, no Visual Studio Code:

      ```go
      code hugo.toml
      ```
      Ou para abrir no notepad:
      ```go
      note hugo.toml
      ```



      {{< tabs tabTotal="3">}}
      {{% tab tabName="Hugo.toml" %}}

  ```toml
baseURL = 'https://colinwilson.gitlab.io'
languageCode = 'en-us'
title = 'My New Hugo Site'

[module]
    [[module.imports]]
        path = "github.com/colinwilson/lotusdocs"
        disable = false
    [[module.imports]]
        path = "github.com/gohugoio/hugo-mod-bootstrap-scss/v5"
        disable = false

[markup.goldmark.renderer]
    unsafe = true

[[menu.primary]]
    name  = "Docs"
    url = "/docs/"
    identifier = "docs"
    weight = 10
```
    {{% /tab %}}
    {{% tab tabName="Hugo.yaml" %}}

  ```yaml
baseURL: 'https://colinwilson.gitlab.io'
languageCode: en-us
title: My New Hugo Site
module:
  imports:
    - path: github.com/colinwilson/lotusdocs
      disable: false
    - path: github.com/gohugoio/hugo-mod-bootstrap-scss/v5
      disable: false
markup:
  goldmark:
    renderer:
      unsafe: true
menu:
  primary:
    - name: Docs
      url: /docs/
      identifier: docs
      weight: 10
```
    {{% /tab %}}
    {{% tab tabName="Hugo.json" %}}

  ```json
{
  "baseURL": "https://colinwilson.gitlab.io",
  "languageCode": "en-us",
  "title": "My New Hugo Site",
  "module": {
    "imports": [
      {
        "path": "github.com/colinwilson/lotusdocs",
        "disable": false
      },
      {
        "path": "github.com/gohugoio/hugo-mod-bootstrap-scss/v5",
        "disable": false
      }
    ]
  },
  "markup": {
    "goldmark": {
      "renderer": {
        "unsafe": true
      }
    }
  },
  "menu": {
    "primary": [
      {
        "name": "Docs",
        "url": "/docs/",
        "identifier": "docs",
        "weight": 10
      }
    ]
  }
}
```
    {{% /tab %}}
    {{< /tabs >}}

  4. Crie algum conteúdo de exemplo.

      ```bash
      hugo new docs/example-page.md
      ```

      ```yaml
      ---
      title: "Example Page"
      date: 2023-08-25T23:36:29+01:00
      draft: false
      ---
      ```

 5.  Crie um arquivo vazio `.gitlab-ci.yml` na raiz do seu repositório local.
      ```shell
      /.gitlab-ci.aml
      ```

  6. Copie e cole o `YAML` abaixo no arquivo de job que você criou
      ```yaml
        image: registry.gitlab.com/pages/hugo/hugo_extended:0.118.2

      variables:
        HUGO_ENV: production

      default:
        tags:
          - docker
          - linux
        before_script:
          - apk add --no-cache go curl bash nodejs
          # - hugo mod get -u $THEME_URL
          ## Uncomment the following if you use PostCSS. See https://gohugo.io/hugo-pipes/postcss/
          #- npm install postcss postcss-cli autoprefixer
    
      test:
        tags:
          - docker
          - linux
        script:
          - hugo
        rules:
          - if: $CI_COMMIT_REF_NAME != $CI_DEFAULT_BRANCH

      pages:
        tags:
          - docker
          - linux
        script:
          - hugo
        artifacts:
          paths:
            - public
        rules:
          - if: $CI_COMMIT_REF_NAME == $CI_DEFAULT_BRANCH
      ```
        

  7. Crie um arquivo .gitignore. Copie o conteúdo abaixo para ele. Isso impede que o seu diretório local /public (e outros recursos) seja confirmado no seu repositório do GitLab.

      ```shell
      /public
      /assets/jsconfig.json
      resources/_gen/
      .hugo_build.lock
      ```

  8. A estrutura do seu site deve ficar semelhante a esta:
      ```shell
      colinwilson.gitlab.io
      ├── archetypes
      ├── assets
      ├── content
      │   └── docs
      │       └── example-page.md
      ├── data
      ├── i18n
      ├── layouts
      ├── static
      ├── themes
      ├── .gitignore
      ├── .gitlab-ci.yml
      ├── .hugo_build.lock
      ├── go.mod
      ├── go.sum
      └── hugo.toml
      ```

  9. Use git init para inicializar seu projeto como um repositório, em seguida, confirme todas as alterações no seu repositório local com uma mensagem de commit como “🎉 commit inicial”. Envie seu repositório local para o repositório que você criou no GitLab no passo 1.





  10. Volte ao seu repositório no GitLab, navegue até Build > Pipelines, e você deverá ver que seu site Hugo foi construído com sucesso.





  11. Agora você deve ser capaz de ver seu site no baseURL (por exemplo, https://colinwilson.gitlab.io) definido no seu arquivo de configuração `hugo.toml` / `hugo.yaml` / `hugo.json`