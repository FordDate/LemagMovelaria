# Lemag Movelaria — landing page

Página única, estática. Sem build, sem dependências: abra `index.html` ou suba a
pasta inteira em qualquer hospedagem (Netlify, Vercel, Hostinger, GitHub Pages).

```
lemag-landing/
├── index.html      ← página completa (HTML + CSS + JS inline)
├── assets/         ← imagens otimizadas
└── README.md
```

> **GitHub:** suba a pasta `assets` inteira junto com o `index.html` (arraste a
> pasta, não os arquivos soltos). Zip não funciona — o GitHub não descompacta.

## ⚠️ Ativar o formulário de contato (coleta de e-mails)

A seção "Vamos conversar" tem um formulário (nome, e-mail, mensagem) que valida os
dados, mas **ainda não está conectado a um provedor**. Hoje ele exibe "Formulário
ainda não conectado" e aponta o cliente ao WhatsApp; não guarda nada. Para ativar:

1. **Formspree** (mais simples p/ site estático): crie um form grátis em
   formspree.io, copie o endpoint (`https://formspree.io/f/xxxxxxx`).
2. No `index.html`, ache `id="contato-form"` e troque
   `data-endpoint="COLE_AQUI_O_ENDPOINT"` pelo seu endpoint.
3. Pronto: os contatos passam a chegar no seu provedor e o formulário mostra
   "Recebido! A gente entra em contato em breve".

Alternativas comuns no Brasil: **Brevo** e **RD Station** (ambos têm formulário/API;
use o endpoint de submissão deles no `data-endpoint`). Há um checkbox de
consentimento (LGPD) já obrigatório no formulário.

## Ajustes de layout e ritmo (última rodada)

- **Cabeçalho menor + `scroll-padding-top: 86px`** — os links do menu param logo
  abaixo do header, sem tampar o título da seção.
- **Ritmo vertical único** — token `--section-y` (104px desktop, 72px mobile)
  aplicado igual em todas as bandas. Isso deu respiro à banda "Vamos conversar" e
  reduziu o vazio antes de "Projetos", mantendo a proporção na página toda.
- **Frase de destaque no lugar dos números** — saiu o "100%", os stats viraram
  "*Três gerações* da mesma família, *14 anos* dedicados à marcenaria" em serifa
  grande, com barra dourada e os termos-chave em itálico dourado.
- **Padrão marcante como no cartão de visita** — a faixa `pattern.png` passou de
  0,16 para 0,9 de opacidade (coluna dourada cheia na borda). Para nunca tocar o
  texto, ela só aparece em telas largas (≥1420px), onde há margem sobrando; abaixo
  disso fica escondida.
- **Hero** — removida a palavra "familiar" ("Marcenaria em Londrina, PR").

## Ajuste de "alto padrão" (versão anterior)

Pacote de refino para elevar a sensação de luxo e reforçar os CTAs:

- **Overlay do herói** refeito — escurece só a faixa esquerda (onde fica o texto)
  e a base, deixando a foto respirar no topo e à direita, em vez do bloco navy
  arroxeado anterior.
- **Paleta mais quente** — base calcário `#efece5` no lugar do cinza `#ebebeb`.
- **Padrão dourado discreto** — de 0,5 para 0,16 de opacidade (fio, não estampa).
- **Mais respiro** — seções com 140px de padding; títulos mais leves (peso 600)
  e com mais espaçamento entre letras.
- **CTAs mais fortes** — "Peça seu orçamento" (herói), botões maiores com sombra,
  linha de reforço "Resposta no mesmo dia. Sem compromisso." e selo de confiança
  (14 anos, atendimento personalizado, tecnologia PUR 40) no fechamento.

## Mudanças da última rodada

- **Título do herói** agora em serifa (caixa mista, editorial).
- **Seção "Agende uma visita" removida** — a Lemag não tem showroom físico. Saiu
  junto o mapa do Google.
- **Newsletter virou formulário de contato** e foi **fundido** com a banda "Vamos
  conversar": formulário (nome + e-mail + mensagem) à esquerda, WhatsApp à direita.
- **Sublinhado do logo removido** (era o `text-decoration` padrão do link).
- **Copy limpa de travessões (—) e separadores (·)** que passavam sensação de texto
  gerado; a regra ficou registrada no `DESIGN.md`.

## Estrutura e movimento

Inspirada em scmovelaria.com.br, adaptada à identidade **clara** da Lemag:

