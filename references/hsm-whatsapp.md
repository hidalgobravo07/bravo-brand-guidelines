# HSMs WhatsApp Bravo (PT-BR)

Como redigir templates HSM (Highly Structured Messages) para o WhatsApp Business da Bravo seguindo as regras da Meta e a voz da marca em português brasileiro.

---

## 1. O que é um HSM e por que importa

HSM é um template de mensagem pré-aprovado pela Meta que a Bravo usa pra enviar comunicações em massa via WhatsApp Business. Cada template precisa ser:

1. **Aprovado pela Meta** (passa por revisão).
2. **Classificado corretamente** (Utility, Marketing, Authentication ou Service).
3. **Conforme as políticas de mensagem do WhatsApp Business**.

Rejeição = template volta pro início. Classificação errada = preço errado e risco de banimento.

---

## 2. Classificação: Utility vs. Marketing

### Utility — para uso operacional

Atende a uma **expectativa do usuário** ligada a uma transação ou ação que ele iniciou.

**Exemplos típicos:**
- Confirmação de cadastro em curso
- Lembrete de boleto/pagamento previamente acordado
- Atualização do status de uma negociação que o cliente já iniciou
- Notificação de proposta concluída
- Confirmação de agendamento

**Custa menos** que Marketing e é mais provável de ser aprovado.

### Marketing — para promoção e reativação

Qualquer mensagem **promocional, de upsell, cross-sell, reativação de lead frio, oferta** ou que peça uma nova ação não acordada antes.

**Exemplos típicos:**
- Reativação de lead que parou de responder
- Promoção sazonal ("Liquidação de Carnaval")
- Convite pra agendar consulta sem agendamento prévio
- Conteúdo educativo "geral"

⚠️ **Erro comum**: tentar classificar mensagens promocionais como Utility usando linguagem de "lembrete". A Meta detecta isso e rejeita (e pode penalizar a conta).

### Regra prática

> Se o cliente **não** está esperando essa mensagem por causa de uma ação que ele iniciou, é **Marketing**.

---

## 3. Estrutura e limites técnicos

### Componentes de um HSM

| Componente | Obrigatório | Limite |
|---|---|---|
| **Header** (Texto, Imagem, Vídeo, Documento) | Não | Texto: 60 caracteres |
| **Body** (corpo da mensagem) | Sim | 1024 caracteres |
| **Footer** | Não | 60 caracteres |
| **Buttons** (até 3 Quick Reply OU até 2 Call to Action) | Não | Quick Reply: 25 chars / CTA URL: 25 chars |

### Variáveis dinâmicas

- Marcadas como `{{1}}`, `{{2}}`, etc.
- Cada variável **precisa** ter um exemplo na submissão pra Meta entender o uso.
- **Não use** variáveis no início ou no fim do body sem texto fixo ao redor — a Meta rejeita.

✅ **Bom**: `"Olá {{1}}, sua negociação foi atualizada..."`
❌ **Ruim**: `"{{1}}, novidade pra você."`

### Mídia no Header

- **Imagem**: JPG ou PNG, máx 5MB. Use o logo Bravo color ou uma arte da campanha (sempre on-brand).
- **Documento**: PDF, máx 100MB. Use para enviar contratos, propostas formais.
- **Vídeo**: MP4, máx 16MB.

---

## 4. Regras de redação Meta — o que NÃO pode

A Meta rejeita templates que contenham:

- ❌ **Promessas exageradas**: "Solução garantida", "100% de aprovação", "Resultado em 24h".
- ❌ **Linguagem ameaçadora**: "Última chance", "Sua conta será encerrada", "Restam 2 horas".
- ❌ **Conteúdo de jogos/apostas, criptomoedas, produtos farmacêuticos, álcool, tabaco, armas, conteúdo adulto**.
- ❌ **Pedido de dados sensíveis na mensagem**: senha, CPF completo, número do cartão.
- ❌ **CAPS LOCK em mais de uma palavra**.
- ❌ **Muitos emojis** (3+ vira flag).
- ❌ **Telefones embarcados no texto** (use o componente CTA).
- ❌ **Links encurtados** (bit.ly, tinyurl) — use URLs completas e claras.
- ❌ **Tom desrespeitoso, ofensivo, condescendente**.

---

## 5. Voz da Bravo aplicada a HSMs

Reaproveitar a tabela de Voz e Tom (ver `references/voz-e-tom.md`):

| Tipo de mensagem | Valor dominante | Tom |
|---|---|---|
| Confirmação operacional (Utility) | Transparência | Humana, clara, direta |
| Lembrete de pagamento | Empatia + Transparência | Compreensiva, sem ameaça |
| Atualização de proposta | Transparência | Honesta, sem floreio |
| Reativação de lead frio | Empatia | Próxima, sem cobrança |
| Convite pra agendar | Vontade | Encorajadora, propositiva |

### Regras de copy específicas pro WhatsApp

