---
weight: 110
title: "Explanation"
description: "Explanation of the creation of the \"About\" page."
icon: "article"
date: "2024-03-20T18:19:15Z"
lastmod: "2024-04-20T19:20:15Z"
draft: false
toc: true
---

This page aims to showcase how the About page was made.

Hugo generates the content of its static websites (mainly) through [Markdown](https://en.wikipedia.org/wiki/Markdown) files. Most of the features explained on this page serve as a Markdown overview. However, [Hugo](https://gohugo.io)'s additional functionalities will also be highlighted.

## Text

General text is written normally by writing our content without any tags or labels. For example:

{{< prism lang="md" >}}
This website's objective is to provide comprehensive (...)
{{< /prism >}}
{{< tabs tabTotal="0">}}
{{< /tabs >}}
Produces:
This website's objective is to provide comprehensive (...)

## Titles

Marking text as a title, subtitle, or a deeper title within the hierarchy is also done through the default Markdown way:

{{< prism lang="md" >}}
# About - This is a title
## Content - This is a subtitle
### Accessibility Features - This is a deeper subtitle within the hierarchy
#### Etc.
{{< /prism >}}
{{< tabs tabTotal="0">}}
{{< /tabs >}}

Hugo can parse this information into a Table of Contents - TOC (found on the right side of each page for this current theme). 
{{< alert context="warning" text="Most themes ignore Titles when generating the TOC since it should only be used on the top of the page, using only the rest of the hierarchy."/>}}

## Bullet Point Lists

A bullet point can be created by simply inserting a dash (" - ") before a line of text. Bullet point lists are a sequence of phrases, each preceded by " - ":

{{< prism lang="md" >}}
- Setup - Item One
- Features - Item Two  
- Etc. 
-Wrong use (missing a space after "-")
{{< /prism >}}
{{< tabs tabTotal="0">}}
{{< /tabs >}}
{{< alert context="warning" text="There should be a space in between the dash and the phrase to bullet point."/>}}

Although not used, there can also be sub-items inside a bullet point list:
- Item
    - Sub-Item
    - Sub-Item
- Item
    - Sub-Item
    
This can be achieved by:
{{< prism lang="md" >}}
- Item
    - Sub-Item
    - Sub-Item
- Item
    - Sub-Item
{{< /prism >}}
{{< tabs tabTotal="0">}}
{{< /tabs >}}
{{< alert context="warning" text="Only whitespaces can precede the dash when creating a bullet point. Visible characters will prevent a bullet point from being created."/>}}


## Highlights, Emphasis, Links

These functionalities are also achieved through Markdown's markup language.

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
{{< alert context="info" text="Only bold text was used in the About page; however, italic, bold italic, and crossed were also exemplified due to their markup similarity. More information on markdown syntax can be explored [here](https://www.markdownguide.org/basic-syntax/#overview)."/>}}

## Separators

There are two ways of drawing a separator:
{{< prism lang="md" >}}
***
and
---
{{< /prism >}}
{{< tabs tabTotal="0">}}
{{< /tabs >}}
{{< alert context="warning" text="In this Hugo theme, due to technical limitations, only the first way (***) should be used."/>}}

## Links

To associate a link to a word, the content of the link is placed in between brackets, followed by the actual URL, in between parentheses:
{{< prism lang="md" >}}
[Hugo](https://gohugo.io)
{{< /prism >}}
{{< tabs tabTotal="0">}}
{{< /tabs >}}
Which generates: [Hugo](https://gohugo.io)

## Hugo Functionalities

{{< alert context="warning" text="These following functionalities are Hugo-specific and may be unavailable in some themes."/>}}

### Tabs

The way to create basic multi-tab navigation components, like the one used in the "About" page, is the following:

{{< prism lang="md" >}}
{ {< tabs tabTotal="3">}}
{ {% tab tabName="Tab One" %}}

This is the content of Tab One.

{ {% /tab %}}
{ {% tab tabName="Tab Two" %}}

This is the content of Tab Two.

{ {% /tab %}}
{ {% tab tabName="Tab Three" %}}

This is the content of Tab Three.

{ {% /tab %}}
{ {< /tabs >}}
{{< /prism >}}
{{< tabs tabTotal="0">}}
{{< /tabs >}}

{{< alert context="warning" text="The space between the brackets on the start of each line (\"{ {(...)\") should be ignored. In this Hugo theme, due to technical limitations, the space needs to be inserted to showcase the code."/>}}
