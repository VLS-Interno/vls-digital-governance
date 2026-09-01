---
documento: CONTRATO DE GOVERNANÇA VLS DIGITAL V1
status: VIGENTE (promovido ao GitHub em 01/09/2026 — VLS-Interno/vls-digital-governance)
data_producao: 2026-08-25
data_promocao: 2026-08-25 (VIGENTE local); 2026-09-01 (promoção formal ao GitHub)
promovido_a_vigente: sim — aprovação explícita do usuário ("pode promover esse contrato como vigente"), registrada em memória de projeto
supersedes: nenhum (é o primeiro)
evidência_histórica_da_decisão: Fase 0 (reconciliação), Fase 0.1 (proposta de estrutura), Fase 0.2 (fechamento de arquitetura/Drive/critério de oficial), Mapa Organizacional GitHub (31/08, decisão de conta canônica) — não repetidas aqui, só referenciadas
---

# Contrato de Governança VLS Digital V1

**Status: VIGENTE**, promovido ao GitHub em 01/09/2026 (`VLS-Interno/vls-digital-governance`, primeiro commit deste repositório). Aprovado pelo usuário em 25/08/2026; a autoridade normativa deste documento, pelas suas próprias regras (Seção 1), agora está completa — não é mais só a versão vigente por decisão do usuário mantida localmente, é o registro promovido.

*Nota: a Seção 4 do brief chegou cortada de novo, terminando em "SUPERSEDED" sem fechar o diagrama. Completei o ciclo com o estado que faltava (EVIDÊNCIA BRUTA, que não entra na cadeia linear) e a leitura de "só 1 vigente por escopo" — avise se havia mais seções planejadas.*

Este é o documento normativo curto que continua valendo depois que a governança entrar em operação. As Fases 0/0.1/0.2 são a evidência histórica de como se chegou a estas regras — não são repetidas aqui.

---

## 1. Princípio fundamental

> **O sistema real é a fonte de verdade sobre o próprio estado. GitHub é a fonte de verdade sobre governança e documentação normativa promovida. Drive é ambiente de trabalho e evidência — nunca autoridade normativa.**

| Sistema | É fonte de verdade sobre |
|---|---|
| Supabase | Estado do banco (schema, dados, RLS) |
| n8n | Workflows ativos/publicados e suas execuções reais |
| Meta | Contas, campanhas, templates — status real da plataforma |
| CRM (implantado) | Comportamento efetivamente em uso |
| GitHub | Governança e documentação normativa **já promovida** |
| Drive | Rascunhos, documentos operacionais, evidência bruta |

Nenhum documento — em GitHub ou Drive — é fonte de verdade sobre o estado de um sistema real. Documento descreve estado; não o é. Onde documento e sistema divergirem, o sistema vence, e a divergência vira uma linha de reconciliação (não é resolvida silenciosamente a favor do documento).

---

## 2. Arquitetura dos repositórios — Modelo C, definitivo

- **Código com repositório próprio permanece nele**: `CRM-VLS`, `Cat-logo-Mestre-de-Templates`.
- **Estado cross-plataforma (sem código próprio) vive em `vls-digital-governance`**: Isis, funil, memória comercial, agendamento, reengajamento, corretor, WhatsApp, Meta, inventário de schema Supabase, inventário de workflows n8n, ADRs, Estado Oficial.
- `vls-digital-governance` **cita, nunca duplica**: toda referência a código de outro repo usa `<repo> @ <commit-sha>` — nunca `main`, `atual` ou `última versão`.
- Documentação interna de um repo de código (como o próprio CRM funciona por dentro) fica só nele. Documentação de como esse repo se encaixa no sistema (integrações, quem chama, o que ele chama) fica só na governança. Nunca as duas coisas nos dois lugares.

---

## 3. GitHub × Drive — tabela definitiva

