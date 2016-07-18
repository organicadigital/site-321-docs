# Valores Padrão

Alguns campos permitem a inserção de valores padrão. Os campos textuais, com suas variações, permitem essa abordagem.

Por exemplo, defina da seguinte forma no YAML:

```
name:
  label: Name
  required: true
  default: John Doe
```

Ao criar um novo cadastro desse tipo, o campo `name` trará o valor `John Doe` como padrão.

Abaixo um exemplo com campos do tipo `editor`:

```
content:
  label: Conteúdo
  type: editor
  default: >
    This is a <strong>HTML field</strong>.
```

> Esta é uma funcionalidade experimental. Campos tipo `image` e `document` ainda não são suportados. Assim como o comportamento poderá ser inexperado para alguns outros tipos de dados.