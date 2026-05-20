# Apresentações Bravo (Google Slides + PowerPoint)

Como produzir slides on-brand no nível McKinsey/BCG. Cobre Google Slides via Apps Script (primário, já que a Bravo usa Google Workspace), python-pptx (para automação local), dimensões, layouts, tipografia, gráficos consulting-grade e padrões extraídos do Management Meeting oficial.

---

## 1. Configuração base do slide

- **Tamanho**: 10" x 5.625" (16:9 widescreen — mesmo do template oficial `assets/templates/template-bravo-2025-2026.pptx`).
- **Em pontos (Apps Script)**: 720 x 405pt.
- **Em EMUs (python-pptx)**: 9144000 x 5143500.

⚠️ Se criar um deck do zero, **prefira sempre** o template oficial como base. Ele já tem 12 layouts prontos (TITLE, SECTION_HEADER, TITLE_AND_BODY, CUSTOM, BLANK, etc.).

---

## 2. Os layouts disponíveis no template

| Layout | Quando usar |
|---|---|
| **TITLE** | Capa do deck. Bravo logo, título grande, subtítulo, mês/ano. Fundo Purple `#302d71` com elementos decorativos do V no canto direito. |
| **SECTION_HEADER_1 / 2** | Separadores entre seções (slide só com nome da seção, em branco sobre Purple). |
| **SECTION_HEADER_1_1** | Separador com país + objetivo/contexto (estilo "country header"). |
| **TITLE_AND_BODY** | Padrão: título no topo + corpo livre. Fundo branco. |
| **TITLE_AND_BODY_1 / 1_1** | Variações com área de chart + texto de apoio. |
| **CUSTOM / CUSTOM_2/3/4** | Layouts pré-desenhados (agenda, divisões em colunas, etc.). |
| **BLANK** | Slide vazio para layouts customizados. |

---

## 3. Os 8 padrões consulting-grade da Bravo

Estes padrões são **obrigatórios** em decks executivos. Foram extraídos do Management Meeting oficial e do Quincenal Adquisición.

### Padrão 1 — Action title (título é a conclusão)

O título do slide **é a resposta**, não o tópico.

✅ **DO**: `"Receita cresceu 31% YoY puxada por Espanha e Itália"`
❌ **DON'T**: `"Análise de receita do Q1"`

O leitor entende a conclusão **só de bater o olho no título**. O slide existe para *provar* essa afirmação.

### Padrão 2 — Subtítulo executivo (dek)

Logo abaixo do título, uma linha em **Montserrat Regular 14pt** sintetiza o achado:

> *"A mejora de nuestro EBITDA proyectado de (116k) para Q1 a el real de (27k), estuvo principalmente en los ingresos de negociación"*

O subtítulo destaca uma **palavra-chave em negrito Jacarta** (a métrica ou o driver), o resto vai em Purple Mid.

### Padrão 3 — Unit annotation (canto superior direito)

Toda visualização com números tem a unidade no **canto superior direito**, em Montserrat Regular 11pt, cor Purple Mid:

- `(EUR 'MMs)` — milhões de euros
- `(EUR '000s)` — milhares de euros
- `(BRL '000s)` — milhares de reais
- `(MXN '000s)` — milhares de pesos mexicanos
- `(COP '000s)` — milhares de pesos colombianos
- `(%)` — percentuais
- `(Local Currency '000s)` — quando mistura moedas

**Sem exceção.** Slide com número sem unit annotation é slide incompleto.

### Padrão 4 — Diff pills (variações entre períodos)

Variações percentuais entre barras de gráfico vão em **pílulas elípticas** sobre as barras:

- **Positiva**: fundo `#d4edda` (verde claro), borda `#28a745`, texto `#155724`, fonte Bold 10pt, formato `+10%`
- **Negativa**: fundo `#f8d7da` (rosa), borda `#dc3545`, texto `#721c24`, fonte Bold 10pt, formato `(4%)` (com parênteses!)
- **Neutro/atenção**: fundo `#fff3cd`, borda `#ffc107`, texto `#856404`

Formato: `+10%` / `+26%` / `(4%)` / `(96%)`. **Negativos sempre com parênteses**, padrão de relatório financeiro.

A pílula fica **entre duas barras**, com uma seta cinza fininha conectando-as.

