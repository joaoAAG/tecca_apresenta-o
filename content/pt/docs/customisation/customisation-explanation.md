---
weight: 200
title: "Explicação"
description: "Explicação de como foi desenvolvida a página de Customização"
icon: "Transcribe"
date: "2024-03-20T18:19:15Z"
lastmod: "2024-04-20T19:20:15Z"
draft: false
toc: true
---

Esta página tem o propósito de mostrar como a página de personalização foi feita. A página de personalização já explica uma grande parte do código utilizado para criar a página. No entanto, esta página servirá como uma visão geral.

## Texto

Os textos descritivos são escritos normalmente, sem nenhuma tag, rótulo ou área. Por exemplo:

The code:
{{< prism lang="md" >}}
Texto simples.
{{< /prism >}}

## Títulos

Títulos e cabeçalhos são definidos usando `#` como prefixos. Quantomais `#`, menor é a posição na hierarquia dos títulos. Hugo tambéminterpreta os cabeçalhos e a respectiva hierarquia para criar aTabela de Conteúdos da página.

## Destaques, Ênfase, Links

Para alcançar texto em Negrito, o texto precisa ter dois asteriscos ou underlines antes e depois.

{{< prism lang="md" >}}
**NEGRITO**
__NEGRITO__
{{< /prism >}}

Para alcançar texto em Itálico, o texto precisa ter um asterisco ou underline antes e depois.

{{< prism lang="md" >}}
*ITALICO*
_ITALICO_
{{< /prism >}}

Para alcançar texto Rasurado, o texto precisa ter dois tils antes e depois.

{{< prism lang="md" >}}
~~RASURADO~~
{{< /prism >}}

Para links de websites:

{{< prism lang="md" >}}
[Nome a mostrar](https://website.com)
{{< /prism >}}

Para links de images:

{{< prism lang="md" >}}
![Create Content](https://tania1998.sirv.com/images_tecaa/green.png)
{{< /prism >}}

Hospedei minhas imagens no site [Sirv](https://my.sirv.com/#/browse/)para poder incluir os links no site.

## Separadores

Para separar áreas, usei três `-`

## Para criar alertas

Para criar alertas, adicionei o seguinte código entre dois colchetes `{{`.
O contexto dos alertas pode ser info, success, danger, warning, primary, light e dark.

{{< prism lang="md" >}}
< alert context= "dark" text="contexto do alerta"/>
{{< /prism >}}

## Para criar áreas de abas

Para criar uma navegação com várias abas nas páginas com um certo número de abas:

{{< prism lang="md" >}}
{ {< tabs tabTotal="nr de abas">}} --> abre abas, define número de abas
{ {% tab tabName="Aba Um" %}} --> nome da primeira aba

Conteúdo

{ {% /tab %}}
{ {% tab tabName="Aba Dois" %}} --> nome da segunda aba

Conteúdo

{ {% /tab %}}
{ {% tab tabName="Aba Três" %}} --> nome da terceira aba

Conteúdo

{ {% /tab %}}
{ {< /tabs >}} --> fecha abas
{{< /prism >}}

## Para adicionar blocos de código

{{< prism lang="md" >}}
    ```linguagem
    código
    ```
{{< /prism >}}

## Para criar tags

Adicione texto entre dois acentos graves `

{{< prism lang="md" >}}
`tag`
{{< /prism >}}
