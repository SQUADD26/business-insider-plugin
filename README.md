# Business Insider: plugin per Claude Code

Copia pubblica del plugin dei tecnici di Business Insider (l'originale è nel repo privato di Squadd). L'accesso ai dati passa dal login dell'MCP: senza un account di Business Insider il plugin non apre niente.

```
claude plugin marketplace add SQUADD26/business-insider-plugin
claude plugin install business-insider@squadd
```

Poi riavvia Claude Code, scrivi `/mcp`, scegli `business-insider` e «Authenticate». Istruzioni complete: [plugin/README.md](plugin/README.md).
