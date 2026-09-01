# vls-digital-governance

**Status desta pasta**: preparada em 25/08/2026 como staging local; promovida ao GitHub em 01/09/2026 como primeiro commit do repositório `VLS-Interno/vls-digital-governance` (decisão de conta canônica: manter em `VLS-Interno`, não `VLS-Constutora-TI`).

## Comece por aqui

1. [`CONTRATO_GOVERNANCA_V1.md`](./CONTRATO_GOVERNANCA_V1.md) — **VIGENTE** (aprovado 25/08/2026). É a constituição deste repositório: princípio fundamental, arquitetura de repositórios (Modelo C), split GitHub×Drive, ciclo de vida documental. Leia isso antes de mexer em qualquer pasta abaixo.
2. `01-estado-atual/` — quando existir, `ESTADO_OFICIAL_V1.md` é o índice do estado real do sistema. Hoje esse documento ainda está em rascunho (ver Fase 0, artifact separado) — a promoção dele é uma decisão distinta da promoção deste contrato.

## Regra de ouro (resumo do contrato — não substitui a leitura completa)

- O sistema real (Supabase, n8n, Meta, CRM implantado) é sempre a fonte de verdade sobre seu próprio estado — nunca um documento aqui.
- Nenhuma pasta aqui duplica documentação interna dos repos de código (`CRM-VLS`, `Cat-logo-Mestre-de-Templates`) — só cita por commit SHA.
- Um documento só vale como norma quando VIGENTE (aprovação explícita do usuário) — rascunho não tem autoridade, mesmo sendo mais recente.

## Estrutura de pastas

| Pasta | Finalidade |
|---|---|
| `01-estado-atual/` | Índice confiável do estado vigente do sistema |
| `02-arquitetura/` | Diagrama e topologia real (confirmada, não desejada) |
| `03-decisoes/` | ADRs — uma decisão por arquivo |
| `04-isis/` | Estado real do prompt/persona/modelo da Isis |
| `05-funil-comercial/` | Vocabulário e estado real do funil |
| `06-memoria/` | Estado da memória comercial estruturada |
| `07-agendamento/` | Fluxo real de agendamento |
| `08-reengajamento/` | Estado dos mecanismos de reengajamento |
| `09-corretor/` | Estado de atribuição e handoff Isis↔corretor |
| `10-crm/` | Estado real do Lead Cockpit (integração de sistema, não código interno) |
| `11-whatsapp/` | Estado de templates e mensageria |
| `12-meta/` | Estado de contas e campanhas Meta Ads |
| `13-supabase/` | Inventário confirmado de schema/RLS/funções |
| `14-n8n/` | Inventário confirmado de workflows |
| `15-auditorias/` | Resumos versionados de rodadas de auditoria (relatório bruto fica no Drive, linkado daqui) |
| `16-backlog/` | Índice de itens abertos/fechados (consolidação de `BACKLOG-VLS` — pendente de decisão) |
| `17-runbooks/` | Procedimentos operacionais testados |
| `18-catalogos/` | Referência ao catálogo mestre (fonte real: repo `Cat-logo-Mestre-de-Templates`) |
| `19-evidencias/` | Anexos de auditoria, organizados por subpasta de data |

Especificação completa de cada pasta (conteúdo permitido/proibido, fonte de dados, responsável, frequência de revisão): ver o artifact da Fase 0.1 ("Fase 0.1 — Proposta de Governança"), ainda não copiado para dentro deste repositório para evitar duplicação — cada pasta abaixo tem um `README.md` curto com a finalidade e um lembrete de onde está a especificação completa.
