---
weight: 100
title: "Customização"
description: "Guia geral sobre customização"
icon: "Tune"
date: "2024-03-20T18:19:15Z"
lastmod: "2024-04-20T19:20:15Z"
draft: false
toc: true
---
---

{{< alert icon="💡" context="success" text="Um guia rápido e básico para personalizar seu site de documentação com o Tema Lotus Docs para atender melhor às suas necessidades." />}}

---

## Requisitos

Antes de começar a personalizar seu site de documentação Hugo, é importante ter um conhecimentos básicos de:

- HTML
- CSS
- Markdown

## Personalização de Texto

Para criar sua página, é provável que você queira usar mecanismos básicos de destaque para o seu texto.

Você pode querer criar um cabeçalho, e para isso, você precisa usar o seguinte código:

```html
# Título
```

para definir outros cabeçalhos menores, você escreverá o seguinte:

```html
## Título2
### Título3
#### Título4
##### Título5
```

Quanto mais # à esquerda do seu texto, menor será o nível do cabeçalho.

Para adicionar Texto em Negrito, existem duas maneiras: texto a **negrito** ou texto a __negrito__, o que aqui você não pode ver a diferença quando renderizado, mas é feito da seguinte maneira:

```md
**assim** ou __assim__
```

Da mesma maneira que, texto em *Itálico* também pode ser conseguido de *duas maneiras distintas*

```md
*assim* ou _assim_
```

Adicionalmente, também é possivel adicionar texto ~~rasurado~~, para isso é necessário o seguinte código:

```md
~~rasurado~~
```

Para adicionar links, use colchetes `[]` para o texto a ser exibido e a URL entre parênteses