### Padrão 5 — Elemento decorativo do V (canto superior esquerdo)

Todo slide (exceto capa e seção) tem o **outline do V** em Viking turquesa (`#5ecada`) + Amethyst (`#aa6cc9`) no canto superior esquerdo. Tamanho: ~30pt de altura. Esse é o "carimbo Bravo" do deck.

### Padrão 6 — Footer logo (canto inferior direito)

Todo slide de conteúdo tem o logo "**bravo**" pequenino (Jacarta `#8062de`, ~18pt de altura) no **canto inferior direito**, com 30px de margem.

### Padrão 7 — Bandeiras circulares como ícone de coluna

Em tabelas/charts comparativos por país, a bandeira é **circular**, ~24pt, posicionada como cabeçalho de coluna. Ordem padrão das bandeiras: 🇲🇽 México → 🇨🇴 Colômbia → 🇪🇸 Espanha → 🇵🇹 Portugal → 🇮🇹 Itália → 🇧🇷 Brasil → Global (Bravo full logo mini).

### Padrão 8 — Source/footnote padronizado

Tudo que vier de dado externo ou cálculo derivado tem:

```
Fonte: Vanex CRM + BigQuery (atualizado 12-05-2026).  Notas: ¹Inclui graduados + créditos parciais.
```

Em **Montserrat Regular 8pt**, cor `#888888`, alinhado à esquerda do slide, 30px do bottom.

---

## 4. Princípios visuais

### Fundos

- **Capa e separadores de seção**: Purple `#302d71` ou Gradient 1 (`#201d49` → `#3d359e`).
- **Conteúdo (corpo)**: branco `#ffffff` na grande maioria dos casos.
- **Slides "destaque"** ou citações: pode usar Gradient 2 ou Gradient 3.
- O elemento decorativo do V (Padrão 5) aparece sutilmente no canto superior esquerdo de quase todo slide.

### Texto sobre fundo

| Fundo | Cor do título | Cor do corpo |
|---|---|---|
| Branco | Purple `#302d71` | `#453d84` ou `#302d71` |
| Purple `#302d71` | Branco `#ffffff` | `#aa97ef` ou `#c8bff3` |
| Gradient 1 (escuro) | Branco `#ffffff` | `#c8bff3` |
| Gradient 2 (lilás) | Branco `#ffffff` | Branco `#ffffff` |
| Gradient 3 (claro) | Purple `#302d71` | `#453d84` |

### Logo e isotipo no slide

- **Capa**: logo completo (`bravo-logo-branco.png`) no canto superior esquerdo, ~80pt de altura, 40px de margem.
- **Rodapé de conteúdo**: ver Padrão 6.
- **Decoração**: ver Padrão 5.
- O isotipo V em outline também pode aparecer **gigante e sutil** (10% opacidade) como background graphic no canto direito de slides de seção.

---

## 5. Tipografia em slides

| Elemento | Fonte | Peso | Tamanho |
|---|---|---|---|
| Título da capa | Montserrat | Bold | 36–44pt |
| Subtítulo da capa | Montserrat | Regular | 18–22pt |
| **Action title** de slide | Montserrat | Bold | 28–32pt |
| **Subtítulo executivo (dek)** | Montserrat | Regular | 14–16pt |
| Cabeçalho de seção dentro do slide | Montserrat | SemiBold | 18–22pt |
| Corpo de parágrafo | Montserrat | Regular | 14–16pt |
| Bullets | Montserrat | Regular | 12–14pt |
| **Unit annotation** | Montserrat | Regular | 10–11pt |
| Legendas de gráfico | Montserrat | Regular | 9–11pt |
| **Diff pills** | Montserrat | Bold | 10pt |
| **Source/footnote** | Montserrat | Regular | 8–9pt |
| Números grandes (KPIs) | Montserrat | Bold | 36–60pt |

---

## 6. Gráficos — hierarquia de cores

A regra mais importante para consistência do deck.

### Para 90% dos gráficos — paleta principal

Ordem hierárquica das séries (1 = mais importante):

