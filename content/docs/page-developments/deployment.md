---
weight: 300
title: "Deployment"
description: "Documention for Deployment Pages"
icon: "article"
date: "2024-03-20T18:20:03Z"
lastmod: "2024-03-20T18:20:03Z"
draft: false
toc: true
---



## 1. Tabs





1. Add tabs to your content
    To add tabs, in the following format:


    {{< tabs tabTotal="1">}}
    {{% tab tabName="Tab example #1" %}}

    Contents of Tab 1

    {{% /tab %}}
    {{< /tabs >}}




2. Example code:


     You will need the following structure:



    ![Tabs structure](https://joaoaag.sirv.com/Images/lotus_tabs.png)




## 2. Images

How to add images.

1. First, you'll need to select a cloud hosting service for your image. Follow our example and choose SIRV.com.

2. Create a free account and upload your image

3. Copy your image path:

    ![Sirv.com Pages Settings](https://joaoaag.sirv.com/Images/lotus_sirv.png)

4. In your code, copy and paste the following code:

    ```yaml
        ![Create image content](/images/yourimage.png "Image Description")
    ```


{{< table >}}
| Code | Description |
|---------|--------|-----|
| `![image description]` | This is the alt text for the image. | 
| `(image_url)` | This is the URL or the path to your image.|
| `""` | This is the image deescription |
{{< /table >}}


## 3.Code Blocks:

Fenced code blocks (code contained by triple backticks above and below) that specify a code language (specified right of the opening fence) will automatically highlight the code content as HTML, eg: `'''yaml`, `'''toml`, `'''bash`:


{{< tabs tabTotal="3">}}
{{% tab tabName="Hugo.toml" %}}

```toml
baseURL = 'https://colinwilson.github.io'
languageCode = 'en-us'
title = 'My New Hugo Site'
```
{{% /tab %}}
{{% tab tabName="Hugo.yaml" %}}

```yaml
baseURL: 'https://colinwilson.github.io'
languageCode: en-us
title: My New Hugo Site
```
{{% /tab %}}
{{% tab tabName="Hugo.json" %}}

```json
{
  "baseURL": "https://colinwilson.github.io",
  "languageCode": "en-us",
  "title": "My New Hugo Site",
}
```
{{% /tab %}}
{{< /tabs >}}






Example for this:


{{< tabs tabTotal="3">}}
{{% tab tabName="Hugo.toml" %}}
````markdown
```toml
baseURL = 'https://colinwilson.github.io'
languageCode = 'en-us'
title = 'My New Hugo Site'
```
````

{{% /tab %}}
{{% tab tabName="Hugo.yaml" %}}

````markdown
```yaml
baseURL: 'https://colinwilson.github.io'
languageCode: en-us
title: My New Hugo Site
```
````

{{% /tab %}}
{{% tab tabName="Hugo.json" %}}

````markdown
```json
{
  "baseURL": "https://colinwilson.github.io",
  "languageCode": "en-us",
  "title": "My New Hugo Site",
}
```
````
{{% /tab %}}
{{< /tabs >}}




### 3.1. Code Fence:

Code fences significantly enhance the clarity and readability of code snippets within your technical documentation. They ensure that code blocks are presented in a visually distinct and easily scannable format.
We employ this technique in section 4 of the "Deployment: GitHub" page to highlight the line containing the `draft`.


{{< table >}}
| Code Fences | Description |
|---------|--------|-----|
| `linenos` | configure line numbers. Valid values are `true`, `false`, `table`, or `inline`. | 
| `hl_lines` | lists a set of line numbers or line number ranges to be highlighted.|
| `linenostart=1` | starts the line number count from 1. |
| `anchorlinenos` | Configure anchors on line numbers. Valid values are `true` or `false`. |
{{< /table >}}

So the following example:

````markdown {hl_lines=[1]}
```toml {linenos=table,hl_lines=[3,"1-2"],linenostart=1,anchorlinenos=true}
baseURL = 'https://colinwilson.github.io'
languageCode = 'en-us'
title = 'My New Hugo Site'
```
````

It will render as: 

```toml {linenos=table,hl_lines=[3,"1-2"],linenostart=1,anchorlinenos=true}
baseURL = 'https://colinwilson.github.io'
languageCode = 'en-us'
title = 'My New Hugo Site'
```





## 4. Alerts:

On deployment pages, we utilize alerts with an "info" context, like this:

{{< alert context="info" text=" This is an alert with an <strong>info</strong> context." />}}


````markdown
{{ < alert context="info" text="This is an alert with an <strong>info</strong> context. It consists of the info theme colour and icon." />}}
````




Additionally, we have other context options available: `success`, `danger`, `warning`, `primary`, `light`, and `dark`.




{{< alert context="success" text=" This is an alert with an <strong>success</strong> context." />}}


{{< alert context="danger" text=" This is an alert with an <strong>danger</strong> context." />}}



{{< alert context="warning" text=" This is an alert with an <strong>warning</strong> context." />}}



{{< alert context="primary" text=" This is an alert with an <strong>primary</strong> context." />}}



{{< alert context="light" text=" This is an alert with an <strong>light</strong> context." />}}



{{< alert context="dark" text=" This is an alert with an <strong>dark</strong> context." />}}

## 5. Links:

During the development of the prerequisites on the two pages, links were utilized to direct users to relevant resources.

1. To create a simple hyperlink to a website, use the following syntax:
    ```markdown
    [Link Text](URL)
    ```
2. Replace Link Text with the text you want to display for the link
    ```markdown
    [A GitHub Account](https://github.com/)
    ```
3. Final result:     [A GitHub Account](https://github.com/)




## 6. Treeview:


We utilized treeviews in point 8 to illustrate the expected project hierarchy structure.

````markdown
```shell
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
````