# Planilhas Bravo (Excel / Google Sheets)

Como aplicar a identidade visual da Bravo em planilhas, dashboards e relatórios tabulares. Cobre formatação de células, cores, gráficos, e código pronto para openpyxl e Google Apps Script.

---

## 1. Princípios gerais

- **Densidade > decoração**. Planilhas existem para mostrar dados, não para "ficar bonita". A marca aparece em pequenos toques.
- **Fonte**: Montserrat se disponível. Caso o ambiente (Google Sheets, Excel sem Montserrat) não tenha, use **"Arial"** como fallback — é a mais próxima visualmente que existe nativamente.
- **Cabeçalhos** sempre em Purple. **Totais e destaques** em Jacarta.
- **Hierarquia visual**: cabeçalho > linhas alternadas (zebra) > totais.

---

## 2. Esquema de cores para tabelas

### Cabeçalho de tabela

| Propriedade | Valor |
|---|---|
| Fundo | Purple `#302d71` |
| Texto | Branco `#ffffff` |
| Peso | **Bold** |
| Alinhamento | Centralizado |

### Linhas de dado

- **Zebra**: alternar entre branco `#ffffff` e lilás bem claro `#eceafa`.
- **Texto**: Purple `#302d71` para destaque, ou cinza escuro `#333333` para texto neutro.
- **Bordas**: brancas, finas — criam efeito de "blocos" separados (estilo do template Bravo).

### Linha de Total

| Propriedade | Valor |
|---|---|
| Fundo | Jacarta `#8062DE` |
| Texto | Branco `#ffffff` |
| Peso | **Bold** |

### Células com KPIs / valores em destaque

| Tipo | Cor de fundo |
|---|---|
| Positivo (verde) | `#b6d7a8` (texto Purple) |
| Neutro (amarelo) | `#fff2cc` (texto Purple) |
| Negativo (rosa) | `#f4cccc` (texto Purple ou vermelho escuro) |

---

## 3. Formatação numérica padrão

| Tipo | Formato | Exemplo |
|---|---|---|
| Moeda (R$) | `R$ #,##0.00` ou `R$ #,##0` | R$ 1.250.000 |
| Moeda em milhares | `#,##0` com header "(R$ '000s)" | 1.250 |
| Moeda em milhões | `#,##0.0` com header "(R$ MM)" | 1,3 |
| Percentual | `0.0%` | 12,3% |
| Variação % positivo | `+0.0%` (verde) | +12,3% |
| Variação % negativo | `0.0%` (vermelho) | -12,3% |
| Quantidade | `#,##0` | 3.471 |

---

## 4. Gráficos em planilha

Use a hierarquia da seção `references/identidade-visual.md`:

- **90% das séries**: paleta primária Bravo (`#3f275b`, `#aa97ef`, cinzas, `#8062de`, `#c8bff3`).
- **10% das séries**: highlights Amethyst `#aa6cc9` ou Viking `#5ecada`.
- **Eixos e linhas auxiliares**: cinza claro `#cccccc` ou `#999999`, NÃO em Purple (evita poluição visual).
- **Título do gráfico**: Montserrat Bold, Purple `#302d71`.
- **Legenda**: Montserrat Regular 10–11pt.

### Tipos de gráfico recomendados por uso

| Uso | Gráfico ideal |
|---|---|
| Comparar grupos em períodos | Barras agrupadas (vertical ou horizontal) |
| Evolução temporal | Linha simples ou área empilhada (claros sobre escuros) |
| Composição de total | Barras 100% empilhadas (preferível a pizza) |
| Distribuição / outliers | Box plot |
| Correlação | Scatter |
| Performance vs. meta | Bullet chart ou barras com linha de meta |

### Evitar

- Gráficos 3D (qualquer um).
- Pizza com mais de 4 fatias.
- Gradientes em barras ou linhas.
- Gráficos com mais de 6 séries sem agrupamento.
- Eixos sem início no zero (a menos que justifique e indique).

---

## 5. Cabeçalhos e estrutura de aba

Para planilhas operacionais (dashboards, relatórios), estrutura recomendada:

```
+-------------------------------------------------------------+
| [Logo Bravo (pequeno)] | TÍTULO DA PLANILHA       (un. unid.)|
| Última atualização: dd/mm/aaaa por @autor                    |
+-------------------------------------------------------------+
| Filtros: [País] [Período] [Equipe]                          |
+-------------------------------------------------------------+
|                                                              |
| TABELA / DASHBOARD                                          |
|                                                              |
+-------------------------------------------------------------+
| Fonte: [origem dos dados]   |   Notas: [obs. metodológicas]  |
+-------------------------------------------------------------+
```

### Linha de cabeçalho da aba

- Logo Bravo (pequeno, 60-80px de altura, canto superior esquerdo).
- Título em Montserrat Bold 16–18pt, cor Purple.
- Unidade de medida entre parênteses no canto direito, Montserrat Regular 11pt.

---

## 6. Código openpyxl (Python) — paleta + estilos

