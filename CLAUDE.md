# CLAUDE.md — Business Insider plugin

## 1. Chi sei e cosa devi ottenere

Questa repo è la copia pubblica del plugin Claude Code di Business Insider (marketplace `squadd`): è quella che i tecnici installano. Deve contenere sempre lo stesso plugin dell'originale.

L'originale sta nella repo `SQUADD26/business-insider`: cartella `plugin/` e `.claude-plugin/marketplace.json`. Qui non si scrive niente di nuovo.

## 2. Lavoro buono e lavoro cattivo

Buono: una PR che porta qui, identico, il cambio già unito in `business-insider/plugin/` (per esempio «Skill: tutti gli strumenti dell'MCP», #1).

Cattivo: modificare qui `plugin/` o `marketplace.json` senza averli cambiati prima nell'originale. Alla prossima copia la modifica si perde e le due versioni divergono.

## 3. Procedure

Nessuna skill di progetto. Unica procedura: allineare la copia all'originale.
1. Cambia e unisci prima `plugin/` (o `marketplace.json`) in `business-insider`.
2. Copia qui gli stessi file (`plugin/.claude-plugin/plugin.json`, `plugin/.mcp.json`, `plugin/README.md`, `plugin/skills/business-insider/SKILL.md`, `.claude-plugin/marketplace.json`).
3. Apri una PR verso `main`.
Differenze volute: nel `README.md` dell'originale c'è un commento in testa che rimanda a questa repo; il `README.md` della radice di questa repo è solo di questa copia.

## 4. Materiali

- `plugin/.mcp.json`: gli indirizzi dell'MCP (produzione e dev).
- `plugin/skills/business-insider/SKILL.md`: la skill d'uso degli strumenti.
- `plugin/README.md`: istruzioni per i tecnici. L'ADR che spiega come è fatto l'MCP è `docs/adr/0020` in `business-insider`.

## 5. Strumenti

- Nessun build, nessun test, nessun workflow.
- Installazione per provare: `claude plugin marketplace add SQUADD26/business-insider-plugin`, poi `claude plugin install business-insider@squadd`.
- Consegna: branch, PR verso `main`, unione.
