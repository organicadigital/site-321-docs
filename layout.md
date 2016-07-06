# Layout

Ao fazer a definição do cadastro, com os campos desejados, conforme descrito em [Linguagem de Marcação](linguagem_de_marcacao.md), será possível personalizar a apresentação do formulário.

Por padrão, o Site 321 gera um formulário vertical, com todos os campos, um abaixo do outro (um por linha). Em pequenos cadastros, isso é o suficiente. Mas, se você busca algo mais organizado, poderá utilizar a personalização de Layout.

Essa personalização poderá ser feita na própria definição de cadastros do Template, na aba *Layout*. Utilize o seguinte formato para organizar seus cadastros:

```
- title: Basic info
- row:
    - col6: name
    - col6: age
- row:
    - col12: bio

- title: Address
- row:
    - col8: address
    - col4: number
- row:
    - col4: district
    - col4: city
    - col4: zip
- row:
    - col12: Personalized <strong>HTML</strong>.
```

Entenda a função de cada campo:

| Campo | Descrição | Pai |
| -- | -- | -- |
| **title** | Gera um título para agrupamento de informações no cadastro. Como se fossem fieldsets, que permitem organizar o cadastro em blocos. | (nenhum) |
| **row** | Cria uma linha no layout, que poderá conter colunas, como se fossem tabelas. | (nenhum) |
| **col[1..12]** | Gera colunas dentro de uma linha. Deverá iniciar com a palavra *col* e terminar com um número de 1 a 12. Utiliza as [grids do Bootstrap](http://getbootstrap.com/css/#grid). Informe o nome da coluna que deverá aparecer nesta coluna, ou um HTML que deverá ser apresentado nesta célula. | **row** |
