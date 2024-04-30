---
weight: 100
title: "Customisation"
description: "General Guide about customization"
icon: "Tune"
date: "2024-03-20T18:20:39Z"
lastmod: "2024-03-20T18:20:39Z"
draft: false
toc: true
---
---

{{< alert icon="💡" context="success" text="A quick and basic guide to personalizing your documentation site with the Theme Lotus Docs to better suit your needs." />}}

---

## Requirements

Before you begin customizing your Hugo documentation site, it is essential to have a basic understanding of the following:

- HTML
- CSS
- Markdown

## Text Personalization

To create your page, you will likely use basic highlighting mechanisms for your text.

You might want to create a header, and for that, you need to use the following code:

```html
# Heading
```

To define other more minor headings, you'll write the following:

```html
## Heading2
### Heading3
#### Heading4
##### Heading5
```

The more `#` on the left of your text, the lower the level of the header.

There are two ways of adding bold text: **bold** text or **bold** text. You can't see the difference when rendered, but it's done as follows:

```md
**this** way or __this__ way
```

In the same way, *Italic* text can also be done *in two ways*

```md
*this* way or _this_ way
```

Additionally, you might need to add a ~~strikethrough~~ to the text, and for that, the code is as follows:

```md
~~strikethrough~~
```

To add links, use square brackets `[]` to display the text and the URL between the parenthesis.

