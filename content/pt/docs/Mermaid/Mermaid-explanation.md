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

Esta página serve para mostrar como foi concebida a página da Sereia. 

## Texto

O texto geral é escrito sem qualquer formatação ou directrizes específicas; basta escrever o texto para o mostrar na página.

{{< prism lang="md" >}}
Basic text.
{{< /prism >}}

---

Texto de base.

## Títulos

A aplicação de formatação de texto, como título, subtítulo ou títulos hierárquicos mais profundos, é realizada usando a sintaxe padrão do Markdown:

Cabeçalhos: Use símbolos de hash (#) para cabeçalhos. O número de símbolos de hash indica o nível do cabeçalho (por exemplo, # para o nível 1, ## para o nível 2, e assim por diante).

Exemplo:

{{< prism lang="md" >}}
# Title
## Subtitle
### Deeper Subtitle
#### Etc.
{{< /prism >}}

Texto de base.
## Prism 

**Prism** é uma biblioteca normalmente usada em temas do Hugo para realçar blocos de código em várias linguagens de programação.

Ela é usada como:

{{< prism lang="md" >}}

< prism lang="md" >
Random content.
< /prism >

{{< /prism >}}


## Pontos

Um marcador é criado simplesmente prefaciando a frase com “-” ou “*”.

Exemplo:

{{< prism lang="md" >}}
- Content 

* Content 2 
{{< /prism >}}

---

Que renderiza como:

- Content 

* Content 2 

#### Sub-itens dentro de uma lista de pontos:

{{< prism lang="md" >}}
- Item
    - Sub-Item
* Item 2
    - Sub-Item 2
{{< /prism >}}

---

Que renderiza como:

- Item
    - Sub-Item
* Item 2
    - Sub-Item 2

## Destaques 

Estas funcionalidades funcionam da mesma forma que o Markdown.

O *Texto em itálico* é obtido rodeando o excerto com **1** asterisco de cada lado:
{{< prism lang="md" >}}
*Italic Text* is achieved through surrounding (...)
{{< /prism >}}

O **Texto em negrito** é obtido rodeando o excerto com **2** asteriscos de cada lado:
{{< prism lang="md" >}}
**Bold Text** is achieved through surrounding (...)
{{< /prism >}}

O ***Texto em itálico e negrito*** é obtido rodeando o excerto com **3** asteriscos de cada lado:
{{< prism lang="md" >}}
***Bold Italic Text*** is achieved through surrounding (...)
{{< /prism >}}

O ~~Texto riscado~~ é obtido rodeando o excerto com **2** tildes de cada lado:
{{< prism lang="md" >}}
~~Crossed-Out Text~~ is achieved through surrounding (...)
{{< /prism >}}

Estas funcionalidades também podem ser misturadas, gerando resultados como: ***~~Texto riscado, negrito, itálico~~***.

## Separadores

Existem duas formas de renderizar um separador:
{{< prism lang="md" >}}
***
and
---
{{< /prism >}}

## Links

Para criar uma ligação, o conteúdo da ligação é colocado entre parênteses, seguido do url, entre parênteses:
{{< prism lang="md" >}}
[Hugo](https://gohugo.io)
{{< /prism >}}

Que vai gerar: [Hugo](https://gohugo.io)

## Alertas

Para criar um alerta:

{{< prism lang="md" >}}
< alert context="primary" text="This is an alert"/>
{{< /prism >}}

---

Que renderiza como:

{{< alert context="primary" text="This is an alert"/>}}


