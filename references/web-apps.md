# Web Apps Bravo (React + Tailwind + shadcn/ui)

Como construir aplicações web, landing pages, dashboards e componentes UI on-brand no nível Linear/Vercel/Stripe. Stack canônica: **Next.js (ou Vite) + React + Tailwind CSS + shadcn/ui + Lucide icons**.

A barra de qualidade é alta. Um app Bravo deve transmitir confiança, calma e competência — não pode parecer "site genérico de fintech".

---

## 1. Setup inicial

### Dependências base

```bash
# Next.js + Tailwind
npx create-next-app@latest meu-app-bravo --typescript --tailwind --app
cd meu-app-bravo

# shadcn/ui
npx shadcn@latest init

# Lucide para ícones
npm install lucide-react

# Montserrat via next/font (recomendado)
# Configurar em app/layout.tsx (ver abaixo)
```

### Configurar Montserrat (next/font)

```tsx
// app/layout.tsx
import { Montserrat } from 'next/font/google';

const montserrat = Montserrat({
  subsets: ['latin'],
  weight: ['400', '500', '600', '700'],
  display: 'swap',
  variable: '--font-montserrat',
});

export default function RootLayout({ children }) {
  return (
    <html lang="pt-BR" className={montserrat.variable}>
      <body className="font-sans antialiased">{children}</body>
    </html>
  );
}
```

---

## 2. Tailwind config — design system completo

```js
// tailwind.config.ts
import type { Config } from 'tailwindcss';

const config: Config = {
  content: ['./app/**/*.{ts,tsx}', './components/**/*.{ts,tsx}'],
  theme: {
    extend: {
      colors: {
        // Paleta Bravo
        bravo: {
          purple:     '#302d71',
          jacarta:    '#8062de',
          amethyst:   '#aa6cc9',
          viking:     '#5ecada',
          'purple-darkest': '#201d49',
          'purple-dark':    '#3d359e',
          'purple-mid':     '#453d84',
          'purple-light':   '#aa97ef',
          'purple-lighter': '#c8bff3',
          'bg-light':       '#eceafa',
          'bg-lighter':     '#f5f3fb',
          pos: '#b6d7a8',
          neu: '#fff2cc',
          neg: '#f4cccc',
        },
        // shadcn/ui semantic tokens (mapeados para Bravo)
        background: 'hsl(var(--background))',
        foreground: 'hsl(var(--foreground))',
        primary: {
          DEFAULT: 'hsl(var(--primary))',
          foreground: 'hsl(var(--primary-foreground))',
        },
        secondary: {
          DEFAULT: 'hsl(var(--secondary))',
          foreground: 'hsl(var(--secondary-foreground))',
        },
        muted: {
          DEFAULT: 'hsl(var(--muted))',
          foreground: 'hsl(var(--muted-foreground))',
        },
        accent: {
          DEFAULT: 'hsl(var(--accent))',
          foreground: 'hsl(var(--accent-foreground))',
        },
        destructive: {
          DEFAULT: 'hsl(var(--destructive))',
          foreground: 'hsl(var(--destructive-foreground))',
        },
        border: 'hsl(var(--border))',
        input: 'hsl(var(--input))',
        ring: 'hsl(var(--ring))',
      },
      fontFamily: {
        sans: ['var(--font-montserrat)', 'Inter', 'system-ui', 'sans-serif'],
      },
      fontSize: {
        // Type scale (px / line-height)
        xs:   ['12px', { lineHeight: '16px' }],
        sm:   ['14px', { lineHeight: '20px' }],
        base: ['16px', { lineHeight: '24px' }],
        lg:   ['18px', { lineHeight: '28px' }],
        xl:   ['20px', { lineHeight: '28px' }],
        '2xl':['24px', { lineHeight: '32px' }],
        '3xl':['30px', { lineHeight: '36px' }],
        '4xl':['36px', { lineHeight: '40px' }],
        '5xl':['48px', { lineHeight: '1' }],
        '6xl':['60px', { lineHeight: '1' }],
      },
      borderRadius: {
        sm: '4px',
        md: '8px',
        lg: '12px',
        xl: '16px',
        '2xl': '24px',
      },
      boxShadow: {
        // Sombras tinted Purple (não preto)
        'bravo-sm': '0 1px 2px 0 rgba(48,45,113,.05)',
        'bravo-md': '0 4px 6px -1px rgba(48,45,113,.08), 0 2px 4px -2px rgba(48,45,113,.08)',
        'bravo-lg': '0 10px 15px -3px rgba(48,45,113,.10), 0 4px 6px -4px rgba(48,45,113,.08)',
        'bravo-xl': '0 20px 25px -5px rgba(48,45,113,.12), 0 8px 10px -6px rgba(48,45,113,.08)',
        'bravo-2xl': '0 25px 50px -12px rgba(48,45,113,.18)',
      },
      backgroundImage: {
        'gradient-1': 'linear-gradient(180deg, #201d49 0%, #3d359e 100%)',
        'gradient-2': 'linear-gradient(135deg, #a96cc9 0%, #6359d2 100%)',
        'gradient-3': 'linear-gradient(180deg, #8062de 0%, #ffffff 100%)',
      },
      keyframes: {
        'fade-in': {
          '0%': { opacity: '0', transform: 'translateY(8px)' },
          '100%': { opacity: '1', transform: 'translateY(0)' },
        },
      },
      animation: {
        'fade-in': 'fade-in 320ms cubic-bezier(0.16, 1, 0.3, 1)',
      },
    },
  },
  plugins: [require('tailwindcss-animate')],
};

export default config;
```

