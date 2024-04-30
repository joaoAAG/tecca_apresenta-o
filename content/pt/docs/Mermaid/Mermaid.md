---
weight: 200
title: "Mermaid"
description: ""
icon: "article"
date: "2024-03-20T18:20:39Z"
lastmod: "2024-03-20T18:20:39Z"
draft: false
toc: true
---

Bem-vindo à página sobre Mermaid.

## O que é o Mermaid? 

Mermaid é uma ferramenta de construção de diagramas e gráficos `baseada em JavaScript` que usa definições de texto com base na syntax Markdown e um renderizador para criar e modificar diagramas complexos. O principal objetivo do Mermaid é ajudar a documentação a acompanhar o desenvolvimento.

## Como usar o Mermaid com o Lotus Docs 

O Mermaid é ativado sempre que o conteúdo que contém a sintaxe do diagrama Mermaid está presente no conteúdo de uma página. É possível inserir diagramas Mermaid utilizando o identificador de linguagem Mermaid com blocos de código de "`" triplos:


{{< prism lang="md" >}}
 ```mermaid
---
title: Gráfico avançado
---
sequenceDiagram
Alice->>João: Olá João como estás?
loop Estado de saúde
    João->>João: Fight against hypochondria
end
Note right of João: Rational thoughts!
João-->>Alice: Ótimo!
João->>Pedro: Então e tu?
Pedro-->>João: Muito bem! 
```
{{< /prism >}}


```mermaid
---
title: Gráfico avançado
---
sequenceDiagram
Alice->>João: Olá João como estás?
loop Estado de saúde
    João->>João: A lutar contra febre
end
Note right of João: Pensamentos racionais!
João-->>Alice: Ótimo!
João->>Pedro: Então e tu?
Pedro-->>João: Muito bem! 
```

Este é um diagrama mais avançado, por isso vamos reduzi-lo a um simples fluxograma.

---

## Fluxograma

### O que é um Fluxograma

Um fluxograma é uma representação gráfica de um processo ou fluxo de trabalho, descrevendo a sequência de etapas, decisões e ações envolvidas. Normalmente, consiste em formas, setas e texto, ilustrando o fluxo de controlo através de um sistema.

Os fluxogramas são utilizados em vários domínios para criar uma mapa visual de procedimentos, analisar processos e comunicar fluxos de trabalho complexos.

### Criar Nós

Como já foi referido, os fluxogramas são compostos por nós. 

Para criar um nó:

{{< prism lang="md" >}}
```mermaid
---
title: Nó
---
flowchart LR
    id
```
{{< /prism >}}

```mermaid
---
title: Nó
---
flowchart LR
    id
```

### Fluxograma básico

O fluxograma mais básico consiste em criar uma implicação de x para y.

{{< prism lang="md" >}}
```mermaid
---
title: Fluxograma básico
---
flowchart LR
    x --> y
```
{{< /prism >}}

```mermaid
---
title: Fluxograma básico
---
flowchart LR
    x --> y
```

### Fluxograma de 1 para Muitos

{{< prism lang="md" >}}
```mermaid
---
title: Fluxograma de 1 para Muitos
---
flowchart LR
    x[a]
    y[b1,b2,b3]

    x --> y
```
{{< /prism >}}


```mermaid
---
title: Fluxograma de 1 para Muitos
---
flowchart LR
    x[a]
    y[b1,b2,b3]

    x --> y
```

### Costumizar o Flowchart

Existem várias formas de personalizar um fluxograma, desde alterar a forma dos nós, mudar a orientação e  até adicionar cores e ícones.


{{< prism lang="md" >}}
```mermaid
---
title: Fluxograma Especial
---
flowchart LR
    
    A[Borda dura] -->|Texto conetor| B(Borda redonda)
    B --> C{Decisão}:::vermelho
    C -->|One| D[Resultado um]:::azul
    C -->|Two| E[Resultado dois]:::verde
    
    classDef vermelho stroke:#f00
    classDef azul stroke:#0f0
    classDef verde stroke:#00f
```
{{< /prism >}}

```mermaid
---
title: Fluxograma Especial
---
flowchart LR
    
    A[Borda dura] -->|Texto conetor| B(Borda redonda)
    B --> C{Decisão}:::vermelho
    C -->|Um| D[Resultado um]:::azul
    C -->|Dois| E[Resultado dois]:::verde
    
    classDef vermelho stroke:#f00
    classDef azul stroke:#0f0
    classDef verde stroke:#00f
```
---