| Conteúdo | GitHub | Drive | Autoridade |
|---|:---:|:---:|---|
| Estado Oficial | ✔ | rascunho antes da promoção | GitHub, só após promoção (Seção 6) |
| ADR | ✔ | rascunho antes da promoção | GitHub, só após promoção |
| Arquitetura (real, confirmada) | ✔ | rascunho antes da promoção | GitHub, só após promoção |
| Prompt real da Isis (espelho) | ✔ | — | GitHub — mas o prompt **em si** só tem autoridade dentro do n8n (Seção 1); o espelho é registro, não a fonte |
| Backlog | ✔ (recomendado) | — | GitHub, se a consolidação recomendada na Fase 0.2 for aprovada |
| Runbooks | ✔ | rascunho antes da promoção | GitHub, só após promoção |
| Catálogo (templates) | ✔ | — | GitHub — padrão já em uso |
| Contratos | — | ✔ | Drive, sempre |
| PDFs | — | ✔ | Drive, sempre |
| Planilhas | — | ✔ | Drive, sempre |
| Apresentações | — | ✔ | Drive, sempre |
| Evidências / screenshots / dumps | — | ✔ | Drive, sempre — imutáveis, nunca normativos |
| Rascunhos (de qualquer documento normativo) | — | ✔ | **Nenhuma**, mesmo que textualmente mais recente que o VIGENTE |

> **Regra central**: um rascunho no Drive pode ser mais novo cronologicamente, mas nunca é mais novo em autoridade. Autoridade só nasce no ato de promoção (Seção 6).

---

## 4. Ciclo de vida documental

```text
RASCUNHO
    ↓
AGUARDANDO_APROVAÇÃO
    ↓
APROVADO
    ↓
VIGENTE ────────────▶ (nova versão aprovada) ────▶ SUPERSEDED
                                                    (permanece no histórico,
                                                     nunca apagado, com
                                                     marcador explícito
                                                     no próprio arquivo)
```

Regras da cadeia:
- Só existe **1 documento VIGENTE por escopo**, a qualquer momento.
- **EVIDÊNCIA BRUTA** não entra nesta cadeia — nasce e morre imutável no Drive, nunca é promovida, nunca é normativa.
- A transição para SUPERSEDED acontece **no mesmo commit** em que a nova versão vira VIGENTE — nunca em dois momentos separados.

---

## 5. Relação entre Estado Oficial, auditoria, ADR e backlog

- **Auditoria** produz evidência e achados — nunca é, ela mesma, o Estado Oficial. Um resumo de auditoria pode virar insumo para uma nova versão do Estado Oficial, mas só via o ciclo da Seção 4.
- **ADR** registra uma decisão já tomada — não substitui o Estado Oficial, é referenciado por ele quando a decisão mudou a arquitetura real.
- **Backlog** rastreia itens abertos/fechados — é atualizado no mesmo turno em que qualquer item muda de estado (regra já vigente no projeto), independente do ciclo de promoção do Estado Oficial.
- **Vocabulário de estado** (10 tags: VERIFIED LIVE / — PARTIAL / BROKEN / CONFIGURED, DOCUMENTED ONLY, PLANNED, STALE DOCUMENTATION, DIVERGENT, ABSENT, UNKNOWN) e o **contrato de atualização** (regras 1-8) definidos na Fase 0.1 continuam valendo integralmente e não são repetidos aqui — são parte deste contrato por referência, não por cópia.

---

## 6. Este próprio documento

Por aplicação direta da Seção 4 a si mesmo: este contrato foi promovido a **VIGENTE** em 25/08/2026, por aprovação explícita do usuário ("pode promover esse contrato como vigente" — mesma régua do estágio 7 do `vls-method`, não inferida de "continue" ou silêncio). A partir de agora ele passa a valer como norma, não como proposta, para qualquer trabalho de governança neste projeto.

**Promoção ao GitHub concluída em 01/09/2026.** Depois de decidida a conta canônica (manter em `VLS-Interno`, não migrar para `VLS-Constutora-TI` — ver Mapa Organizacional GitHub, 31/08), este documento e a estrutura de pastas da Seção 2/Fase 0.1 foram commitados e enviados como primeiro commit de `VLS-Interno/vls-digital-governance`. O repositório existia como casco vazio desde antes de 25/08; este é o commit que o popula pela primeira vez.
