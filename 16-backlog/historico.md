# Histórico — itens concluídos, superseded, cancelados e duplicados

Promovido em 01/09/2026 (Fase 6 do saneamento do backlog). Índice compacto — a narrativa completa de cada item permanece na origem (memória de projeto, investigação), citada por link/data, nunca duplicada aqui (Contrato de Governança V1, §2, "cita, nunca duplica").

Campos: `id` · `título` · `origem` (investigação/auditoria que gerou) · `decisão_associada` · `implementação` (commit/versionId) · `data_conclusão` · `evidência_conclusão` (prefixo `MÉTRICA:` = evidência operacional real, `CÓDIGO:` = config/código confirmado presente) · `motivo` (quando cancelado/superseded) · `substituído_por`.

## Concluídos

| ID | Título | Origem | Decisão associada | Implementação | Data conclusão | Evidência | Motivo | Substituído por |
|---|---|---|---|---|---|---|---|---|
| S1-B | RLS sem policy UPDATE anon (`lead_sessions`) | Auditoria 28/08, §3 "dívida fantasma" | — | — | 01/09/2026 | MÉTRICA: RLS ativo, zero policies de escrita (VERIFIED LIVE) | Causa raiz real identificada (ausência de policy, não % de nodes migrados) | — |
| R12 | Extração do reengajamento p/ workflow dedicado | Achado 10/08, corte 13/08 | — | `TkASmZ2CDSC8NO7I` | 19/08/2026 | MÉTRICA: 3 ciclos de tráfego real limpo, zero perda | — | — |
| R14 | Dupla mensagem de reengajamento no mesmo ciclo | Sync pontual 20/08 | — | guarda de 3 dias, `fn_sessao_e_cordoba()` | 23/08/2026 | MÉTRICA: self-join, zero pares duplicados em 72h | — | — |
| L11 | Gate de nome bloqueia 87% da base (caminho WhatsApp) | Achado 09/08 | — | `fn_confirmar_reuniao_video` | 14/08/2026 | MÉTRICA: backfill sustentado, NULL em só 47/788 (~6%) (Auditoria 28/08) | — | — |
| L12 | Backfill dos leads não cobertos por L11 | Achado 09/08 | — | Opção C, 607 leads promovidos | 15/08/2026 | MÉTRICA: 0 leads com nome ainda em risco | — | — |
| G2 | Validação path CRM-humano (`timeline_lead`) | Achado 20/08 | — | `usuario_id`/`origem_evento` | 20/08/2026 | MÉTRICA: 10 eventos reais confirmados, mais recente 20/08 22:38 UTC | — | — |
| F4 | Constraint UNIQUE (corretor,lead) ativo | Review Pipeline original, 31/07 | — | Índice já existia | 28/08/2026 (confirmado) | CÓDIGO: `pg_indexes` confirma existência — checar `indisvalid` antes de tratar como definitivo | Resolvido silenciosamente, nunca fechado no registro | — |
| Amnésia do corretor | `fn_finalizar_turno_pipeline` nunca gravava mensagem do corretor | Achado 20/08 (2ª opinião) | — | Fix + cap N=3/corretor + TTL 10min→6h | 20/08/2026 | MÉTRICA: texto real do corretor gravado pós-20/08, dados reais confirmados | — | — |
| I7 | Missão autônoma Isis (telemetria, vigência de campanha etc.) | F0-F5 publicadas 18-19/08 | — | `isis_llm_usage`, `vw_campanhas_vigentes`, Regra 7 | 28/08/2026 (confirmação Auditoria) | MÉTRICA: 72 linhas, tráfego contínuo (medição mais recente que os "0 conversas" de 19/08) | — | — |
| I8 | Isis Confirmadora, liberação do piloto | Liberação 26/08 | — | Filtros hardcoded removidos, guarda `reuniaoNoFuturo()` | 28/08/2026 (confirmação Auditoria) | MÉTRICA: 0 crashes desde 26/08, execução real 40494 | — | — |
| MC-2 | Backfill histórico da memória comercial | 25/08 | — | Opção C, 1828 fatos | 25/08/2026 | MÉTRICA: contagem íntegra confirmada (191 determinísticos + 110 dossiês + 1518 LLM + 9 extração ao vivo) | — | — |
| MC-3 | Fase 2 Onda 1 (vocabulário 25→41 chaves) | 26/08 | — | `fn_ler_memoria_comercial` | 28/08/2026 (corrigido pela 2ª opinião — Auditoria já confirmava, reconciliação inicial tinha invertido) | MÉTRICA: 12/41 chaves em tráfego real de 3 dias | Cobertura das 29 chaves restantes é monitoramento, não bloqueio deste item | — |
| I1 | Nomenclatura "Isis V3"/"Epic 1" | Nota de reconciliação 27/08 | Gate, linha "🟡 Decisão" item 6 | — | 30/08/2026 | MÉTRICA: V3 absorve V2, já documentado desde 01/08 | Resíduo não bloqueante: estrutura de Epics não aparece no prompt real | — |
| GOV-2 | Qual versão do Backlog Executivo prevalece | Achado 25/08 | Gate, linha 169 | — | 30/08/2026 | Decisão registrada — Drive é oficial | Não cascateia para GOV-5 (aposentadoria de fato do repo), que segue sem decisão | — |
| PII-1 | Views/dashboard público expondo PII sem autenticação | Achado 20/08 (P0) | — | `security_invoker`, `REVOKE SELECT anon`, rota serverless `/api/data.js` | 21/08/2026 | MÉTRICA: replay real confirma chave antiga morta (`401 permission denied`) | — | — |
| GOV-1 | Criar repositório GitHub `vls-digital-governance` de fato + 1º commit | Achado 25/08 | Mapa Organizacional GitHub (31/08), decisão D1 (manter conta `VLS-Interno`) | Commits `4c991c4` + `0ce546c`, push manual do usuário | 01/09/2026 | MÉTRICA: confirmado ao vivo via `git ls-remote` — `refs/heads/master` bate com o commit local | — | — |
| GOV-3 | Confirmar relação `VLS-Constutora-TI` × `VLS-Interno` (mesma org? rename?) | Achado 25/08, Mapa Organizacional GitHub (31/08) | — | — | 01/09/2026 | MÉTRICA: navegador autenticado confirma redirect automático de `VLS-Constutora-TI/CRM-VLS` → `VLS-Interno/CRM-VLS`; listagem oficial de repos de `VLS-Constutora-TI` não inclui `CRM-VLS` nem `Cat-logo-Mestre-de-Templates` | 1 repositório, 1 dono atual (`VLS-Interno`), URL antiga preservada como redirect nativo do GitHub — não é ambiguidade real | — |

