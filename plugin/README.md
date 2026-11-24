# Business Insider in Claude: istruzioni per i tecnici

1. In Claude Code: `/plugin marketplace add SQUADD26/business-insider-plugin`, poi `/plugin install business-insider@squadd`.
2. Riavvia Claude Code, scrivi `/mcp`, scegli `business-insider` e «Authenticate».
3. Nel browser entra con il tuo account di Business Insider e premi «Consenti». Lo staff Squadd lavora su tutte le organizzazioni, gli altri sulle proprie.
4. Chiedi a Claude, per esempio: «Carica ~/Downloads/listino.pdf nell'organizzazione Studio Rossi» o «Salva in Studio Rossi la trascrizione Fathom della call di ieri».
5. In claude.ai o Claude Desktop: Impostazioni → Connettori → Aggiungi connettore personalizzato, indirizzo `https://businessinsider.squaddcrm.com/mcp`. Lì funziona tutto tranne il caricamento di file dal computer.

Sul dev: server `business-insider-dev` (`https://businessinsider-dev.squaddcrm.com/mcp`).
