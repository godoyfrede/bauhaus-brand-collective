---
name: brandloop
description: |
  Loop de verificacao e correcao de consistencia de marca. Use quando o brand book precisa
  de revisoes iterativas: inconsistencias entre fases, ajustes de paleta, refinamento de tom
  de voz. Executa verify→fix→verify em loop com escalacao inteligente.

  Triggers: "verifica a consistencia", "ajusta a marca", "loop de correcao", "refina o brand book",
  "fica em loop ate ficar consistente", "/brandloop".
argument-hint: "<tarefa e criterio de conclusao>"
allowed-tools: [Read, Write, Edit, Glob, Grep, Bash, WebSearch, WebFetch, Agent]
---

# BrandLoop — Loop Verify-Fix de Consistencia

Execute um loop de verificacao e correcao de consistencia da marca ate que todos os criterios
sejam atendidos ou o limite de seguranca seja atingido.

## Protocolo de Loop

### Inicializacao
1. Defina o **criterio de conclusao** (ex: "todas as cores com contraste WCAG AA", "tom de voz alinhado com arquetipos", "brand book completo e consistente")
2. Leia todos os artefatos em `docs/brand/`
3. Execute verificacao inicial e registre o estado base
4. Inicie o loop

### Loop Principal

```
ITERACAO N:
  1. Verificar estado atual dos artefatos
  2. Se CONSISTENTE → declarar sucesso e encerrar
  3. Se INCONSISTENTE → diagnosticar qual artefato e o problema
  4. Aplicar correcao (menor alteracao possivel)
  5. Verificar novamente
  6. Registrar resultado da iteracao
  7. Avancar para N+1
```

### Checklist de Verificacao

**Consistencia Visual:**
- [ ] Cores do color-system.md referenciadas corretamente no visual-identity.md
- [ ] Fontes do typography-spec.md complementam o logo (logo-spec.md)
- [ ] Estilo fotografico coerente com paleta de cores
- [ ] Todos os contrastes WCAG AA verificados

**Consistencia Estrategica:**
- [ ] Tom de voz (voice-guide.md) reflete arquetipos (brand-strategy.md)
- [ ] Tagline (copy-samples.md) alinhada com posicionamento
- [ ] Personalidade visual coerente com personalidade verbal
- [ ] UVP presente e consistente em todos os documentos

**Completude:**
- [ ] Todos os 9 artefatos obrigatorios existem
- [ ] Todas as secoes dentro de cada artefato estao preenchidas
- [ ] BRAND-BOOK.md reflete a versao mais recente de cada artefato
- [ ] Nenhuma referencia a "a definir" ou "[placeholder]"

### Escalacao Inteligente

**Apos 3 falhas com a MESMA inconsistencia:**
- Pesquisar via WebSearch boas praticas para o ponto especifico
- Mudar abordagem de correcao
- Registrar: "Abordagem A falhou 3x. Tentando abordagem B baseada em [fonte]"

**Apos 3 falhas com ABORDAGENS DIFERENTES:**
- Pausar imediatamente
- Reportar ao usuario: o que foi tentado, o que falhou, o que precisa de decisao humana

**Limite absoluto: 10 iteracoes**
- Se nao concluido apos 10 iteracoes → pausar e reportar situacao completa

### Padroes de Erro com Escalacao Imediata
Os seguintes problemas NAO entram em loop — escalacao imediata para o usuario:
- Contradicao entre posicionamento e identidade visual (decisao estrategica)
- Usuario nao aprovou uma fase que depende de outra
- Artefato obrigatorio completamente ausente
- Conflito entre instrucoes do usuario em fases diferentes

### Formato de Relatorio por Iteracao

```
Iteracao N/10:
- Verificado: [o que foi checado]
- Resultado: ✅ CONSISTENTE / ❌ INCONSISTENTE
- Problema: [descricao]
- Correcao: [o que foi alterado e em qual arquivo]
- Proximo: [o que sera verificado]
```

### Relatorio Final

```markdown
# BrandLoop — Relatorio Final

**Status:** CONSISTENTE ✅ / BLOQUEADO ❌
**Iteracoes:** N/10
**Criterio atingido:** [sim/nao]

## Correcoes Aplicadas
1. [Artefato]: [o que foi corrigido]
2. ...

## Estado Final
- Visual: [consistente/inconsistente]
- Estrategico: [consistente/inconsistente]
- Completude: [completo/incompleto]

[Se BLOQUEADO:]
Para desbloquear: [o que precisa de decisao humana]
```