---

## 3. globals.css — CSS vars do shadcn/ui mapeados para Bravo

```css
/* app/globals.css */
@tailwind base;
@tailwind components;
@tailwind utilities;

@layer base {
  :root {
    /* Mapeia tokens Bravo para variáveis HSL do shadcn */
    --background: 0 0% 100%;                    /* white */
    --foreground: 244 43% 31%;                  /* #302d71 purple */

    --card: 0 0% 100%;
    --card-foreground: 244 43% 31%;

    --popover: 0 0% 100%;
    --popover-foreground: 244 43% 31%;

    --primary: 257 68% 63%;                     /* #8062de jacarta */
    --primary-foreground: 0 0% 100%;

    --secondary: 248 89% 96%;                   /* #eceafa bg-light */
    --secondary-foreground: 244 43% 31%;

    --muted: 248 89% 96%;
    --muted-foreground: 246 38% 38%;            /* #453d84 mid */

    --accent: 184 60% 61%;                      /* #5ecada viking */
    --accent-foreground: 244 43% 31%;

    --destructive: 0 76% 56%;
    --destructive-foreground: 0 0% 100%;

    --border: 248 50% 90%;
    --input: 248 50% 90%;
    --ring: 257 68% 63%;                        /* jacarta */

    --radius: 8px;
  }

  .dark {
    --background: 244 43% 19%;                  /* #201d49 */
    --foreground: 0 0% 100%;
    --card: 244 43% 27%;
    --card-foreground: 0 0% 100%;
    --popover: 244 43% 27%;
    --popover-foreground: 0 0% 100%;
    --primary: 257 68% 63%;
    --primary-foreground: 0 0% 100%;
    --secondary: 244 43% 27%;
    --secondary-foreground: 0 0% 100%;
    --muted: 244 43% 27%;
    --muted-foreground: 251 65% 77%;
    --accent: 184 60% 61%;
    --accent-foreground: 244 43% 19%;
    --border: 244 30% 35%;
    --input: 244 30% 35%;
    --ring: 257 68% 63%;
  }
}

@layer base {
  * { @apply border-border; }
  body { @apply bg-background text-foreground; }
}
```

---

## 4. Componentes shadcn/ui customizados Bravo

### 4.1 Button

```tsx
// components/ui/button.tsx (customização do shadcn Button)
import { cva, type VariantProps } from 'class-variance-authority';
import { cn } from '@/lib/utils';

const buttonVariants = cva(
  'inline-flex items-center justify-center whitespace-nowrap rounded-md font-medium ' +
  'transition-all focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-bravo-jacarta ' +
  'focus-visible:ring-offset-2 disabled:pointer-events-none disabled:opacity-50',
  {
    variants: {
      variant: {
        // Primário: Jacarta solid
        primary:   'bg-bravo-jacarta text-white hover:bg-bravo-purple-dark shadow-bravo-sm',
        // Secundário: outline Jacarta
        secondary: 'border-2 border-bravo-jacarta text-bravo-jacarta hover:bg-bravo-bg-light',
        // Ghost: invisível com hover
        ghost:     'text-bravo-purple hover:bg-bravo-bg-light',
        // Destructive
        destructive: 'bg-red-600 text-white hover:bg-red-700',
        // Link
        link: 'text-bravo-jacarta underline-offset-4 hover:underline',
      },
      size: {
        sm: 'h-9 px-3 text-sm',
        md: 'h-10 px-4 text-sm',
        lg: 'h-12 px-6 text-base',
        icon: 'h-10 w-10',
      },
    },
    defaultVariants: { variant: 'primary', size: 'md' },
  }
);

export interface ButtonProps
  extends React.ButtonHTMLAttributes<HTMLButtonElement>,
    VariantProps<typeof buttonVariants> {}

export function Button({ className, variant, size, ...props }: ButtonProps) {
  return <button className={cn(buttonVariants({ variant, size }), className)} {...props} />;
}
```

