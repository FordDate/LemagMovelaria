# Lemag Movelaria — landing page

Página única, estática. Sem build, sem dependências: abra `index.html` ou suba a
pasta inteira em qualquer hospedagem (Netlify, Vercel, Hostinger, S3).

```
lemag-landing/
├── index.html      ← página completa (HTML + CSS inline)
├── assets/         ← 11 imagens otimizadas (~1,2 MB no total)
└── README.md
```

## CTA

Todos os 5 pontos de contato apontam para o mesmo link, com mensagem pré-preenchida:

```
https://wa.me/5543999968353?text=Olá! Gostaria de solicitar um orçamento de móveis planejados.
```

`(43) 9.9996-8353` → `5543999968353` (55 = Brasil, 43 = DDD). Para trocar o número
ou o texto, busque por `wa.me` no `index.html` — são 5 ocorrências.

## Fontes

| Uso | Fonte | Substituta |
|---|---|---|
| Títulos e botões | Montserrat Bold | — (Google Fonts) |
| Olho de seção, números | Cambria Bold | Caladea |
| Texto e subtítulos | Calibri | Carlito |

**Cambria e Calibri são fontes proprietárias da Microsoft** e não podem ser
servidas como webfont. Quem tem Windows/Office vê as originais; os demais caem
para Caladea e Carlito, que são substitutas livres *metricamente compatíveis* —
o layout não muda. Isso foi medido: numa mesma frase de teste, Carlito e Calibri
dão exatamente a mesma largura (437,67 px); Caladea fica a 1,5% do Cambria.

Montserrat, Caladea e Carlito vêm do Google Fonts (uma requisição). Para uso
totalmente offline, baixe os `.woff2` e troque o `<link>` por `@font-face`.

## Cores

Extraídas por amostragem dos pixels do portfólio, e documentadas em
`../DESIGN.md`.

| Token | Hex | Uso |
|---|---|---|
| `--navy` | `#0a004a` | títulos, texto de destaque, rodapé |
| `--gold` | `#b18c2f` | **só decorativo**: barra, padrão, fundo de botão |
| `--gold-text` | `#7c6221` | dourado para texto |
| `--gold-muted` | `#c4ab6d` | padrão decorativo, acentos no rodapé |
| `--sand` | `#d3c49f` | filetes e divisores |
| `--neutral` | `#ebebeb` | fundo de toda a página |
| `--ink` | `#000000` | corpo de texto |

**Não existe branco neste sistema** — o fundo é `#ebebeb`. O que parece cartão
branco no portfólio é o próprio fundo aparecendo por um recorte. A logo original
(`logo.png`) vem com fundo branco opaco, então aqui ela foi tratada com blend
`multiply` sobre o neutro.

### Acessibilidade

Os 23 estilos de texto da página passam no WCAG AA (verificado com script, não no olho).

O dourado da marca (`#b18c2f`) rende só **2,64:1** sobre o fundo `#ebebeb` —
reprova para texto normal (4,5:1) e também para texto grande (3:1). Por isso ele
nunca é usado em tipografia aqui: os títulos dourados usam `#7c6221`, o mesmo tom
escurecido a 70%, que dá 4,86:1. Sobre o navy o dourado é seguro (8,45:1), que é
como o rodapé funciona.

Se preferir fidelidade exata ao portfólio impresso em vez da conformidade,
troque `--gold-text` por `#b18c2f` — mas saiba que os títulos deixam de passar.

## Conteúdo

Todo o texto é da própria empresa, extraído das 20 páginas do portfólio
(história, diferenciais, parceria Studio 8, tecnologia PUR 40, as 7 etapas do
processo, vistorias de 30/90 dias). Nada foi inventado.

## Pendências

- [ ] Confirmar se pode publicar a foto dos sócios (Leandro e Matheus) no site.
- [ ] Trocar as fotos por versões em alta: as atuais foram extraídas de PNGs
      achatados do portfólio, então já passaram por uma recompressão.
- [ ] Domínio próprio + favicon.
- [ ] Se quiser rastrear conversão, adicionar evento de clique nos links do WhatsApp.
