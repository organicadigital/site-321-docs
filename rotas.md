# Rotas

O Site321 prevê a funcionalidade de rotas.

As rotas permitem a criação de URLs para sites e aplicações, com possibilidade de utilização de variáveis e controle de rotas órfãs (rotas cuja página não existe mais), com redirecionamento.

É uma funcionalidade experimental disponível de forma restrita.

## Configuração

* Acesse o menu Rotas;
* Clique em cadastrar;
* No campo "Padrão de URI", utilize o padrão que você deseja usar. P. ex: `/#{slug}/`. Variáveis com espaçamentos e caracteres especiais serão convertidos em padrão de URL;
* Em "Padrão de Redirecionamento" você poderá escolher para onde o padrão anterior deverá redirecionar. Ex, você pode redirecionar `/#{code}` para `/most-readable/#{code}`;
* Em "Template" escolha o template que irá ser responsável por gerar as rotas. Cara cadastro desse template será elegível a uma rota, e é de lá que as variáveis serão buscadas. Portanto tenha certeza que as variáveis existem nesse cadastro;
* Em "Redirecionar Registros Órfãos" você poderá definir o que fazer quando uma rota aponta para um conteúdo que foi excluído. Automaticamente você poderá enviar para uma outra rota. P. ex: Se você tiver um cadastro de produtos que pertencem a uma categoria e, ao excluir o produto você quiser mandar para a página genérica da categoria, você poderá usar esse campo para tal.

### Outras opções

O Site321 tem suporte a i18n, portanto as rotas também poderão respeitar esse padrão. Para contextualizar a sua rota com o idioma, você poderá utilizar a variável especial `$locale`.

Ex:

`/#{$locale}/#{slug}`

## Conclusão

Está claro que esta funcionalidade ainda precisa de melhorias de usabilidade para ficar totalmente entendida em seu potencial. Entretanto é uma ferramenta poderosa que pode lhe gerar excelentes resultados em SEO.


