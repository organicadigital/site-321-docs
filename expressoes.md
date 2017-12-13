# Expressões

Em algum locais é possível utilizar algumas expressões e pequenas regras de negócio.

Para isso, utilizamos [Liquid](https://github.com/Shopify/liquid).

TODO: Melhorar descrição aqui

O Site 321 disponibiliza os dados em formato JSON para uso como variáveis.

## Filtros Personalizados

Para simplificar a utilização das expressões e regras de negócio, alguns filtros específicos do Site 321 foram criados. Confira abaixo.

### find_association

Associações são passadas para o Liquid somente como variáveis. Para buscar os dados relacionados será necessário utilizar esse filtro. Imagine o seguinte modelo:

* Template `user`:

```
username:
    label: Username
    type: string
    required: true
email:
    label: E-mail
    type: email
    required: true
```

* Template `log`:

```
user:
    label: User
    type: association
    module: user
    required: true
content:
    label: Log Content
    type: text
    required: true
```

Para acessar o e-mail do usuário através do template `log`, utilize a expressão da seguinte forma:

```javascript
{% assign user = user.id | find_association module: 'user' %}
{{ user.email }}
```

### api_query

Executa uma busca em uma API do Site321. Exemplo:

```javascript
{% capture query_string %}
  {
    'name': {
      'contains': ['Foo']
    }
  }
{% endcapture %}

{% assign data = query_string | api_query module: 'user' %}
```

A "query_string" neste caso sempre será em formato JSON, simplificando a construção do filtro.