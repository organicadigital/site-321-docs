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

Caso seja necessário um editor mais simples, sem muitos botões de formatação, é possível utilizar o editor mini, como segue:

```
description:
  label: Description
  type: editor
  mode: mini
```

# code\_editor

Editor de código rico, com syntax higlight. Conta com as seguintes opções:

* `mode: css` - Tipo de sintaxe \(CSS, HTML, Ruby, PHP, ...\)
* `theme: monokai`  - Tema padrão do Highlight \(Monokai, Github, …\)

Utiliza o Editor [Ace](https://ace.c9.io/). Para todas as opções de `mode` e `theme`, consultar [https://ace.c9.io/build/kitchen-sink.html](https://ace.c9.io/build/kitchen-sink.html).

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
* `legend: false` - Permite a exibição de uma legenda quando `true` \(recomendamos usar esse campo como o `alt` da imagem\). Default: `false`
* `sizes`: Tamanhos pré-definidos de imagens que já deverão ser geradas. Isso evitará latência na primeira requisição desses tamanhos.

Exemplo:

```
avatar:
  label: Avatar
  type: image
  sizes:
    - 100x100
    - 200x200#
```

# document

Cadastro de documentos \(pdfs, textos.\). Conta também com as opções abaixo:

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

* `format: "DD/MM/YYYY"` - Formato de apresentação da data. Para uma referência completa, consultar [http://momentjs.com/docs/\#/displaying/format/](http://momentjs.com/docs/#/displaying/format/). Default: `"DD/MM/YYYY"` .

Exemplo:

```
birthday:
  label: Birthday
  type: date
  format: "DD/MM/YYYY"
```

# datetime

Datepicker para seleção de datas e horas. O formato da data pode ser especificado com a opção abaixo:

* `format: "DD/MM/YYYY HH:mm:ss"` - Formato de apresentação da data e hora. Para uma referência completa, consultar [http://momentjs.com/docs/\#/displaying/format/](http://momentjs.com/docs/#/displaying/format/). Default: `"DD/MM/YYYY HH:mm:ss"` .

Exemplo:

```
meeting:
  label: Meeting
  type: datetime
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

Utilizado para especificar URLs. É feita uma validação básica verificando se a informação é uma URL \(se começa com http://, https://, ...\).

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

# auto\_increment

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

`options` recebe uma lista de opções, com `label` \(Opção visual para o usuário selecionar\) e `value` \(valor do campo select que irá no submit do formulário\).

Se for interessante disponibilizar várias opções, utilize `multiple: true`.

Exemplo:

```
creditcard_type:
  label: Credit Card Type
  type: choice
  multiple: true
  options:
    - label: Visa
      value: visa
    - label: Mastercard
      value: master
```

# user

Herdando o comportamento do campo `choice`, permite criar uma seleção de usuários. Cria um grupo de checkboxes, ou um select único, de acordo com o que for especificado.

Permite escolher um escopo de role que deverá ser respeitado. Se nenhuma role for informada, pegará todos os usuários do site.

```
user:
    label: User
    type: user
    role: Role Name
    required: true
    multiple: false
```

# template

Cria um campo select que mostra o nome dos outros templates. Salvará o slug do template relacionado, e trará as APIs do template relacionado.

Levando em conta um template `Newsletter`, assim:

```
email:
  label: E-mail
  type: email
  required: true
```

Imagine um outro template `Theme`, que possui uma configuração do formulário de submissão para inscrição na newsletter:

```
news_form:
  label: Newsletter Form
  type: template
  default: newsletter
```

Isso trará todos os templates para um select, deixando como default o com slug `newsletter`.

# form

Cria um campo select que mostra o nome dos formulários disponíveis. Salvará o slug do form relacionado, e trará os dados do formulário na API.

Exemplo:

```
form:
  label: Subscription form
  type: form
```

# page

Cria um campo select que mostra o nome de páginas existentes. Salvará o id da página \(content\) relacionada. Trará na API o ID do content e o slug do template, para que seja possível trabalhar com o dado.

Levando em conta um template Menu, assim:

```
name:
  label: Name
  type: string
  required: true
page:
  label: Page
  type: page
```

O cadastro gerado permitirá criar itens relacionando o campo com uma nova página.

# location

Cria um campo especial que permite a seleção de um endereço, integrando com o Google Maps. Permite que o usuário insira o endereço com um autocomplete, buscando tanto por endereço quanto por nome de estabelecimento.

Além disso, o usuário pode selecionar o ponto no mapa com drag and drop do pin, e informar manualmente latitude e longitude.

Exemplo:

```
place:
  label: Place
  type: location
```

# meta\_description

Campo especial com validações para desenvolvimento de uma meta description, para o Google, demonstrando o tamanho ideal do texto.

Exemplo:

```
description:
  label: Meta description for Google
  type: meta_description
```



