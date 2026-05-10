---
name: brandautopilot
description: |
  Executa o pipeline Bauhaus Brand Collective de forma autonoma end-to-end, sem interrupcoes para
  aprovacao em cada fase. Use quando o usuario quer "autopilot total" ou criacao rapida de marca.
  Ideal para MVPs, marcas pessoais ou prototipacao de identidade.

  Triggers: "autopilot:", "faz a marca toda", "modo autopilot", "cria tudo sozinho", "/brandautopilot".
argument-hint: "<descricao da marca ou negocio>"
allowed-tools: [Read, Write, Edit, Glob, Grep, Bash, WebSearch, WebFetch, Agent]
---

# BrandAutopilot — Execucao Autonoma

Execute o pipeline Bauhaus Brand Collective de forma autonoma. Informe progresso a cada fase concluida,
mas nao pare para aguardar aprovacoes — exceto a aprovacao final do Brand Book (sempre confirma).

## Roteamento por Modelo

| Fase | Agente | Modelo | Justificativa |
|------|--------|--------|---------------|
| Discovery | kandinsky | Sonnet | Conversacional |
| Pesquisa | moholy | Sonnet | Busca e sintese |
| Visual Identity | klee | Sonnet | Conceituacao criativa |
| Typography & Color | bayer | Sonnet | Sistema tecnico |
| Voice & Copy | itten | Sonnet | Geracao textual |
| Brand Book | breuer | Sonnet | Consolidacao |

## Protocolo de Execucao Autonoma

### 1. Detectar Estado Inicial
- Se `docs/brand/PROGRESS.md` existe com pipeline incompleto → retomar da ultima fase
- Se nao existe → iniciar pipeline do zero

### 2. Skip Logic (Artefatos Existentes)
Antes de executar cada fase, verifique se o artefato ja existe:
- `brand-strategy.md` existe e valido? → skip fase 0
- `research-brief.md` existe e valido? → skip fase 1
- `visual-identity.md` existe e valido? → skip fase 2
- `typography-spec.md` + `color-system.md` existem? → skip fase 3
- `voice-guide.md` existe e valido? → skip fase 4

### 3. Execucao por Fase

**Fase 0+1 (Discovery + Pesquisa):**
- Kandinsky faz discovery com base no input do usuario (sem perguntas — usa input como contexto)
- Moholy executa pesquisa web em paralelo
- Produz: brand-strategy.md + research-brief.md + moodboard.md
- Atualiza PROGRESS.md
- Informa: "✅ Fase 0+1 concluida: estrategia e pesquisa realizadas"

**Fase 2 (Identidade Visual):**
- Klee recebe estrategia + moodboard, escolhe a direcao mais alinhada
- Produz: visual-identity.md + logo-spec.md
- Atualiza PROGRESS.md
- Informa: "✅ Fase 2 concluida: identidade visual definida"

**Fase 3 (Tipografia & Cores):**
- Bayer recebe visual identity, define sistema tipografico e cromatico
- Produz: typography-spec.md + color-system.md
- Atualiza PROGRESS.md
- Informa: "✅ Fase 3 concluida: tipografia e cores definidas"

**Fase 4 (Tom de Voz):**
- Itten recebe estrategia + sistema visual, define voz e gera exemplos
- Produz: voice-guide.md + copy-samples.md
- Atualiza PROGRESS.md
- Informa: "✅ Fase 4 concluida: tom de voz e copy definidos"

**Fase 5 (Brand Book):**
- Breuer consolida TUDO em BRAND-BOOK.md com QA de consistencia
- Se encontrar inconsistencias → corrige autonomamente e registra
- Produz: BRAND-BOOK.md
- Atualiza PROGRESS.md
- Informa: "✅ Fase 5 concluida: Brand Book montado"

**Aprovacao Final:**
- **SEMPRE confirma antes de declarar entrega**, mesmo no autopilot:
  > "Brand Book completo. Aqui esta o resultado final: [resumo]. Aprova a entrega?"
- Apos confirmacao: Gropius gera FINAL_REPORT.md
- Declara: ✅ ENTREGA APROVADA — Bauhaus Brand Collective Autopilot concluido.

### 4. Maximo de Tentativas por Fase
- Cada fase tem maximo 3 tentativas antes de reportar ao usuario
- Se pesquisa web falha → tenta fontes alternativas
- Se inconsistencia detectada → tenta resolucao automatica

### 5. Log de Estado Central
Mantenha `docs/brand/autopilot-state.md` com:
```markdown
# Autopilot State
**Iniciado:** [timestamp]
**Fase atual:** [N]
**Tentativas fase atual:** [N]

## Log de execucao
- [timestamp] Fase 0: iniciada
- [timestamp] Fase 0: concluida ✅
- [timestamp] Fase 1: iniciada
...
```
