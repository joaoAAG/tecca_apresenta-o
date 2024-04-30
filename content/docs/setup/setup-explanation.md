---
weight: 100
title: "Setup - Explanation"
description: ""
icon: "article"
date: "2024-04-20T18:51:35+01:00"
lastmod: "2024-04-20T18:51:35+01:00"
draft: false
toc: true
author: "Paulo Rodrigues"
---

Here we will talk about how the Setup page was created

## List

For the list part, it's simple, just put the character "-" before the sentence and the list will be formed:

```shell
- git
- Go ≥ v1.19
- Hugo ≥ v0.117.0 (Extended Version)
```

## Tags

In sections 2.1 and 3, short code labels were used. These tags make it possible to create a menu that offers different information on the same topic. In our case, we use short code labels to present the different ways to automatically install Lotus Docs on different operating systems. This way, users no longer need to search for installation instructions specific to their operating system; just access the corresponding section and select your operating system.

To use tags, you must start by opening the tab using ``{{ < tabs tabTotal="n" > }}``, where "n" corresponds to the number of divisions required. For example, on the configuration page, we set "n" to 4 for section 2.1 and 3 for section 3. Next, we need to define the tab name using the code ``{{ % tab tabName="Linux" % }}``, and then you can insert the content of the tab. To finish dividing the tab, use ``{{ %/tab % }}``, and to close the entire tab section, use ``{{ </tabs > }}``.

{{< prism lang="md" >}}
{{ < tabs tabTotal="4"> }}
{{ % tab tabName="Linux" % }}

## content...

{{ % /tab % }}

## more tabs...

{{ < /tabs > }}
{{< /prism >}}

## Highlights and Emphasis

When writing texts, it is sometimes important to highlights specific parts so that users can better understand the key points of the sentences, such as important commands or codes. To do this, simply place the grave accent (``) at the beginning and end of the words you want to highlights.

Another way is to use asterisks (**), both before and after the words, making them bold and emphasize the sentence.

Examples of how this was used on the 'Setup' page:

{{< prism lang="md" >}}
...

To build second level menu items, first create a directory called **"parent"** that has a file called ``_index.md``. For example:

...
{{< /prism >}}

In this example, asterisks were used to emphasize the word **"parent"**, while grave accents were used to highlight a file.

## Links

During the process of creating the "Setup" page, it was also necessary to create links, both external and internal. For external links, the following code was used: ``[Word that will contain the link](URL of the external site)``. While for internal links, for example, this code was used: ``[Word that will contain the link](\docs\deployment)``.

## Lines of codes and commands

To differentiate code lines or commands and highlight them for users, we chose to use **shell** and the **prism** shortcode.

### Shell

**Shell** is a command-line interface that allows users to interact with an operating system via text. We used **shell** to indicate that these lines can be used as commands or code. An example used on the Setup page is:

{{< prism lang="shell" >}}

```shell
brew install hugo
```

{{< /prism >}}

This allows users to copy this line and paste it into their Linux terminals to install Hugo.

### Prism

**Prism** is a shortcode that highlights lines of code intended for text languages like ``Markdown`` and ``HTML``. In the creation of the Setup page, **prism** was used to avoid conflicts between commands. For example, when a snippet contained a **shell** command within another, we opted to use **prism** to ensure clarity and avoid confusion.

Example of using **prism**:

{{< prism lang="md" >}}
{{ < prism lang="md" > }}
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
{{ < /prism > }}
{{< /prism >}}

## Alerts

To highlight some important notes in the documentation, we used the Alert shortcode, as it allowed the creation of text boxes with different appearances. On the page in question, we opted for the **alert info**, which displays a box with blue-toned background and an "i" icon before the phrase, indicating additional information:

![Alert Example](https://paulorodrigues-isep.sirv.com/TECAA/Alert.png)

Here is an example of how to create an alert box.

```shell
{{ < alert context="info" text="Keep in mind that _index.md files are only meant to be used to modify header settings. It won't make a difference if you add any material that isn't among the variables allowed in the header."/> }}
```

## Images

To add images to the Setup page, we used the image hosting service [Sirv](https://my.sirv.com/), which offers free image hosting services. By hosting images on **Sirv**, we are able to improve the site's performance, as there's no need to render the images; **Sirv** does that for us, resulting in just displaying the images in our documentation.

Here's an example of how to display the image in the documentation:

```shell
![Preview Site Publish](https://paulorodrigues-isep.sirv.com/TECAA/Preview_Site_Publish.png)
```

The title of the image is within brackets `[]`, while the image URL is within parentheses `()`.

On **Sirv**, simply upload the image and then copy the link:

![Sirv Copy Link](https://paulorodrigues-isep.sirv.com/TECAA/Sirv_Copy_Link.png)

**Sirv** also offers image customization options, such as size, to improve site performance.

![Sirv Customization](https://paulorodrigues-isep.sirv.com/TECAA/customization.png)


## Treeview

Furthermore, **treeviews** were used in section 8. This is because the discussion about directories was addressed there, and **treeviews** are the best option for representing directory hierarchies. With them, it's possible to create a hierarchical view of folders, showing users how their files are organized in the end.

In section 8.1, the **treeview** was presented as follows:

{{< prism lang="md" >}}

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

{{< /prism >}}

This way, it was possible to show how the directory would look after creating a second level of folders.

![Treeview](https://paulorodrigues-isep.sirv.com/TECAA/Treeview.png)
