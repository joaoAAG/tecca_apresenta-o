---
weight: 300
title: "Distribuição em páginas github"
description: "Como fazer a distribuição num repositório GitLab"
icon: "code"
date: "2024-03-20T18:20:03Z"
lastmod: "2024-03-20T18:20:03Z"
draft: false
toc: true
---

## Visão Geral

O GitHub Pages fornece hospedagem estática rápida e segura com SSL para páginas pessoais, organizacionais ou de projeto diretamente de um repositório do GitHub. Usando [GitHub Actions](https://github.com/features/actions), esse serviço simplifica fluxos de trabalho de desenvolvimento e construções.

## Pré-requisitos

1. [Uma Conta no GitHub](https://github.com/)
2. [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
3. [Crie um site Hugo usando o tema Lotus Docs](https://lotusdocs.dev/docs/quickstart/#create-a-new-lotus-docs-site)

## Procedimento

  1. Crie um novo repositório 

      Crie um novo repositório no GitHub, por exemplo, [https://github.com/joaoAAG/Tecaa.git](https://github.com/joaoAAG/Tecaa.git)

  2. Altere a Fonte do GitHub Pages para GitHub Actions

      Visite seu repositório do GitHub e navegue até `Configurações > Páginas`. Altere a Fonte para GitHub Actions.

      ![Configurações do GitHub Pages](https://joaoaag.sirv.com/Images/lotus_github1.png "Construção e Implantação-Antes")
      ![Configurações do GitHub Pages](https://joaoaag.sirv.com/Images/lotus_github2.png "Construção e Implantação-Depois")
  3. Crie um servidor Hugo localmente

     ```bash
      hugo new site collinwilson.github.io
      cd colinwilson.github.io
      ```
      1. Atualize o arquivo de configuração do seu site (`hugo.toml` / `hugo.yaml` / `hugo.json`) para incluir os módulos do tema necessários e atualize o seu baseURL para o seu GitHub Pages pretendido 

      {{< tabs tabTotal="3">}}
      {{% tab tabName="Hugo.toml" %}}


  ```toml
      baseURL = 'https://colinwilson.github.io'
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
baseURL: 'https://colinwilson.github.io'
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
     "baseURL": "https://colinwilson.github.io",
  "languageCode": "en-us",
  "title": "My New Hugo Site",
  "module": {
    "imports": [
      {
        "path": "github.com/colinwilson/lotusdocs",
        "disable": false
      },
      {
        "path": "github.com/gohugoio/hugo-mod-bootstrap-scss/ v5",
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

  4. Crie uma página de exemplo

      ```bash
      hugo new docs/example-page.md
      ```

      If the `draft` is true, then make it false.

      ```yaml {linenos=table,hl_lines=[4],anchorlinenos=true}
      ---
      title: "Example Page"
      date: 2023-08-25T23:36:29+01:00
      draft: false
      ---
      ```

  5. Crie um arquivo `hugo.yaml` vazio no seu repositório local

      ```bash
      .github/workflows/hugo.yaml
      ```

  6. Copie e cole o YAML abaixo no hugo.yaml que você criou. Altere o nome do branch e a versão do Hugo conforme necessário.

     ```yaml
      # Exemplo de fluxo de trabalho para construir e implantar um site Hugo no GitHub Pages
      name: Deploy Hugo site to Pages

      on:
        # Roda em push direcionando para o branch padrão
        push:
          branches:
          - main

      # Permite que você execute este fluxo de trabalho manualmente na guia Ações
      
      workflow_dispatch:

      # Define as permissões do GITHUB_TOKEN para permitir a implantação no GitHub Pages
      permissions:
        contents: read
        pages: write
        id-token: write

      # Permite apenas uma implantação concorrente, ignorando as execuções enfileiradas entre a execução em andamento e a última enfileirada.
      # No entanto, NÃO cancele execuções em andamento, pois queremos permitir que essas implantações de produção sejam concluídas.
      concurrency:
        group: "pages"
        cancel-in-progress: false

      # Padrão para bash
      defaults:
        run:
          shell: bash

      jobs:
        # Job de construção
        build:
          runs-on: ubuntu-latest
          env:
            HUGO_VERSION: 0.118.2
          steps:
          - name: Install Hugo CLI
             run: |
              wget -O ${{ runner.temp }}/hugo.deb https://github.com/gohugoio/hugo/releases/download/v${HUGO_VERSION}/hugo_extended_${HUGO_VERSION}_linux-amd64.deb \
              && sudo dpkg -i ${{ runner.temp }}/hugo.deb
          - name: Checkout
            uses: actions/checkout@v4
            with:
              submodules: recursive
              fetch-depth: 0
          - name: Setup Pages
            id: pages
            uses: actions/configure-pages@v3
          - name: Install Node.js dependencies
            run: "[[ -f package-lock.json || -f npm-shrinkwrap. json ]] && npm ci || true"
          - name: Build with Hugo
            env:
              # Para máxima compatibilidade retroativa com os módulos Hugo
              HUGO_ENVIRONMENT: production
              HUGO_ENV: production
            run: |
              hugo \
                  --gc \
                  --minify \
                  --baseURL "${{ steps.pages.outputs.base_url }}/"
          - name: Upload artifact
            uses: actions/upload-pages-artifact@v1
            with:
              path: ./public

        # Job de Implantação
        deploy:
          environment:
            name: github-pages
            url: ${{ steps.deployment.outputs.page_url }}
          runs-on: ubuntu-latest
          needs: build
          steps:
          - name: Deploy to GitHub Pages
            id: deployment
            uses: actions/deploy-pages@v2
      ```



  7. Confirme todas as mudanças no seu repositório local com uma mensagem de confirmação como "Novo site & fluxo de trabalho".

      ```bash
      git commit -m "Novo site & fluxo de trabalho"
      ```
      
      
      E envie seu repositório local para o repositório que você criou no GitHub

      ```bash
      git push -u origin main
      ```

      ```bash
      git commit -m "Novo site & fluxo de trabalho"
      git push -u origin main
      ```


  8. No menu principal do GitHub, escolha Ações.

      ![GitHub ações](https://joaoaag.sirv.com/Images/lotus_github3.png "Na etapa de implantação, você verá um link para seu site ativo 🎉.") 

