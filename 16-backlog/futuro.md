# Futuro — itens válidos, deliberadamente fora do horizonte atual

Promovido em 01/09/2026 (Fase 5 do saneamento do backlog). Origem: reconciliação Auditoria (28/08) + Triagem (28/08) contra o `Backlog Executivo Consolidado — Julho 2026.md`, Seção 2.1.

**Regra**: um item aqui não volta ao backlog ativo automaticamente por tempo decorrido — só via uma nova rodada de triagem que reavalie o critério de reabertura.

| ID | Título | Motivo de não ser agora | Última triagem | Critério de reabertura |
|---|---|---|---|---|
| A2 | Tenant boundary ausente no schema | Sem driver de negócio há 5+ semanas (confirmado VERIFIED LIVE, 0 colunas de tenant em qualquer tabela) | 28/08/2026 | Decisão de produto sobre necessidade de multi-tenant |
| C1.5 | Instagram, atribuição `referral` a confirmar | Só relevante se atribuição de anúncio IG importar para o negócio | 09/08/2026 | Necessidade confirmada de medir atribuição de DM de IG |
| G4 | Manual message capability | Decisão de negócio, sem urgência nova | 26/07/2026 | Decisão explícita do usuário de priorizar |
| F10 / F11 / F15 | SSOT `dados_coletados`/`dados_pipeline`; view de objeções sempre vazia; Aggregate Root "Atendimento" (ADR-009) | Decisão de arquitetura já registrada, sem execução; F10/F11 só resolvem dentro de F15 | 31/07/2026 | Retomada do Review Pipeline "Onda 2" |
| I4 | `conhece_regiao` campo morto | 3/788 leads preenchidos, 0 leituras confirmadas | 26/07/2026 | Uso real do campo identificado |
| MC-5 | Confirmação progressiva ativa (Opção B) | Opção A (passiva) já em uso por decisão do usuário | 24/08/2026 | Reavaliação da Opção A após período de observação |
| CAT-1 | Reconciliar `whatsapp_templates` (Supabase) com templates reais na Meta | "Fase 5" de limpeza operacional nunca executada; repo de referência já saneado | 23/08/2026 | Ciclo de governança/catálogo dedicado |
| CAT-2 | Decidir conexão/aposentadoria dos 19 templates órfãos do funil de reunião | Zero uso desde a criação (03-12/07), nunca conectado a workflow | 23/08/2026 | Idem CAT-1 |
| CAT-3 | Corrigir `status_meta` de `realbiz_reforco_es_ar` | Achado revertido — expectativa de "aprovado" era falsa, precisa reverificar na Meta | 23/08/2026 | Idem CAT-1 |
| CAT-4 | Divergência de nomes `cobranca_feedback_corretor_*` + reclassificação Utilidade→Marketing | Baixa urgência, sem dano ativo confirmado | 23/08/2026 | Idem CAT-1 |

**Fora desta lista, de propósito**: `CAT-5` não entra aqui — é `NAO_CONFIRMADO`, não `FUTURO` (um item sem confirmação não pode ser chamado "válido, só não agora"). Permanece na fila de investigação/validação (ver `historico.md`, nota final, ou a Seção 8 do Backlog Executivo).
