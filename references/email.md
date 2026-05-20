# E-mail Bravo (HTML, copy, estrutura)

Como redigir e produzir e-mails on-brand. Cobre estrutura, copy, código HTML e regras visuais.

---

## 1. Tipos de e-mail

| Tipo | Quando | Tom dominante |
|---|---|---|
| **Onboarding** | Após cadastro | Transparência + Vontade |
| **Atualização operacional** | Mudança de status, proposta enviada | Transparência |
| **Cobrança suave** | Lembrete de pagamento acordado | Empatia + Transparência |
| **Reativação** | Lead frio, cliente inativo | Empatia |
| **Conteúdo educativo** | Newsletter, dicas financeiras | Empatia + Transparência |
| **Promocional** | Campanhas sazonais | Vontade + Coragem |

---

## 2. Estrutura visual padrão (HTML)

Layout responsivo, 600px de largura máxima.

```
┌─────────────────────────────────────────┐
│ HEADER (foto com máscara V + logo)      │
│ Altura: 200-300px                       │
├─────────────────────────────────────────┤
│                                         │
│ TÍTULO PRINCIPAL                        │
│ (Montserrat Bold, Purple, 24-28pt)      │
│                                         │
│ Texto introdutório, 2-4 linhas curtas.  │
│                                         │
│ Texto adicional, se necessário.         │
│                                         │
│  [BOTÃO CTA TURQUESA]                  │
│  (Viking #5ecada, raio 8px)             │
│                                         │
├─────────────────────────────────────────┤
│ FOOTER                                  │
│ Isotipo V • País • Site • Redes sociais │
│ + texto legal pequeno                   │
└─────────────────────────────────────────┘
```

### Header — foto com máscara

- **Mood**: bem-estar pós-dívida (ver `references/identidade-visual.md`).
- **Máscara**: quadrada ou circular com base no isotipo V.
- **Filtros**: Cooling filter (80) a 10% + Violet a 15%.
- **Logo Bravo** (versão branca) sobreposto no canto superior esquerdo.

### Botão CTA

| Propriedade | Valor |
|---|---|
| Cor de fundo | Viking `#5ecada` |
| Cor do texto | Purple `#302d71` |
| Fonte | Montserrat Bold |
| Tamanho | 14–16pt |
| Padding | 12px 32px |
| Border-radius | 8px |
| Texto | Verbo no imperativo, máx 25 caracteres |

✅ Bons CTAs: "Ver minha proposta", "Iniciar consulta", "Saiba mais"
❌ CTAs ruins: "Clique aqui", "Confira", "Saiba mais agora mesmo já!"

### Footer

Sempre incluir:
- Isotipo Bravo (versão branca sobre fundo escuro ou color sobre fundo claro)
- País de operação
- URL oficial (ex: bravocredito.com.br)
- Ícones de redes sociais (Instagram, Facebook, LinkedIn)
- Texto legal pequeno (CNPJ, endereço, link de descadastro)
- Link de cancelar inscrição em conformidade com LGPD

---

## 3. Cores e tipografia no e-mail

### Cores

| Elemento | Cor |
|---|---|
| Fundo principal do e-mail | Branco `#ffffff` |
| Fundo do header (se sem foto) | Purple `#302d71` ou Gradient 1 |
| Fundo do footer | Purple `#302d71` |
| Título | Purple `#302d71` |
| Corpo de texto | `#453d84` ou `#333333` |
| Link inline | Jacarta `#8062DE` (sublinhado) |
| Botão CTA primário | Viking `#5ecada` |
| Botão CTA secundário | Jacarta `#8062DE` |

### Tipografia em e-mail

⚠️ **Atenção**: web fonts (Montserrat) podem não renderizar em todos os clientes de e-mail (Outlook!). Use fallback.

```css
font-family: 'Montserrat', Arial, Helvetica, sans-serif;
```