```python
from openpyxl import Workbook
from openpyxl.styles import PatternFill, Font, Alignment, Border, Side

# === Paleta Bravo ===
PURPLE_HEX   = "302D71"
JACARTA_HEX  = "8062DE"
AMETHYST_HEX = "AA6CC9"
VIKING_HEX   = "5ECADA"
LIGHT_BG     = "ECEAFA"  # lilás claro para zebra
MID_PURPLE   = "453D84"
WHITE        = "FFFFFF"
GREEN_POS    = "B6D7A8"
YELLOW_NEU   = "FFF2CC"
RED_NEG      = "F4CCCC"

# === Estilos prontos ===
def header_style():
    return {
        "fill": PatternFill("solid", fgColor=PURPLE_HEX),
        "font": Font(name="Montserrat", bold=True, color=WHITE, size=12),
        "alignment": Alignment(horizontal="center", vertical="center"),
    }

def total_row_style():
    return {
        "fill": PatternFill("solid", fgColor=JACARTA_HEX),
        "font": Font(name="Montserrat", bold=True, color=WHITE, size=11),
    }

def zebra_light_style():
    return {
        "fill": PatternFill("solid", fgColor=LIGHT_BG),
        "font": Font(name="Montserrat", color=PURPLE_HEX, size=10),
    }

def zebra_white_style():
    return {
        "fill": PatternFill("solid", fgColor=WHITE),
        "font": Font(name="Montserrat", color=PURPLE_HEX, size=10),
    }

def apply_style(cell, style_dict):
    for prop, value in style_dict.items():
        setattr(cell, prop, value)

# === Exemplo de uso ===
wb = Workbook()
ws = wb.active
ws.title = "Dashboard"

# Cabeçalho
headers = ["Métrica", "México", "Colômbia", "Brasil", "Total"]
for col_idx, header in enumerate(headers, start=1):
    cell = ws.cell(row=1, column=col_idx, value=header)
    apply_style(cell, header_style())

# Dados (zebra)
data = [
    ["Receita", 4297, 646, 320, 5263],
    ["EBITDA", 1659, -649, -68, 942],
]
for row_idx, row in enumerate(data, start=2):
    for col_idx, value in enumerate(row, start=1):
        cell = ws.cell(row=row_idx, column=col_idx, value=value)
        style = zebra_light_style() if row_idx % 2 == 0 else zebra_white_style()
        apply_style(cell, style)

# Linha de Total
total_row = ["Total Geral", 5956, -3, 252, 6205]
total_idx = len(data) + 2
for col_idx, value in enumerate(total_row, start=1):
    cell = ws.cell(row=total_idx, column=col_idx, value=value)
    apply_style(cell, total_row_style())

wb.save("dashboard_bravo.xlsx")
```

---

## 7. Google Apps Script — paleta + helpers

Para automação dentro de Google Sheets (como os scripts que o time já usa em refunds, dispatches etc.):

```javascript
// Paleta Bravo — use como constantes globais
const BRAVO_COLORS = {
  PURPLE:    '#302d71',
  JACARTA:   '#8062de',
  AMETHYST:  '#aa6cc9',
  VIKING:    '#5ecada',
  MID_PUR:   '#453d84',
  LIGHT_PUR: '#aa97ef',
  BG_LIGHT:  '#eceafa',
  WHITE:     '#ffffff',
  // Semânticas
  GREEN_POS: '#b6d7a8',
  YELLOW:    '#fff2cc',
  RED_NEG:   '#f4cccc',
};

// === Helpers de estilo ===

function applyHeaderStyle(range) {
  range.setBackground(BRAVO_COLORS.PURPLE)
       .setFontColor(BRAVO_COLORS.WHITE)
       .setFontFamily('Montserrat')
       .setFontWeight('bold')
       .setHorizontalAlignment('center')
       .setVerticalAlignment('middle');
}

function applyTotalRowStyle(range) {
  range.setBackground(BRAVO_COLORS.JACARTA)
       .setFontColor(BRAVO_COLORS.WHITE)
       .setFontFamily('Montserrat')
       .setFontWeight('bold');
}

function applyZebraStyle(range) {
  const numRows = range.getNumRows();
  for (let i = 0; i < numRows; i++) {
    const row = range.offset(i, 0, 1, range.getNumColumns());
    const bg = i % 2 === 0 ? BRAVO_COLORS.BG_LIGHT : BRAVO_COLORS.WHITE;
    row.setBackground(bg)
       .setFontColor(BRAVO_COLORS.PURPLE)
       .setFontFamily('Montserrat');
  }
}

// === Formatação condicional para variações ===

function applyKpiConditionalFormatting(range) {
  const rules = SpreadsheetApp.newConditionalFormatRule()
    .whenNumberGreaterThan(0)
    .setBackground(BRAVO_COLORS.GREEN_POS)
    .setRanges([range])
    .build();
  // ... idem para negativo (RED_NEG) e neutro (YELLOW)
  const sheet = range.getSheet();
  const existingRules = sheet.getConditionalFormatRules();
  existingRules.push(rules);
  sheet.setConditionalFormatRules(existingRules);
}
```

---

## 8. Checklist final antes de compartilhar uma planilha

- [ ] Cabeçalho da aba tem logo + título em Montserrat Bold Purple?
- [ ] Tabelas têm cabeçalho Purple com texto branco?
- [ ] Linhas de Total estão em Jacarta com texto branco bold?
- [ ] Zebra está consistente (branco / `#eceafa`)?
- [ ] Gráficos usam paleta principal (90%) + highlights (10%) onde necessário?
- [ ] Sem gráficos 3D, sem pizza com >4 fatias, sem gradientes em barras?
- [ ] Formatação numérica está coerente (sem mistura de milhares e milhões na mesma coluna)?
- [ ] Unidade de medida está explícita na linha do cabeçalho ou no título?
- [ ] Fonte original dos dados está indicada no rodapé?
