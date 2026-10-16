# cayolc.github.io

Código do site [cayolc.github.io](https://cayolc.github.io), feito com [Quarto](https://quarto.org).

## No dia a dia

- `quarto preview` abre o site no navegador e atualiza a cada arquivo salvo.
- Para publicar, faça commit e push na branch `main`. O GitHub renderiza e publica sozinho em um ou dois minutos; o andamento aparece na aba **Actions** do repositório.

## Onde está cada coisa

| Português | Inglês | Conteúdo |
|---|---|---|
| `index.qmd` | `en/index.qmd` | Página inicial |
| `pesquisa.qmd` | `en/research.qmd` | Dissertação, TCC, iniciação científica |
| `blog.qmd` | `en/blog.qmd` | Lista dos posts (automática) |
| `posts/` | `en/posts/` | Um post por pasta; `modelo/` e `template/` são modelos |
| `ensino.qmd` | `en/teaching.qmd` | Ensino (rascunho, fora do menu) |

Outros arquivos:

| Arquivo | Conteúdo |
|---|---|
| `_quarto.yml` | Menu, idiomas, tema, rodapé |
| `arquivos/` | PDFs: dissertação, slides |
| `refs.bib` | Bibliografia dos posts |
| `_macros.qmd` | Macros LaTeX dos posts |
| `tema/` | Cores, tipografia e o script do seletor de idioma |

Trechos marcados com `{.preencher}` aparecem com fundo amarelo até serem trocados pelo texto definitivo.

## Dois idiomas

As páginas em inglês ficam na pasta `en/`, que tem o idioma trocado para inglês no `en/_metadata.yml` (por isso aparecem "Theorem" e "Proof" em vez de "Teorema" e "Demonstração").

O menu de idioma leva à mesma página no outro idioma. Para traduzir um post, copie-o para `en/posts/` com o mesmo nome de pasta: `posts/derivados/` e `en/posts/derivados/` ficam ligados automaticamente. Se um post só existir em um idioma, o menu leva ao blog do outro.

No `_quarto.yml`, cada item do menu tem `{.so-pt}` ou `{.so-en}`, que decide em quais páginas ele aparece. Uma página nova com nomes diferentes nos dois idiomas precisa ser acrescentada à lista `nomes` em `tema/idioma.html`.

## Escrever um post

1. Copie `posts/modelo/` para `posts/nome-do-post/`.
2. No cabeçalho, troque título, data, descrição e categorias e apague a linha `draft: true`. Enquanto ela existir, o post aparece no `quarto preview`, mas não é publicado.
3. Ambientes: `::: {#thm-nome}` … `:::`, com os prefixos `thm`, `lem`, `cor`, `prp`, `cnj`, `def`, `exm`, `exr`; demonstração em `::: {.proof}`. Referência cruzada com `@thm-nome`; citação com `@chave`, usando as chaves do `refs.bib`.
4. As macros de `_macros.qmd` valem nos posts que têm `{{< include /_macros.qmd >}}` logo depois do cabeçalho, como os modelos.

Figuras em TikZ: compile a figura (classe `standalone`), gere o SVG com `dvisvgm --pdf --no-fonts figura.pdf` e inclua com `![Legenda](figura.svg){#fig-nome}`.

## PDFs

Coloque o arquivo em `arquivos/` e faça o link: `[PDF](arquivos/dissertacao.pdf)`.

## Ensino

Quando quiser publicar a seção, apague `draft: true` de `ensino.qmd` e de `en/teaching.qmd` e descomente as abas *Ensino* e *Teaching* no `_quarto.yml`.