| Elemento | Tamanho | Peso |
|---|---|---|
| Título | 24–28pt | Bold |
| Subtítulo | 18–20pt | SemiBold |
| Corpo | 14–16pt | Regular |
| Botão | 14–16pt | Bold |
| Footer | 11–12pt | Regular |
| Texto legal | 9–10pt | Regular |

---

## 4. Regras de copy pra e-mail

### Linha de assunto (Subject line)

- **Tamanho**: máx 50 caracteres (mobile corta o resto).
- **Direto**: diga o que tem dentro.
- **Sem CAPS** (parece spam).
- **Sem mais de 1 emoji** (e só se fizer sentido).

✅ Bons assuntos:
- "{{Nome}}, sua proposta está pronta"
- "Quanto você economiza liquidando hoje"
- "Sua negociação foi atualizada"
- "Bravo aqui — uma novidade pra você"

❌ Assuntos ruins:
- "URGENTE!!! Sua dívida vai aumentar 🚨💸" (ameaçador, CAPS, emoji demais)
- "Confira nossa nova solução de débito" (genérico)
- "Re: Re: Fwd: Sua proposta" (falso encadeamento)

### Preheader (texto de preview)

- 80–120 caracteres.
- Complementa o assunto, não repete.
- Aparece como continuação do subject na inbox.

Exemplo:
- **Subject**: "Sua proposta com a Bravo está pronta"
- **Preheader**: "Veja quanto você pode economizar negociando sua dívida com desconto."

### Body

- Comece com saudação simples + nome: `Olá, {{Nome}}!` ou `Oi, {{Nome}}!`
- **1 ideia principal** por e-mail. Se tiver mais coisa, faz outro e-mail depois.
- **Parágrafos curtos** (máx 3 linhas).
- **Linguagem do cliente**: nada de jargão técnico ("renegociação extrajudicial" → "negociar com seu banco").
- **CTA único e claro**, no meio ou no fim do corpo.
- **Assinatura** opcional. Quando usar:
  - Nome da pessoa (ex: "Renata, da Bravo")
  - OU "Equipe Bravo"
  - NUNCA "Atenciosamente, Marketing Bravo" — frio demais.

### Encerramento

Pode usar o tagline `Bravo, acredite em você.` em e-mails de campanha ou momentos importantes (não em todo e-mail operacional).

---

