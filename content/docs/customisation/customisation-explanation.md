---
weight: 200
title: "Explanation"
description: "Explanation of the creation of the Customisation page."
icon: "Transcribe"
date: "2024-03-20T18:19:15Z"
lastmod: "2024-04-20T19:20:15Z"
draft: false
toc: true
---

This page serves the purpose to showcase how the customization page was made. The customization page already explains a great part of the code utilized to create the page. However, this page will serve as a overview.

## Text

The descriptive texts are written normally without any tags, labels or areas. E.g

The code:
{{< prism lang="md" >}}
Simple text.
{{< /prism >}}
***
Renderizes as:
Simple text.

## Titles

Titles and headings are defined using `#` as prefixes. The more `#`the lower the position in the hierarchy of titles.
Hugo also intrepret the headings and respective hierarchy to create the Table of Contents for the page.

## Highlights, Emphasis, Links

To achieve bold text, the text needs to have two asterisks or underscores before and after.

{{< prism lang="md" >}}
**BOLD**
__BOLD__
{{< /prism >}}

To achieve ITALIC text, the text needs to have one asterisk or underscore before and after.

{{< prism lang="md" >}}
*ITALIC*
_ITALIC_
{{< /prism >}}

To achieve STRIKETHROUGH text, the text needs to have two tildes before and after.

{{< prism lang="md" >}}
~~STRIKETHROUGH~~
{{< /prism >}}

For website links:

{{< prism lang="md" >}}
[Name to display](https://website.com)
{{< /prism >}}

For image links:

{{< prism lang="md" >}}
![Create Content](https://tania1998.sirv.com/images_tecaa/green.png)
{{< /prism >}}

I hosted my images in [Sirv](https://my.sirv.com/#/browse/) to be able to include the links in the website.

## Separators

To separate areas, I used three `-`

## To create alerts

To create alerts, I added the following code between double curled `{{`.
The context of alerts can be info, success, danger, warning, primary, light and dark.

{{< prism lang="md" >}}
< alert context= "dark" text="alert context"/>
{{< /prism >}}

## To create tab areas

To create a multi tab naviagation in the pages with a certain number os tabs:

{{< prism lang="md" >}}
{ {< tabs tabTotal="nr of tabs">}} --> open tabs, define number of tabs
{ {% tab tabName="Tab One" %}} --> name of the first tab

Content

{ {% /tab %}}
{ {% tab tabName="Tab Two" %}} --> name of the second tab

Content

{ {% /tab %}}
{ {% tab tabName="Tab Three" %}} --> name of the third tab

Content

{ {% /tab %}}
{ {< /tabs >}} --> close tabs
{{< /prism >}}

## To add code blocks

{{< prism lang="md" >}}
    ```codelanguage
    code
    ```
{{< /prism >}}

## To create tags

Added text between two `

{{< prism lang="md" >}}
`tag`
{{< /prism >}}
