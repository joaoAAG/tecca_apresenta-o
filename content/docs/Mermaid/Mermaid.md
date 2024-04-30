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

Welcome to the mermaid page.

## What is Mermaid? 

Mermaid is a `JavaScript-based` diagramming and charting tool that uses Markdown-inspired text definitions and a renderer to create and modify complex diagrams. The main purpose of Mermaid is to help documentation catch up with development.

## How to use Mermaid with Lotus Docs 

Mermaid is enabled whenever content containing Mermaid diagram syntax is present in a page’s content. You can insert Mermaid diagrams by using the mermaid language identifier with triple backtick codeblocks:


{{< prism lang="md" >}}
 ```mermaid
---
title: Advanded graph
---
sequenceDiagram
Alice->>John: Hello John, how are you?
loop Healthcheck
    John->>John: Fight against hypochondria
end
Note right of John: Rational thoughts!
John-->>Alice: Great!
John->>Bob: How about you?
Bob-->>John: Jolly good! 
```
{{< /prism >}}

```mermaid
sequenceDiagram
Alice->>John: Hello John, how are you?
loop Healthcheck
    John->>John: Fight against hypochondria
end
Note right of John: Rational thoughts!
John-->>Alice: Great!
John->>Bob: How about you?
Bob-->>John: Jolly good! ```
```

This is a more adavanced diagram, so lets scale it back to a simple flowchart.

---

## Flowchart

### What is a flowchart

A flowchart is a graphical representation of a process or workflow, depicting the sequence of steps, decisions, and actions involved. It typically consists of shapes, arrows, and text, illustrating the flow of control through a system.

Flowcharts are used across various domains to visually map out procedures, analyze processes, and communicate complex workflows.

### Create nodes

As mentioned before, flowchart are composed by nodes. To create a node:

{{< prism lang="md" >}}
```mermaid
---
title: Node
---
flowchart LR
    id
```
{{< /prism >}}

```mermaid
---
title: Node
---
flowchart LR
    id
```

### Basic Flowchart

The most basic flowchart consist of creating an implication of x to y.

{{< prism lang="md" >}}
```mermaid
---
title: Simple Flowchart
---
flowchart LR
    x --> y
```
{{< /prism >}}

```mermaid
---
title: Simple Flowchart
---
flowchart LR
    x --> y
```

### One to Many Flowchart

{{< prism lang="md" >}}
```mermaid
---
title: 1 to Many Flowchart
---
flowchart LR
    x[a]
    y[b1,b2,b3]

    x --> y
```
{{< /prism >}}


```mermaid
---
title: 1 to Many Flowchart
---
flowchart LR
    x[a]
    y[b1,b2,b3]

    x --> y
```

### Costumize Flowchart

There are various ways to costumize a flowchart, from chaging the nodes shape, changing orientation to adding colors and icons.


{{< prism lang="md" >}}
```mermaid
---
title: Special Flowchart
---
flowchart LR
    
    A[Hard edge] -->|Link text| B(Round edge)
    B --> C{Decision}:::red
    C -->|One| D[Result one]:::blue
    C -->|Two| E[Result two]:::green
    
    classDef red stroke:#f00
    classDef green stroke:#0f0
    classDef blue stroke:#00f
```
{{< /prism >}}



```mermaid
---
title: Special Flowchart
---
flowchart LR
    
    A[Hard edge] -->|Link text| B(Round edge)
    B --> C{Decision}:::red
    C -->|One| D[Result one]:::blue
    C -->|Two| E[Result two]:::green

    classDef red stroke:#f00
    classDef green stroke:#0f0
    classDef blue stroke:#00f
```
---

{{< alert context="primary" text="All extra information about Flowcharts can be found in [Flowchart](https://mermaid.js.org/syntax/flowchart.html)"/>}}

## Pie Chart diagram



### What is a Pie Chart

A pie chart is a circular statistical graphic divided into slices to illustrate numerical proportions. Each slice represents a proportionate part of the whole data set, typically displayed as a percentage of the total. Pie charts are commonly used to visualize data distribution and show the relative size of different categories or components within a dataset. 

```mermaid
---
title: Pets adopted by volunteers
---
pie

    "Dogs" : 386
    "Cats" : 85
    "Rats" : 15
