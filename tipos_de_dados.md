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

* `mode: css` - Tipo de sintaxe (CSS, HTML, Ruby, PHP, ...)
* `theme: monokai`  - Tema padrão do Highlight (Monokai, Github, …)

Utiliza o Editor [Ace](https://ace.c9.io/). Para todas as opções de `mode` e `theme`, consultar https://ace.c9.io/build/kitchen-sink.html.

Exemplo:
```
css:
  label: CSS
  type: code_editor
  mode: css
  theme: github # Default: monokai
```

# image

Cadastro de imagens. Conta também com as opções abaixo:

* `multiple: false` - Permite o cadastro de várias imagens no mesmo item, quando for `true`. Default: `false`.
* `legend: false` - Permite a exibição de uma legenda quando `true` (recomendamos usar esse campo como o `alt` da imagem). Default: false

Exemplo:
```
avatar:
  label: Avatar
  type: image
```

# document

Cadastro de documentos (pdfs, textos.). Conta também com as opções abaixo:

* `multiple: false` - Permite o cadastro de vários documentos no mesmo item, quando for `true`. Default: `false`.
* `legend: false` - Permite a exibição de uma legenda quando `true`. Default: false

Exemplo:
```
curriculum:
  label: Curriculum
  type: document
```

# boolean

Checkbox clássico. Se estiver marcado é `true`, se não estiver é `false`.

Exemplo:
```
enabled:
  label: Enabled?
  type: boolean
```

# date

Datepicker para seleção de datas. O formato da data pode ser especificado com a opção abaixo:

* `format: "DD/MM/YYYY"` - Formato de apresentação da data. Para uma referência completa, consultar http://momentjs.com/docs/#/displaying/format/. Default: `"DD/MM/YYYY"` .

Exemplo:
```
birthday:
  label: Birthday
  type: date
  format: "DD/MM/YYYY"
```

# date_time

Datepicker para seleção de datas e horas. O formato da data pode ser especificado com a opção abaixo:

* `format: "DD/MM/YYYY HH:mm:ss"` - Formato de apresentação da data e hora. Para uma referência completa, consultar http://momentjs.com/docs/#/displaying/format/. Default: `"DD/MM/YYYY HH:mm:ss"` .

Exemplo:
```
meeting:
  label: Meeting
  type: date_time
  format: "DD/MM/YYYY HH:mm:ss"
```
