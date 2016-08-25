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

# color

Campo de seleção de cores. Por padrão, abre uma lista de cores pré-definidas para o usuário selecionar:

Exemplo:
```
color:
  label: Select the best color for you
  type: color
```

Você poderá personalizar as cores a serem selecionadas, com o campo `options`:

```
color:
  label: Select the best color for you
  type: color
  options:
    - 'black'
    - '#FF0000'
    - 'rgb(255,255,255)'
```

Se for desejado um colopicker com maior precisão, utilze o campo `simple: false`:

```
color:
  label: Mix your color
  type: color
  simple: false
```

Será criado um componente de "mistura" de cores.

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

# slug

Utilizado para gerar URL’s amigáveis. Conta com a opção abaixo:

* `canditate: nome_campo` - Referência um campo para ser utilizado caso o `slug`.

Exemplo:
```
post_title:
  label: Post Title
  required: true
friendly_id:
  label: Friendly ID
  type: slug
  candidate: post_title
```

# email

Utilizado para especificar e-mails. É feita uma validação básica verificando se a informação é um e-mail válido.

Exemplo:
```
email:
  label: E-mail
  type: email
```

# url

Utilizado para especificar URLs. É feita uma validação básica verificando se a informação é uma URL (se começa com http://, https://, ...).

Exemplo:
```
url:
  label: URL
  type: url
```

# integer

Utilizado para cadastrar números inteiros.

Exemplo:
```
age:
  label: Age
  type: integer
```

# auto_increment

Utilizado para sequência numérica simples.

Exemplo:
```
id:
  label: ID
  type: auto_increment
```

# currency

Utilizado para valores tipo moeda. Aceita as seguintes opções:

* `prefix: 'R$'` - Prefixo da moeda. Default: 'R$'
* `cents_separator: ','` - Separador de centavos. Default: ','
* `thousands_separator: '.'` - Separador de milhar. Default: '.'

Exemplo:
```
salary:
  label: Salary
  type: currency
  prefix: 'US$'
  cents_separator: '.'
  thousands_separator: ','
```

# choice

Permite a seleção de um item declarado em `options`. A opção declarada é mantida como um campo `string`.

`options` recebe uma lista de opções, com `label` (Opção visual para o usuário selecionar) e `value` (valor do campo select que irá no submit do formulário).

Exemplo:
```
creditcard_type:
  label: Credit Card Type
  type: choice
  options:
    - label: Visa
      value: visa
    - label: Mastercard
      value: master
```

# location

Cria um campo especial que permite a seleção de um endereço, integrando com o Google Maps. Permite que o usuário insira o endereço com um autocomplete, buscando tanto por endereço quanto por nome de estabelecimento.

Além disso, o usuário pode selecionar o ponto no mapa com drag and drop do pin, e informar manualmente latitude e longitude.

Exemplo:
```
place:
  label: Place
  type: location
```