{{< alert context="primary" text="Toda a informação extra sobre Fluxogramas pode ser encontrada em: [Fluxograma](https://mermaid.js.org/syntax/flowchart.html)"/>}}

## Gráfico Circulrar

### O que é um gráfico circular

Um Gráfico Circular é um gráfico estatístico circular dividido em fatias para ilustrar proporções numéricas. Cada fatia representa uma parte proporcional de todo o conjunto de dados, normalmente apresentada como uma percentagem do total. Os gráficos de pizza são normalmente utilizados para visualizar a distribuição de dados e mostrar a dimensão relativa de diferentes categorias ou componentes num conjunto de dados. 

```mermaid
---
title: Animais adotados
---
pie

    "Cães" : 386
    "Gatos" : 85
    "Ratos" : 15
```

### Sintaxe do gráfico circular

Drawing a pie chart is really simple in mermaid.

* Iniciar com a palavra-chave pie para iniciar o diagrama
* ShowData para apresentar os valores reais dos dados após o texto da legenda. Isto é OPCIONAL
* Seguido da palavra-chave title e do seu valor em string para dar um título ao gráfico circular. Isto é OPCIONAL
* Seguido de dataSet. As fatias da tarte serão ordenadas no sentido dos ponteiros do relógio pela mesma ordem que as etiquetas.
* Etiqueta para uma secção do diagrama circular entre aspas “ ”.
* Seguido de : dois pontos como separador
* Seguido de um valor numérico positivo (suportado até duas casas decimais)

---

{{< alert context="primary" text="Toda a informação extra sobre Gráficos Circulares pode ser encontrada em: [Gráficos Circulares](https://mermaid.js.org/syntax/pie.html)"/>}}

### Gráfico circular básico

{{< prism lang="md" >}}
```mermaid
---
title: Gráfico circular básico
---
pie showData
    
    pie showData
    title Elementos chave em produto X
    "Cálcio" : 42.96
    "Potássio" : 50.05
    "Magnésio" : 10.01
    "Ferro" :  5
```
{{< /prism >}}


```mermaid
---
title: Gráfico circular básico
---
pie showData
    title Elementos chave em produto X
    "Cálcio" : 42.96
    "Potássio" : 50.05
    "Magnésio" : 10.01
    "Ferro" :  5
```

---

## Gráfico de Quadrante

### O que é um gráfico de quadrante

Um gráfico de quadrantes é uma representação gráfica que divide os dados em quatro quadrantes com base em dois eixos. Cada eixo representa uma dimensão ou variável diferente, e os quadrantes são definidos dividindo a área do gráfico em quatro secções iguais. 

Os gráficos de quadrantes são normalmente utilizados para analisar e visualizar relações de dados, particularmente quando se comparam dois conjuntos de variáveis ou critérios. Ajudam a identificar padrões, tendências e valores atípicos no conjunto de dados, permitindo aos utilizadores categorizar os pontos de dados em diferentes quadrantes com base nas suas posições relativamente aos eixos

```mermaid
quadrantChart
    title Alcance e Interesse nas campanhas
    x-axis Baixo Alcance --> Alto Alcance
    y-axis Baixo Interesse --> Alto Interesse
    quadrant-1 Deviamos expandir
    quadrant-2 Precisamos de promover
    quadrant-3 Reavaliar
    quadrant-4 Tem de ser melhorado
    Campanha A: [0.3, 0.6]
    Campanha B: [0.45, 0.23]
    Campanha C: [0.57, 0.69]
    Campanha D: [0.78, 0.34]
    Campanha E: [0.40, 0.34]
    Campanha F: [0.35, 0.78]
```
---

### Sintaxe do Gráfico de Quadrantes

* Title
O título é uma breve descrição do gráfico e será sempre apresentado na parte superior do gráfico

Exemplo:
quadrantChart
    title Isto é um gráfico exemplo

* `x-axis`
O eixo x determina o texto que será apresentado no eixo x. No eixo x existem duas partes, esquerda e direita, podendo passar ambas ou apenas a esquerda. A declaração deve começar com o eixo x, depois o texto do eixo esquerdo seguido do delimitador --> e depois o texto do eixo direito.

