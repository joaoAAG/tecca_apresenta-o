---
weight: 200
title: "Setup"
icon: "rocket_launch"
date: "2024-03-20T18:19:36Z"
lastmod: "2024-04-20T18:19:36Z"
description: "A quick start guide to get started in Lotus Doc and how this page was made"
draft: false 
toc: true
tags: ["Beginners"]
author: "Paulo Rodrigues"
---

## System Requirements

- git
- Go ≥ v1.19
- Hugo ≥ v0.117.0 (Extended Version)

## Installation

### Auto Installation
Install the [Hugo CLI](https://github.com/gohugoio/hugo/releases/tag/v0.124.1), using the specific instructions for your operating system below:

{{< tabs tabTotal="4">}}
{{% tab tabName="Linux" %}}

Your Linux distro’s package manager may include Hugo. If this is the case, install it directly using your distro’s package manager – for instance, in Ubuntu, run the following command. This will install the extended edition of Hugo:

```shell
sudo apt install hugo
```

{{% /tab %}}

{{% tab tabName="Homebrew (macOS)"%}}

If you use the package manager [Homebrew](https://brew.sh/), run the brew install command in your terminal to install Hugo:


```shell
brew install hugo
```

{{% /tab %}}

{{% tab tabName="Windows (Chocolatey)"%}}

If you use the package manager [Chocolatey](https://chocolatey.org/), run the ``choco install`` command in your terminal to install Hugo:

```shell
choco install hugo --confirm
```

{{% /tab %}}


{{% tab tabName="Windows (Scoop)"%}}

If you use the package manager [Scoop](https://scoop.sh/), run the ``scoop install`` command in your terminal to install Hugo:

```shell
scoop install hugo
```

{{% /tab %}}

{{< /tabs >}}

### Manual Installation

The Hugo GitHub repository contains pre-built versions of the Hugo command-line tool for various operating systems, which can be found on the [Releases page](https://github.com/gohugoio/hugo/releases/tag/v0.124.1)

For more instruction on installing these releases, refer to [Hugo’s documentation](https://gohugo.io/installation/)

## Create a New Lotus Docs Site

(Explicar como criar novas paginas e com as configuras inicialmente)

With Hugo installed, create a new Hugo project using the ``hugo new`` command:

```shell
hugo new site my-docs-site && cd my-docs-site
```

Now use the ``hugo mod init`` command to initialize your project as a Hugo Module:

```shell
hugo mod init my-docs-site
```

{{< alert context="info" text="Note: You may initialize your site using the path to its git repository, for example, ``hugo mod init github.com/<user>/<my-docs-site>/``, if it already has one."/>}}

From the choices below, select your chosen way to apply the Lotus Docs theme to your newly created website:

{{< tabs tabTotal="3">}}
{{% tab tabName="Add as a Hugo Module" %}}

Lines ``5 through 11`` below need be edited to add the Hugo Bootstrap module and the Lotus Docs theme to the ``hugo.toml`` configuration file:

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

{{% tab tabName="Add as a Git submodule" %}}
Set up Git and create a submodule by cloning the Lotus Docs theme repository:

```shell
git init
git submodule add https://github.com/colinwilson/lotusdocs themes/lotusdocs
```

Replace the configuration in your current ``hugo.toml`` config file with the following:
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

{{% tab tabName="Clone theme files" %}}
You can clone the Lotus Docs theme into the ``themes`` subfolder of your project if you would rather modify and update the theme on your own.

To clone the Lotus Docs theme into your ``themes`` subfolder, use the following command from the root directory of your project:

```shell
git clone https://github.com/colinwilson/lotusdocs themes/lotusdocs
```

Lines ``5 through 14`` below need be edited to include the Hugo Bootstrap module and the Lotus Docs theme to the ``hugo.toml`` configuration file:

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

{{< alert context="info" text="Hugo ≥ v0.110.0 introduced ``hugo.toml`` as the default config base filename. Consider rename your ``config.toml`` file to ``hugo.toml`` if you're using a previous version of Hugo."/>}}
{{< /tabs >}}

## Create New Content

Create a file in the ``content/docs`` directory by navigating to the root of your Hugo project and using the ``hugo new`` command:

```shell
hugo new docs/new-page.md
```

This will produce the ``new-page.md`` markdown file with the default front matter as follows:

```shell
---
weight: 999
title: "New Page"
icon: "article"
date: "2024-04-17T18:19:36Z"
lastmod: "2024-04-17T18:19:36Z"
description: "This new page has the Lotus Documents theme"
draft: true 
toc: true
---
```

The front matter code that was used to generate this page is displayed in the code below, along with some markdown from the body:

{{< prism lang="md" >}}
---
weight: 200
title: "New Page"
icon: "article"
date: "2024-04-17T18:19:36Z"
lastmod: "2024-04-17T18:19:36Z"
description: "This new page has the Lotus Documents theme"
draft: true 
toc: true
publishdate: "2023-05-03T22:37:22+01:00"
tags: ["Beginners"]
---

## Create New Content

Navigate to the root of your Hugo project and use the `hugo new` command to create a file in the `content/docs` directory:

```shell
hugo new docs/examplepage.md
```
...
{{< /prism >}}

## Preview your Site

Using the ``hugo server -D`` command, you can now examine your new Lotus Documents website after creating some sample content:

```shell
hugo server -D
```

When you go to localhost:1313/docs/, a card link to the previously generated New Page should appear:
![Create Content](https://paulorodrigues-isep.sirv.com/TECAA/create_content.png)

## Configure Content

### Ordering Content

For content ordering and menu creation, Lotus Docs use a straightforward weighting system.

All content is arranged in a certain sequence and the menu structure (which includes the sidebar menu and page navigation buttons) is automatically generated using the front matter ``weight`` variable. Higher priority is assigned to lower weight values. Lower weight items are prioritized and arranged in this manner on the menu.

For example:

New Page:

```shell
---
weight: 200
title: "New Page"
icon: "article"
date: "2024-04-17T18:19:36Z"
lastmod: "2024-04-17T18:19:36Z"
description: "This new page has the Lotus Documents theme"
draft: true 
toc: true
tags: ["Beginners"]
publishdate: "2023-05-03T22:37:22+01:00"
---
```

New Page 2:

```shell
---
weight: 100
title: "New Page 2"
icon: "article"
date: "2024-04-17T18:19:36Z"
lastmod: "2024-04-17T18:19:36Z"
description: "This new page has the Lotus Documents theme"
draft: true 
toc: true
tags: ["Beginners"]
publishdate: "2023-05-03T22:37:22+01:00"
---
```

Result: 
![Ordening Content](https://paulorodrigues-isep.sirv.com/TECAA/Ordering_Content.png)

### Content description

It is imperative that the website provides readers with an understandable summary of its contents, complete with an educational headline and succinct explanation. The 'title' and 'description' variables can be changed to do this based on the theme of your website. For instance, the website may look something like this if its goal is to demonstrate how to use Lotus Docs to build up a basic configuration for documentation:

```shell
---
weight: 300
title: "Setup"
icon: "article"
date: "2024-03-20T18:19:36Z"
lastmod: "2024-03-20T18:19:36Z"
description: "A quick start guide to get started in Lotus Doc and how this page was made"
draft: true 
toc: true
---
```

And this would be the result:
![Content Description](https://paulorodrigues-isep.sirv.com/TECAA/Content_description.png)

### Content icon

You may alter the symbol that shows up in your page's layout to make it stand out from the rest and make the pages easier to distinguish from one another.

```shell
---
weight: 300
title: "Setup"
icon: "rocket_launch"
date: "2024-03-20T18:19:36Z"
lastmod: "2024-03-20T18:19:36Z"
description: "A quick start guide to get started in Lotus Doc and how this page was made"
draft: true 
toc: true
---
```

And this would be the result:
![Content Icon](https://paulorodrigues-isep.sirv.com/TECAA/Content_Icon.png)

If you want to see more about icons in Lotus Docs, you can consult the [Customization](docs/customisation/customisation.md) page

## Document title

You can create a file called "_index.md" if you need to rename your document's title from the "Docs" default to something more pertinent:

```shell
hugo new docs/_index.md
```

And now all you have to do is access the file ``_index.md`` and change the title:

```shell
---
weight: 999
title: "New Docs Title"
description: ""
icon: "article"
date: "2024-04-19T16:14:44+01:00"
lastmod: "2024-04-19T16:14:44+01:00"
draft: true
toc: true
---
```

And this is how it appears visually:
![New Docs Title](https://paulorodrigues-isep.sirv.com/TECAA/Docs_Title.png)


{{< alert context="info" text="Keep in mind that _index.md files are only meant to be used to modify header settings. It won't make a difference if you add any material that isn't among the variables allowed in the header."/>}}


## Second Level Menu Items

### Create Second Level

To build second level menu items, first create a directory called **"parent"** that has a file called ``_index.md``. For example:

```shell
hugo new docs/parent-directory/_index.md
```

An ``_index.md`` file is created by the aforementioned command within the ``content/docs/parent-directory`` directory:

```treeview
content/
└── docs/
    ├── parent-directory/
    │   └── _index.md
    ├── new-page.md
    ├── new-page-2.md
    ├── setup.md
    └── _index.md
```

### Add new page to second level

As before, second level items can now be created inside the parent directory. To make a post within the newly established ``parent-directory``, use the ``hugo new`` command once more:

```shell
hugo new docs/parent-directory/new-page-3.md
```

Your directory/file structure should now look like this:

```treeview
content/
└── docs/
    ├── parent-directory/
    │   ├── _index.md
    │   └── new-page-3.md
    ├── new-page.md
    ├── new-page-2.md
    ├── setup.md
    └── _index.md
```

And visually it will look like this:

Overall:
![Overall](https://paulorodrigues-isep.sirv.com/TECAA/overall.png)

In the `parent-directory` directory:
![Parent Directory](https://paulorodrigues-isep.sirv.com/TECAA/Parent_Directory.png)

### Config second level content

To configure content for the second level, the process is similar to that for the first level. Simply access the second level's _index.md file and adjust the title and description to provide more information about the specific content present at that level, helping the user with navigation and location.

```shell
---
weight: 999
title: "New Parent Directory"
description: "This is an example of how to create a second level"
icon: "article"
date: "2024-04-19T15:22:56+01:00"
lastmod: "2024-04-19T15:22:56+01:00"
draft: true
toc: true
---
```

And the result is like this:
![Parent Directory Description](https://paulorodrigues-isep.sirv.com/TECAA/New_Parent_Directory.png)

And to order the second level menu items is the same way as for the other contents, just change the ``weight`` of the ``_index.md`` file:
```shell
---
weight: 150
title: "New Parent Directory"
description: "This is an example of how to create a second level"
icon: "article"
date: "2024-04-19T15:22:56+01:00"
lastmod: "2024-04-19T15:22:56+01:00"
draft: true
toc: true
---
```

And with that, it changes position in the menu items
![Secund Level New Order](https://paulorodrigues-isep.sirv.com/TECAA/Secund_Level_New_Order.png)

## Publish pages

During the earlier stages of the process, we worked with draft pages. However, once a page is finished, you need to transform it from a draft into a ready-to-publish version. This process is simple: just modify the ``draft`` variable to ``false`` or, alternatively, ``remove this variable completely``. This ensures that the page is ready to publish.

Showing an example with the Setup page:
```shell
---
weight: 300
title: "Setup"
icon: "rocket_launch"
date: "2024-03-20T18:19:36Z"
lastmod: "2024-03-20T18:19:36Z"
description: "A quick start guide to get started in Lotus Doc and how this page was made"
draft: false 
toc: true
---
```

From this moment on, the page will be considered published. This means that when viewing the site preview, it will no longer be necessary to enter the ``hugo server -D`` command. Now, you can use the ``hugo server`` command to view all published pages, excluding those that are in draft.

Before proceeding, it is important to confirm that you have made changes to the ``first level _index.md`` file. If you have changed it, make sure the ``draft`` variable is set to ``false``. In our example, since we changed the title and the ``draft`` is marked as ``true``, we will need to modify this variable as well.

```shell
---
weight: 999
title: "New Docs Title"
description: ""
icon: "article"
date: "2024-04-19T16:14:44+01:00"
lastmod: "2024-04-19T16:14:44+01:00"
draft: false
toc: true
---
```

{{< alert context="info" text="Note: If you did not create a _index.md file for the first level because you did not need to modify any information, you do not need to create it to set the draft to false, as this is already the default value if _index.md does not have been created."/>}}

**Showing what the page preview looks like:**

When doing ``hugo server -D``:
![Preview Site Draft](https://paulorodrigues-isep.sirv.com/TECAA/preview_site_draft.png)

Here you can see that ``DRAFT`` has already disappeared from the setup page content, as well as from the document title

When doing ``hugo server``:
![Preview Site Publish](https://paulorodrigues-isep.sirv.com/TECAA/Preview_Site_Publish.png)

This is a very important step to later be able to [Deployed](/docs/deployment.md) your document

## License

Lotus Docs is distributed under the MIT license, which is an extremely flexible and permissive software license. Colin Wilson, the inventor of Lotus Docs, offers unrestricted freedom to anybody to use, modify, and distribute the program, provided that the copyright notice and license are included with all copies. Users can use the program for any purpose, including selling, without incurring any costs or royalties. There are no specific promises that the program will operate, and the authors are not liable for any harm caused by its usage. In brief, the MIT License gives users total freedom to use the program whatever they choose, with little duties or limits.

## Additional Resources

- [Lotus Docs](https://lotusdocs.dev/docs/overview/)
- [Lotus Docs GitHub](https://github.com/colinwilson/lotusdocs)

## FAQs
**1. Question:** How do I install Lotus Docs?

**Answer:** You can install Lotus Docs by following the instructions provided in the installation section of the documentation. Make sure to meet the system requirements and follow the appropriate installation method for your operating system.

**2. Question:** How do I create a new site using Lotus Docs?

**Answer:** The process of creating a new site with Lotus Docs is detailed in the "Create a New Lotus Docs Site" section. Follow the provided steps, including installing Hugo, initializing the project, and applying the Lotus Docs theme.

**3. Question:** How do I add new content to my Lotus Docs site?

**Answer:** You can add new content to your Lotus Docs site by creating new Markdown files in the content/docs folder. Use the hugo new command followed by the file path to create new content.

**4. Question:** How can I customize the appearance of my Lotus Docs site?

**Answer:** This question can be answered by viewing the [Customization page](docs/customisation/customisation.md).

**5. Question:** How do I publish a page on my Lotus Docs site?

**Answer:** Once a page is ready to be published, you need to change the ``draft`` variable to ``false`` in the corresponding Markdown file. This marks the page as ready for publishing and is detailed in the "Publish pages" section of the documentation.

**6. Question:** How was this page made?

**Answer:** You can see how this page was made by turning on the page: [Creation process Setup](docs/setup/setup-explanation.md)