1. `#3f275b` (Purple bem escuro) — série principal/atual
2. `#aa97ef` (Lilás claro) — série secundária/budget
3. `#cccccc` (Cinza médio) — referência/benchmark
4. `#999999` (Cinza escuro) — séries de menor importância
5. `#8062de` (Jacarta) — quarta série, se necessária
6. `#c8bff3` (Lilás muito claro) — quinta série
7. `#ffffff` (Branco) — sobre fundo escuro

### Para 10% — highlights pontuais

Quando você quer destacar UMA série específica:
- `#aa6cc9` (Amethyst) — destaque "quente"
- `#5ecada` (Viking) — destaque "frio/contraponto"

### Semântica (positivo/neutro/negativo)

- **Verde claro** `#b6d7a8`: variação positiva, meta atingida
- **Amarelo claro** `#fff2cc`: neutro / atenção
- **Rosa claro** `#f4cccc`: variação negativa, alerta

---

## 7. Tabelas (formato "Bravo")

Padrão visto no Management Meeting:

- **Cabeçalho**: fundo Purple `#302d71`, texto branco bold centralizado, padding vertical 12pt.
- **Linhas de dado**: fundo lilás bem claro `#eceafa` ou alternando com branco (zebra).
- **Linhas "Total"**: fundo Jacarta `#8062de` com texto branco bold.
- **Bordas**: brancas, 1pt — efeito de "blocos" separados.
- **Países** (quando aplicável): bandeira circular como ícone de cabeçalho de coluna.
- **Unit annotation** no canto superior direito da tabela: `(EUR '000s)`, `(BRL '000s)`.
- **Diff %**: coluna dedicada com texto colorido (verde `+10%`, vermelho `(4%)`).

---

## 8. Templates de chart consulting-grade

### Bar chart com YoY comparison + diff pills

Padrão dos slides 4-7 do Management Meeting:

```
2024  2025  2026  Budget 2026
 194   214   269    254
       └─+10%──┘
              └─+26%─┘
                    └─+6%─┘
```

4 barras (3 históricas + 1 budget), com **pílulas de diff** entre cada par sequencial. Labels acima das barras. Categoria abaixo. Unit annotation no topo direito.

### Waterfall / EBITDA bridge

Padrão do slide 9 (Colombia EBITDA bridge):

- Barras verticais com **start** e **end** sólidas em Purple `#302d71`.
- **Aumentos** em verde `#b6d7a8` com sinal `+`.
- **Reduções** em rosa `#f4cccc` com parênteses.
- Linhas pontilhadas conectando os topos das barras.
- Labels com o valor da variação dentro de cada barra.

### Funnel comercial

Padrão do slide 15 (Amazonas Funnel):

```
Leads     ████████████████  8,076
   └─ 46% conv ─┘
F2        ███████████        3,767
   └─ 61% conv ─┘
Planes    ████              2,297
```

Trapezoides empilhados verticalmente, com **taxa de conversão entre etapas** em pílulas. Pode mostrar **dois funis lado a lado** (antes/depois) com a coluna do meio explicando o que mudou.

### Scenario comparison (2-up)

Padrão dos slides do Quincenal Adquisición (Real vs Pto):

- Duas colunas idênticas: "Real" e "FCST/PTO".
- Cada coluna mostra os mesmos KPIs em sequência.
- Coluna direita (Real) destaca em Jacarta `#8062de` quando bate ou supera, vermelho quando fica abaixo.

### 2x2 matrix

Para priorização (impacto × esforço), opportunity sizing, BCG-style:

- Quadrantes com fundo `#f5f3fb` (top-right e bottom-left) e branco (outros).
- Eixos em Purple Mid `#453d84`, labels em Purple `#302d71`.
- Bullets como bolhas Jacarta com label, posicionados conforme os eixos.

### KPI cards (4-up ou 6-up)

Padrão do slide 4 (KPIs Q1 2026):

- Card branco com sombra `--shadow-md`.
- **Número grande** em Bold Purple 36pt no topo.
- **Label** em Regular Purple Mid 11pt embaixo.
- **Diff vs período anterior** em pílula colorida.
- Mini-sparkline (4-6 pontos) opcional no rodapé do card.

---

## 9. Google Slides via Apps Script (PRIMARY)

A Bravo usa Google Workspace. Apps Script é o caminho mais direto para gerar/editar decks programaticamente.

### Setup

