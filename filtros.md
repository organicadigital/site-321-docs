# Filtros

O Site321 permite que dados sejam filtrados através da sua API, com uma diversa gama de possibilidades.

Imagine a API `/api/v2/<token>/contents/course` com os seguintes dados:

```
{
  "current_page": 1,
  "next_page": null,
  "total_pages": 1,
  "total_count": 2,
  "limit": 20,
  "items": [
    {
      "name": "Foo",
      "meta_description": "This is a Foo Meta Description",
      "background": null,
      "id": "5a1d22f1-82c3-47fe-a011-dea33f374fa6",
      "touched_by_last_importation": false,
      "html_page_url": nil,
      "created_at": "2017-12-02T10:13:56.809-02:00",
      "updated_at": "2017-12-03T20:19:11.689-02:00"
    },
    {
      "name": "Bar",
      "meta_description": "This is a Bar Meta Description",
      "background": null,
      "id": "5a1d22f1-82c3-47fe-a011-dea33f37g197",
      "touched_by_last_importation": false,
      "html_page_url": nil,
      "created_at": "2017-12-02T10:14:56.452-02:00",
      "updated_at": "2017-12-03T20:19:12.879-02:00"
    }
  ]
}
```

Você poderá filtrar ela passando parâmetros por Query String, no seguinte formato: `/api/v2/<token>/contents/course?search[name][contains][0]=Foo&search[meta_description][start][0]=This`

Como você pode ver, esse padrão de `search` permite a composição de diversos filtros na API. Você pode compor a query com diversos tipos de dados e filtros, respeitando o seguinte padrão: ```search[<field>][<type>][<index>]=<value>``` 

Onde:

*  ```<field>```: Nome do campo a ser buscado;
*  ```<type>```: Tipo de busca a ser processada;
*  ```<index>```: Índice de busca sendo 0 ou 1. Utilizado para tipos de busca com intervalo (between);
*  ```<value>```: Valor da query.

## Tipos Disponíveis

### contains

Faz a busca no campo vendo se ele contém o conteúdo, em qualquer parte do texto. Ex: `/api/v2/<token>/contents/course?search[name][contains][0]=Foo`

### start

Faz a busca no campo vendo se ele inicia com o conteúdo. Ex: `/api/v2/<token>/contents/course?search[name][start][0]=Foo`

