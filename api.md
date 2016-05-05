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

Dado o seguinte template:

```
/api/v2/<token>/contents/projects
```

```
{
  current_page: 1,
  next_page: null,
  total_pages: 1,
  total_count: 3,
  limit: 20,
  items: [
    {
      name: "Design XYZ",
      id: "f7a7646d-0800-4848-9627-02d8d977ebcc",
      type: "design",
      customer_id: "115f9220-1300-11e6-a148-3e1d05defe78",
      created_at: "2016-04-22T12:02:20.974-03:00",
      updated_at: "2016-04-22T12:02:20.974-03:00"
    },
    {
      name: "Site Foo Bar",
      id: "43f025cf-3201-4417-8211-4e58e7fec18d",
      type: "site",
      customer_id: "115f9658-1300-11e6-a148-3e1d05defe78",
      created_at: "2016-04-22T12:02:11.604-03:00",
      updated_at: "2016-04-22T12:02:11.604-03:00"
    },
    {
      name: "Landing page ABC",
      id: "43f025cf-3201-4417-8211-4e58e7fec18d",
      type: "landing_page",
      customer_id: "115f9658-1300-11e6-a148-3e1d05defe78",
      created_at: "2016-04-22T12:02:11.604-03:00",
      updated_at: "2016-04-22T12:02:11.604-03:00"
    }
  ]
}
```

- Para buscar dados por um determinado campo e valor:

```
/api/v2/<token>/contents/projects?search[type]=site
```

- Para buscar dados por um determinado campo e múltiplos valores:

```
/api/v2/<token>/contents/projects?search[type][]=site&search[type][]=design
```

- Para buscar dados por múltiplos campos:

```
/api/v2/<token>/contents/projects?search[type]=site&search[customer_id]=115f9658-1300-11e6-a148-3e1d05defe78
```

## Menus

Da mesma forma que os templates, os Menus possuem API disponível. Para listar todos os menus, utilize:

```
/api/v2/<token>/menus
```

Se você quiser os dados de um menu específico, utilize:

```
/api/v2/<token>/menus/<nome_do_menu>
```