```javascript
// Constantes da marca
const BRAVO = {
  PURPLE: '#302d71', JACARTA: '#8062de', AMETHYST: '#aa6cc9', VIKING: '#5ecada',
  PURPLE_DARK: '#3d359e', PURPLE_MID: '#453d84',
  LIGHT_PUR: '#aa97ef', LIGHTER: '#c8bff3', BG_LIGHT: '#eceafa',
  WHITE: '#ffffff',
  GREEN_POS: '#d4edda', GREEN_BORDER: '#28a745', GREEN_TEXT: '#155724',
  RED_NEG: '#f8d7da', RED_BORDER: '#dc3545', RED_TEXT: '#721c24',
  FONT: 'Montserrat',
};

// Slide é 720x405pt (16:9 widescreen)
const SLIDE_W = 720;
const SLIDE_H = 405;
```

### Helpers fundamentais

```javascript
/** Cria um novo deck Bravo no Drive e retorna o objeto Presentation. */
function createBravoDeck(title) {
  const pres = SlidesApp.create(title);
  // Setar 16:9 widescreen
  pres.setPageSize(SlidesApp.PageSize.WIDESCREEN_16x9);
  return pres;
}

/** Aplica fundo Purple a um slide. */
function setPurpleBackground(slide) {
  slide.getBackground().setSolidFill(BRAVO.PURPLE);
}

/** Aplica fundo Gradient 1 (não nativo no Slides — usar retângulo full-bleed). */
function setGradient1Background(slide) {
  // Slides não suporta gradiente nativo via Apps Script.
  // Workaround: retângulo full-bleed com fill gradiente.
  // Como Apps Script tampouco suporta gradient fills programaticamente,
  // a prática é: deixe o template oficial com gradiente já pronto e use os layouts dele.
  // Fallback: solid Purple Dark #201d49.
  slide.getBackground().setSolidFill('#201d49');
}

/** Adiciona o action title padrão Bravo. */
function addActionTitle(slide, text, options) {
  options = options || {};
  const isDark = options.darkBg || false;
  const tb = slide.insertTextBox(text, 30, 25, SLIDE_W - 60, 45);
  const tr = tb.getText();
  tr.getTextStyle()
    .setFontFamily(BRAVO.FONT)
    .setBold(true)
    .setFontSize(28)
    .setForegroundColor(isDark ? BRAVO.WHITE : BRAVO.PURPLE);
  // Underline visual (linha sutil abaixo) — desenhar como Line element
  slide.insertLine(SlidesApp.LineCategory.STRAIGHT, 30, 78, 130, 78)
       .getLineFill().setSolidFill(BRAVO.PURPLE);
  return tb;
}

/** Adiciona o dek (subtítulo executivo) abaixo do título. */
function addDek(slide, text, highlightWord) {
  const tb = slide.insertTextBox(text, 30, 82, SLIDE_W - 60, 30);
  const tr = tb.getText();
  tr.getTextStyle()
    .setFontFamily(BRAVO.FONT)
    .setBold(false)
    .setFontSize(14)
    .setForegroundColor(BRAVO.PURPLE_MID);
  // Destacar palavra-chave em Bold Jacarta, se fornecida
  if (highlightWord) {
    const txt = tr.asString();
    const idx = txt.indexOf(highlightWord);
    if (idx >= 0) {
      const range = tr.getRange(idx, idx + highlightWord.length);
      range.getTextStyle().setBold(true).setForegroundColor(BRAVO.JACARTA);
    }
  }
  return tb;
}

/** Adiciona unit annotation no canto superior direito. */
function addUnit(slide, unitText) {
  const tb = slide.insertTextBox(unitText, SLIDE_W - 130, 28, 100, 18);
  tb.getText().getTextStyle()
    .setFontFamily(BRAVO.FONT)
    .setFontSize(11)
    .setForegroundColor(BRAVO.PURPLE_MID);
  tb.getText().getParagraphStyle()
    .setParagraphAlignment(SlidesApp.ParagraphAlignment.END);
  return tb;
}

/** Adiciona footer logo "bravo" no canto inferior direito. */
function addFooterLogo(slide) {
  const tb = slide.insertTextBox('bravo', SLIDE_W - 70, SLIDE_H - 28, 50, 22);
  tb.getText().getTextStyle()
    .setFontFamily(BRAVO.FONT)
    .setBold(true)
    .setFontSize(14)
    .setForegroundColor(BRAVO.JACARTA);
  tb.getText().getParagraphStyle()
    .setParagraphAlignment(SlidesApp.ParagraphAlignment.END);
  return tb;
}

/** Adiciona uma diff pill verde ou vermelha. Formato value: "+10%" ou "(4%)". */
function addDiffPill(slide, x, y, value, isPositive) {
  const w = 50, h = 22;
  const pill = slide.insertShape(SlidesApp.ShapeType.ROUND_RECTANGLE, x, y, w, h);
  pill.getFill().setSolidFill(isPositive ? BRAVO.GREEN_POS : BRAVO.RED_NEG);
  pill.getBorder().setWeight(1);
  pill.getBorder().getLineFill().setSolidFill(isPositive ? BRAVO.GREEN_BORDER : BRAVO.RED_BORDER);
  pill.getText().setText(value);
  pill.getText().getTextStyle()
    .setFontFamily(BRAVO.FONT)
    .setBold(true)
    .setFontSize(10)
    .setForegroundColor(isPositive ? BRAVO.GREEN_TEXT : BRAVO.RED_TEXT);
  pill.getText().getParagraphStyle()
    .setParagraphAlignment(SlidesApp.ParagraphAlignment.CENTER);
  return pill;
}

/** Adiciona source/footnote no rodapé. */
function addSource(slide, text) {
  const tb = slide.insertTextBox(text, 30, SLIDE_H - 22, SLIDE_W - 100, 16);
  tb.getText().getTextStyle()
    .setFontFamily(BRAVO.FONT)
    .setFontSize(8)
    .setForegroundColor('#888888');
  return tb;
}
```

