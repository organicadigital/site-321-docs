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
{% assign user = user.id | find_association 'user' %}
{{ user.email }}
```

### api_call

Executa uma busca em uma API do Site321. Exemplo:

```javascript
{% assign data = 'search[name][contains][0]=Foo' | api_call 'user' %}
```

O primeiro argumento representa a query string a ser enviada. Consulte o tópico [Filtros](/filtros.md) para mais informações.