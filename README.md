# Hub de Performance — BrandField

Portal centralizado para navegação dos relatórios de performance digital da agência **BrandField**. Agrupa relatórios de Tráfego Pago (Meta Ads e Google Ads) e Orgânico (Instagram e outros canais) organizados por cliente, ano e mês.

## Estrutura de arquivos

```
/
├── index.html                        # Hub principal — lista todos os clientes
├── assets/
│   └── logo-brandfield.svg           # Logo da agência (favicon compartilhado)
└── clientes/
    └── {slug-do-cliente}/
        ├── index.html                # Redireciona para o hub do ano atual (2026)
        └── 2026/
            ├── index.html            # Hub do ano — lista meses e canais disponíveis
            ├── relatorio_pago_{mes}_2026.html      # Relatório de Tráfego Pago
            ├── relatorio_organico_{mes}_2026.html  # Relatório Orgânico
            ├── janeiro/index.html    # Página temporária (redireciona ou exibe "em breve")
            ├── fevereiro/index.html
            └── organico/
                ├── janeiro/index.html
                └── fevereiro/index.html
```

## Clientes ativos

| Cliente | Slug | Canais | Relatórios disponíveis |
|---------|------|--------|------------------------|
| Gairdin CG | `gairdin-cg` | Meta Ads, Google Ads, Orgânico | Pago Jan/Fev · Orgânico Fev |
| Gairdin SP | `gairdin-sp` | Meta Ads, Google Ads, Orgânico | — |
| Funky Fresh | `funky-fresh` | Meta Ads, Google Ads, Orgânico | Orgânico Jan/Fev |
| Dois Amores Doces | `dois-amores-doces` | Meta Ads, Google Ads, Orgânico | Orgânico Fev |
| Dois Amores Garden | `dois-amores-garden` | Meta Ads, Google Ads, Orgânico | Orgânico Fev |
| Demolição Cristão | `demolicao-cristao` | Meta Ads, Orgânico | Orgânico Fev |
| Thomaz Lanches | `thomaz-lanches` | Meta Ads, Google Ads, Orgânico | — |
| Casa Colonial | `casa-colonial` | Orgânico | Orgânico Fev |
| Enoteca Decanter | `decanter` | Orgânico | — |
| Terroir Cozinha | `terroir` | Orgânico | — |
| Villa Raiano | `villa-raiano` | Orgânico | — |
| MT Tastes | `mt-tastes` | Orgânico | — |
| MS Conecta | `msconecta` | Orgânico | Orgânico Fev |

## Convenção de nomenclatura dos relatórios

```
relatorio_{canal}_{mes}_{ano}.html
```

Exemplos:
- `relatorio_pago_janeiro_2026.html` — Tráfego Pago de Janeiro 2026
- `relatorio_organico_fevereiro_2026.html` — Orgânico de Fevereiro 2026

## Como adicionar um novo relatório

1. Gere o arquivo HTML do relatório seguindo a convenção acima.
2. Salve o arquivo em `/clientes/{slug-do-cliente}/{ano}/`.
3. Abra o hub do cliente (`/clientes/{slug-do-cliente}/{ano}/index.html`) e atualize o card do mês correspondente:
   - Troque o `<div class="card card--pending">` por `<a class="card card--available" href="../{nome-do-arquivo}.html">`.
   - Troque o badge `badge--pending` por `badge--available`.
4. Se o cliente for novo, adicione-o ao hub principal (`/index.html`) e crie a estrutura de pastas.

## Como adicionar um novo cliente

1. Crie a pasta: `clientes/{novo-slug}/`.
2. Crie `clientes/{novo-slug}/index.html` com redirecionamento para `./2026/index.html`.
3. Crie `clientes/{novo-slug}/2026/index.html` copiando o modelo de outro hub de cliente e ajustando nome e canais.
4. Adicione o novo cliente ao `index.html` raiz na lista `clients-grid`.

## Tecnologias

- HTML5 + CSS3 puro (sem frameworks ou build step)
- Fontes: [Playfair Display](https://fonts.google.com/specimen/Playfair+Display) e [DM Sans](https://fonts.google.com/specimen/DM+Sans) via Google Fonts
- Hospedagem: estático (GitHub Pages, Netlify ou similar)

## Boas práticas adotadas

- Todos os arquivos em UTF-8 sem BOM (enforçado via `.gitattributes`)
- `lang="pt-BR"` em todos os documentos
- `prefers-reduced-motion` respeitado no CSS
- Atributos `aria-label` e `aria-labelledby` nas listas e seções
- Favicon SVG compartilhado via caminhos relativos
- Redirecionamento automático para o ano mais recente via `meta http-equiv="refresh"`