### Exemplo: criar um slide consulting-grade do zero

```javascript
function createKPISlide() {
  const pres = createBravoDeck('Bravo Q2 Review');
  const slide = pres.appendSlide(SlidesApp.PredefinedLayout.BLANK);

  // 1) Action title
  addActionTitle(slide, 'Receita cresceu 31% YoY puxada por Espanha e Itália');

  // 2) Dek
  addDek(
    slide,
    'A mejora viene de fee revenue (+38%) que compensa la caída del loan business (-5%) en NIM',
    'fee revenue'
  );

  // 3) Unit annotation
  addUnit(slide, "(EUR 'MMs)");

  // 4) Adicione aqui os gráficos / cards / tabelas...

  // 5) Footer
  addFooterLogo(slide);
  addSource(slide, 'Fonte: Vanex CRM + BigQuery (atualizado 12-05-2026).');

  return pres.getUrl();
}
```

### Tabela consulting-grade via Apps Script

```javascript
/** Cria uma tabela Bravo (header Purple, zebra lilás, total Jacarta).
 *  data = [[header...], [row1...], [row2...], ..., ['Total', ...]]  */
function insertBravoTable(slide, x, y, w, h, data) {
  const numRows = data.length;
  const numCols = data[0].length;
  const table = slide.insertTable(numRows, numCols, x, y, w, h);

  for (let r = 0; r < numRows; r++) {
    for (let c = 0; c < numCols; c++) {
      const cell = table.getCell(r, c);
      const isHeader = r === 0;
      const isTotal = data[r][0] === 'Total' || data[r][0] === 'TOTAL';
      cell.getText().setText(String(data[r][c]));

      const ts = cell.getText().getTextStyle();
      ts.setFontFamily(BRAVO.FONT).setFontSize(11);

      if (isHeader) {
        cell.getFill().setSolidFill(BRAVO.PURPLE);
        ts.setBold(true).setForegroundColor(BRAVO.WHITE);
      } else if (isTotal) {
        cell.getFill().setSolidFill(BRAVO.JACARTA);
        ts.setBold(true).setForegroundColor(BRAVO.WHITE);
      } else {
        // Zebra: linhas pares (depois do header) em lilás claro
        cell.getFill().setSolidFill(r % 2 === 1 ? BRAVO.WHITE : BRAVO.BG_LIGHT);
        ts.setForegroundColor(BRAVO.PURPLE);
      }
    }
  }
  return table;
}
```

### Inserir o logo da Bravo do Drive

