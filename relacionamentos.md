# Relacionamentos

Outra *feature* interessante do Site 321, são os relacionamentos entre cadastros e páginas. Entenda sua utilidade a seguir.

## Many-to-One

Em vários momentos precisamos relacionar dois cadastros. A exemplo de orientação a objetos, ou bancos de dados relacionais, você cria uma entidade simples, a exemplo "Category", e outra mais complexa, como "Post". Category possui somente o atributo `name` e Post, `title` e um campo `category`. Esse campo `category` é do tipo "Category" citado anteriormente.

Para fazer isso no Site 321 você deve adicionar um campo no YAML, com o atributo `type` com valor `association`, e o atributo `module` com o valor sendo o nome do template de página que deseja relacionar.

Por exemplo, imagine que você tem dois templates:

* category
```
name:
    label: Name
```
* post
```
title:
    label: Title
category:
    label: Category
    type: association
    module: category
```

O mapeamento acima lhe permitirá cadastrar categorias e relacionar posts a elas. Um novo campo em "Post", do tipo select, aparecerá para escolha da categoria.

## One-to-Many

Da mesma forma que no relacionamento Many-to-One, podemos fazer o relacionamento inverso.

Usando o mesmo contexto de "Post" e "Category", imagine que você queira fazer um novo cadastro chamado "Edition", onde você agrupa os posts em Edições. Por questões de usabilidade, você quer que, ao editar ou visualizar uma edição, você possa adionar Posts pela mesma interface.

1) Marque a Edição assim:

```
name:
  label: Name
```

2) Adicione `edition` ao template do Post:

```
title:
    label: Title
category:
    label: Category
    type: association
    module: category
edition:
    label: Edition
    type: association
    module: edition
```

3) Edite o template da Edição e em "Relacionamentos" selecione "Edition" no campo **Template**  e automaticamente deverá aparecer `edition` em **Campo**. Escolha um **Título** como, por exemplo, "Edition's Posts" e salve.

Tudo ocorrendo normalmente, ao visualizar ou editar uma Edition, aparecerão os posts relacionados e a possibilidade de adicionar posts extras.
