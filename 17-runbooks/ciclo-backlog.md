# Runbook — Ciclo de vida do backlog VLS

**Status: procedimento testado e confirmado** — não é proposta teórica. Rodou de ponta a ponta entre 28/08 e 01/09/2026 (Auditoria → Triagem → Gate → reconciliação → saneamento de 98 itens), com resultado real aplicado ao `Backlog Executivo Consolidado — Julho 2026.md` e a este repositório. Promovido em 01/09/2026 (Fase 10 do saneamento do backlog).

## Princípio central

> Backlog ativo = só trabalho que ainda exige ação. Concluído sai; histórico e futuro nunca são apagados, só relocados com referência.

O problema que este runbook evita: cada auditoria nova acrescentando itens sem nunca retirar os antigos transforma o backlog num cemitério de descobertas em vez de uma lista operacional — foi exatamente o que aconteceu entre 26/07 e 27/08 (Seção 2 do Backlog Executivo abandonada por 19 dias, itens fechados retidos em até 3 lugares do mesmo documento).

## O ciclo

```
INVESTIGAÇÃO / AUDITORIA
        ↓
ACHADO
        ↓
TRIAGEM                    ← agrupa por frente, decide destino
        ↓ (5 destinos possíveis)
DECISÃO (quando necessária)
        ↓
GATE DE ADMISSÃO           ← 4 perguntas: problema confirmado? decisão
        ↓                     necessária? implementação clara? validação possível?
AÇÃO / EXECUÇÃO
        ↓
HOMOLOGAÇÃO / VALIDAÇÃO FUNCIONAL   ← nunca pular esta etapa
        ↓
CONCLUÍDO
        ↓
HISTÓRICO                  ← nunca apagado, sempre com referência
```

## Regra de suficiência de evidência (o eixo que evita fechamento prematuro)

"Código/config confirmado presente" (git log, definição lida, node lido) prova que algo foi **publicado**, não que **funciona com uso real**. Só fecha como `CONCLUÍDO`:
- Execução real repetida (ex.: 2+ execuções sem perda)
- Contagem/tráfego crescendo de forma verificável
- Ausência confirmada de incidente por uma janela definida
- Constraint de banco autoaplicada (ex.: UNIQUE index — o motor garante, não precisa de tráfego para provar)
- Operação única com contagem final verificada (ex.: backfill)

**Não é suficiente sozinho**: "commit confirmado", "código presente", "config lida". Fica `AGUARDANDO_VALIDAÇÃO`.

**Regra de aplicação simétrica** (achado real desta sessão, 01/09): a regra vale nos dois sentidos — rebaixar um item quando a evidência é fraca, mas também **promover** um item quando a evidência ficou mais forte que da última vez. Aplicar só numa direção é viés, não conservadorismo.

## Os 8 estados

| Estado | Ativo? | Critério de saída |
|---|---|---|
| Aberto | Sim | Início de implementação ou bloqueio/decisão identificados |
| Aguardando decisão | Sim | Decisão registrada |
| Bloqueado | Sim | Dependência resolvida |
| Em andamento | Sim | Publicado |
| Aguardando validação | Sim | Evidência operacional real observada |
| Concluído | Não | — |
| Cancelado / Superseded | Não | — |
| Futuro | Não (índice separado) | Nova rodada de triagem decide reativar |

## Regra contra duplicação (achado real: colisão de ID F3/F6/F7/F9/F10/F11 entre Review Pipeline e ressalvas Isis V2, 01/09)

Antes de criar item novo:
```
ACHADO NOVO
   ↓
Existe item ativo (Seção 8 do Backlog Executivo)?
   SIM → atualiza o existente
   NÃO ↓
Existe no histórico (16-backlog/historico.md)?
   SIM → verificar se é reabertura, não item novo
   NÃO ↓
Existe em futuro (16-backlog/futuro.md)?
   SIM → reavaliar, não duplicar
   NÃO → só então, criar item novo
```
Nenhum ID novo reaproveita um prefixo de letra já em uso por outra família sem sufixo de domínio.

## Regra de reabertura

```
HISTÓRICO (linha preservada, nunca apagada)
   ↓
REABERTURA — cria item novo com campo reaberto_de: [id histórico original]
   ↓
BACKLOG_ATIVO
```
Nunca duas linhas de histórico com o mesmo fato; nunca a linha histórica reescrita.

## Onde cada coisa vive

| O quê | Onde | Fonte de verdade? |
|---|---|---|
| Backlog ativo | `Backlog Executivo Consolidado — Julho 2026.md` (Drive), Seção 8 | Sim (GOV-2, 30/08/2026) |
| Histórico | `16-backlog/historico.md` (este repositório) | Índice — narrativa completa fica na origem |
| Futuro | `16-backlog/futuro.md` (este repositório) | Índice |
| Fila de investigação (`NAO_CONFIRMADO`) | Seção 8 do Backlog Executivo, sem estado definitivo | — até confirmação |
| Evidência bruta | Memória de projeto / investigação original | Sim, sobre o fato pontual |

## Precedente que fundamenta este runbook

Sessão de 01/09/2026: `Mapa Organizacional GitHub VLS` → `Ciclo de Vida do Backlog VLS` → `Saneamento do Backlog VLS` (98 itens reconciliados, revisados por 2ª opinião independente que corrigiu 5 erros reais antes da aplicação) → Fases 1-9 executadas com gates explícitos (READ-ONLY → proposta → aprovação → execução), cada write verificada ao vivo pós-escrita, nunca só pela mensagem de sucesso da ferramenta. Ver memória de projeto `project_vls_saneamento_backlog_98itens_01set` e `project_vls_decisoes_travas_d1_d4_01set` para o registro completo.
