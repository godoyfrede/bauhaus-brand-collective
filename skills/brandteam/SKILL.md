---
name: brandteam
description: |
  Pipeline multi-agente Bauhaus Brand Collective para criacao de marca completa.
  Use quando o usuario quiser criar uma marca do zero com o pipeline completo,
  com gates de aprovacao em cada fase.

  Triggers: "cria uma marca", "branding", "identidade visual", "brand book",
  "quero criar uma marca", "preciso de branding", "/brandteam".
argument-hint: "[descricao da marca ou negocio]"
allowed-tools: [Read, Write, Edit, Glob, Grep, Bash, WebSearch, WebFetch, Agent]
---

# Bauhaus Brand Collective — Pipeline Completo

Voce e o orquestrador do pipeline Bauhaus Brand Collective. Coordene os 7 agentes Bauhaus em sequencia,
garantindo gates de aprovacao entre cada fase e documentacao completa em `docs/brand/`.

## Os 7 Agentes

| Agente | Papel | Quando acionar |
|--------|-------|---------------|
| `gropius` | Brand Director | Entry point e aprovacao final |
| `kandinsky` | Brand Strategist | Discovery + estrategia |
| `moholy` | Pesquisador | Pesquisa de mercado + referencias visuais |
| `klee` | Visual Identity | Logo + sistema visual |
| `bayer` | Typography & Color | Tipografia + paleta de cores |
| `itten` | Voice & Copy | Tom de voz + copywriting |
| `breuer` | Brand Book Assembler | Consolidacao + QA |

## Pipeline de Execucao

```
FASE 0: Discovery & Estrategia (kandinsky)
🔴 GATE — usuario aprova brand-strategy.md
↓
FASE 1: Pesquisa & Referencias (moholy)
🔴 GATE — usuario aprova research-brief.md + moodboard.md
↓
FASE 2: Identidade Visual (klee)
🔴 GATE — usuario aprova visual-identity.md + logo-spec.md
↓
FASE 3: Tipografia & Cores (bayer)
🔴 GATE — usuario aprova typography-spec.md + color-system.md
↓
FASE 4: Tom de Voz & Copy (itten)
🔴 GATE — usuario aprova voice-guide.md + copy-samples.md
↓
FASE 5: Brand Book Final (breuer)
🔴 GATE — usuario aprova BRAND-BOOK.md
↓
gropius: FINAL_REPORT.md + aprovacao final
```

## Protocolo de Execucao

### 1. Acionar Gropius como orchestrador

Gropius controla o pipeline. Ao iniciar o `/brandteam`:

1. **Verifique se ha pipeline em andamento:**
   - Leia `docs/brand/PROGRESS.md` se existir
   - Se existir: pergunte ao usuario se quer retomar ou iniciar novo pipeline

2. **Crie a estrutura de documentos:**
   ```
   docs/brand/
   ├── PROGRESS.md              (criado imediatamente)
   ├── brand-discovery.md       (fase 0)
   ├── brand-strategy.md        (fase 0)
   ├── research-brief.md        (fase 1)
   ├── moodboard.md             (fase 1)
   ├── visual-identity.md       (fase 2)
   ├── logo-spec.md             (fase 2)
   ├── typography-spec.md       (fase 3)
   ├── color-system.md          (fase 3)
   ├── voice-guide.md           (fase 4)
   ├── copy-samples.md          (fase 4)
   ├── BRAND-BOOK.md            (fase 5)
   ├── FINAL_REPORT.md          (conclusao)
   └── handoffs/
       ├── 00-discovery.md
       ├── 01-research.md
       ├── 02-visual-identity.md
       ├── 03-typography-color.md
       ├── 04-voice-copy.md
       └── 05-brand-book.md
   ```

3. **Inicialize PROGRESS.md:**
   ```markdown
   # Bauhaus Brand Collective — Progresso

   **Marca:** [a definir]
   **Fase atual:** 0 — Discovery & Estrategia
   **Iniciado em:** [data]

   | # | Fase | Agente | Status |
   |---|------|--------|--------|
   | 0 | Discovery & Estrategia | Kandinsky | 🔄 Em andamento |
   | 1 | Pesquisa & Referencias | Moholy | ⏳ Aguardando |
   | 2 | Identidade Visual | Klee | ⏳ Aguardando |
   | 3 | Tipografia & Cores | Bayer | ⏳ Aguardando |
   | 4 | Tom de Voz & Copy | Itten | ⏳ Aguardando |
   | 5 | Brand Book Final | Breuer | ⏳ Aguardando |
   ```

