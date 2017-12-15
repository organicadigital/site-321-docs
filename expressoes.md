# Expressões

Em algum locais é possível utilizar algumas expressões e pequenas regras de negócio.

Para isso, utilizamos [Liquid](https://github.com/Shopify/liquid).

TODO: Melhorar descrição aqui

O Site 321 disponibiliza os dados em formato JSON para uso como variáveis.

## Filtros Personalizados

Para simplificar a utilização das expressões e regras de negócio, alguns filtros específicos do Site 321 foram criados. Confira abaixo.

### slices_of

Quebra um array em sub arrays com a quantidade de itens informada. P. ex:

```
{% assign array = "a|b|c|d" | split: '|' %}
{% assign slices = array | slices_of: 2 %}
{{slices}}
```

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

### filter_module

Executa uma busca em um modelo do Site321. Exemplo:

```javascript
{% assign data = '{"name":{"start":{"0":"B"}}}' | filter_module 'user', 'pt-BR' %}
```

O primeiro argumento representa a query a ser enviada. Consulte o tópico [Filtros](/filtros.md) para mais informações. É uma representação JSON da busca, sendo mais fácil de construir para fins de leitura.   

O último argumento é o locale a ser pesquisado.