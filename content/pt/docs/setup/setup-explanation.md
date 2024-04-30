---
weight: 100
title: "Setup - Explanation"
description: ""
icon: "article"
date: "2024-04-20T18:51:35+01:00"
lastmod: "2024-04-20T18:51:35+01:00"
draft: false
toc: true
author: "Paulo Rodrigues"
---

Aqui vamos falar sobre como a página de Configuração foi criada

## Lista

Para a parte da lista, é simples, basta colocar o caractere "-" antes da frase e a lista será formada:

```shell
- git
- Go ≥ v1.19
- Hugo ≥ v0.117.0 (Versão Extendida)
```

## Tags

Nas secções 2.1 e 3, foram utilizadas tags de código curto. Estas tags permitem criar um menu que oferece diferentes informações sobre o mesmo tema. No nosso caso, utilizamos tags de código curto para apresentar as diferentes formas de instalar automaticamente o Lotus Docs em diferentes sistemas operativos. Desta forma, os utilizadores já não precisam de procurar instruções de instalação específicas para o seu sistema operativo; basta aceder à secção correspondente e selecionar o seu sistema operativo.

Para utilizar tags, é necessário começar por abrir o separador utilizando ``{{ < tabs tabTotal="n" > }}``, onde "n" corresponde ao número de divisões necessárias. Por exemplo, na página de configuração, definimos "n" como 4 para a secção 2.1 e 3 para a secção 3. Em seguida, precisamos de definir o nome do separador utilizando o código ``{{ % tab tabName="Linux" % }}``, e depois pode inserir o conteúdo do separador. Para terminar a divisão do separador, utilize ``{{ %/tab % }}``, e para fechar toda a secção do separador, utilize ``{{ </tabs > }}``.

{{< prism lang="md" >}}
{{ < tabs tabTotal="4"> }}
{{ % tab tabName="Linux" % }}

## conteúdo...

{{ % /tab % }}

## mais separadores...

{{ < /tabs > }}
{{< /prism >}}

## Destaques e Ênfase

Ao escrever textos, por vezes é importante destacar partes específicas para que os utilizadores possam entender melhor os pontos-chave das frases, como comandos importantes ou códigos. Para fazer isso, basta colocar o acento grave (``) no início e no final das palavras que deseja destacar.

Outra forma é usar asteriscos (**), tanto antes como depois das palavras, tornando-as em negrito e enfatizando a frase.

Exemplos de como isso foi usado na página de 'Configuração':

{{< prism lang="md" >}}
...

Para construir itens de menu de segundo nível, primeiro crie um diretório chamado **"pai"** que tenha um ficheiro chamado ``_index.md``. Por exemplo:

...
{{< /prism >}}

Neste exemplo, os asteriscos foram usados para enfatizar a palavra **"pai"**, enquanto os acentos graves foram usados para destacar um ficheiro.

## Hiperligações

Durante o processo de criação da página de "Configuração", também foi necessário criar hiperligações, tanto externas como internas. Para hiperligações externas, foi utilizado o seguinte código: ``[Palavra que conterá o link](URL do site externo)``. Enquanto para hiperligações internas, por exemplo, foi utilizado este código: ``[Palavra que conterá o link](\docs\deployment)``.

## Linhas de código e comandos

Para diferenciar as linhas de código ou comandos e destacá-los para os utilizadores, optamos por usar **shell** e o shortcode **prism**.

### Shell

**Shell** é uma interface de linha de comando que permite aos utilizadores interagir com um sistema operativo através de texto. Utilizamos **shell** para indicar que estas linhas podem ser usadas como comandos ou código. Um exemplo usado na página de Configuração é:

{{< prism lang="shell" >}}

```shell
brew install hugo
```

{{< /prism >}}

Isto permite aos utilizadores copiar esta linha e colá-la nos seus terminais Linux para instalar o Hugo.

### Prism