### 4.2 Card

```tsx
export function Card({ className, ...props }: React.HTMLAttributes<HTMLDivElement>) {
  return (
    <div
      className={cn(
        'rounded-lg border border-bravo-bg-light bg-white p-6 shadow-bravo-sm transition-shadow hover:shadow-bravo-md',
        className
      )}
      {...props}
    />
  );
}

export function CardHeader({ className, ...props }) {
  return <div className={cn('mb-4 space-y-1', className)} {...props} />;
}

export function CardTitle({ className, ...props }) {
  return (
    <h3 className={cn('text-xl font-bold text-bravo-purple', className)} {...props} />
  );
}

export function CardDescription({ className, ...props }) {
  return (
    <p className={cn('text-sm text-bravo-purple-mid', className)} {...props} />
  );
}
```

### 4.3 Input

```tsx
export function Input({ className, ...props }: React.InputHTMLAttributes<HTMLInputElement>) {
  return (
    <input
      className={cn(
        'flex h-10 w-full rounded-md border border-bravo-bg-light bg-white px-3 py-2 text-sm',
        'placeholder:text-bravo-purple-mid/60',
        'focus:border-bravo-jacarta focus:outline-none focus:ring-2 focus:ring-bravo-jacarta/20',
        'disabled:cursor-not-allowed disabled:opacity-50',
        className
      )}
      {...props}
    />
  );
}
```

### 4.4 Badge / Diff Pill

```tsx
import { cva } from 'class-variance-authority';

const badgeVariants = cva(
  'inline-flex items-center rounded-full px-2.5 py-0.5 text-xs font-bold',
  {
    variants: {
      variant: {
        default:  'bg-bravo-bg-light text-bravo-purple',
        primary:  'bg-bravo-jacarta text-white',
        positive: 'bg-bravo-pos/40 text-green-800 border border-green-600/30',
        negative: 'bg-bravo-neg/40 text-red-800 border border-red-600/30',
        neutral:  'bg-bravo-neu/60 text-yellow-800 border border-yellow-600/30',
      },
    },
    defaultVariants: { variant: 'default' },
  }
);

export function Badge({ className, variant, ...props }) {
  return <span className={cn(badgeVariants({ variant }), className)} {...props} />;
}

// Diff Pill (helper específico)
export function DiffPill({ value, isPositive }: { value: number; isPositive?: boolean }) {
  const positive = isPositive ?? value >= 0;
  const formatted = positive ? `+${value}%` : `(${Math.abs(value)}%)`;
  return (
    <Badge variant={positive ? 'positive' : 'negative'}>
      {formatted}
    </Badge>
  );
}
```

### 4.5 Table consulting-grade

```tsx
export function Table({ className, ...props }: React.HTMLAttributes<HTMLTableElement>) {
  return (
    <div className="w-full overflow-auto rounded-lg border border-bravo-bg-light">
      <table className={cn('w-full text-sm', className)} {...props} />
    </div>
  );
}

export function TableHeader({ className, ...props }) {
  return (
    <thead
      className={cn('bg-bravo-purple text-white [&_tr]:border-b-0', className)}
      {...props}
    />
  );
}

export function TableBody({ className, ...props }) {
  return <tbody className={cn('[&_tr:nth-child(even)]:bg-bravo-bg-light/40', className)} {...props} />;
}

export function TableHead({ className, ...props }) {
  return (
    <th
      className={cn(
        'h-12 px-4 text-left align-middle text-sm font-bold tracking-tight',
        className
      )}
      {...props}
    />
  );
}

export function TableRow({ className, ...props }) {
  return (
    <tr
      className={cn('border-b border-bravo-bg-light transition-colors hover:bg-bravo-bg-light/60', className)}
      {...props}
    />
  );
}

export function TableCell({ className, ...props }) {
  return (
    <td className={cn('px-4 py-3 align-middle text-bravo-purple', className)} {...props} />
  );
}

export function TableTotalRow({ className, ...props }) {
  return (
    <tr
      className={cn('!bg-bravo-jacarta font-bold text-white [&>td]:text-white', className)}
      {...props}
    />
  );
}
```