```javascript
function addBravoLogo(slide, variant) {
  // variant: 'color' | 'branco'
  // Suba os PNGs transparentes da skill para o Drive e use o fileId aqui.
  const LOGO_IDS = {
    'color': '1XXXXXXXXXXXXXXXXXXXX',  // bravo-logo-color.png (transparente)
    'branco': '1YYYYYYYYYYYYYYYYYYY',  // bravo-logo-branco.png (transparente)
  };
  const fileId = LOGO_IDS[variant];
  const blob = DriveApp.getFileById(fileId).getBlob();
  return slide.insertImage(blob, 30, 25, 100, 28);  // top-left, 100x28pt
}
```

---

## 10. python-pptx (automação local)

### Constantes prontas

```python
from pptx.dml.color import RGBColor
from pptx.util import Inches, Pt, Emu

# Dimensões oficiais Bravo
SLIDE_WIDTH = Inches(10)
SLIDE_HEIGHT = Inches(5.625)

# Paleta Primária
PURPLE   = RGBColor(0x30, 0x2d, 0x71)
JACARTA  = RGBColor(0x80, 0x62, 0xDE)
AMETHYST = RGBColor(0xAA, 0x6C, 0xC9)
VIKING   = RGBColor(0x5E, 0xCA, 0xDA)
WHITE    = RGBColor(0xFF, 0xFF, 0xFF)

# Complementar
PURPLE_DARKEST  = RGBColor(0x20, 0x1D, 0x49)
PURPLE_DARK     = RGBColor(0x3D, 0x35, 0x9E)
PURPLE_MID      = RGBColor(0x45, 0x3D, 0x84)
PURPLE_LIGHT    = RGBColor(0xAA, 0x97, 0xEF)
PURPLE_LIGHTER  = RGBColor(0xC8, 0xBF, 0xF3)
PURPLE_BG_LIGHT = RGBColor(0xEC, 0xEA, 0xFA)

# Charts — hierarquia
CHART_PRIMARY = [
    RGBColor(0x3F, 0x27, 0x5B), RGBColor(0xAA, 0x97, 0xEF),
    RGBColor(0xCC, 0xCC, 0xCC), RGBColor(0x99, 0x99, 0x99),
    RGBColor(0x80, 0x62, 0xDE), RGBColor(0xC8, 0xBF, 0xF3),
]
CHART_HIGHLIGHT = [RGBColor(0xAA, 0x6C, 0xC9), RGBColor(0x5E, 0xCA, 0xDA)]

# Diff pills
GREEN_FILL   = RGBColor(0xD4, 0xED, 0xDA)
GREEN_BORDER = RGBColor(0x28, 0xA7, 0x45)
GREEN_TEXT   = RGBColor(0x15, 0x57, 0x24)
RED_FILL     = RGBColor(0xF8, 0xD7, 0xDA)
RED_BORDER   = RGBColor(0xDC, 0x35, 0x45)
RED_TEXT     = RGBColor(0x72, 0x1C, 0x24)

FONT_FAMILY = "Montserrat"
```

### Helper: diff pill

```python
from pptx.shapes.autoshape import Shape
from pptx.enum.shapes import MSO_SHAPE
from pptx.util import Pt, Emu

def add_diff_pill(slide, left_emu, top_emu, value: str, is_positive: bool):
    """Adiciona uma diff pill consulting-grade. value: '+10%' ou '(4%)'."""
    width = Pt(50)
    height = Pt(22)
    shape = slide.shapes.add_shape(MSO_SHAPE.ROUNDED_RECTANGLE, left_emu, top_emu, width, height)
    fill = shape.fill
    fill.solid()
    fill.fore_color.rgb = GREEN_FILL if is_positive else RED_FILL
    line = shape.line
    line.color.rgb = GREEN_BORDER if is_positive else RED_BORDER
    line.width = Pt(1)
    tf = shape.text_frame
    tf.text = value
    p = tf.paragraphs[0]
    p.alignment = 2  # centered
    run = p.runs[0]
    run.font.name = FONT_FAMILY
    run.font.bold = True
    run.font.size = Pt(10)
    run.font.color.rgb = GREEN_TEXT if is_positive else RED_TEXT
    return shape
```

### Helper: action title + dek + unit annotation

