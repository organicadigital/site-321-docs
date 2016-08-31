# Campos Ocultos

Em alguns momentos, será desejado esconder algum campo. 

Por exemplo, se você possui um formulário que recebe dados de APIs externas, que não são úteis para o usuário final, poderá ser interessante esconder.

Outro caso comum é em relacionamentos. Na modal aberta ao cadastrar um campo relacionado, um campo do tipo select aparece mostrando o registro pai, de onde a modal foi aberta. Você poderá desejar esconder ele, impedindo que o usuário troque essa informação.

Para isso, utilize o atributo `hidden: true`.

Ex:

```
name:
  label: Name
  hidden: true
```

Isso fará que com que o campo fique no HTML, mas um `display: none` será aplicado ao `wrapper` do campo.