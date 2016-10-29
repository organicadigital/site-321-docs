# Validação

O Site 321 possui algumas validações disponíveis. Aqui falaremos um pouco sobre elas.

## required

A mais simples e utilizada é `required`. Ela torna um campo obrigatório de ser preenchido.

Exemplo:

```
name:
  label: Name
  type: string
  required: true
```

No caso de não informar a propriedade `required`, ou utilizar o valor `false`, não será validada a obrigatoriedade.

## matcher

Permite a validação do campo utilizando uma expressão regular (regex). O padrão de expressões regulares é o do Ruby. Consulte em http://ruby-doc.org/core-2.1.1/Regexp.html#method-c-new mais informações.

```
name:
  label: Name
  type: string
  required: true
  matcher: Foo|Bar
  matcher_message: must contain Foo or Bar
```

Utilize `matcher_message` para a mensagem de erro a ser apresentada ao usuário.

**Importante:** O `matcher` deverá ser informado sem as barras delimitadoras. Correto: `Foo|Bar`; Errado: `/Foo|Bar/`.

## max_length

Permite definir o tamanho máximo do conteúdo do campo.

O exemplo abaixo fará a validação do tamanho máximo do texto, impedindo que um registro que extrapole esse tamanho seja salvo:

```
description:
  label: Description
  type: text
  max_length: 200
```

Além disso, cria uma representação visual da quantidade de caracteres já usados.

Ao habilitar o campo `max_length`, algumas outras opções ficarão disponíveis:

* `stop_on_max_length`: Caso `false`, não bloqueia a entrada dos dados (default: `true`);
*  `count_down_text`: Mensagem apresentada abaixo do campo, mostrando os campos restantes (default: `Caracteres restantes:`)