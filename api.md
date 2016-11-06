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

### Listagem de Dados
Caso você queira retornar as informações de uma API específica, utilize:

```
/api/v2/<token>/contents/<nome_do_template>
```

#### Limite de Registros

Por questões de performance, a listagem dos registros possui um limite. O limite padrão são de 20 registros por página.

Se você precisar, poderá modificar esse limite. Mas por segurança, o máximo de registros que você poderá trazer serão 100 por vez.

Utilize o parâmetro `per` para modificar esse limite.

Ex:

```
/api/v2/<token>/contents/<nome_do_template>?per=100
```


#### Paginação

Como você provavelmente terá mais do que 100 registro em alguns cadastros, será necessário iterar as páginas.

Para isso, utilize o padrâmetro `page`.

Ex:

```
/api/v2/<token>/contents/<nome_do_template>?per=100
```

#### Filtro por Locale

Na utilização de vários locales, é possível filtrar por um idioma específico. Supondo que o site seja em Português do Brasil e Inglês (pt-BR e en), listando da forma tradicional trará todos os dados, agrupados por locale:

```
/api/v2/<token>/contents/<nome_do_template>
```

Se você quiser apenas um idioma, é possível especificar da seguinte forma:

```
/api/v2/<token>/contents/<nome_do_template>?only_locale=<locale>
```

Esse parâmetro vale para a busca de registros únicos, trazendo somente o idioma especificado.

### Pesquisa de dados

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

### Busca de Registro Único

Para listar apenas um registro específico, utilize a seguinte API:

```
/api/v2/<token>/contents/<nome_do_template>/<id_do_content>
```

Assim você terá acesso ao registro desejado. Se o site tiver suporte a i18n, utilize o `?only_locale=` para trazer somente determinado idioma. P. ex:

```
/api/v2/<token>/contents/<nome_do_template>/<id_do_content>?only_locale=<locale>
```

### Criação de Registros


**IMPORTANTE:** Para utilizar em formulários públicos, como formulários de contato em sites, leia mais abaixo e NUNCA utilize seu token principal.

Caso você tenha habilitado a inserção de dados via API, você pode utilizar chamadas POST para insersão de dados. 

Para isso, utilize o nome dos campos como parâmetros. O exemplo abaixo utiliza [curl](https://curl.haxx.se/) para insersão de dados no cadastro:

```
curl --data "name=Website&type=site&customer_id=115f9658-1300-11e6-a148-3e1d05defe78" / 
  http://beta.site321.com.br/api/v2/<token>/contents/projects
```

Por padrão os dados são inseridos como inativos. Para deixá-los ativos, utilize `active=true` juntamente aos demais parâmetros.

Além disso, você poderá passar um parâmetro especial, chamado `redirect_url`, com uma URL para redirectionar após salvar os registros com sucesso. Em caso de falha ao salvar, haverá um redirecionamento para a URL de origem, com os erros em um parâmetro chamado `errors`.


#### Submissão em Formulários Públicos

O Site 321 fornece uma forma conveniente de criar formulários de contato, através de URLs que recebem submissões públicas. Para isso, habilite a insersão via API, vá na página de APIs e pegue a URL correspondente.

A URL se parecerá com `http://beta.site321.com.br/api/contents/<public_token>`. Veja que essa URL esconde o nome do template, garantindo maior segurança.

### Alteração de Registros

Para alterar um registro, envie um verbo PUT para a URL do registro. Ex:

```
curl -X PUT --data "name=Website&type=site&customer_id=115f9658-1300-11e6-a148-3e1d05defe78" / 
  http://beta.site321.com.br/api/v2/<token>/contents/projects/115f9658-1300-11e6-a148-3e1d05defggj
```

O padrão de URL será o mesmo de leitura de registro único, mudando apenas o verbo REST:

```
/api/v2/<token>/contents/<nome_do_template>/<id_do_content>
```

No caso de sites com i18n, submeta os registros da seguinte forma: `<locale>[<nome_atributo>]=<valor>`. Ex:

```
curl -X PUT --data "pt-BR[name]=MeuSite&en[name]=MyWebSite" / 
  http://beta.site321.com.br/api/v2/<token>/contents/projects/115f9658-1300-11e6-a148-3e1d05defggj
```

**IMPORTANTE:** Atributos omitidos serão considerados nulos. Observe isso para não perder informações de traduções, p. ex.

### Exclusão de Registros

Para excluir um registro, envie um verbo DELETE para o endpoint do registro. Ex:

```
curl -X DELETE http://beta.site321.com.br/api/v2/<token>/contents/projects/115f9658-1300-11e6-a148-3e1d05defggj
```

Isso excluirá o registro, incluindo suas traduções.

## Menus

Da mesma forma que os templates, os Menus possuem API disponível. Para listar todos os menus, utilize:

```
/api/v2/<token>/menus
```

Se você quiser os dados de um menu específico, utilize:

```
/api/v2/<token>/menus/<nome_do_menu>
```