```python
from pptx.util import Inches, Pt
from pptx.enum.text import PP_ALIGN

def add_action_title(slide, text: str, dark_bg: bool = False):
    tb = slide.shapes.add_textbox(Inches(0.3), Inches(0.25), Inches(9.4), Inches(0.6))
    p = tb.text_frame.paragraphs[0]
    run = p.add_run()
    run.text = text
    run.font.name = FONT_FAMILY
    run.font.bold = True
    run.font.size = Pt(28)
    run.font.color.rgb = WHITE if dark_bg else PURPLE
    return tb

def add_dek(slide, text: str, highlight: str = None):
    tb = slide.shapes.add_textbox(Inches(0.3), Inches(0.85), Inches(9.4), Inches(0.4))
    tf = tb.text_frame
    p = tf.paragraphs[0]
    if highlight and highlight in text:
        before, after = text.split(highlight, 1)
        for txt, bold, color in [(before, False, PURPLE_MID), (highlight, True, JACARTA), (after, False, PURPLE_MID)]:
            r = p.add_run()
            r.text = txt
            r.font.name = FONT_FAMILY
            r.font.size = Pt(14)
            r.font.bold = bold
            r.font.color.rgb = color
    else:
        r = p.add_run()
        r.text = text
        r.font.name = FONT_FAMILY
        r.font.size = Pt(14)
        r.font.color.rgb = PURPLE_MID
    return tb

def add_unit(slide, unit: str):
    tb = slide.shapes.add_textbox(Inches(8.4), Inches(0.3), Inches(1.3), Inches(0.3))
    p = tb.text_frame.paragraphs[0]
    p.alignment = PP_ALIGN.RIGHT
    r = p.add_run()
    r.text = unit
    r.font.name = FONT_FAMILY
    r.font.size = Pt(11)
    r.font.color.rgb = PURPLE_MID
    return tb
```

---

## 11. Erros comuns a evitar

- ❌ Título de slide que é tópico, não conclusão.
- ❌ Slide sem unit annotation quando tem números.
- ❌ Diff % escrito como texto comum ao invés de pílula colorida.
- ❌ Usar Arial, Calibri, ou qualquer fonte que não seja Montserrat.
- ❌ Texto Purple sobre fundo Amethyst (contraste baixo).
- ❌ Gradientes em texto **e** fundo no mesmo slide.
- ❌ Mais de 3 cores brilhantes da paleta primária no mesmo slide (vira ruído).
- ❌ Distorcer o logo ou usar versão recolorida.
- ❌ Slides com 8+ bullets — quebre em 2 slides.
- ❌ Emojis bandeira ao invés das bandeiras circulares oficiais.
- ❌ Logo "bravo" escrito como texto comum (use a imagem oficial).
- ❌ Esquecer source/footnote em slide de dados.
- ❌ Slide de conteúdo sem footer logo no canto direito.

---

## 12. Workflow recomendado

1. **Copie o template oficial** (`assets/templates/template-bravo-2025-2026.pptx`) ou abra um Google Slides novo e aplique tema Bravo.
2. **Estrutura SCQA**: capa → agenda → seções (cada uma com SECTION_HEADER) → conclusão executiva → backup/anexo.
3. **Cada slide**: comece pelo **action title**. Se você não consegue escrever o título-conclusão em 1 frase, refaça o slide.
4. **Em cada slide**, escolha o layout mais próximo do que precisa em vez de criar do zero.
5. **Mantenha a hierarquia**: 1 ideia principal por slide.
6. **Para gráficos**: comece pela hierarquia de cores principais (seção 6).
7. **Aplique os 8 padrões consulting-grade** (seção 3). Diff pills, unit annotation, source — tudo automático.
8. **Revise**: cores na paleta? Logo certo? Tipografia Montserrat? Tagline (se usado) correto? Footer? Source?

---

## 13. Checklist final (slide a slide)

- [ ] Action title (conclusão, não tópico)?
- [ ] Dek com palavra-chave em Bold Jacarta?
- [ ] Unit annotation no canto superior direito?
- [ ] Diff pills em todos os comparativos %?
- [ ] Bandeiras circulares (se há comparação por país)?
- [ ] Footer logo no canto inferior direito?
- [ ] Source/footnote padronizado?
- [ ] Cores na paleta?
- [ ] Tipografia Montserrat em tudo?
- [ ] 1 mensagem por slide?
