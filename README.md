# Vox Aurora — Protótipo de site coral

Site institucional estático para um coral fictício (`Vox Aurora`). Todo o conteúdo é genérico e demonstrativo: nomes, datas, valores, endereços e e-mails são inventados.

## Stack

- HTML estático, CSS puro com variáveis e JS vanilla.
- Fontes via Google Fonts (Cormorant Garamond + Inter).
- SVGs inline para logo, favicon, hero, retrato do maestro e mídia (sem assets externos).
- Sem build step, sem dependências.

## Estrutura

```
coral-site/
├── index.html        # Página única com 7 seções ancoradas
├── styles.css        # Design tokens + layout responsivo
├── script.js         # Menu mobile, reveal-on-scroll, form demo
├── favicon.svg       # Favicon
├── assets/
│   └── logo.svg      # Logo standalone (também inline no header)
└── README.md
```

## Seções (âncoras)

| Âncora        | Conteúdo                                                                 |
|---------------|--------------------------------------------------------------------------|
| `#inicio`     | Hero com 2 CTAs (Ver agenda / Participar de audições) + KPIs             |
| `#sobre`      | História do coral, maestro fictício, 3 pilares                           |
| `#agenda`     | 3 concertos com data, local, duração, repertório, status, CTA           |
| `#audicoes`   | 4 etapas + vozes procuradas + critérios + CTA de inscrição               |
| `#midia`      | Grid editorial: 1 vídeo grande, 1 áudio, 1 vídeo pequeno, 2 fotos        |
| `#apoie`      | 3 cotas (Aurora, Lumen featured, Patrocínio institucional)               |
| `#contato`    | Info + formulário demo (sem envio real, validação visual + mensagem ok)  |

## Design

- **Paleta:** vinho profundo (`#4A1422`) + marfim (`#F4EFE6`) + grafite quente (`#2A2421`) + dourado discreto (`#B8893F`).
- **Tipografia:** Cormorant Garamond (display, editorial) + Inter (UI/body).
- **Estética:** editorial, contida, com momentos quentes em vinho profundo (seção de audições) e dourado como acento pontual (CTAs especiais, dot do logo, badges).
- **Layout:** mobile-first, breakpoint em 860px. Grids editoriais com spans assimétricos na seção de mídia.

## Como editar textos

Todo o conteúdo está em `index.html`, organizado por `<section id="...">`. Para mudar:

- **Nome do coral** → busque `Vox Aurora` (header, brand-name, footer, meta tags).
- **Maestro fictício** → busque `Helena Vasconcelos` no bloco `.maestro-card`.
- **Agenda** → 3 blocos `<article class="agenda-item">` em `#agenda`. Edite `.day`, `.month`, `.year`, `h4`, `.agenda-meta`, `.agenda-rep` e o `<span class="status-badge ...">` (`open`/`soon`/`full`).
- **Audições** → blocos `.aud-step` (etapas) e `.aud-side` (vozes/critérios).
- **Mídia** → cards `.media-card` com classe de span (`large`/`medium`/`small`).
- **Apoie** → blocos `.tier` (o do meio leva `.featured`).
- **Contato** → bloco `.contato-info` e campos do `<form>`.

## Como ajustar visual

- **Cores** → variáveis CSS no topo de `styles.css` (`:root { --c-* }`).
- **Tipografia** → variáveis `--f-display`, `--f-body` e a escala `--fs-*`.
- **Espaçamento de seções** → `--space-section`.
- **Largura máxima** → `--container` (1200px).

## Próximos ajustes possíveis

1. **Fotografia real:** substituir os SVGs decorativos por fotos do coral (manter aspect-ratio dos containers para não quebrar grid).
2. **Backend de contato:** o `<form>` já tem `id="contact-form"`; basta apontá-lo para um endpoint (Formspree, função serverless, etc.) e remover o `preventDefault` em `script.js`.
3. **Página de agenda detalhada:** transformar cada `.agenda-item` em link para `/concertos/lumen.html` etc.
4. **Acessibilidade extra:** adicionar `<track>` em áudios/vídeos reais, transcrições, e foco visível com mais contraste.
5. **SEO:** adicionar `sitemap.xml`, JSON-LD `Event` para concertos, `MusicGroup` para o coral.

## Deploy

O projeto está pronto para `deploy_website(project_path="/home/user/workspace/coral-site")`. Não há build step.