- **Herói em carrossel de tela cheia** — 5 fotos de projeto que trocam sozinhas
  (crossfade + leve zoom "ken burns"), com setas, indicadores e chamada por cima.
- **Bandas tonais alternadas** dividem os tópicos e eliminam o vazio branco:
  claro (`#ebebeb`) → banda navy (manifesto) → greige (`#e3ded5`, diferenciais)
  → claro (projetos) → navy (contato/rodapé).
- **Movimento no scroll** — títulos, textos, cards e imagens surgem com *fade-up*
  conforme entram na tela (IntersectionObserver). O cabeçalho fica transparente
  sobre o herói e vira sólido (com a logo colorida) ao rolar.
- **Carrossel de projetos** — trilho horizontal arrastável, com setas.
- Tudo respeita `prefers-reduced-motion` (desliga animações para quem pede).

## CTA

Os pontos de contato apontam para o mesmo link, com mensagem pré-preenchida:

```
https://wa.me/5543999968353?text=Olá! Gostaria de solicitar um orçamento de móveis planejados.
```

`(43) 9.9996-8353` → `5543999968353`. Para trocar número ou texto, busque por
`wa.me` no `index.html`.

## Assets

| Arquivo | Origem |
|---|---|
| `logo.png` | logo LEMAG que você enviou (PNG sem fundo), usado no cabeçalho |
| `pattern.png` | o padrão que você enviou, usado nas faixas decorativas das bordas |
| `favicon-32/180/512.png`, `apple-touch-icon.png` | gerados do arquivo de favicon que você enviou |
| `slide1–5.jpg` | fotos do carrossel do herói |
| `g1–g8.jpg` | fotos do carrossel de projetos |
| `socios.jpg` | recorte da foto dos sócios |

## Fontes

| Uso | Fonte | Substituta (web) |
|---|---|---|
| Títulos e botões | Montserrat Bold | — (Google Fonts) |
| Olho de seção, números, palavras em itálico | Cambria Bold | Caladea |
| Texto e subtítulos | Calibri | Carlito |

Cambria e Calibri são proprietárias da Microsoft e não podem ser servidas como
webfont. Quem tem Windows/Office vê as originais; os demais caem para Caladea e
Carlito, substitutas livres **metricamente compatíveis** — o layout não muda.

## Cores

| Token | Hex | Uso |
|---|---|---|
| `--navy` | `#0a004a` | títulos, bandas escuras, rodapé |
| `--gold` | `#b18c2f` | **só decorativo**: padrão, barra, fundo de botão |
| `--gold-text` | `#755c1f` | dourado para texto (passa AA nas bandas clara e greige) |
| `--gold-muted` | `#c4ab6d` | palavras em itálico e acentos sobre navy |
| `--neutral` | `#efece5` | banda clara base (calcário quente) |
| `--surface-2` | `#e6e0d5` | banda greige que divide tópicos |

**Não existe branco no sistema.** A logo e o padrão têm fundo transparente de
verdade (o branco que aparece num visualizador é a transparência renderizada).

### Acessibilidade

Todos os textos passam no WCAG AA (verificado por script, sem erros de console e
sem overflow horizontal em desktop e mobile).

O dourado da marca (`#b18c2f`) só rende 2,64:1 sobre fundo claro e reprova para
texto — por isso, em tipografia, os títulos/olhos usam `#755c1f`; o dourado cheio
fica em elementos decorativos e fundos de botão. Sobre navy o dourado é seguro
(8,45:1).

## Conteúdo — o que mudou nesta versão

- **Removida** a seção "Do briefing ao pós-entrega" (a lista de 7 etapas).
- **Removido** o número "30/90 dias de vistoria pós-entrega" dos indicadores.
- O card "Cuidado pós-entrega" foi **reescrito** para falar do acompanhamento
  após a instalação **sem prometer a vistoria marcada em 30/90 dias** — era a
  mesma "vistoria marcada" que você mandou remover. Se quiser o card fora de vez,
  ou o texto de outro jeito, é só avisar.

Todo o restante do texto continua sendo o da empresa, extraído do portfólio.

## Pendências

- [ ] Confirmar se pode publicar a foto dos sócios no site.
- [ ] Trocar as fotos por versões em alta (as atuais vieram de PNGs achatados do
      portfólio e já passaram por recompressão).
- [ ] Domínio próprio.
- [ ] Se quiser rastrear conversão, adicionar evento de clique nos links do WhatsApp.
