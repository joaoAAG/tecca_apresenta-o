---
weight: 300
title: "GitHub Pages Deployment"
description: "How to make deployment to a gitlab repository"
icon: "code"
date: "2024-03-20T18:20:03Z"
lastmod: "2024-03-20T18:20:03Z"
draft: false
toc: true
---

## Overview

GitHub Pages provides quick, SSL-secured static hosting for personal, organizational, or project pages directly from a GitHub repository. Using [GitHub Actions](https://github.com/features/actions), this service simplifies development workflows and builds.

## Prerequisites

1. [A GitHub Account](https://github.com/)
2. [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
3. [Create a Hugo site using the Lotus Docs theme](https://lotusdocs.dev/docs/quickstart/#create-a-new-lotus-docs-site)

## Procedure

  1. Create a new repository 

      Create a new repository on GitHub, e.g., [https://github.com/joaoAAG/Tecaa.git](https://github.com/joaoAAG/Tecaa.git)

  2. Change GitHub Pages Source to GitHub Actions

      Visit your GitHub repository and navigate to `Settings > Pages`. Change the Source to GitHub Actions.

      ![GitHub Pages Settings](https://joaoaag.sirv.com/Images/lotus_github1.png "Build and deployment-Before")

      ![GitHub Pages Settings](https://joaoaag.sirv.com/Images/lotus_github2.png "Build and deployment-After")

  3. Create a Hugo server locally

     ```bash
      hugo new site collinwilson.github.io
      cd colinwilson.github.io
      ```
      1. Update your site’s config file (`hugo.toml` / `hugo.yaml` / `hugo.json`) to include the required theme modules and update your baseURL to your intended GitHub Pages 

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

  4. Create an example page

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

  5. Create an empty hugo.yaml file in your local repository

      ```bash
      .github/workflows/hugo.yaml
      ```

  6. Copy and paste the YAML below into the hugo.yaml you created. Change the branch name and Hugo version as needed.

     ```yaml
      # Sample workflow for building and deploying a Hugo site to GitHub Pages
      name: Deploy Hugo site to Pages

      on:
        # Runs on pushes targeting the default branch
        push:
          branches:
          - main

      # Allows you to run this workflow manually from the Actions tab
      workflow_dispatch:

      # Sets permissions of the GITHUB_TOKEN to allow deployment to GitHub Pages
      permissions:
        contents: read
        pages: write
        id-token: write

      # Allow only one concurrent deployment, skipping runs queued between the run in-progress and latest queued.
      # However, do NOT cancel in-progress runs as we want to allow these production deployments to complete.
      concurrency:
        group: "pages"
        cancel-in-progress: false

      # Default to bash
      defaults:
        run:
          shell: bash

      jobs:
        # Build job
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
              # For maximum backward compatibility with Hugo modules
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

        # Deployment job
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



  7. Commit all the changes to your local repository with a commit message of something like “New site & workflow”.

      ```bash
      git commit -m "New site & workflow"
      ```
      And push your local repo to the repository you created on GitHub

      ```bash
      git push -u origin main
      ```

      ```bash
      git commit -m "New site & workflow"
      git push -u origin main
      ```


  8. From GitHub’s main menu, choose Actions.

      ![GitHub actions](https://joaoaag.sirv.com/Images/lotus_github3.png "Under the deploy step, you will see a link to your live site 🎉.") 

