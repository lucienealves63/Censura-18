# Censura 18

Página publicada no GitHub Pages com o catálogo **Mais Vendidos de Outubro** da Censura 18.

## Conteúdo

- `Encerramento do site C18.html` — página principal: catálogo "Mais Vendidos de Outubro" em 31 páginas
  (campanha publicada originalmente em PDF).

## Características

- **Autônoma:** todas as 31 páginas estão embutidas como imagens JPEG em base64.
  Não há dependências externas (sem CDN, fontes remotas ou imagens hospedadas em terceiros),
  então a página funciona offline e não quebra se um servidor de imagens sair do ar.
- **Sem build:** é um único arquivo HTML estático, servido diretamente pelo GitHub Pages.
- **Nome do arquivo mantido** de propósito, para preservar a URL já divulgada.
- **Responsiva:** abaixo de 820 px de largura cada página ocupa 100% da tela e a imagem escala
  junto (proporção 793,6:1122,56), sem necessidade de pinçar ou dar zoom.
- **Link na última página:** o bloco "Acesse já o nosso link" tem uma área clicável sobre a imagem
  que leva a `https://censura18.my.canva.site/c18` (com `aria-label`, foco visível e área de toque
  de 66% da largura da página).
- **Carregamento leve:** apenas a primeira página é carregada imediatamente
  (`loading="eager" fetchpriority="high"`); as demais usam `loading="lazy" decoding="async"`.

## Publicação

O site fica em **https://lucienealves63.github.io/Censura-18/** e é publicado pelo workflow
[`.github/workflows/pages.yml`](.github/workflows/pages.yml) a cada push na `main`:

- o Pages está configurado no modo **GitHub Actions** (`build_type: workflow`), então nenhum build
  é executado — o repositório é apenas empacotado (`actions/upload-pages-artifact`) e publicado
  (`actions/deploy-pages`);
- o environment `github-pages` aceita deploy **somente da branch `main`**;
- dá para disparar manualmente em **Actions → Deploy GitHub Pages → Run workflow**.

`index.html` é a porta de entrada: redireciona na hora (meta refresh + `location.replace`) para
`Encerramento do site C18.html`, com botão de fallback caso o redirecionamento esteja bloqueado.

Links:

- raiz (com redirect): https://lucienealves63.github.io/Censura-18/
- catálogo direto: https://lucienealves63.github.io/Censura-18/Encerramento%20do%20site%20C18.html

Toda alteração passa por um pull request antes de ir ao ar.

## Como atualizar o catálogo

1. Gere a nova versão do catálogo em HTML (por exemplo, a partir do PDF da campanha).
2. Substitua o conteúdo de `Encerramento do site C18.html`, mantendo as imagens embutidas em base64.
3. Ajuste o `<title>`, faça commit e abra um pull request para a `main`.
