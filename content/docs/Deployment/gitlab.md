---
weight: 300
title: "GitLab Pages Deployment"
description: "How to make deployment to a gitlab repository"
icon: "code"
date: "2024-03-20T18:20:03Z"
lastmod: "2024-03-20T18:20:03Z"
draft: false
toc: true
---

## Overview

GitLab provides a comprehensive DevOps platform delivered as a single application, enabling teams to collaborate, manage, and accelerate the software development lifecycle. With built-in CI/CD, version control, and issue tracking, GitLab streamlines the development process and enhances team productivity.

## Prerequisites

1. [A GitLab Account](https://about.gitlab.com/)
2. [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
3. [Create a Hugo site using the Lotus Docs theme](https://lotusdocs.dev/docs/quickstart/#create-a-new-lotus-docs-site)

## Procedure

  1. Create a new repository on GitLab, e.g., `[https://gitlab.com/lordcodex/lotustheme_tecaa]`.

     Select GitLab Pages as the Project deployment target:

      ![GitLab Pages](https://joaoaag.sirv.com/Images/lotus_gitlab.png "Gitlabs blank repository")

  2. Create a new Hugo project using the hugo new command:

      ```bash
      hugo new site collinwilson.github.io
      cd colinwilson.github.io
      ```
      Initialize your project as a Hugo Module using the hugo mod init command:

      ```bash
      hugo mod init my-docs-site
      ```

  3.  Update your site’s config file (`hugo.toml` / `hugo.yaml` / `hugo.json`) to include the required theme modules and update your baseURL to your intended GitLab Pages domain e.g. colinwilson.gitlab.io. You can also configure a `[[menu.primary]]` item. This creates a link on the landing page to the docs/ section.

      {{< alert context="info" text="You can access the site's files via your command line interface. Various code editors, such as <strong>Notepad and VS Code</strong>, are available for use.  " />}}


      To open, for example, in Visual Studio Code:

      ```go
      code hugo.toml
      ```
      Or to open on notepad:
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

  4. Create some example content.

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

 5. Create an empty `.gitlab-ci.yml` file at the root of your local repository.
      ```shell
      /.gitlab-ci.aml
      ```

  6. Copy and paste the `YAML` below into the job file you created.
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
        

  7. Create a `.gitignore` file. Copy the contents below into it. This prevents your local /public directory (and other resources) being committed to to your GitLab repository.

      ```shell
      /public
      /assets/jsconfig.json
      resources/_gen/
      .hugo_build.lock
      ```

  8. Your site structure should now look similar to the one below:

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

  9. Use git int to initialize your project as a repository, then commit all the changes to your local repository with a commit message of something like “🎉 initial commit”. Push your local repo to the repository you created on GitLab in step 1.





  10. Revisit your repository on GitLab, navigate to Build > Pipelines, and you should see that your Hugo site was successfully built.





  11. You should now be able to see your site at the baseURL (e.g. https://colinwilson.gitlab.io) defined in your `hugo.toml` / `hugo.yaml` / `hugo.json` config file