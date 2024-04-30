---
weight: 110
title: "Mermaid Page Explanation"
description: "Explanation of the creation of the \"Mermaid\" page."
icon: "article"
date: "2024-03-20T18:19:15Z"
lastmod: "2024-04-20T19:20:15Z"
draft: false
toc: true
---

This page serves to show how the Mermaid page was conceived. 

## Text

General text is written without any specific formatting or guidelines; simply typing the text will display it on the page.

{{< prism lang="md" >}}
Basic text.
{{< /prism >}}

---

Basic text.

## Titles

Applying text formatting such as title, subtitle, or deeper hierarchical titles is accomplished using the standard Markdown syntax:

Headers: Use hash symbols (#) for headers. The number of hash symbols indicates the level of the header (e.g., # for level 1, ## for level 2, and so on).

Example:

{{< prism lang="md" >}}
# Title
## Subtitle
### Deeper Subtitle
#### Etc.
{{< /prism >}}

## Prism 

**Prism** is a syntax highlighting library commonly used in Hugo themes to highlight code blocks in various programming languages.

It is used as:

{{< prism lang="md" >}}

< prism lang="md" >
Random content.
< /prism >

{{< /prism >}}


## Bullet Points

A bullet point is created by simply prefacing the sentence with "-" or "*".

Example:

{{< prism lang="md" >}}
- Content 

* Content 2 
{{< /prism >}}

---

Wich renders as:

- Content 

* Content 2 

#### Sub-items inside in a bullet point list:

{{< prism lang="md" >}}
- Item
    - Sub-Item
* Item 2
    - Sub-Item 2
{{< /prism >}}

---

Wich renders as:

- Item
    - Sub-Item
* Item 2
    - Sub-Item 2

## Highlights

These functionalities work the same as Markdown.

*Italic Text* is achieved through surrounding the excert with **1** asterisk on each side:
{{< prism lang="md" >}}
*Italic Text* is achieved through surrounding (...)
{{< /prism >}}

**Bold Text** is achieved through surrounding the excert with **2** asterisks on each side:
{{< prism lang="md" >}}
**Bold Text** is achieved through surrounding (...)
{{< /prism >}}

***Bold Italic Text*** is achieved through surrounding the excert with **3** asterisks on each side:
{{< prism lang="md" >}}
***Bold Italic Text*** is achieved through surrounding (...)
{{< /prism >}}

~~Crossed-Out Text~~ is achieved through surrounding the excert with **2** tildes on each side:
{{< prism lang="md" >}}
~~Crossed-Out Text~~ is achieved through surrounding (...)
{{< /prism >}}

These functionalities can also be mixed, generating outputs like: ***~~Crossed-Out, Bold, Italic Text~~***.

## Separators

There are two ways of drawing a separator:
{{< prism lang="md" >}}
***
and
---
{{< /prism >}}

## Links

To create a link, the content of the link is placed in between brackets, followed by the url, in between parentheses:
{{< prism lang="md" >}}
[Hugo](https://gohugo.io)
{{< /prism >}}

Which generates: [Hugo](https://gohugo.io)

## Alerts

To create an alert:

{{< prism lang="md" >}}
< alert context="primary" text="This is an alert"/>
{{< /prism >}}

---

Renders as:

{{< alert context="primary" text="This is an alert"/>}}


