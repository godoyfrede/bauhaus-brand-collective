<p align="center">
  <img src="assets/cover.png" alt="Bauhaus Brand Collective" width="600">
</p>

# Bauhaus Brand Collective

> 7 agentes Bauhaus especializados em criacao de marca: da estrategia ao Brand Book.

Pipeline multi-agente para [Claude Code](https://claude.ai/claude-code) com gates de aprovacao, pesquisa visual real e tom de voz fundamentado.

## Os 7 Agentes

| Agente | Referencia | Papel |
|--------|-----------|-------|
| **Gropius** | Walter Gropius | Orquestrador / Brand Director |
| **Kandinsky** | Wassily Kandinsky | Brand Strategist (Discovery + Posicionamento) |
| **Moholy** | Laszlo Moholy-Nagy | Pesquisador de Mercado & Referencias Visuais |
| **Klee** | Paul Klee | Visual Identity Designer |
| **Bayer** | Herbert Bayer | Typography & Color System |
| **Itten** | Johannes Itten | Voice & Copy Strategist |
| **Breuer** | Marcel Breuer | Brand Book Assembler + QA |

## Pipeline

```
Kandinsky (estrategia) → Moholy (pesquisa) → Klee (visual) → Bayer (tipo+cor) → Itten (voz) → Breuer (brand book)
```

Cada fase tem um gate de aprovacao. O usuario controla o ritmo.

## Skills

| Skill | Descricao |
|-------|-----------|
| `/brandteam` | Pipeline completo com gates de aprovacao |
| `/brandautopilot` | Execucao autonoma (para no Brand Book final) |
| `/brandloop` | Loop de verificacao/correcao de consistencia |

## Instalacao

```bash
claude plugins install .
```

Ou adicione manualmente ao `installed_plugins.json`:

```json
"bauhaus-brand-collective@bauhaus-brand-local": [
  {
    "scope": "user",
    "installPath": "<caminho-do-repo>",
    "version": "1.0.0"
  }
]
```

## Uso

```
/brandteam Quero criar uma marca para minha startup de educacao
```

Ou no modo autopilot:

```
/brandautopilot Marca premium de cafe artesanal chamada "Origem"
```

## Output

O pipeline produz `docs/brand/` com:

- `brand-strategy.md` — posicionamento, arquetipos, UVP
- `research-brief.md` — analise competitiva de marca
- `moodboard.md` — referencias visuais com URLs
- `visual-identity.md` — conceito do logo e sistema visual
- `logo-spec.md` — especificacoes tecnicas
- `typography-spec.md` — familias, escala, pareamento
- `color-system.md` — paleta com tokens e WCAG
- `voice-guide.md` — tom de voz e principios verbais
- `copy-samples.md` — exemplos de copy por canal
- **`BRAND-BOOK.md`** — documento final consolidado

## Autor

Criado por **Frederico Clemente** ([@godoyfrede](https://github.com/godoyfrede))

## Licenca

CC-BY-4.0
