# cayolc.github.io

Código do site [cayolc.github.io](https://cayolc.github.io), feito com [Quarto](https://quarto.org).

## No dia a dia

- `quarto preview` abre o site no navegador e atualiza a cada arquivo salvo.
- Para publicar, faça commit e push na branch `main`. O GitHub renderiza e publica sozinho em um ou dois minutos; o andamento aparece na aba **Actions** do repositório.

## Onde está cada coisa

| Arquivo | Conteúdo |
|---|---|
| `_quarto.yml` | Menu, idioma, tema, rodapé |
| `index.qmd` | Página *Sobre* |
| `pesquisa.qmd` | TCC e dissertação |
| `blog.qmd` | Lista dos posts (automática) |
| `posts/` | Um post por pasta; `posts/modelo/` é o modelo |
| `ensino.qmd` | Ensino (rascunho, fora do menu) |
| `arquivos/` | PDFs: TCC, dissertação, slides |
| `refs.bib` | Bibliografia dos posts |
| `_macros.qmd` | Macros LaTeX dos posts |
| `tema/` | Cores e tipografia |

Trechos marcados com `{.preencher}` aparecem com fundo amarelo até serem trocados pelo texto definitivo.

## Escrever um post

1. Copie `posts/modelo/` para `posts/nome-do-post/`.
2. No cabeçalho, troque título, data, descrição e categorias e apague a linha `draft: true`. Enquanto ela existir, o post aparece no `quarto preview`, mas não é publicado.
3. Ambientes: `::: {#thm-nome}` … `:::`, com os prefixos `thm`, `lem`, `cor`, `prp`, `cnj`, `def`, `exm`, `exr`; demonstração em `::: {.proof}`. Referência cruzada com `@thm-nome`; citação com `@chave`, usando as chaves do `refs.bib`.
4. As macros de `_macros.qmd` valem nos posts que têm `{{< include /_macros.qmd >}}` logo depois do cabeçalho, como o modelo.

Figuras em TikZ: compile a figura (classe `standalone`), gere o SVG com `dvisvgm --pdf --no-fonts figura.pdf` e inclua com `![Legenda](figura.svg){#fig-nome}`.

## PDFs

Coloque o arquivo em `arquivos/` e faça o link: `[PDF](arquivos/tcc.pdf)`.

## Ensino

Quando houver o primeiro curso, apague `draft: true` de `ensino.qmd` e descomente a aba *Ensino* no `_quarto.yml`.