---

## 5. Padrões de layout

### 5.1 Hero section (landing page)

```tsx
export function Hero() {
  return (
    <section className="relative overflow-hidden bg-gradient-1 px-6 py-24 text-white sm:py-32">
      {/* Elemento decorativo do V — abstrato no canto direito */}
      <div className="absolute right-0 top-0 h-full w-1/3 opacity-10">
        <svg viewBox="0 0 200 200" className="h-full w-full">
          <polygon points="50,0 100,200 110,200 60,0" fill="#5ecada" />
          <polygon points="100,0 150,200 160,200 110,0" fill="#aa6cc9" />
        </svg>
      </div>

      <div className="relative mx-auto max-w-3xl">
        <Badge variant="primary" className="mb-6 bg-bravo-viking text-bravo-purple">
          Plano sem juros, sem letra pequena
        </Badge>
        <h1 className="text-5xl font-bold leading-tight sm:text-6xl">
          Saia das dívidas <span className="text-bravo-viking">sem perder o sono</span>.
        </h1>
        <p className="mt-6 text-lg leading-relaxed text-bravo-purple-lighter">
          Com a Bravo, você negocia diretamente com seu credor, fecha um plano que cabe no seu
          bolso e volta a ter controle das suas finanças.
        </p>
        <div className="mt-10 flex flex-wrap gap-4">
          <Button size="lg" variant="primary" className="bg-bravo-viking text-bravo-purple hover:bg-white">
            Consulte seu caso
          </Button>
          <Button size="lg" variant="ghost" className="text-white hover:bg-white/10">
            Como funciona →
          </Button>
        </div>
      </div>
    </section>
  );
}
```

### 5.2 KPI Dashboard card (4-up grid)

```tsx
interface KPIProps {
  label: string;
  value: string;
  unit?: string;
  diff?: { value: number; isPositive?: boolean };
  sparkline?: number[];
}

export function KPICard({ label, value, unit, diff }: KPIProps) {
  return (
    <Card>
      <div className="flex items-start justify-between">
        <div>
          <p className="text-sm font-medium text-bravo-purple-mid">{label}</p>
          <p className="mt-2 text-3xl font-bold text-bravo-purple">
            {value}
            {unit && (
              <span className="ml-1 text-base font-normal text-bravo-purple-mid">{unit}</span>
            )}
          </p>
        </div>
        {diff && <DiffPill value={diff.value} isPositive={diff.isPositive} />}
      </div>
    </Card>
  );
}

// Uso:
<div className="grid grid-cols-1 gap-4 sm:grid-cols-2 lg:grid-cols-4">
  <KPICard label="Receita Q1" value="29,2" unit="MM" diff={{ value: 31 }} />
  <KPICard label="EBITDA" value="5,4" unit="MM" diff={{ value: 58 }} />
  <KPICard label="Novos clientes" value="18.793" diff={{ value: 7 }} />
  <KPICard label="Churn" value="6,1" unit="%" diff={{ value: -10 }} />
</div>
```

### 5.3 Dashboard layout (sidebar + main)

```tsx
export function DashboardLayout({ children }: { children: React.ReactNode }) {
  return (
    <div className="flex min-h-screen bg-bravo-bg-lighter">
      {/* Sidebar */}
      <aside className="hidden w-64 flex-col bg-bravo-purple-darkest p-6 lg:flex">
        <Link href="/" className="mb-12 block">
          <img src="/bravo-logo-branco.png" alt="Bravo" className="h-8 w-auto" />
        </Link>
        <nav className="space-y-1">
          <SidebarLink href="/" icon={Home}>Visão geral</SidebarLink>
          <SidebarLink href="/clients" icon={Users}>Clientes</SidebarLink>
          <SidebarLink href="/operations" icon={BarChart3}>Operações</SidebarLink>
        </nav>
      </aside>

      {/* Main */}
      <main className="flex-1 overflow-y-auto p-8">{children}</main>
    </div>
  );
}

function SidebarLink({ href, icon: Icon, children }) {
  return (
    <Link
      href={href}
      className="flex items-center gap-3 rounded-md px-3 py-2 text-sm text-bravo-purple-lighter
                 transition-colors hover:bg-white/5 hover:text-white"
    >
      <Icon className="h-4 w-4" />
      {children}
    </Link>
  );
}
```