```

### Pie Chart Syntax

Drawing a pie chart is really simple in mermaid.

* Start with pie keyword to begin the diagram
* showData to render the actual data values after the legend text. This is OPTIONAL
* Followed by title keyword and its value in string to give a title to the pie-chart. This is OPTIONAL
* Followed by dataSet. Pie slices will be ordered clockwise in the same order as the labels.
* label for a section in the pie diagram within " " quotes.
* Followed by : colon as separator
* Followed by positive numeric value (supported up to two decimal places)

---

{{< alert context="primary" text="All extra information about Pie charts can be found in [Pie Charts](https://mermaid.js.org/syntax/pie.html)"/>}}

### Basic Pie Chart

{{< prism lang="md" >}}
```mermaid
---
title: Special Flowchart
---
pie showData
    
    pie showData
    title Key elements in Product X
    "Calcium" : 42.96
    "Potassium" : 50.05
    "Magnesium" : 10.01
    "Iron" :  5
```
{{< /prism >}}


```mermaid
pie showData
    title Key elements in Product X
    "Calcium" : 42.96
    "Potassium" : 50.05
    "Magnesium" : 10.01
    "Iron" :  5
```

---

## Quadrant Chart

### What is a Quadrant Chart

A quadrant chart is a graphical representation that divides data into four quadrants based on two axes. Each axis represents a different dimension or variable, and the quadrants are defined by dividing the chart area into four equal sections. 

Quadrant charts are commonly used to analyze and visualize data relationships, particularly when comparing two sets of variables or criteria. They help identify patterns, trends, and outliers within the dataset, allowing users to categorize data points into different quadrants based on their positions relative to the axes

```mermaid
quadrantChart
    title Reach and engagement of campaigns
    x-axis Low Reach --> High Reach
    y-axis Low Engagement --> High Engagement
    quadrant-1 We should expand
    quadrant-2 Need to promote
    quadrant-3 Re-evaluate
    quadrant-4 May be improved
    Campaign A: [0.3, 0.6]
    Campaign B: [0.45, 0.23]
    Campaign C: [0.57, 0.69]
    Campaign D: [0.78, 0.34]
    Campaign E: [0.40, 0.34]
    Campaign F: [0.35, 0.78]
```

---

### Quadrant Chart Syntax 

Title
The title is a short description of the chart and it will always render on top of the chart.

Example
quadrantChart
    title This is a sample example

* `x-axis`
The x-axis determines what text would be displayed in the x-axis. In x-axis there is two part left and right you can pass both or you can pass only left. The statement should start with x-axis then the left axis text followed by the delimiter --> then right axis text.

Example
x-axis <text> --> <text> both the left and right axis text will be rendered.
x-axis <text> only the left axis text will be rendered.

* `y-axis`
The y-axis determines what text would be displayed in the y-axis. In y-axis there is two part top and bottom you can pass both or you can pass only bottom. The statement should start with y-axis then the bottom axis text followed by the delimiter --> then top axis text.

Example
y-axis <text> --> <text> both the bottom and top axis text will be rendered.
y-axis <text> only the bottom axis text will be rendered.

* `Quadrants text`
The quadrant-[1,2,3,4] determine what text would be displayed inside the quadrants.

Example
quadrant-1 <text> determine what text will be rendered inside the top right quadrant.
quadrant-2 <text> determine what text will be rendered inside the top left quadrant.
quadrant-3 <text> determine what text will be rendered inside the bottom left quadrant.
quadrant-4 <text> determine what text will be rendered inside the bottom right quadrant.

* `Points`
Points are used to plot a circle inside the quadrantChart. The syntax is <text>: [x, y] here x and y value is in the range 0 - 1.

Example
Point 1: [0.75, 0.80] here the Point 1 will be drawn in the top right quadrant.
Point 2: [0.35, 0.24] here the Point 2 will be drawn in the bottom left quadrant.

---

{{< alert context="primary" text="All extra information about Quadrant charts can be found in [Quadrant Charts](https://mermaid.js.org/syntax/quadrantChart.html)"/>}}

### Basic Quadrant Chart 

Code:

{{< prism lang="md" >}}
```mermaid
---
title: Basic Quadrant Chart
---
quadrantChart
  x-axis Urgent --> Not Urgent
  y-axis Not Important --> "Important ❤"
  quadrant-1 Plan
  quadrant-2 Do
  quadrant-3 Delegate
  quadrant-4 Delete

```
{{< /prism >}}


```mermaid
---
title: Basic Quadrant Chart
---
quadrantChart
  x-axis Urgent --> Not Urgent
  y-axis Not Important --> "Important ❤"
  quadrant-1 Plan
  quadrant-2 Do
  quadrant-3 Delegate
  quadrant-4 Delete