For example, you might need to add a [Youtube link](https://www.youtube.com/), and to do this, you need to add the following code:

```md
[Youtube link](https://www.youtube.com/) 
```

Adding images is very similar to the way we implement the URLs.

![Printscreen LandingPage](https://tania1998.sirv.com/images_tecaa/lotusdocs_hero.webp)

Just use a `!` before the square brackets `[]` and add the link to the image between the parenthesis.

```md
![Printscreen LandingPage](https://tania1998.sirv.com/images_tecaa/lotusdocs_hero.webp)
```

## Alerts

Alerts are typically used to display information in a highlighted manner.
Lotus Docs support `Alerts with context, Alerts with custom Emoji Icons, Alerts with No Icons and the possibility to render Markdown and HTML inside an Alert.

### Alerts with Context

The CONTEXT can be `info,` `success,` `danger,` `warning,` `primary,` `light`, and `dark.` To implement one alert, add the following code between `{{double curly brackets }}`

```md
< alert context="context" text="This is an Alert with an emoji with the success context." />
```

To use the different alert contexts, change the context value for each one of the following:

`alert context= "info"`
{{< alert context= "info" text="Info alert context"/>}}

`alert context= "success"`
{{< alert context= "success" text="Success alert context"/>}}

`alert context= "danger"`
{{< alert context= "danger" text="Danger alert context"/>}}

`alert context= "warning"`
{{< alert context= "warning" text="Warning alert context"/>}}

`alert context= "primary"`
{{< alert context= "primary" text="Primary alert context"/>}}

`Note: When in dark mode, light and dark alerts are inverted.`</p>

`alert context= "light"`
{{< alert context= "light" text="Light alert context"/>}}

`alert context= "dark"`
{{< alert context= "dark" text="Dark alert context"/>}}

### Alerts with custom Emoji Icon

While still using the context parameter, you can change the Emoji icon on the left of the Alert text.
You only need to Copy and Paste emojis from this [Emoji](https://getemoji.com/) website to get emojis.

{{< alert icon="🤚🏻" context="success" text="This is an Alert with an emoji with the success context." />}}
To do this, add the following code between `{{double curly brackets }}`

```md
< alert icon="🤚🏻" context="success" text="This is an Alert with an emoji with the success context." />
```

### Alerts with no Icon

 To get an alert with no icon, only set the `icon` parameter to a space `alert icon=" "`

{{< alert icon=" " context= "danger" text="Alert with no icon with the danger context!"/>}}

### Render Markdown and HTML inside an Alert

To do this, ensure that in the `hugo.toml` configuration file, the parameter `unsafe` is set to `true` under the `[markup.goldmark.renderer].`

```md
[markup.goldmark.renderer]
  unsafe = true
```

Now, to render Markdowns and HTML inside and Alert, it is needed to [pair shortcodes](https://gohugo.io/content-management/shortcodes/) with `%` delimiters, as following:

```html
{{ alert icon="🎅🏼" context="success" }}
This ***paired shortcode*** alert contains a **markdown** list and header:

#### My Christmas List:
1. A doll
2. Books
3. Socks

Merry Christmas!
{{ /alert }}
```

which **results** in:

{{% alert icon="🎅🏼" context="success" %}}
This ***paired shortcode*** alert contains a **markdown** list and header:

#### My Christmas List

1. A doll
2. Books
3. Socks

Merry Christmas!
{{% /alert %}}

---

## Core Site Options

### Icons

#### Add Icons to your Headings

To add icons to content titles, add to the `hugo.toml` file the following:

```md
 [params.docs]
 titleIcon = true
```

The icon that shows as a prefix to the content title will be set according to the `icon:` definition at the top of the page. Each definition is related to an icon that can be seen in the [Google Icon styles](https://fonts.google.com/icons?icon.style=Outlined&icon.platform=web);

#### Add Icons to the sidebar

To add icons to the sidebar content titles, add to the `hugo.toml` file the following:

```md
 [params.docs]
 sidebarIcons = true
```

### Accent color

By default, the Lotus Docs theme has a blue accent color. However, you can change the accent color. This color affects links, buttons, and icons.
To do this, go to the `hugo.toml` file:

```md
 [params.docs]
 themeColor = "color"
```

This color can be `blue,` `green,` `red,` `yellow,` `emerald,` `cardinal,` `magenta`, or `cyan.`

{{< tabs tabTotal="8" aria-label="Accent Colors">}}
{{% tab tabName="blue" aria-selected="true" %}}

![Blue Accent Print](https://tania1998.sirv.com/images_tecaa/blue.png)

{{% /tab %}}
{{% tab tabName="green" %}}

![Green Accent Print](https://tania1998.sirv.com/images_tecaa/green.png)

{{% /tab %}}
{{% tab tabName="red" %}}

![Red Accent Print](https://tania1998.sirv.com/images_tecaa/red.png)

{{% /tab %}}
{{% tab tabName="yellow" %}}

![Yellow Accent Print](https://tania1998.sirv.com/images_tecaa/yellow.png)

{{% /tab %}}
{{% tab tabName="emerald" %}}

![Emerald Accent Print](https://tania1998.sirv.com/images_tecaa/emerald.png)

{{% /tab %}}
{{% tab tabName="cardinal" %}}

![Cardinal Accent Print](https://tania1998.sirv.com/images_tecaa/cardinal.png)

{{% /tab %}}
{{% tab tabName="magenta" %}}

![Magenta Accent Print](https://tania1998.sirv.com/images_tecaa/magenta.png)

{{% /tab %}}
{{% tab tabName="cyan" %}}

![Cyan Accent Print](https://tania1998.sirv.com/images_tecaa/cyan.png)

{{% /tab %}}
{{< /tabs >}}

### Dark Mode

By default, the dark mode is set to false.
To set it to true as default, go to the `hugo.toml` file:

```md
 [params.docs]
 darkMode = true
```

### Font changing

A font is a set of characters with a specific style and size used for displaying text in a
consistent manner, which can impact a website's overall design and feel.
The Lotus Docs website has, by default, three sets of fonts, `sans_serif_font,` `secondary_font`, and `mono_font.`
To change the fonts, add the following code to the file `hugo.toml` :

```hugo
[params]
sans_serif_font = "Times New Roman"
secondary_font = "Calibri"
mono_font = "Arial"
```

You can define another font in each parameter and see where each applies to the pages.

#### Add Google Fonts

For extra customization, you can use other fonts that can be found on the [Google Fonts site](https://fonts.google.com/)

To add new fonts, you need to implement an array of fonts with the name of the fonts and the sizes
to load. E.g. I want to load the [Montserrat](https://fonts.google.com/specimen/Montserrat?query=mont) and [Gluten](https://fonts.google.com/specimen/Gluten?query=gl) fonts, in the weights 300 and 400
respectively.

{{< alert context= "warning" text="Fonts have their unique set of weights, please confirm before loading fonts."/>}}

in the `hugo.toml` file implement the following code:

```md
[params]
  google_fonts = [["Montserrat", "300"],["Gluten", "400"]]
  sans_serif_font = "Gluten"
  secondary_font = "Montserrat"
  mono_font = "Arial"
```

That will change the Fonts from:

{{< tabs tabTotal="2">}}
{{% tab tabName="Default Fonts" %}}

![Site with Default Fonts](https://tania1998.sirv.com/images_tecaa/default_font.png)

{{% /tab %}}
{{% tab tabName="Customised fonts" %}}

![Site with Custom Fonts](https://tania1998.sirv.com/images_tecaa/custom_font.png)

{{% /tab %}}
{{< /tabs >}}

{{< alert context= "info" text="It is possible to customize the fonts even further by editing the website's HTML and CSS files. We invite you to explore this functionality on your own!."/>}}

---

## Syntax Highlighting

To enhance and personalize code blocks, you can use Syntax Highlighting.
 Its is possible to use [Prism](https://prismjs.com/), which Lotus Docs supports or [Chroma](https://github.com/alecthomas/chroma) the Hugo's built-in code highlighter. </p>
 **Prism** is enabled by default using the `param.docs.prism` in the file `hugo.toml`. </p>
**Chroma** is enabled by setting in the file `hugo.toml` under `[params.docs]` the following: `prism = false`.

When using fenced code blocks, enclosed by triple backticks, specify the code language next to the opening backticks, and the code will be automatically highlighted.

```html
 <html>
  <head>
   <title>Buy our new t-shirt!</title>
  </head>
  <body>
   <!-- Use action="/create-buy-session.php" if your server is PHP-based. -->
   <form action="/create-buy-session" method="POST">
    <button type="submit">BUY</button>
   </form>
  </body>
 </html>
```

### Results

{{< tabs tabTotal="2">}}
{{% tab tabName="Prism" %}}

[Prism Highlight](https://prismjs.com/) - Supports ≈ 290 languages, check website for more information.

```md
[params.docs]
prism = true
```

![Prism Theme Deafult](https://tania1998.sirv.com/images_tecaa/Prism_default.png)

{{% /tab %}}
{{% tab tabName="Chroma" %}}

 [Chroma Highlight](https://github.com/alecthomas/chroma) - Supports ≈ 200 languages, check website for more information.

```md
[params.docs]
prism = false
```

![Chroma Highlighter](https://tania1998.sirv.com/images_tecaa/Chroma.png)

{{% /tab %}}
{{< /tabs >}}

### Personalize Prism Theme

You can also personalize the Prism theme by changing the `prismTheme` parameter under `[params.docs]` in the config files.

For example, in `hugo.toml`, you only need to:

{{< tabs tabTotal="4">}}
{{% tab tabName="Lotusdocs" %}}

```md
[params.docs]
 prismTheme = "lotusdocs"
```

To get:
![Prism Theme Deafult](https://tania1998.sirv.com/images_tecaa/Prism_default.png)

{{% /tab %}}
{{% tab tabName="Solarized-light" %}}

```md
[params.docs]
 prismTheme = "solarized-light"
```

To get:
![Prism Theme Solarized Light](https://tania1998.sirv.com/images_tecaa/Prism_solarizedlight.png)

{{% /tab %}}
{{% tab tabName="Twilight" %}}

```md
[params.docs]
 prismTheme = "twilight"
```

To get:
![Prism Theme Twilight](https://tania1998.sirv.com/images_tecaa/Prism_twilight.png)

{{% /tab %}}
{{% tab tabName="Lucario" %}}

```md
[params.docs]
 prismTheme = "lucario"
```

To get:
![Prism Theme Lucario](https://tania1998.sirv.com/images_tecaa/Prism_lucario.png)

{{% /tab %}}
{{< /tabs >}}

---

## Landing page Templates

Currently, when creating a website with the Lotus Docs template, the landing page of a Lotus Docs website has four sections you can scroll through.
Each of the sections is one of four templates, and each has its own set of parameters for customization.

{{< tabs tabTotal="4">}}
{{% tab tabName="Hero" %}}

The first template shown is the hero, a basic template with two sections. On the left text and Call To Action buttons and the right a image.

This `Hero template` can be configurable in 8 components, as illustrated below:

![Hero Landing Page](https://tania1998.sirv.com/images_tecaa/lotusdocs_hero.webp)

{{% /tab %}}
{{% tab tabName="Feature Grid" %}}

A list of features with multiple rows in a 3-column grid. Each feature on the grid consists of an icon, title, and descriptive text.

This `Feature Grid template` can be configurable in 6 components, as illustrated below:

![Feature Grid Landing Page](https://tania1998.sirv.com/images_tecaa/lotus_featuregrid.webp)

{{% /tab %}}
{{% tab tabName="Image + Text" %}}

Similar to the Hero template, this third template displays two columns; it is a basic template with two sections that can display an image, descriptive text, lists, and Call to Action Buttons.

This `Image and Text template` can be configurable in 5 components, as illustrated below:

![Image and text Landing Page](https://tania1998.sirv.com/images_tecaa/lotus_imagetext.webp)

{{% /tab %}}
{{% tab tabName="Image Compare" %}}

This last template utilizes the [ImageCompareViewer](https://github.com/kylewetton/image-compare-viewer) library to display before and after images, using an auto-generated tab to slide between the image comparison sets.

This `Image Compare template` can be configurable in 5 components, as illustrated below:

![Image Compare Landing Page](https://tania1998.sirv.com/images_tecaa/lotus_imagecompare.webp)

{{% /tab %}}
{{< /tabs >}}

## Additional Resources

- [Lotus Docs Documentation](https://lotusdocs.dev/)