### 5.4 Feature grid

```tsx
const features = [
  { icon: ShieldCheck, title: 'Sem juros, sem taxa', desc: 'O valor que você combina é o que paga.' },
  { icon: Clock,       title: 'Plano em 1 dia',     desc: 'Análise rápida e simulação personalizada.' },
  { icon: Heart,       title: 'Atendimento humano', desc: 'Pessoas que entendem sua situação.' },
];

export function FeatureGrid() {
  return (
    <section className="py-24">
      <div className="mx-auto max-w-6xl px-6">
        <h2 className="text-3xl font-bold text-bravo-purple">Por que a Bravo</h2>
        <div className="mt-12 grid gap-6 sm:grid-cols-3">
          {features.map((f) => (
            <Card key={f.title}>
              <div className="mb-4 inline-flex h-12 w-12 items-center justify-center
                              rounded-lg bg-bravo-bg-light text-bravo-jacarta">
                <f.icon className="h-6 w-6" />
              </div>
              <CardTitle className="text-xl">{f.title}</CardTitle>
              <CardDescription className="mt-2 text-base">{f.desc}</CardDescription>
            </Card>
          ))}
        </div>
      </div>
    </section>
  );
}
```

---

## 6. Estados de UI (obrigatórios em qualquer app sério)

### Loading

```tsx
// Skeleton
<div className="animate-pulse">
  <div className="h-4 w-3/4 rounded bg-bravo-bg-light" />
  <div className="mt-2 h-4 w-1/2 rounded bg-bravo-bg-light" />
</div>

// Spinner (use Lucide Loader2)
<Loader2 className="h-5 w-5 animate-spin text-bravo-jacarta" />
```

### Empty state

```tsx
export function EmptyState({ icon: Icon, title, description, action }) {
  return (
    <div className="flex flex-col items-center justify-center py-16 text-center">
      <div className="mb-6 inline-flex h-16 w-16 items-center justify-center
                      rounded-full bg-bravo-bg-light text-bravo-jacarta">
        <Icon className="h-8 w-8" />
      </div>
      <h3 className="text-xl font-bold text-bravo-purple">{title}</h3>
      <p className="mt-2 max-w-sm text-bravo-purple-mid">{description}</p>
      {action && <div className="mt-6">{action}</div>}
    </div>
  );
}
```

### Error state

```tsx
<div className="rounded-lg border border-red-200 bg-red-50 p-4">
  <div className="flex items-start gap-3">
    <AlertCircle className="h-5 w-5 flex-shrink-0 text-red-600" />
    <div>
      <h4 className="text-sm font-bold text-red-900">Algo deu errado</h4>
      <p className="mt-1 text-sm text-red-800">{message}</p>
    </div>
  </div>
</div>
```

---

## 7. Acessibilidade (não-negociável)

- **Contraste**: mínimo 4.5:1 para texto regular, 3:1 para texto grande/decorativo (WCAG AA). Use o site contrast-ratio.com pra validar.
- **Focus visible**: todo elemento interativo tem `focus-visible:ring-2 focus-visible:ring-bravo-jacarta focus-visible:ring-offset-2`.
- **ARIA labels** em ícones-botão sem texto: `<button aria-label="Fechar"><X /></button>`.
- **Semântica HTML**: use `<button>`, `<nav>`, `<main>`, `<header>`, `<section>` corretamente. Nunca `<div onClick>` quando deveria ser `<button>`.
- **Heading hierarchy**: 1 `<h1>` por página, depois `<h2>`, `<h3>`. Sem pular níveis.
- **Reduce motion**: respeite `prefers-reduced-motion` para animações.

```css
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: 0.01ms !important;
    transition-duration: 0.01ms !important;
  }
}
```

---

## 8. Padrões anti-genéricos (o que NÃO fazer)

Para o app não parecer template:

