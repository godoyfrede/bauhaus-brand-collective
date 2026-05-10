# Bauhaus Brand Collective — Documentacao Completa

**Versao:** 1.0.0
**Categoria:** Branding / Identity Design
**Modelo base:** claude-sonnet-4-6

---

## Sumario

1. [Visao Geral](#1-visao-geral)
2. [Arquitetura do Time](#2-arquitetura-do-time)
3. [Pipeline Detalhado](#3-pipeline-detalhado)
4. [Perfil Completo de cada Agente](#4-perfil-completo-de-cada-agente)
5. [Skills Disponiveis](#5-skills-disponiveis)
6. [Artefatos Produzidos](#6-artefatos-produzidos)
7. [Gates de Aprovacao](#7-gates-de-aprovacao)
8. [Integracao com Outros Times](#8-integracao-com-outros-times)
9. [Instalacao e Uso](#9-instalacao-e-uso)
10. [Diagrama ASCII do Pipeline](#10-diagrama-ascii-do-pipeline)
11. [FAQ](#11-faq)

---

## 1. Visao Geral

### O que e o Bauhaus Brand Collective

O **Bauhaus Brand Collective** e um plugin multi-agente para o Claude Code que transforma uma ideia de negocio em uma marca completa — da estrategia ao Brand Book documentado e pronto para uso.

O plugin resolve um dos problemas mais comuns de startups e novos produtos: marcas criadas sem intencao estrategica, onde nome, visual e voz nao conversam entre si. O Bauhaus Brand Collective impoe rigor metodologico antes de qualquer decisao estetica ser tomada.

Sao 7 agentes especializados em sequencia: da estrategia de marca (Kandinsky) a pesquisa de mercado (Moholy), da identidade visual (Klee) ao sistema tipografico e cromatico (Bayer), do tom de voz (Itten) a consolidacao final (Breuer) — tudo orquestrado por Gropius com coerencia total.

### Filosofia Bauhaus

A metafora central e a escola Bauhaus (1919-1933), que unificou arte, craft e tecnologia sob o principio de que forma segue funcao. Cada agente e nomeado com um mestre da Bauhaus cuja especialidade espelha seu papel no pipeline:

| Mestre | Especialidade Original | Papel no Plugin |
|--------|----------------------|-----------------|
| Walter Gropius | Fundador, visao unificada | Orquestrador — garante coerencia |
| Wassily Kandinsky | Teoria abstrata, essencia | Estrategia — extrai a essencia da marca |
| Laszlo Moholy-Nagy | Fotografia, materiais, pesquisa | Pesquisa — investiga o mercado real |
| Paul Klee | Composicao, forma, cor | Visual — cria a identidade visual |
| Herbert Bayer | Tipografia, design grafico | Sistema — define tipo e cor com precisao |
| Johannes Itten | Expressao, subjetividade | Voz — da personalidade verbal a marca |
| Marcel Breuer | Produto funcional, execucao | Montagem — consolida o brand book final |

### Principios Fundamentais

- **Gates obrigatorios**: nenhuma fase avanca sem aprovacao explicita
- **Estrategia antes de estetica**: nunca uma cor e escolhida antes do posicionamento existir
- **Evidencia antes de opiniao**: Moholy pesquisa o mercado real antes de Klee criar
- **Consistencia verificada**: Breuer faz QA cruzado antes de entregar
- **Acessibilidade integrada**: Bayer verifica contrastes WCAG em toda paleta
- **Rastreabilidade**: cada decisao visual se justifica pela estrategia de Kandinsky

---

## 2. Arquitetura do Time

### Criterio de Selecao de Modelos

| Modelo | Agentes | Motivo |
|--------|---------|--------|
| `claude-sonnet-4-6` | Todos os 7 agentes | Raciocinio profundo para estrategia, criacao visual, pesquisa web e redacao |

---

### Tabela dos 7 Agentes

| Agente | Mestre | Papel | Responsabilidades | Restricoes |
|--------|--------|-------|-------------------|-----------|
| `gropius` | Walter Gropius | Orquestrador | Entry point, roteamento, gates, PROGRESS.md, aprovacao final | Nunca pula gates; nunca toma decisoes criativas; questiona inconsistencias |
| `kandinsky` | Wassily Kandinsky | Brand Strategist | Discovery socratico, posicionamento, arquetipos, UVP, personalidade | Nunca sugere elementos visuais; nunca inventa dados de mercado |
| `moholy` | Laszlo Moholy-Nagy | Pesquisador | Concorrentes de marca, referencias visuais, tendencias, moodboard | Nunca inventa referencias; nunca toma decisoes visuais; sempre cita URLs |
| `klee` | Paul Klee | Visual Identity | Conceito de logo, sistema visual, variantes, aplicacoes, grid | Nunca define cores HEX; nunca define fontes especificas; descreve para execucao |
| `bayer` | Herbert Bayer | Typography & Color | Familias tipograficas, escala, paleta de cores, tokens, contraste WCAG | Nunca escolhe cores sem WCAG; nunca altera conceito de Klee |
| `itten` | Johannes Itten | Voice & Copy | Personalidade verbal, espectro de tom, vocabulario, exemplos de copy | Nunca define visuais; nunca contradiz estrategia de Kandinsky |
| `breuer` | Marcel Breuer | Brand Book Assembler | Consolidacao, QA de consistencia, BRAND-BOOK.md final | Nunca cria conteudo novo; nunca entrega com inconsistencias |

### Principio de Separacao de Responsabilidades

| Agente | Define | Nao define |
|--------|--------|-----------|
| Kandinsky | Posicionamento, arquetipos, UVP | Cores, fontes, logo |
| Moholy | Referencias e evidencias de mercado | Direcao criativa final |
| Klee | Conceito visual e sistema de marca | Cores HEX, fontes especificas |
| Bayer | Tipografia e paleta com tokens | Conceito do logo, tom de voz |
| Itten | Personalidade verbal e copy | Elementos visuais |
| Breuer | Brand book consolidado | Conteudo original |

---

## 3. Pipeline Detalhado

### Visao Linear das Fases

O pipeline possui 6 fases numeradas de 0 a 5, mais a entrega final por Gropius.

---

### Fase 0 — Discovery & Estrategia

| Elemento | Detalhe |
|----------|---------|
| **Agente** | Kandinsky |
| **Input** | Ideia ou briefing do usuario |
| **Processo** | 2-3 blocos de perguntas tematicas: essencia/proposito, publico/contexto, personalidade/diferencial |
| **Artefatos** | `brand-discovery.md` + `brand-strategy.md` |
| **Gate** | Gropius apresenta posicionamento + arquetipos. Usuario valida estrategia |

**Conteudo de brand-strategy.md:**
Proposito (missao/visao/valores), posicionamento (framework Para/Que/E/Diferente de/Porque), arquetipos de Jung (primario + secundario), personalidade da marca (4 dimensoes), territorio, UVP, taglines candidatas, briefing para Moholy.

---

### Fase 1 — Pesquisa & Referencias

| Elemento | Detalhe |
|----------|---------|
| **Agente** | Moholy |
| **Input** | `brand-strategy.md` |
| **Processo** | Pesquisa web: concorrentes de marca, Behance, Brand New, Dribbble, tendencias |
| **Artefatos** | `research-brief.md` + `moodboard.md` |
| **Gate** | Gropius apresenta insights + moodboard. Usuario valida direcao criativa |

**Protocolo de pesquisa:**
1. Concorrentes de marca (3-5 players) — posicionamento e estilo visual
2. Referencias visuais reais com URLs (Behance, Dribbble, Brand New)
3. Tendencias de branding na categoria
4. Cliches a evitar
5. Briefing para Klee com direcao recomendada

---

### Fase 2 — Identidade Visual

| Elemento | Detalhe |
|----------|---------|
| **Agente** | Klee |
| **Input** | `brand-strategy.md` + `moodboard.md` |
| **Processo** | 2-3 direcoes conceituais → usuario escolhe → desenvolvimento completo |
| **Artefatos** | `visual-identity.md` + `logo-spec.md` |
| **Gate** | Gropius apresenta identidade visual. Usuario valida conceito |

**Conteudo de logo-spec.md:**
Descricao detalhada do logo (grid, proporcoes, significado), variantes (horizontal, vertical, icone, mono, negativo), area de protecao, tamanho minimo, usos incorretos (don'ts), briefing para Bayer.

---

### Fase 3 — Tipografia & Cores

| Elemento | Detalhe |
|----------|---------|
| **Agente** | Bayer |
| **Input** | `visual-identity.md` + `logo-spec.md` |
| **Processo** | Selecao tipografica + pareamento + escala + paleta completa com WCAG |
| **Artefatos** | `typography-spec.md` + `color-system.md` |
| **Gate** | Gropius apresenta sistema tipografico e paleta. Usuario valida |

**Verificacoes obrigatorias:**
- Contraste WCAG AA (4.5:1 texto normal, 3:1 large text)
- Licenciamento de fontes verificado
- Tokens estruturados para implementacao (JSON)
- Briefing para Itten

---

### Fase 4 — Tom de Voz & Copy

| Elemento | Detalhe |
|----------|---------|
| **Agente** | Itten |
| **Input** | `brand-strategy.md` + `color-system.md` |
| **Processo** | Personalidade verbal + espectro + principios + exemplos por canal |
| **Artefatos** | `voice-guide.md` + `copy-samples.md` |
| **Gate** | Gropius apresenta tom de voz + exemplos. Usuario valida |

**Conteudo de copy-samples.md:**
Tagline, manifesto, bio (3 versoes), headlines por contexto, social media (Instagram, LinkedIn), email (welcome, newsletter), CTAs, mensagens de erro/estado vazio.

---

### Fase 5 — Brand Book Final

| Elemento | Detalhe |
|----------|---------|
| **Agente** | Breuer |
| **Input** | TODOS os artefatos anteriores (9 arquivos) |
| **Processo** | QA de consistencia cruzada → consolidacao em documento unico |
| **Artefato** | `BRAND-BOOK.md` |
| **Gate** | Gropius apresenta brand book. Usuario da aprovacao final |

**QA de consistencia (checklist):**
- Cores do color-system batem com visual-identity?
- Fontes do typography-spec complementam o logo?
- Tom de voz e coerente com arquetipos?
- Tagline reflete posicionamento?
- Contrastes WCAG verificados?
- Todas as variantes de logo especificadas?

---

### Conclusao — Entrega Final

| Elemento | Detalhe |
|----------|---------|
| **Agente** | Gropius |
| **Processo** | Compara brand book com briefing original, verifica completude |
| **Artefato** | `FINAL_REPORT.md` |
| **Declaracao** | "ENTREGA APROVADA — Bauhaus Brand Collective concluido." |

---

## 4. Perfil Completo de cada Agente

---

### 4.1 Gropius — O Brand Director

**Identidade:** Gropius e o orquestrador — a visao unificadora que garante que estrategia, visual e voz formam um todo coerente. Como Walter Gropius uniu artes, design e industria sob um teto, este agente une todos os especialistas sob uma marca.

**Principios:**
- Unico entry point do pipeline
- Nunca pula um gate de aprovacao
- Nunca toma decisoes criativas pelo usuario
- Mantem PROGRESS.md atualizado a cada fase
- Unico com poder de declarar entrega completa

**Modos de roteamento:**
- *Pipeline completo* — "criar uma marca", "branding", "brand book"
- *Modo cirurgico* — "so o logo" → Klee; "so as cores" → Bayer; "so a voz" → Itten
- *Retomada* — le PROGRESS.md e continua de onde parou

---

### 4.2 Kandinsky — O Brand Strategist

**Identidade:** Kandinsky busca a essencia abstrata antes da forma visivel. Extrai proposito, valores, personalidade e posicionamento — os fundamentos sobre os quais tudo sera construido.

**Processo:**
1. Bloco 1: Essencia e proposito (problema, identidade, valores, visao)
2. Bloco 2: Publico e contexto (perfil, alternativas, diferencial, momento)
3. Bloco 3: Personalidade e diferencial (marcas admiradas, espectro, anti-comportamento)
4. Sintese em brand-strategy.md com posicionamento, arquetipos e UVP
5. Handoff para Moholy com briefing de pesquisa

**Outputs:** `brand-discovery.md`, `brand-strategy.md`

---

### 4.3 Moholy — O Pesquisador

**Identidade:** Moholy investiga o mundo real com curiosidade incansavel. Traz evidencias concretas — URLs, screenshots, dados — para que decisoes criativas sejam fundamentadas.

**Processo:**
1. Pesquisa concorrentes de marca (3-5 players, posicionamento e estilo)
2. Busca referencias visuais reais (Behance, Dribbble, Brand New)
3. Mapeia tendencias e cliches da categoria
4. Analisa naming patterns (se aplicavel)
5. Monta moodboard descritivo com justificativas
6. Handoff para Klee com direcao recomendada

**Outputs:** `research-brief.md`, `moodboard.md`

---

### 4.4 Klee — O Visual Identity Designer

**Identidade:** Klee transforma estrategia e referencias em forma visual concreta. Cria o conceito do logo e o sistema de marca com precisao poetica — descrevendo com exatidao suficiente para um designer executar.

**Processo:**
1. Le estrategia + moodboard
2. Apresenta 2-3 direcoes conceituais distintas
3. Desenvolve direcao aprovada com especificacao completa
4. Define sistema visual (elementos secundarios, iconografia, fotografia)
5. Especifica aplicacoes-chave
6. Handoff para Bayer com briefing de tipografia e energia de cor

**Outputs:** `visual-identity.md`, `logo-spec.md`

---

### 4.5 Bayer — O Tipografo & Color Systemist

**Identidade:** Bayer e precisao funcional. Transforma a direcao visual em um sistema tecnico de tipografia e cores — acessivel, escalavel e implementavel.

**Processo:**
1. Seleciona familias tipograficas (display + body + mono)
2. Justifica pareamento tipografico
3. Define escala completa (h1-h6, body, caption, overline)
4. Cria paleta (primaria, secundaria, neutros, semantica)
5. Verifica TODOS os contrastes WCAG AA
6. Gera tokens estruturados (JSON)
7. Handoff para Itten com briefing de energia verbal

**Outputs:** `typography-spec.md`, `color-system.md`

---

### 4.6 Itten — O Voice & Copy Strategist

**Identidade:** Itten explora a expressao interior — como a marca se manifesta em palavras. Define personalidade verbal, espectro de tom e cria exemplos concretos que nenhuma outra marca poderia usar.

**Processo:**
1. Traduz arquetipos em atributos verbais (4-5 adjetivos + anti-atributos)
2. Posiciona marca em 4 dimensoes de tom (formalidade, humor, entusiasmo, tecnicidade)
3. Cria 5 principios de voz ("Nos fazemos X, nao Y")
4. Define vocabulario (palavras-poder + proibidas)
5. Adapta tom por canal (site, redes, email, atendimento)
6. Gera exemplos concretos de copy
7. Handoff para Breuer

**Outputs:** `voice-guide.md`, `copy-samples.md`

---

### 4.7 Breuer — O Brand Book Assembler

**Identidade:** Breuer transforma conceitos em produto funcional. Consolida todos os artefatos em um unico Brand Book coerente — verificando consistencia antes de entregar.

**Processo:**
1. Le TODOS os 9 artefatos obrigatorios
2. Executa checklist de QA cruzado
3. Reporta e resolve inconsistencias (com aprovacao)
4. Monta BRAND-BOOK.md com indice navegavel
5. Entrega documento pronto para uso

**Outputs:** `BRAND-BOOK.md`

---

## 5. Skills Disponiveis

### `/brandteam` — Pipeline Completo

**Quando usar:** Criacao de marca do zero com controle total.

**Comportamento:** Executa todas as 6 fases em sequencia com gate de aprovacao entre cada uma. O usuario decide o ritmo.

**Exemplo:**
```
/brandteam Quero criar uma marca para minha startup de educacao online
```

---

### `/brandautopilot` — Execucao Autonoma

**Quando usar:** Prototipacao rapida, marcas pessoais, MVPs.

**Comportamento:** Executa todas as fases sem parar para aprovacao — exceto a aprovacao final do Brand Book. Informe progresso a cada fase.

**Exemplo:**
```
/brandautopilot Marca premium de cafe artesanal, publico 25-40, nome "Origem"
```

---

### `/brandloop` — Loop de Verificacao

**Quando usar:** Brand book ja existe mas precisa de refinamento/correcao.

**Comportamento:** Executa verify→fix→verify em loop ate atingir consistencia total ou limite de 10 iteracoes.

**Exemplo:**
```
/brandloop Verifica se as cores e o tom de voz estao alinhados com os arquetipos
```

---

## 6. Artefatos Produzidos

### Estrutura de Output

```
docs/brand/
├── PROGRESS.md              (Gropius — painel de controle)
├── brand-discovery.md       (Kandinsky — registro do discovery)
├── brand-strategy.md        (Kandinsky — posicionamento completo)
├── research-brief.md        (Moholy — analise competitiva)
├── moodboard.md             (Moholy — referencias visuais)
├── visual-identity.md       (Klee — conceito e sistema visual)
├── logo-spec.md             (Klee — especificacoes tecnicas do logo)
├── typography-spec.md       (Bayer — familias, escala, regras)
├── color-system.md          (Bayer — paleta + tokens + WCAG)
├── voice-guide.md           (Itten — tom de voz e principios)
├── copy-samples.md          (Itten — exemplos por canal)
├── BRAND-BOOK.md            (Breuer — documento final consolidado)
├── FINAL_REPORT.md          (Gropius — aprovacao final)
├── context-snapshot.json    (Gropius — anti-context-stale)
└── handoffs/
    ├── 00-discovery.md
    ├── 01-research.md
    ├── 02-visual-identity.md
    ├── 03-typography-color.md
    ├── 04-voice-copy.md
    └── 05-brand-book.md
```

### Artefato Principal: BRAND-BOOK.md

O Brand Book final contém 9 secoes:
1. A Marca (proposito, valores, UVP, tagline)
2. Estrategia (posicionamento, arquetipos, personalidade, publico)
3. Identidade Visual (conceito, elementos graficos, fotografia)
4. Logo (principal, variantes, grid, clear space, don'ts)
5. Tipografia (familias, escala, regras)
6. Cores (paletas, semantica, WCAG, tokens)
7. Tom de Voz (personalidade, espectro, principios, vocabulario)
8. Aplicacoes (cartao, redes sociais, email, site)
9. Do's and Don'ts (visual + verbal)

---

## 7. Gates de Aprovacao

### Formato padrao de gate

```
"Fase [N] concluida. Deseja:
1. Aprovar e avancar para [proxima fase]
2. Editar algum ponto desta entrega
3. Refazer esta fase do inicio"
```

### Gates por fase

| Gate | Apos fase | O que e apresentado |
|------|-----------|---------------------|
| Gate 0 | Discovery | Posicionamento + arquetipos + UVP |
| Gate 1 | Pesquisa | Insights de mercado + moodboard |
| Gate 2 | Visual | Conceito de logo + sistema visual |
| Gate 3 | Tipo+Cor | Paleta + tipografia + contrastes WCAG |
| Gate 4 | Voz | Tom de voz + exemplos de copy |
| Gate 5 | Brand Book | Documento final consolidado |

### Regras de gate

- Silencio NAO e aprovacao — Gropius aguarda resposta explicita
- Edicoes geram V2 do artefato (nunca sobrescrita silenciosa)
- O usuario pode pedir para refazer qualquer fase a qualquer momento

---

## 8. Integracao com Outros Times

### ← UX Research Lab (Entrada)

**Quando usar:** Antes de Kandinsky iniciar o discovery. Personas e insights de usuario enriquecem a estrategia.

**O que Kandinsky faz com esses dados:**
- Perfil do publico validado → posicionamento mais preciso
- Linguagem dos usuarios → informa tom de voz de Itten
- Dores reais → fortalece a proposta de valor

### ← Deep Market Research (Entrada)

**Quando usar:** Antes de Moholy pesquisar. Dados de mercado pre-existentes aceleram a pesquisa.

**O que Moholy faz com esses dados:**
- Concorrentes ja mapeados → foco em analise visual (nao repetir pesquisa)
- Tendencias identificadas → direcionam moodboard

### → Design System Factory (Saida)

**Quando usar:** Apos o Brand Book estar aprovado e o produto precisar de um design system.

**Artefatos que alimentam o Design System Factory:**
- `brand-strategy.md` → Bono (estrategia visual do DS)
- `color-system.md` → Hendrix (tokens de cor)
- `typography-spec.md` → Hendrix (tokens tipograficos)
- `visual-identity.md` → Cobain (direcao de componentes)

### → Sgt. Peppers AI Band (Saida)

**Quando usar:** Quando o produto precisa ser construido apos a marca existir.

**Artefatos uteis:**
- `brand-strategy.md` → John (contexto para o PRD)
- `copy-samples.md` → Paul (copy para UI)

---

## 9. Instalacao e Uso

### Instalacao como plugin Claude Code

1. Clone o repositorio
2. O plugin e reconhecido via `.claude-plugin/plugin.json`
3. Agentes e skills ficam disponiveis automaticamente

### Registro manual

Adicione ao `installed_plugins.json`:

```json
"bauhaus-brand-collective@bauhaus-brand-local": [
  {
    "scope": "user",
    "installPath": "<caminho-do-repo>",
    "version": "1.0.0"
  }
]
```

### Uso direto

**Pipeline completo:**
```
/brandteam Quero criar uma marca para [descricao]
```

**Modo autopilot:**
```
/brandautopilot [descricao completa da marca]
```

**Agente especifico:**
```
@gropius    — orquestrador (entry point)
@kandinsky  — estrategia de marca
@moholy     — pesquisa e referencias
@klee       — identidade visual
@bayer      — tipografia e cores
@itten      — tom de voz e copy
@breuer     — brand book final
```

**Exemplos de ativacao:**
```
"Cria uma marca para meu SaaS de produtividade"
"Preciso so de uma paleta de cores acessivel"
"Quero definir o tom de voz da minha marca"
"Faz o brand book completo no modo autopilot"
"Verifica se a marca esta consistente"
```

---

## 10. Diagrama ASCII do Pipeline

```
              BAUHAUS BRAND COLLECTIVE
                        │
             ┌──────────▼──────────┐
             │       GROPIUS       │ ← entry point
             │    Brand Director   │
             └──────────┬──────────┘
                        │
             ┌──────────▼──────────┐
             │      KANDINSKY      │
             │   Brand Strategist  │
             │  brand-strategy.md  │
             └──────────┬──────────┘
                        │ 🔴 GATE
             ┌──────────▼──────────┐
             │       MOHOLY        │
             │    Pesquisador      │
             │  research-brief.md  │
             │    moodboard.md     │
             └──────────┬──────────┘
                        │ 🔴 GATE
             ┌──────────▼──────────┐
             │        KLEE         │
             │  Visual Identity    │
             │ visual-identity.md  │
             │    logo-spec.md     │
             └──────────┬──────────┘
                        │ 🔴 GATE
             ┌──────────▼──────────┐
             │        BAYER        │
             │  Typography & Color │
             │ typography-spec.md  │
             │  color-system.md    │
             └──────────┬──────────┘
                        │ 🔴 GATE
             ┌──────────▼──────────┐
             │        ITTEN        │
             │   Voice & Copy      │
             │   voice-guide.md    │
             │  copy-samples.md    │
             └──────────┬──────────┘
                        │ 🔴 GATE
             ┌──────────▼──────────┐
             │       BREUER        │
             │  Brand Book + QA    │
             │   BRAND-BOOK.md     │
             └──────────┬──────────┘
                        │ 🔴 GATE FINAL
             ┌──────────▼──────────┐
             │       GROPIUS       │
             │   Entrega Final     │
             │  FINAL_REPORT.md    │
             └─────────────────────┘

             ↓ HANDOFFS DE ENTRADA        ↓ HANDOFFS DE SAIDA
  ┌─────────────────────────┐    ┌────────────────────────────────┐
  │    UX Research Lab      │    │    Design System Factory       │
  │  personas-overview.md   │    │  brand-strategy → Bono         │
  │  insight-report.md      │    │  color-system → Hendrix        │
  │       → Kandinsky       │    │  typography-spec → Hendrix     │
  ├─────────────────────────┤    │  visual-identity → Cobain      │
  │  Deep Market Research   │    ├────────────────────────────────┤
  │  competitive-analysis   │    │    Sgt. Peppers AI Band        │
  │       → Moholy          │    │  brand-strategy → John (PRD)   │
  └─────────────────────────┘    │  copy-samples → Paul (UI)      │
                                 └────────────────────────────────┘
```

---

## 11. FAQ

**P: Posso usar apenas um agente sem o pipeline completo?**
R: Sim. Gropius detecta pedidos cirurgicos (ex: "preciso so de uma paleta de cores") e aciona apenas o agente necessario.

**P: O plugin gera imagens do logo?**
R: Nao. Klee descreve o logo com precisao suficiente para um designer (ou IA de geracao de imagem) executar. O output e textual — specs, nao assets.

**P: Preciso de pesquisa de usuario antes de usar o pipeline?**
R: Nao e obrigatorio. Kandinsky tem perguntas proprias para entender o publico. Mas dados do UX Research Lab enriquecem significativamente a estrategia.

**P: Como o brand book se conecta com o Design System Factory?**
R: Os artefatos de Bayer (typography-spec.md, color-system.md) alimentam diretamente Hendrix (tokens). O brand-strategy.md alimenta Bono. E uma integracao nativa.

**P: Posso refazer apenas uma fase do pipeline?**
R: Sim. A qualquer momento voce pode pedir para refazer uma fase especifica. Gropius gerencia o impacto cascata nas fases seguintes.

**P: O que acontece se Breuer encontrar inconsistencias?**
R: Breuer reporta a inconsistencia, sugere correcao e pede aprovacao antes de ajustar. Nunca corrige silenciosamente.

**P: O /brandautopilot pula a aprovacao final?**
R: Nao. Mesmo no modo autopilot, a aprovacao final do Brand Book e obrigatoria. E o unico gate que nunca e pulado.

**P: Como uso o /brandloop?**
R: Quando o brand book ja existe mas voce quer verificar consistencia (ex: mudou uma cor e quer garantir que tudo ainda funciona). Loop maximo: 10 iteracoes.

**P: Posso personalizar os agentes?**
R: Sim, editando os arquivos em `agents/`. Respeite a secao "Identidade e Origem" (licenca exige preservacao da atribuicao).

**P: Em que idioma os artefatos sao gerados?**
R: Portugues (Brasil) por padrao, com termos tecnicos de design em ingles quando relevante.
