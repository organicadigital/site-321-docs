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