- ❌ **Sombras pretas** — sempre tinted Purple (já no config).
- ❌ **Gradientes "soft purple to pink"** — só os 3 aprovados.
- ❌ **Border radius gigante em tudo** (`rounded-3xl` em todo card vira meme) — siga a escala.
- ❌ **Glassmorphism / blur excessivo** — não é a vibe Bravo.
- ❌ **Ícones em cards de feature todos com mesmo gradiente** — varie sutilmente: Jacarta solid, Viking solid, outline Purple.
- ❌ **Hero com foto de "casal feliz olhando boletos"** — clichê de fintech. Use o V abstrato, ilustração geométrica, ou foto autêntica (regra de tratamento de foto na seção `references/identidade-visual.md`).
- ❌ **Botões 100% width em desktop** — só em mobile.
- ❌ **Toda CTA em "Saiba mais"** — verbo de ação específico (ver `references/voz-e-tom.md`).
- ❌ **Texto cinza puro `text-gray-500`** — use `text-bravo-purple-mid` (#453d84), respeita a marca.
- ❌ **Dark mode "preto absoluto"** — use Purple Darkest `#201d49` como background.

---

## 9. Performance (essencial para credibilidade)

- **Imagens**: Next/Image sempre. Logo da Bravo PNG transparente já está otimizado nesta skill.
- **Fonts**: next/font (já no setup) — auto-hospeda, sem FOIT.
- **Code splitting**: route-based no Next.js já é default.
- **Métricas alvo (Lighthouse)**:
  - LCP < 2.5s
  - FID < 100ms
  - CLS < 0.1
  - Score Performance ≥ 90

---

## 10. Componentes prontos para usar (checklist de cobertura)

Quando o usuário pedir um app Bravo, garanta que esses estão disponíveis:

- [ ] `Button` (5 variants × 4 sizes)
- [ ] `Input`, `Textarea`, `Select`, `Checkbox`, `Radio`, `Switch`
- [ ] `Card`, `CardHeader`, `CardTitle`, `CardDescription`
- [ ] `Badge`, `DiffPill`
- [ ] `Table` + variants (TableHeader, TableBody, TableRow, TableCell, TableTotalRow)
- [ ] `Dialog` / `Modal`
- [ ] `Toast` / `Sonner`
- [ ] `Tabs`
- [ ] `Tooltip`
- [ ] `Dropdown / Popover`
- [ ] `Avatar`
- [ ] `Separator`
- [ ] `Skeleton` (loading)
- [ ] `EmptyState`
- [ ] `ErrorState`

Todos com cores Bravo, fonte Montserrat, tokens de design respeitados.

---

## 11. Para Artifacts no Claude (sem CDN do shadcn)

Se você está produzindo o app **como artifact no Claude.ai** (ou seja, em ambiente sem instalação de pacotes externos), use shadcn's component-prefab pattern: inline as classes Tailwind direto nos componentes, sem `cva` (que precisa do pacote `class-variance-authority`).

Exemplo de um botão self-contained para artifact:

```tsx
function Button({ variant = 'primary', size = 'md', className = '', children, ...props }) {
  const base = 'inline-flex items-center justify-center rounded-md font-medium transition-all ' +
               'focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-offset-2';
  const variants = {
    primary:   'bg-[#8062de] text-white hover:bg-[#3d359e] focus-visible:ring-[#8062de]',
    secondary: 'border-2 border-[#8062de] text-[#8062de] hover:bg-[#eceafa]',
    ghost:     'text-[#302d71] hover:bg-[#eceafa]',
  };
  const sizes = {
    sm: 'h-9 px-3 text-sm',
    md: 'h-10 px-4 text-sm',
    lg: 'h-12 px-6 text-base',
  };
  return (
    <button className={`${base} ${variants[variant]} ${sizes[size]} ${className}`} {...props}>
      {children}
    </button>
  );
}
```

Note as cores hex inline com `[#8062de]` — funciona em artifacts onde o `tailwind.config` customizado não está disponível.

---

## 12. Checklist antes de entregar um app

- [ ] Tailwind config com paleta Bravo e tokens completos?
- [ ] Montserrat configurada via next/font?
- [ ] Sombras são tinted Purple, nunca preto puro?
- [ ] Border radius segue a escala (4/8/12/16/24)?
- [ ] Spacing segue a escala 8pt?
- [ ] Contraste WCAG AA (4.5:1) validado?
- [ ] Estados de loading, empty, error implementados?
- [ ] Focus visible em todos os elementos interativos?
- [ ] Diff pills usadas em qualquer comparação %?
- [ ] Logo Bravo com fundo transparente (assets desta skill)?
- [ ] Lucide para ícones (não emojis decorativos)?
- [ ] Não tem nenhum dos anti-padrões da seção 8?
- [ ] Lighthouse Performance ≥ 90?
- [ ] Copy em PT-BR com "você", seguindo `voz-e-tom.md`?