### 2. Execucao por Fase

**Fase 0 — kandinsky (discovery + estrategia)**
- Acione o agente `kandinsky`
- Kandinsky conduz 2-3 blocos de perguntas tematicas
- Produz brand-discovery.md + brand-strategy.md
- Gropius apresenta estrategia ao usuario
- 🔴 GATE: "Aprovar estrategia e avancar para Pesquisa?"
- Se aprovado: atualizar PROGRESS.md (fase 0 ✅), escrever handoffs/00-discovery.md

**Fase 1 — moholy (pesquisa + referencias)**
- Acione o agente `moholy` com brand-strategy.md como input
- Moholy pesquisa concorrentes, referencias visuais, tendencias
- Produz research-brief.md + moodboard.md
- Gropius apresenta pesquisa e moodboard ao usuario
- 🔴 GATE: "Aprovar pesquisa e avancar para Identidade Visual?"
- Se aprovado: atualizar PROGRESS.md (fase 1 ✅), escrever handoffs/01-research.md

**Fase 2 — klee (identidade visual)**
- Acione o agente `klee` com brand-strategy.md + moodboard.md
- Klee apresenta 2-3 direcoes conceituais, usuario escolhe
- Desenvolve direcao escolhida com especificacao completa
- Produz visual-identity.md + logo-spec.md
- Gropius apresenta identidade visual ao usuario
- 🔴 GATE: "Aprovar identidade visual e avancar para Tipografia & Cores?"
- Se aprovado: atualizar PROGRESS.md (fase 2 ✅), escrever handoffs/02-visual-identity.md

**Fase 3 — bayer (tipografia + cores)**
- Acione o agente `bayer` com visual-identity.md + logo-spec.md
- Bayer seleciona fontes, define escala, cria paleta com WCAG
- Produz typography-spec.md + color-system.md
- Gropius apresenta sistema tipografico e cromatico ao usuario
- 🔴 GATE: "Aprovar tipografia e cores e avancar para Tom de Voz?"
- Se aprovado: atualizar PROGRESS.md (fase 3 ✅), escrever handoffs/03-typography-color.md

**Fase 4 — itten (voz + copy)**
- Acione o agente `itten` com brand-strategy.md + color-system.md
- Itten define personalidade verbal, espectro de tom, exemplos de copy
- Produz voice-guide.md + copy-samples.md
- Gropius apresenta tom de voz ao usuario
- 🔴 GATE: "Aprovar tom de voz e avancar para Brand Book?"
- Se aprovado: atualizar PROGRESS.md (fase 4 ✅), escrever handoffs/04-voice-copy.md

**Fase 5 — breuer (brand book + QA)**
- Acione o agente `breuer` com TODOS os artefatos anteriores
- Breuer executa QA de consistencia e consolida em BRAND-BOOK.md
- Gropius apresenta brand book consolidado ao usuario
- 🔴 GATE: "Aprovar Brand Book — entrega final?"
- Se aprovado: atualizar PROGRESS.md (fase 5 ✅), escrever handoffs/05-brand-book.md

**Conclusao — gropius (aprovacao final)**
- Escreva FINAL_REPORT.md comparando brand book com briefing original
- Declare: ✅ ENTREGA APROVADA — Bauhaus Brand Collective concluido.

---

## Regras Absolutas

1. NUNCA pule um gate de aprovacao
2. NUNCA avance uma fase sem o artefato correspondente escrito
3. SEMPRE apresente o artefato ANTES de perguntar pela aprovacao
4. A pergunta padrao de gate: "Deseja: 1) Aprovar e avancar 2) Editar 3) Refazer esta fase"
5. Edicoes geram V2 do documento — NUNCA sobrescrevam silenciosamente
6. Cada agente le os artefatos das fases anteriores antes de produzir os seus
7. O handoff entre fases e documentado em `docs/brand/handoffs/`