Exemplo 
x-axis <text> --> <text> tanto o texto do eixo esquerdo como o do eixo direito serão processados.
x-axis <text> apenas o texto do eixo esquerdo será processado.

* `y-axis`
O eixo y determina o texto que será apresentado no eixo y. No eixo y há duas partes, superior e inferior, podendo passar ambas ou apenas a inferior. A declaração deve começar com o eixo y, depois o texto do eixo inferior seguido do delimitador --> e depois o texto do eixo superior.

Exemplo
y-axis <text> --> <text> tanto o texto do eixo inferior como o do eixo superior serão processados.
y-axis <text> apenas o texto do eixo inferior será processado.

* `Quadrants text`
O quadrante-[1,2,3,4] determina o texto que será apresentado no interior dos quadrantes.

Exemplo 
quadrant-1 <text> determinam o texto que será apresentado no quadrante superior direito.
quadrant-2 <text> determinam o texto que será apresentado no quadrante superior esquerdo.
quadrant-3 <text> determina o texto que será apresentado no quadrante inferior esquerdo.
quadrant-4 <text> determina o texto que será apresentado no quadrante inferior direito.

* `Points`
Os pontos são utilizados para traçar um círculo no interior do quadrantChart. A sintaxe é <text>: [x, y], em que os valores x e y se situam no intervalo 0 - 1.

Exemplo 
Point 1: [0.75, 0.80] aqui o Ponto 1 será desenhado no quadrante superior direito.
Point 2: [0.35, 0.24] aqui o Ponto 2 será desenhado no quadrante inferior esquerdo.

---

{{< alert context="primary" text="Toda a informação extra sobre Gráficos de Quadrantes pode ser encontrada em: [Gráfico de Quadrantes](https://mermaid.js.org/syntax/quadrantChart.html)"/>}}

### Gráfico de quadrantes básico 

Código:

{{< prism lang="md" >}}
```mermaid
---
title: Basic Quadrant Chart
---
quadrantChart
  x-axis Urgente --> "Não é" urgente
  y-axis "Não é" importante --> "Importante ❤"
  quadrant-1 Planear
  quadrant-2 Fazer
  quadrant-3 Delegar
  quadrant-4 Eliminar

```drant-4 Eliminar
```
{{< /prism >}}


```mermaid
---
title: Basic Quadrant Chart
---
quadrantChart
  x-axis Urgente --> "Não é" urgente
  y-axis "Não é" importante --> "Importante ❤"
  quadrant-1 Planear
  quadrant-2 Fazer
  quadrant-3 Delegar
  quadrant-4 Eliminar

```
---

{{< alert context="danger" text="No caso de o diagrama conter palavras que levem acentos, é necessário colocar essas palavras entre aspas, caso contrário não irá funcionar."/>}}

--- 

## Diagrama de Classe
### O que é um diagrama de classes

Um diagrama de classe é um tipo de diagrama UML (Unified Modeling Language) que representa a estrutura de um sistema, descrevendo as classes de objetos dentro dele, seus atributos, métodos e as relações entre eles. 

Os diagramas de classes são utilizados principalmente na engenharia de software e na conceção de sistemas para visualizar a estrutura de sistemas orientados para objectos. Fornecem um plano para a conceção de aplicações de software, ajudando os programadores a compreender as relações entre diferentes classes, a planear a implementação de código e a garantir consistência e clareza no processo de conceção.

```mermaid
---
title: Animal exemplo
---
classDiagram
    note "De Pato até Zebra"
    Animal <|-- Pato
    note for Pato "Consegue voar\n Consegue nadar\n Consegue Mergulhar\n pode ajudar na depuração"
    Animal <|-- Peixe
    Animal <|-- Zebra
    Animal : +int idade 
    Animal : +String género
    Animal: +éMamífero()
    Animal: +acasala()
    class Pato{
        +String corDoBico
        +nada()
        +quack()
    }
    class Fish{
        -int tamanhoEmCm
        -consegueComer()
    }
    class Zebra{
        +bool é_selvagem
        +corre()
    }