```

--- 

## Class Diagram
### What is a Class Diagram

A class diagram is a type of UML (Unified Modeling Language) diagram that represents the structure of a system by depicting the classes of objects within it, their attributes, methods, and the relationships between them. 

Class diagrams are used primarily in software engineering and system design to visualize the structure of object-oriented systems. They provide a blueprint for designing software applications, helping developers understand the relationships between different classes, plan the implementation of code, and ensure consistency and clarity in the design process.

```mermaid
---
title: Animal example
---
classDiagram
    note "From Duck till Zebra"
    Animal <|-- Duck
    note for Duck "can fly\ncan swim\ncan dive\ncan help in debugging"
    Animal <|-- Fish
    Animal <|-- Zebra
    Animal : +int age
    Animal : +String gender
    Animal: +isMammal()
    Animal: +mate()
    class Duck{
        +String beakColor
        +swim()
        +quack()
    }
    class Fish{
        -int sizeInFeet
        -canEat()
    }
    class Zebra{
        +bool is_wild
        +run()
    }
```

--- 

### Class Diagram Syntax

* UML provides mechanisms to represent class members, such as attributes and methods, and additional information about them. A single instance of a class in the diagram contains three compartments:

* The top compartment contains the name of the class. It is printed in bold and centered, and the first letter is capitalized. It may also contain optional annotation text describing the nature of the class.

* The middle compartment contains the attributes of the class. They are left-aligned and the first letter is lowercase.

* The bottom compartment contains the operations the class can execute. They are also left-aligned and the first letter is lowercase.

---

{{< alert context="primary" text="All extra information about Quadrant Diagrams can be found in [Class Diagram](https://mermaid.js.org/syntax/classDiagram.html)"/>}}

### Basic Class Diagram

{{< prism lang="md" >}}
```mermaid
---
title: Bank example
---
classDiagram
    class BankAccount
    BankAccount : +String owner
    BankAccount : +Bigdecimal balance
    BankAccount : +deposit(amount)
    BankAccount : +withdrawal(amount)
```
{{< /prism >}}

```mermaid
---
title: Bank example
---
classDiagram
    class BankAccount
    BankAccount : +String owner
    BankAccount : +Bigdecimal balance
    BankAccount : +deposit(amount)
    BankAccount : +withdrawal(amount)
```
---

## Timeline Diagram
### What is a Timeline Diagram

A Timeline Diagram is a visual representation that displays events, tasks, or milestones along a chronological axis. It typically consists of horizontal bars or lines representing the duration or occurrence of each event, with labels or markers indicating key points in time. 

Timeline diagrams are used to illustrate the sequence of events or activities over a period, providing a clear and concise overview of temporal relationships. They are commonly utilized in project management, historical analysis, storytelling, and process visualization

```mermaid
timeline
        title England's History Timeline
        section Stone Age
          7600 BC : Britain's oldest known house was built in Orkney, Scotland
          6000 BC : Sea levels rise and Britain becomes an island.<br> The people who live here are hunter-gatherers.
        section Bronze Age
          2300 BC : People arrive from Europe and settle in Britain. <br>They bring farming and metalworking.
                  : New styles of pottery and ways of burying the dead appear.
          2200 BC : The last major building works are completed at Stonehenge.<br> People now bury their dead in stone circles.
                  : The first metal objects are made in Britain.Some other nice things happen. it is a good time to be alive.
```

### Timeline Diagram Synxtax

* The syntax for creating Timeline diagram is simple. You always start with the timeline keyword to let mermaid know that you want to create a timeline diagram.

* After that there is a possibility to add a title to the timeline. This is done by adding a line with the keyword title followed by the title text.

* Then you add the timeline data, where you always start with a time period, followed by a colon and then the text for the event. Optionally you can add a second colon and then the text for the event. So, you can have one or more events per time period.

---

{{< alert context="primary" text="All extra information about Timeline Diagrams can be found in [Timeline Diagram](https://mermaid.js.org/syntax/timeline.html)"/>}}

### Basic Timeline Diagram

{{< prism lang="md" >}}
```mermaid
timeline
    title History of Social Media Platform
    2002 : LinkedIn
    2004 : Facebook : Google
    2005 : Youtube
    2006 : Twitter
```
{{< /prism >}}

```mermaid
timeline
    title History of Social Media Platform
    2002 : LinkedIn
    2004 : Facebook : Google
    2005 : Youtube
    2006 : Twitter
```