## 5. Snippet HTML — template básico

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Bravo</title>
  <style>
    body { margin: 0; padding: 0; background: #f5f5fd; font-family: 'Montserrat', Arial, sans-serif; }
    .container { max-width: 600px; margin: 0 auto; background: #ffffff; }
    .header { background: #302d71; padding: 32px; color: #ffffff; }
    .content { padding: 32px; color: #453d84; }
    h1 { color: #302d71; font-size: 26px; font-weight: bold; margin: 0 0 16px; }
    p { font-size: 15px; line-height: 1.5; margin: 0 0 16px; }
    .cta {
      display: inline-block;
      padding: 12px 32px;
      background: #5ecada;
      color: #302d71;
      text-decoration: none;
      font-weight: bold;
      border-radius: 8px;
      font-size: 15px;
    }
    .footer {
      background: #302d71;
      color: #aa97ef;
      padding: 24px;
      font-size: 11px;
      text-align: center;
    }
    .footer a { color: #5ecada; text-decoration: none; }
  </style>
</head>
<body>
  <div class="container">
    <div class="header">
      <img src="https://cdn.bravo.com.br/logo-branco.png" alt="Bravo" height="32">
    </div>

    <div class="content">
      <h1>Olá, {{Nome}}!</h1>
      <p>Texto principal do e-mail. Conciso, direto, em "você".</p>
      <p>Um segundo parágrafo, se necessário, com a ação esperada.</p>
      <p style="margin: 32px 0;">
        <a href="https://bravocredito.com.br/proposta/{{ID}}" class="cta">Ver minha proposta</a>
      </p>
      <p style="font-size: 13px; color: #6359d2;">
        Bravo, acredite em você.
      </p>
    </div>

    <div class="footer">
      <p>Bravo • Brasil • <a href="https://bravocredito.com.br">bravocredito.com.br</a></p>
      <p>Você está recebendo esse e-mail porque se cadastrou na Bravo. <a href="{{UnsubscribeURL}}">Descadastrar</a></p>
    </div>
  </div>
</body>
</html>
```

---

## 6. Exemplos de copy completa

### E-mail 1: Confirmação de proposta

**Subject**: `{{Nome}}, sua proposta com a Bravo está pronta`
**Preheader**: `Veja quanto você pode economizar negociando suas dívidas.`

**Body:**
```
Olá, {{Nome}}!

A gente analisou seu caso e tem uma proposta pra você.

Conseguimos negociar um desconto de até {{Desconto}}% no valor da sua dívida com {{Credor}}.

Pra ver os detalhes do seu plano e confirmar, é só clicar abaixo.

[Ver minha proposta]

Qualquer dúvida, é só responder esse e-mail. Estamos aqui pra te ajudar.

Bravo, acredite em você.
```

---

### E-mail 2: Reativação de lead

**Subject**: `Voltar a falar com a Bravo?`
**Preheader**: `Sem pressão e sem compromisso — só uma conversa.`

**Body:**
```
Oi, {{Nome}}!

Faz um tempo que a gente não conversa. Sua situação com as dívidas mudou desde então?

Se ainda quiser negociar com desconto, a Bravo continua aqui. Sem compromisso e sem pressão — só uma análise gratuita do seu caso.

[Falar com a Bravo]
```

---

### E-mail 3: Lembrete de pagamento

**Subject**: `Parcela do seu plano vence em {{Dias}} dias`
**Preheader**: `Sua negociação tá em dia. É só conferir os detalhes.`

**Body:**
```
Olá, {{Nome}}!

Lembrete rápido: a próxima parcela do seu plano com a Bravo vence em {{DataVencimento}}.

Valor: R$ {{Valor}}

O boleto já foi enviado pro seu e-mail. Se precisar de uma segunda via, é só clicar abaixo.

[Ver segunda via]

Obrigado por confiar na Bravo.
```

---

## 7. Erros comuns a evitar

- ❌ Subject linha em CAPS LOCK ou com 3+ emojis.
- ❌ Imagens sem texto alternativo (`alt` é obrigatório por LGPD/acessibilidade).
- ❌ Fonte que não tem fallback (Outlook não tem Montserrat).
- ❌ Botão CTA com texto muito longo ("Clique aqui agora mesmo pra resolver suas dívidas").
- ❌ Mais de um CTA principal no mesmo e-mail.
- ❌ Header sem logo Bravo.
- ❌ Footer sem link de descadastro (problema legal sério).
- ❌ Tom condescendente ou de cobrança agressiva — sempre empatia.
- ❌ Promessa exagerada no body ("Quitação 100% garantida").
- ❌ Pedir CPF, RG, senha ou dados sensíveis dentro do e-mail.

---

## 8. Checklist final antes de disparar

- [ ] Subject line ≤ 50 chars, sem CAPS, sem excesso de emoji?
- [ ] Preheader complementa o subject (não repete)?
- [ ] Header tem logo Bravo (branco sobre fundo escuro)?
- [ ] Título principal está em Purple `#302d71` Montserrat Bold?
- [ ] Corpo está em "você", tom de pelo menos 1 dos 4 valores?
- [ ] CTA único, claro, em verbo no imperativo?
- [ ] Botão CTA está em Viking `#5ecada` com radius 8px?
- [ ] Footer tem isotipo + país + site + redes sociais?
- [ ] Tem link de descadastro (LGPD)?
- [ ] Imagens têm `alt` text?
- [ ] Testou em modo escuro (alguns clientes invertem cores)?
- [ ] Testou no mobile (>50% dos e-mails são abertos no celular)?
