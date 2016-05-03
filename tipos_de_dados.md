# Tipos de Dados

Conforme descrito em [Linguagem de Marcação](linguagem_de_marcacao.md), utilizando YAML você poderá descrever várias configurações dos seus campos. Uma das principais é o tipo de dados, representado pela palavra-chave `type`.

Confira a seguir os tipos disponíveis.

## string

Tipo padrão de texto. Quando nenhum type for especificado para o item, o Site 321 irá inferir que este é do tipo `string`.

Exemplo:
```
firstname:
  label: First Name
  type: string
  required: true
lastname: # type não definido, assumindo o padrão string
  label: Last Name
  required: true
```

# text

Tipo texto grande. A diferença do tipo `text` para o tipo `string` é o tamanho da caixa de texto que ficará disponível para gerenciar o conteúdo. Será criada uma `<textarea>`.

Exemplo:
```
description:
  label: Description
  type: text
```

# editor

Editor rico. É possível alterar o código HTML, adicionar classes, ID’s, colocar imagens, formatação de texto, alinhamento. Utiliza o plugin [CKeditor](http://ckeditor.com/).

Exemplo:
```
description:
  label: Description
  type: editor
```

# code_editor

Editor de código rico, com syntax higlight. Conta com as seguintes opções:

* `mode`: "css" - Tipo de sintaxe (CSS, HTML, Ruby, PHP, ...)
* `theme`: "monokai"  - Tema padrão do Highlight (Monokai, Github, …)

Utiliza o Editor [Ace](https://ace.c9.io/). Para todas as opções de `mode` e `theme`, consultar https://ace.c9.io/build/kitchen-sink.html.

Exemplo:
```
css:
  label: CSS
  type: code_editor
  mode: css
  theme: github # Default: monokai
```