Por exemplo, você pode precisar adicionar um [link do Youtube](https://www.youtube.com/) e para fazer isso, você precisa adicionar o seguinte código:

```md
[link do Youtube](https://www.youtube.com/)
```

Para adicionar imagens, é muito semelhante à forma como implementamos URLs.

![Template Hero Landing Page](https://tania1998.sirv.com/images_tecaa/lotusdocs_hero.webp)

Basta usar `!` antes dos colchetes `[]` e colocar o link da imagem entre os parêntesis.

```md
![Template Hero Landing Page](https://tania1998.sirv.com/images_tecaa/lotusdocs_hero.webp)
```

## Alertas

Alertas geralmente são usados para exibir informações de forma destacada.
O Lotus Docs suporta `Alertas com contexto, Alertas com Ícones de Emoji personalizados, Alertas sem Ícones e a possibilidade de renderizar Markdown e HTML dentro de um Alerta.

### Alerts with Contex

O CONTEXT pode ser `info`, `success`, `danger`, `warning`, `primary`, `light` and `dark`. Para implementar um alerta, adicione o seguinte código, entre `{{chaves duplas }}`

```md
< alert context="context" text="This is an Alert with an emoji with the success context." />
```

Para usar os diferentes contextos de alerta, altere o valor do contexto para cada um dos seguintes:

`alert context= "info"`
{{< alert context= "info" text="Contexto do Alerta - Info"/>}}

`alert context= "success"`
{{< alert context= "success" text="Contexto do Alerta - Success"/>}}

`alert context= "danger"`
{{< alert context= "danger" text="Contexto do Alerta - Danger"/>}}

`alert context= "warning"`
{{< alert context= "warning" text="Contexto do Alerta - Warning"/>}}

`alert context= "primary"`
{{< alert context= "primary" text="Contexto do Alerta - Primary"/>}}

`Note: when in dark mode, light and dark alerts are inverted.`</p>

`alert context= "light"`
{{< alert context= "light" text="Contexto do Alerta - Light"/>}}

`alert context= "dark"`
{{< alert context= "dark" text="Contexto do Alerta - Dark"/>}}

### Alertas com Ícone de Emoji personalizado

Ainda usando o parâmetro de contexto, você pode alterar o ícone de Emoji que aparece à esquerda do texto do Alerta.
Para obter emojis, você só precisa copiar e colar emojis deste [website](https://getemoji.com/).

{{< alert icon="🤚🏻" context="success" text="Este é um Alerta com um emoji com o contexto de sucesso.." />}}
Para fazer isso, adicione o seguinte código, entre `{{chaves duplas}}`

```md
< alert icon="🤚🏻" context="success" text="Este é um Alerta com um emoji com o contexto de sucesso.." />
```

### Alertas sem Ícone

 Para obter um alerta sem ícone, defina apenas o parâmetro `icon` para um espaço vazio `alert icon=" "`

{{< alert icon=" " context= "danger" text="Alerta sem ícone com o contexto de perigo!"/>}}

### Renderizar Markdown e HTML dentro de um Alerta

Para fazer isso, certifique-se de que no ficheiro de configuração `hugo.toml`, o parâmetro `unsafe` esteja definido como `true` em `[markup.goldmark.renderer]`

```md
[markup.goldmark.renderer]
    unsafe = true
```

Agora, para renderizar Markdowns e HTML dentro de um Alerta, é necessário [emparelhar shortcodes](https://gohugo.io/content-management/shortcodes/) com delimitadores `%`, semelhante ao código seguinte:

```html
{{ alert icon="🎅🏼" context="success" }}
Este ***shortcode em pares*** alerta contém uma lista **markdown** e cabeçalho:

#### Minha Lista de Natal:
1. Uma boneca
2. Livros
3. Meias

Feliz Natal!
{{ /alert }}
```

o que **resulta** em:

{{% alert icon="🎅🏼" context="success" %}}
Este ***shortcode em pares*** alerta contém uma lista **markdown** e cabeçalho:

#### Minha Lista de Natal:
1. Uma boneca
2. Livros
3. Meias

Feliz Natal!
{{% /alert %}}

---

## Opções Principais do Site

### Ícones

#### Adicionar Ícones aos seus Títulos

Para adicionar ícones aos títulos de conteúdo, adicione ao ficheiro `hugo.toml` o seguinte:

```md
 [params.docs]
 titleIcon = true
```

O ícone que aparece como prefixo ao título do conteúdo será definido de acordo com a definição `icon:`no topo da página. Cada definição está relacionada a um ícone que pode ser visto nos  [Estilos de ícone do Google](https://fonts.google.com/icons?icon.style=Outlined&icon.platform=web);

#### Adicionar Ícones à barra lateral

Para adicionar ícones aos títulos de conteúdo da barra lateral, adicione ao ficheiro `hugo.toml` o seguinte: 

```md
 [params.docs]
 sidebarIcons = true
```

### Cor de destaque

Por padrão, o tema Lotus Docs tem uma cor de destaque azul, no entanto, você pode alterar a cor de destaque. Esta cor afeta links, botões e ícones.
Para fazer isso, vá para o ficheiro `hugo.toml`:

```md
 [params.docs]
 themeColor = "color"
```

Esta cor pode ser`blue`, `green`, `red`, `yellow`, `emerald`, `cardinal`, `magenta` and `cyan`. (pt: Azul, verde, vermelho, amarelo, esmeralda, cardeal, magenta e ciano);

{{< tabs tabTotal="8">}}
{{% tab tabName="azul" %}}

![Destaque azul](https://tania1998.sirv.com/images_tecaa/blue.png)

{{% /tab %}}
{{% tab tabName="verde" %}}

![Destaque verde](https://tania1998.sirv.com/images_tecaa/green.png)

{{% /tab %}}
{{% tab tabName="vermelho" %}}

![Destaque vermelho](https://tania1998.sirv.com/images_tecaa/red.png)

{{% /tab %}}
{{% tab tabName="amarelo" %}}

![Destaque amarelo](https://tania1998.sirv.com/images_tecaa/yellow.png)

{{% /tab %}}
{{% tab tabName="esmeralda" %}}

![Destaque esmeralda](https://tania1998.sirv.com/images_tecaa/emerald.png)

{{% /tab %}}
{{% tab tabName="cardeal" %}}

![Destaque cardeal](https://tania1998.sirv.com/images_tecaa/cardinal.png)

{{% /tab %}}
{{% tab tabName="magenta" %}}

![Destaque magenta](https://tania1998.sirv.com/images_tecaa/magenta.png)

{{% /tab %}}
{{% tab tabName="ciano" %}}

![Destaque ciano](https://tania1998.sirv.com/images_tecaa/cyan.png)

{{% /tab %}}
{{< /tabs >}}

### Modo Escuro

Por padrão, o modo escuro é definido como falso.
Para definir como verdadeiro por padrão, vá para o ficheiro `hugo.toml`.

```md
 [params.docs]
  darkMode = true
```

### Mudança de Fonte

Uma fonte é um conjunto de caracteres com um estilo e tamanho específicos, usados para exibir texto de maneira consistente, o que pode impactar o design geral e a sensação de um site.
O site Lotus Docs tem por padrão três conjuntos de fontes, `sans_serif_font`, `secondary_font` e `mono_font`.
Para mudar as fontes, adicione o seguinte código ao ficheiro `hugo.toml` :

```hugo
[params]
sans_serif_font = "Times New Roman"
secondary_font = "Calibri"
mono_font = "Arial"
```

Em cada parâmetro, você pode definir outra fonte e ver onde cada uma se aplica nas páginas.

#### Adicionar Fontes do Google

Para personalização adicional, você pode usar outras fontes que podem ser encontradas no [site Google Fonts](https://fonts.google.com/)

Para adicionar novas fontes, você precisa implementar uma matriz de fontes com o nome das fontes e os tamanhos
a carregar. Por exemplo, quero carregar as fontes [Montserrat](https://fonts.google.com/specimen/Montserrat?query=mont) e [Gluten](https://fonts.google.com/specimen/Gluten?query=gl) nos pesos 300 e 400
respectivamente

{{< alert context= "warning" text="As fontes têm seu próprio conjunto único de pesos, verifique antes de carregar as fontes."/>}}

no ficheiro `hugo.toml` implemente o seguinte código:

```md
[params]
    google_fonts = [["Montserrat", "300"],["Gluten", "400"]]
    sans_serif_font = "Gluten"
    secondary_font = "Montserrat"
    mono_font = "Arial"
```

Resultados da alteração das fontes:

{{< tabs tabTotal="2">}}
{{% tab tabName="Fontes Padrão" %}}

![Pagina com Fontes default](https://tania1998.sirv.com/images_tecaa/default_font.png)

{{% /tab %}}
{{% tab tabName="Fontes Personalizadas" %}}

![Pagina com Fontes personalizadas](https://tania1998.sirv.com/images_tecaa/custom_font.png)

{{% /tab %}}
{{< /tabs >}}

{{< alert context= "info" text="É possível personalizar ainda mais as fontes editando os ficheiros HTML e CSS do site. Convidamos você a explorar essa funcionalidade por conta própria!"/>}}

---

## Realce de Sintaxe

Para realçar e personalizar blocos de código, você pode usar Realce de Sintaxe.
É possível usar o [Prism](https://prismjs.com/), , que o Lotus Docs suporta ou o [Chroma](https://github.com/alecthomas/chroma) o realçador de código integrado do Hugo. </p>
 **Prism** stá habilitado por padrão usando o `param.docs.prism` no ficheiro `hugo.toml`. </p>
**Chroma**  é habilitado definindo no ficheiro `hugo.toml` em `[params.docs]`o seguinte: `prism = false` .

Ao usar blocos de código delimitados por três crases, especifique a linguagem de código ao lado da abertura das crases e o código será destacado automaticamente.

```html
 <html>
   <head>
     <title>Compre nossa nova camiseta!</title>
   </head>
   <body>
     <!-- Use action="/create-buy-session.php" if your server is PHP based. -->
     <form action="/create-buy-session" method="POST">
       <button type="submit">COMPRAR</button>
     </form>
   </body>
 </html>
```

### Results

{{< tabs tabTotal="2">}}
{{% tab tabName="Prism" %}}

[Prism Highlight](https://prismjs.com/) - Suporta ≈ 290 linguagens, verifique o site para mais informações.

```
[params.docs]
prism = true
```

![Tema Prism](https://tania1998.sirv.com/images_tecaa/Prism_default.png)

{{% /tab %}}
{{% tab tabName="Chroma" %}}

 [Chroma Highlight](https://github.com/alecthomas/chroma) - Suporta ≈ 200 linguagens, verifique o site para mais informações.

```md
[params.docs]
prism = false
```

![Tema Chroma](https://tania1998.sirv.com/images_tecaa/Chroma.png)

{{% /tab %}}
{{< /tabs >}}

### Personalizar Tema do Prism

Você também pode personalizar o tema do Prism alterando o parâmetro `prismTheme` em `[params.docs]` nos ficheiros de configuração.

Por exemplo, em `hugo.toml` você só precisa:

{{< tabs tabTotal="4">}}
{{% tab tabName="Lotusdocs" %}}

```md
[params.docs]
  prismTheme = "lotusdocs"
```

To get:
![Tema Prism Default](https://tania1998.sirv.com/images_tecaa/Prism_default.png)

{{% /tab %}}
{{% tab tabName="Solarized-light" %}}

```md
[params.docs]
  prismTheme = "solarized-light"
```

To get:
![Tema Prism Solarized Light](https://tania1998.sirv.com/images_tecaa/Prism_solarizedlight.png)

{{% /tab %}}
{{% tab tabName="Twilight" %}}

```md
[params.docs]
  prismTheme = "twilight"
```

To get:
![Tema Prism Twilight](https://tania1998.sirv.com/images_tecaa/Prism_twilight.png)

{{% /tab %}}
{{% tab tabName="Lucario" %}}

```md
[params.docs]
  prismTheme = "lucario"
```

To get:
![Tema Prism Lucario](https://tania1998.sirv.com/images_tecaa/Prism_lucario.png)

{{% /tab %}}
{{< /tabs >}}

---

## Modelos de Landing page

Atualmente, ao criar um site com o modelo Lotus Docs, a página de destino de um site Lotus Docs tem quatro seções pelas quais você pode rolar.
Cada uma das seções é um dos quatro modelos, cada um deles tem seu próprio conjunto de parâmetros para personalização.

{{< tabs tabTotal="4">}}
{{% tab tabName="Hero" %}}

O primeiro modelo mostrado é o Hero, é um modelo básico com duas seções. À esquerda texto e botões de Chamada Para Ação e à direita uma imagem.

Este `modelo Hero` pode ser configurável em 8 componentes, como ilustrado abaixo:

![Template Hero Landing Page](https://tania1998.sirv.com/images_tecaa/lotusdocs_hero.webp)

{{% /tab %}}
{{% tab tabName="Feature Grid" %}}

Uma lista de recursos, com várias linhas em uma grade de 3 colunas. Cada recurso listado na grade consiste em um ícone, título e texto descritivo.

Este `Modelo Feature Grid` pode ser configurável em 6 componentes, como ilustrado abaixo:

![Template Feature Grid Landing Page](https://tania1998.sirv.com/images_tecaa/lotus_featuregrid.webp)

{{% /tab %}}
{{% tab tabName="Imagem + Texto" %}}

Semelhante ao modelo Hero, este terceiro modelo exibe duas colunas, é um modelo básico com duas seções que podem exibir uma imagem, texto descritivo, listas e botões de Chamada para Ação.

Este `Modelo Imagem e Texto` pode ser configurável em 5 componentes, como ilustrado abaixo:

![Template Image e Texto Landing Page](https://tania1998.sirv.com/images_tecaa/lotus_imagetext.webp)

{{% /tab %}}
{{% tab tabName="Comparação de Imagem" %}}

Este último modelo utiliza a biblioteca[ImageCompareViewer](https://github.com/kylewetton/image-compare-viewer) para exibir imagens antes e depois, utilizando uma aba gerada automaticamente para deslizar entre os conjuntos de comparação de imagens.

Este `modelo de Comparação de Imagem` pode ser configurável em 5 componentes, como ilustrado abaixo:

![Template Comparação de Imagem Landing Page](https://tania1998.sirv.com/images_tecaa/lotus_imagecompare.webp)

{{% /tab %}}
{{< /tabs >}}

## Recursos Adicionais

- [Documentação Lotus Docs](https://lotusdocs.dev/)