**Prism** é um shortcode que destaca linhas de código destinadas a linguagens de texto como ``Markdown`` e ``HTML``. Na criação da página de Configuração, **prism** foi usado para evitar conflitos entre comandos. Por exemplo, quando um snippet continha um comando **shell** dentro de outro, optamos por usar **prism** para garantir clareza e evitar confusão.

Exemplo de uso de **prism**:

{{< prism lang="md" >}}
{{ < prism lang="md" > }}
---
weight: 200
title: "Nova Página"
icon: "artigo"
date: "2024-04-17T18:19:36Z"
lastmod: "2024-04-17T18:19:36Z"
description: "Esta nova página tem o tema Lotus Documents"
rascunho: verdadeiro 
toc: verdadeiro
publishdate: "2023-05-03T22:37:22+01:00"
tags: ["Iniciantes"]
---

## Criar Novo Conteúdo

Navegue até à raiz do seu projeto Hugo e utilize o comando `hugo new` para criar um ficheiro no diretório `content/docs`:

```shell
hugo new docs/paginaexemplo.md
```
...
{{ < /prism > }}
{{< /prism >}}

## Alertas

Para destacar algumas notas importantes na documentação, utilizamos o shortcode Alert, pois permitia a criação de caixas de texto com diferentes aparências. Na página em questão, optamos pelo **alerta de informação**, que exibe uma caixa com fundo em tons de azul e um ícone "i" antes da frase, indicando informações adicionais:

![Exemplo de Alerta](https://paulorodrigues-isep.sirv.com/TECAA/Alert.png)

Aqui está um exemplo de como criar uma caixa de alerta.

```shell
{{ < alert context="info" text="Tenha em mente que os ficheiros _index.md destinam-se apenas a ser usados para modificar as configurações do cabeçalho. Não fará diferença se adicionar algum material que não esteja entre as variáveis permitidas no cabeçalho."/> }}
```

## Imagens

Para adicionar imagens à página de Configuração, utilizamos o serviço de hospedagem de imagens [Sirv](https://my.sirv.com/), que oferece serviços gratuitos de hospedagem de imagens. Ao hospedar imagens no **Sirv**, conseguimos melhorar o desempenho do site, pois não é necessário renderizar as imagens; o **Sirv** faz isso por nós, resultando apenas na exibição das imagens na nossa documentação.

Aqui está um exemplo de como exibir a imagem na documentação:

```shell
![Visualização da Publicação do Site](https://paulorodrigues-isep.sirv.com/TECAA/Preview_Site_Publish.png)
```

O título da imagem está entre colchetes `[]`, enquanto a URL da imagem está entre parênteses `()`.

No **Sirv**, basta carregar a imagem e depois copiar o link:

![Copiar Link no Sirv](https://paulorodrigues-isep.sirv.com/TECAA/Sirv_Copy_Link.png)

O **Sirv** também oferece opções de personalização de imagens, como tamanho, para melhorar o desempenho do site.

![Personalização no Sirv](https://paulorodrigues-isep.sirv.com/TECAA/customization.png)


## Treeview

Além disso, **treeviews** foram usados na secção 8. Isso porque a discussão sobre diretórios foi abordada lá, e **treeviews** são a melhor opção para representar hierarquias de diretórios. Com eles, é possível criar uma visualização hierárquica de pastas, mostrando aos utilizadores como seus arquivos estão organizados no final.

Na secção 8.1, o **treeview** foi apresentado da seguinte forma:

{{< prism lang="md" >}}

```treeview
conteúdo/
└── docs/
    ├── diretório-pai/
    │   └── _index.md
    ├── nova-página.md
    ├── nova-página-2.md
    ├── configuração.md
    └── _index.md
```

{{< /prism >}}

Desta forma, foi possível mostrar como o diretório ficaria após a criação de um segundo nível de pastas.

![Treeview](https://paulorodrigues-isep.sirv.com/TECAA/Treeview.png)
