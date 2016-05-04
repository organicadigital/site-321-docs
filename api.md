# API

**Versão atual da API: v2**

O Site 321 disponibiliza APIs para consulta e manipulação de dados. Para cada template é disponibilizada uma API, que pode ser consultada em `Configurações > API's`.

Em todas as URLs é necessário passar o token para consulta aos dados, disponível na mesma página.

As APIs implementam REST e o tipo de dados disponível é JSON.

## Templates

Para listar todos os templates (Cadastros ou Páginas), utilize a seguinte API:

```
/api/v2/<token>/contents
```

Caso você queira retornar as informações de uma API específica, utilize:

```
/api/v2/<token>/contents/<nome_do_template>
```

### Busca de dados

TODO explicar como buscar dados usando os parâmetros

## Menus

Da mesma forma que os templates, os Menus possuem API disponível. Para listar todos os menus, utilize:

```
/api/v2/<token>/menus
```

Se você quiser os dados de um menu específico, utilize:

```
/api/v2/<token>/menus/<nome_do_menu>
```