## Superseded / substituídos

| ID | Título | Origem | Implementação | Data conclusão | Evidência | Motivo | Substituído por |
|---|---|---|---|---|---|---|---|
| F5 | `feedbacks_corretor` acoplado a `encerrar=true` | Review Pipeline original | — | 20/08/2026 | Causa raiz original (amnésia do corretor) já corrigida em item próprio | Causa raiz original superada | **BL-02** |
| F8 | Retry inconsistente entre nodes | Review Pipeline original | — | 28/08/2026 (Auditoria) | Achado mais específico e grave no mesmo domínio | — | **BL-05** |
| E2 | Isis confirma antes de reservar slot | Achado 09/08 (ex-N2) | AGV-1, constraint nova | 22/08/2026 | Sintoma coberto pela constraint de AGV-1 | Causa comportamental raiz não reverificada — reabre se recorrer | **AGV-1** |
| SEC-1 | 6 RPCs SECURITY DEFINER sem guarda | Achado colateral de PII-1, 20/08 | `EXECUTE` revogado, guard `fn_require_auth_or_n8n()` | 21/08/2026 | MÉTRICA: validação real com `SET LOCAL ROLE anon` (preservar mesmo após superseded) | Recorte pequeno de iniciativa maior já concluída (O0-1, 20/07) | **O0-1 / SEC-2** |
| "reuniao_estado" duplicado | Achado de duplicação entre `reuniao_estado` (governado) e `reuniao_agendada`+`slots_agenda` | Achado 10/08, Triagem §7 | — | 01/09/2026 (fusão) | Mesma evidência de G7 | Registrado como 2 linhas do mesmo achado no backlog original | **G7** |

## Cancelados

| ID | Título | Origem | Data conclusão | Motivo |
|---|---|---|---|---|
| Botões interativos (gates de confirmação WhatsApp) | Proposta de botões interativos nos gates de confirmação | Proposta 27/08 | 27/08/2026 (tarde/noite) | Pausados a pedido do usuário após 2 reprovações de 2ª opinião — decisão de parar, não "aguardando nova rodada" |

## Duplicados

*(a única duplicata confirmada nesta rodada — "reuniao_estado" — já está listada em Superseded acima, por ter destino/substituto nomeado, não uma remoção pura.)*

---

**Fila de investigação/validação — não é histórico, não é futuro, não é backlog ativo.** 10 itens seguem `NAO_CONFIRMADO`, cada um com pendência específica registrada: `GOV-4` (promover Baseline 25/08 a Nível 1), `GOV-5` (aposentar `BACKLOG-VLS` de fato), `M1` (status Meta do teste 80km), `Spend cap "Ricardo Valese"` (P0, aguarda MCP com acesso à conta), `CAT-5` (família `followup_corretor_*` abandonada?), `E1` (Google Calendar idempotência), `TF-6 2º nó` (dual-write draft, motivo da edição de 28/08 desconhecido), `G1` (identificar os 2 gaps P2), `X3` (Instagram "Robson" hardcoded), `R4` (residuais Sheets Córdoba). Permanecem na Seção 8 do Backlog Executivo até confirmação. `GOV-3` saiu desta lista em 01/09/2026 — confirmado, ver Concluídos acima.
