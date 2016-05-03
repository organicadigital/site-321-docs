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