```

---

### Sintaxe do diagrama de classes

* A UML fornece mecanismos para representar membros de classe, como atributos e métodos, e informações adicionais sobre eles. Uma única instância de uma classe no diagrama contém três compartimentos:

* O compartimento superior contém o nome da classe. Ele é impresso em negrito e centralizado, e a primeira letra é maiúscula. Também pode conter texto de anotação opcional descrevendo a natureza da classe.

* O compartimento do meio contém os atributos da classe. Eles são alinhados à esquerda e a primeira letra é minúscula.

* O compartimento inferior contém as operações que a classe pode executar. Elas também são alinhadas à esquerda e a primeira letra é minúscula.

---

{{< alert context="primary" text="Toda a informação extra sobre Diagramas de ClassesDiagramas de Classes pode ser encontrada em: [Diagramas de Classes](https://mermaid.js.org/syntax/classDiagram.html)"/>}}

### Diagrama de Classes básico

{{< prism lang="md" >}}
```mermaid
---
title: Banco exemplo
---
classDiagram
    class ContaBancária
    ContaBancária : +String Dono
    ContaBancária : +Bigdecimal Saldo
    ContaBancária : +depósito(quantidade)
    ContaBancária : +levantamento(quantidade)
```
{{< /prism >}}

```mermaid
---
title: Banco exemplo
---
classDiagram
    class ContaBancária
    ContaBancária : +String Dono
    ContaBancária : +Bigdecimal Saldo
    ContaBancária : +depósito(quantidade)
    ContaBancária : +levantamento(quantidade)
```
---

## Diagrama de linha do tempo
### O que é um diagrama de linha do tempo

Um diagrama de linha do tempo é uma representação visual que exibe eventos, tarefas ou marcos ao longo de um eixo cronológico. Ele normalmente consiste em barras ou linhas horizontais que representam a duração ou a ocorrência de cada evento, com rótulos ou marcadores indicando pontos-chave no tempo. 

Os diagramas de linha do tempo são utilizados para ilustrar a sequência de eventos ou actividades ao longo de um período, fornecendo uma visão clara e concisa das relações temporais. São normalmente utilizados na gestão de projectos, análise histórica, narração de histórias e visualização de processos

```mermaid
timeline
        title England's History Timeline
        section Idade da pedra
          7600 a.C.: A mais antiga casa conhecida da Grã-Bretanha foi construída em Orkney, na Escócia
          6000 a.C.: O nível do mar sobe e a Grã-Bretanha torna-se uma ilha.<br> As pessoas que aqui vivem são caçadores-recolectores.
        section Idade do Bronze
          2300 BC : Chegam pessoas da Europa e instalam-se na Grã-Bretanha. <br>Trazem a agricultura e a metalurgia.
                  : Surgem novos estilos de cerâmica e novas formas de enterrar os mortos.
          2200 BC : As últimas grandes obras de construção são concluídas em Stonehenge.<br> As pessoas enterram agora os seus mortos em círculos de pedra.
                  : Os primeiros objectos de metal são fabricados na Grã-Bretanha e outras coisas agradáveis acontecem. É uma boa altura para estar vivo.
```

### Sintaxe do diagrama de linha de tempo

* A sintaxe para criar um diagrama de linha do tempo é simples. Começa-se sempre com a palavra-chave timeline para que o Mermaid saiba que se pretende criar um diagrama de timeline.

* Depois disso, há a possibilidade de adicionar um título à linha de tempo. Isto é feito adicionando uma linha com a palavra-chave título seguida do texto do título.

* Em seguida, adiciona os dados da linha cronológica, onde começa sempre com um período de tempo, seguido de dois pontos e do texto do evento. Opcionalmente, pode adicionar um segundo ponto e depois o texto do evento. Assim, pode ter um ou mais eventos por período de tempo.

---

{{< alert context="primary" text="Toda a informação extra sobre Diagrama de Linha do Tempo pode ser encontrada em: [Diagrama de Linha do Tempo](https://mermaid.js.org/syntax/timeline.html)"/>}}

### Diagrama de Linha de Tempo básico

{{< prism lang="md" >}}
```mermaid
timeline
    title História da plataforma de redes sociais
    2002 : LinkedIn
    2004 : Facebook : Google
    2005 : Youtube
    2006 : Twitter
```
{{< /prism >}}

```mermaid
timeline
    title História da plataforma de redes sociais
    2002 : LinkedIn
    2004 : Facebook : Google
    2005 : Youtube
    2006 : Twitter
```