1. **Sempre "você"**, nunca "senhor(a)" ou "tu".
2. **Nome da marca**: sempre **Bravo** (não "bravo", não "Go Bravo", não "Bravo Brasil").
3. **Saudação**: simples ("Olá, {{1}}!" ou "Oi, {{1}}!").
4. **Frases curtas**: WhatsApp é mobile-first. Quebre em linhas curtas. Use `\n\n` pra separar parágrafos.
5. **CTA claro**: cada HSM idealmente termina com 1 ação esperada — clicar no botão, responder com uma palavra-chave, etc.
6. **Sem números de telefone embarcados** no body — use o botão CTA com `tel:` ou o link do agendamento.
7. **Sem dramatizar**: a pessoa já está com dívidas; ela não precisa de mais pressão.

---

## 6. Exemplos de templates aprovados (PT-BR)

### Exemplo 1: Confirmação de cadastro (Utility)

**Categoria**: Utility
**Idioma**: Português (BR)

**Body:**
```
Olá, {{1}}!

Recebemos o seu cadastro na Bravo. Em breve, um especialista vai entrar em contato pra te apresentar opções pra liquidar suas dívidas com desconto.

Enquanto isso, se quiser saber mais sobre como funciona, é só responder essa mensagem.
```

**Footer:**
```
Bravo
```

---

### Exemplo 2: Atualização de proposta (Utility)

**Categoria**: Utility
**Idioma**: Português (BR)

**Body:**
```
{{1}}, sua proposta com a Bravo foi atualizada.

Conseguimos um desconto de {{2}} no valor da sua dívida com {{3}}.

Pra ver os detalhes e confirmar o seu plano, é só clicar abaixo.
```

**Button (CTA URL):**
```
Ver minha proposta
```

---

### Exemplo 3: Reativação de lead frio (Marketing)

**Categoria**: Marketing
**Idioma**: Português (BR)

**Body:**
```
Oi, {{1}}!

Faz um tempo que a gente não conversa. Sua situação com as dívidas mudou desde então?

Se ainda quiser uma negociação com desconto, a Bravo continua aqui pra te ajudar. Sem compromisso, sem pressão.
```

**Buttons (Quick Reply):**
```
[Quero negociar]   [Agora não]
```

---

### Exemplo 4: Lembrete de pagamento acordado (Utility)

**Categoria**: Utility
**Idioma**: Português (BR)

**Body:**
```
Olá, {{1}}!

A parcela do seu plano com a Bravo vence em {{2}}.

Valor: R$ {{3}}

Você já recebeu o boleto por e-mail. Se precisar de uma segunda via, é só responder essa mensagem.
```

---

### Exemplo 5: Convite pra agendar consulta (Marketing)

**Categoria**: Marketing
**Idioma**: Português (BR)

**Body:**
```
{{1}}, e se a gente conversar 15 minutos sobre suas dívidas?

Um especialista da Bravo pode analisar seu caso e mostrar quanto você pode economizar liquidando com desconto.

Sem custo, sem compromisso.
```

**Button (CTA URL):**
```
Agendar agora
```

---

## 7. Sequência psicológica de reativação (15 dias)

Estrutura recomendada pra cadência de recuperação de lead frio, com gatilhos psicológicos:

| Dia | Gatilho | Tom |
|---|---|---|
| **D+1** | Empatia / reconhecimento | "A gente entende. Decisões financeiras são difíceis." |
| **D+3** | Prova social | "Já ajudamos milhares de pessoas no Brasil a sair das dívidas." |
| **D+6** | Educação | "Sabia que você pode pagar até 70% menos pela sua dívida?" |
| **D+9** | Urgência leve (sem ameaça) | "Os juros não esperam. Quanto antes negociar, melhor o desconto." |
| **D+12** | Reciprocidade | "Posso te enviar uma simulação personalizada agora — é grátis." |
| **D+15** | Encerramento respeitoso | "Esse é meu último contato. Sempre que quiser, é só voltar." |

⚠️ **Importante**: TODOS esses são **Marketing** (não Utility). Não tente classificar como Utility pra economizar.

---

## 8. Checklist final antes de submeter o HSM

- [ ] Categoria está correta (Utility se operacional; Marketing se promocional)?
- [ ] Nome da marca está como **Bravo** no body?
- [ ] Tratamento em "você", não "senhor(a)" nem "tu"?
- [ ] Variáveis têm texto fixo antes e depois (não estão isoladas)?
- [ ] Cada variável tem um exemplo definido?
- [ ] Não tem CAPS LOCK em mais de uma palavra?
- [ ] Não tem números de telefone embarcados (use botão CTA)?
- [ ] Não tem palavras-gatilho proibidas ("última chance", "garantido", "100%", etc.)?
- [ ] Tom encaixa em um dos 4 valores Bravo?
- [ ] CTA é claro e único?
- [ ] Idioma marcado como "Português (BR)" — não Portuguese (Portugal)?
- [ ] Footer (se usado) tem só "Bravo" ou info regulatória curta?
