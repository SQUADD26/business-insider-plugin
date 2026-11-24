---
name: business-insider
description: Usa quando lavori su Business Insider per un cliente Squadd con l'MCP business-insider - caricare un PDF, Word o testo dal computer, salvare la trascrizione di una call di Fathom, cercare o leggere l'archivio di un'organizzazione, creare o spostare cartelle e documenti, fare una domanda alla chat del cliente.
---

# Business Insider per i tecnici Squadd

Gli strumenti stanno nel server MCP `business-insider` (produzione) o `business-insider-dev` (sviluppo). Al primo uso Claude apre il browser: entra con l'account di Business Insider e premi «Consenti». Lo staff Squadd lavora su tutte le organizzazioni clienti, gli altri solo sulle proprie. Se gli strumenti rispondono 401, scrivi `/mcp` e scegli «Authenticate».

## Prima di tutto: l'organizzazione

Ogni strumento dell'archivio vuole `org`, l'id dell'organizzazione. Trovalo con `organizzazioni` e `cerca` (parte del nome). Se escono più organizzazioni, chiedi all'utente quale; non indovinare. Salva nel Condiviso (`section: "shared"`), che vedono tutti i membri del cliente, salvo richiesta diversa.

## Caricare un file dal computer

PDF, Word (.docx), testo o Markdown, fino a 50 MB. Il file non passa nel messaggio: va caricato con curl.

1. `carica_file` con `org`, `name` (col suffisso, es. `Listino 2026.pdf`), `size` in byte (`stat -c %s <file>` su Linux, `stat -f %z <file>` su Mac), `section` e, se serve, `parentId`. Risponde con `uploadId` e il `comando` curl già pronto.
2. Lancia il comando col percorso vero del file. Deve stampare 200.
3. `conferma_file` con `org` e `id` = `uploadId`: solo ora il file compare nell'archivio.
4. La lettura del testo parte da sola e dura da pochi secondi a qualche minuto. `stato_file` dice a che punto è (`readStatus: "read"`); prima non si trova con `cerca` per il testo.

Più file: un giro per file. Se `conferma_file` dice che il file non è arrivato, rilancia curl e riconferma.

## Salvare la trascrizione di una call di Fathom

1. Con l'MCP di Fathom trova la call e prendi trascrizione e riassunto (`get_meeting_transcript`, `get_meeting_summary`).
2. `crea_trascrizione` con `org`, `title` (es. `Call con Rossi, 24 novembre 2026`), `date` (istante ISO), `participants`, `source: "Fathom"`, `url` della registrazione, `section` e `markdown`: prima il riassunto, poi la trascrizione intera, una riga per intervento (`**Nome** (mm:ss): frase`).

Non riassumere al posto della trascrizione: salvala intera, è la fonte che la chat del cliente userà.

## Cercare, leggere, ordinare

- `archivio`: cartelle, documenti, mappe e file (filtri `section`, `type`, `parentId`).
- `cerca`: parole in nomi e testo di documenti, mappe e file letti, con l'estratto.
- `leggi_voce`, `leggi_contenuto` (i blocchi di un documento), `stato_file`, `scarica_file` (link firmato).
- `crea_voce` (una cartella: `type: "folder"`), `crea_documento` (da Markdown), `sposta` (anche per rinominare).
- `chiedi` con `wait: true`: una domanda alla chat dell'organizzazione, che risponde con l'archivio del cliente. Scala il credito del cliente.

## Dove non c'è la shell

In claude.ai e Claude Desktop (connettore `https://businessinsider.squaddcrm.com/mcp`) tutto funziona tranne il caricamento di un file dal computer, che chiede curl. Lì si porta il contenuto come documento con `crea_documento`.
