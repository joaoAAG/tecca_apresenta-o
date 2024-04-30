---
weight: 110
title: "Explicação"
description: "Explicação da criação da página \"Sobre\"."
icon: "article"
date: "2024-03-20T18:19:15Z"
lastmod: "2024-04-20T19:20:15Z"
draft: false
toc: true
---

O objetivo desta página é mostrar como a página "Sobre" foi feita.

O Hugo gera o conteúdo dos seus websites estáticos (principalmente) através de ficheiros [Markdown](https://en.wikipedia.org/wiki/Markdown). A maioria das funcionalidades explicadas nesta página servem como uma visão geral de Markdown, no entanto, as funcionalidades adicionais do [Hugo](https://gohugo.io) também serão destacadas.

## Texto

O texto geral é escrito normalmente, apenas escrevendo o nosso conteúdo sem quaisquer tags ou rótulos. Por exemplo:

{{< prism lang="md" >}}
O objetivo deste website é fornecer uma explicação abrangente (...)
{{< /prism >}}
{{< tabs tabTotal="0">}}
{{< /tabs >}}
Produz:
O objetivo deste website é fornecer uma explicação abrangente (...)

## Títulos

Marcar texto como título, subtítulo ou um título mais profundo dentro da hierarquia também é feito através do modo padrão do Markdown:

{{< prism lang="md" >}}
# Sobre - Este é um título
## Conteúdo - Este é um subtítulo
### Funcionalidades de Acessibilidade - Este é um subtítulo mais profundo dentro da hierarquia
#### Etc.
{{< /prism >}}
{{< tabs tabTotal="0">}}
{{< /tabs >}}

O Hugo é capaz de analisar esta informação e criar uma Tabela de Conteúdos - TOC (encontrada no lado direito de cada página, para este tema atual).
{{< alert context="warning" text="A maioria dos temas ignora os Títulos ao gerar a TOC, pois deve ser usado apenas no topo da página, utilizando apenas o resto da hierarquia."/>}}

## Marcadores e Listas

Um marcador pode ser criado simplesmente inserindo um hífen (" - ") antes de uma linha de texto. Listas de marcadores são uma sequência de frases, cada uma precedida por " - ":

{{< prism lang="md" >}}
- Configuração - Item Um
- Funcionalidades - Item Dois  
- Etc. 
-Uso Errado (falta um espaço após "-")
{{< /prism >}}
{{< tabs tabTotal="0">}}
{{< /tabs >}}
{{< alert context="warning" text="Deve haver um espaço entre o hífen e a frase para criar um marcador."/>}}

Embora não utilizado, também pode haver sub-itens dentro de uma lista de pontos:
- Item
    - Sub-Item
    - Sub-Item
- Item
    - Sub-Item
    
O que pode ser alcançado por:
{{< prism lang="md" >}}
- Item
    - Sub-Item
    - Sub-Item
- Item
    - Sub-Item
{{< /prism >}}
{{< tabs tabTotal="0">}}
{{< /tabs >}}
{{< alert context="warning" text="Apenas espaços em branco podem preceder o hífen ao criar um marcador. Caracteres visíveis impedirão que um marcador seja criado."/>}}


## Destaques, Ênfase, Links

Estas funcionalidades também são alcançadas através da linguagem de normal do Markdown.

*Texto Itálico* é alcançado ao rodear o texto com **1** asterisco em cada lado:
{{< prism lang="md" >}}
*Texto Itálico* é alcançado ao rodear (...)
{{< /prism >}}

**Texto em Negrito** é alcançado ao rodear o texto com **2** asteriscos em cada lado:
{{< prism lang="md" >}}
**Texto em Negrito** é alcançado ao rodear (...)
{{< /prism >}}

***Texto em Negrito Itálico*** é alcançado ao rodear o texto com **3** asteriscos em cada lado:
{{< prism lang="md" >}}
***Texto em Negrito Itálico*** é alcançado ao rodear (...)
{{< /prism >}}

~~Texto Riscado~~ é alcançado ao rodear o texto com **2** tils em cada lado:
{{< prism lang="md" >}}
~~Texto Riscado~~ é alcançado ao rodear (...)
{{< /prism >}}

Estas funcionalidades também podem ser misturadas, gerando frases como: ***~~Texto Riscado, em Negrito, Itálico~~***.
{{< alert context="info" text="Apenas texto em negrito foi usado na página 'Sobre', no entanto, itálico, negrito itálico e riscado também foram exemplificados devido à sua semelhança de marcação. Mais informações sobre a sintaxe do markdown podem ser exploradas [aqui](https://www.markdownguide.org/basic-syntax/#overview)."/>}}

## Separadores

Existem duas formas de desenhar um separador:
{{< prism lang="md" >}}
***
e
---
{{< /prism >}}
{{< tabs tabTotal="0">}}
{{< /tabs >}}

{{< alert context="warning" text="Neste tema do Hugo, devido a limitações técnicas, apenas a primeira forma (***) deve ser usada."/>}}

## Funcionalidades do Hugo

{{< alert context="warning" text="As seguintes funcionalidades são específicas do Hugo e podem não estar disponíveis em alguns temas."/>}}

### Abas

A forma de criar componentes de navegação com várias abas básicas, como a usada na página "Sobre", é a seguinte:

{{< prism lang="md" >}}
{ {< tabs tabTotal="3">}}
{ {% tab tabName="Aba Um" %}}

Este é o conteúdo da Aba Um

{ {% /tab %}}
{ {% tab tabName="Aba Dois" %}}

Este é o conteúdo da Aba Dois

{ {% /tab %}}
{ {% tab tabName="Aba Três" %}}

Este é o conteúdo da Aba Três

{ {% /tab %}}
{ {< /tabs >}}
{{< /prism >}}
{{< tabs tabTotal="0">}}
{{< /tabs >}}

{{< alert context="warning" text="O espaço entre as chavetas no início de cada linha (\"{ {(...)\") deve ser ignorado. Neste tema do Hugo, devido a limitações técnicas, o espaço precisa de ser inserido para mostrar o código."/>}}
