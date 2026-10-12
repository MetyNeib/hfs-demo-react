# HFS Demo React

Demo Horeca Food Service realizzata con React, TypeScript e Vite. Include ordine manuale, FastOrder WhatsApp simulato, bozze e storico, schede clienti, catalogo e statistiche.

Questa e la versione React precedente alla migrazione Rails, corrispondente alla demo originale sulla porta 4173. Il codice applicativo proviene dal tag `v1.0.0-react` (commit `0e8d016dc4d15206fcca470a2a6301a332ac17fc`). Non contiene Amelia3 o le modifiche sperimentali per iOS 12.

Tutti i dati sono sintetici. Ordini, sincronizzazione, WhatsApp, email e PDF sono simulazioni; non vengono effettuati invii commerciali reali. Il seed approvato e conservato senza modifiche.

## Avvio

Richiede Node.js 22.12 o successivo e npm.

```sh
git clone https://github.com/MetyNeib/hfs-demo-react.git
cd hfs-demo-react
npm ci
npm run dev
```

Apri http://127.0.0.1:5173/#/. Su Windows PowerShell puoi usare `npm.cmd` al posto di `npm`.

## Build e anteprima

```sh
npm run build
npm run preview
```

Apri http://127.0.0.1:4173/#/. Le porte devono essere libere. La cartella `dist/` contiene la build statica: servirla tramite HTTP, senza aprire `index.html` direttamente dal filesystem.

Per una prova sulla rete locale:

```sh
npm run preview -- --host 0.0.0.0
```

Dal tablet sulla stessa rete apri `http://IP-DEL-PC:4173/#/`. L'accesso dipende anche dalle impostazioni di rete e firewall del computer.

## Dati e funzionamento

- Agente sintetico Marco Rossi, otto clienti assegnati.
- Orologio demo fisso al 22 settembre 2026.
- Un solo carrello condiviso tra ordine manuale e WhatsApp simulato.
- Stato salvato nel browser con la chiave `hfs-agent-demo-v1`.
- Il comando Reset demo ripristina il seed sintetico iniziale.
- Nessun backend, account ERP o chiave API richiesta.

## Verifiche

```sh
npm run validate:data
npm test
npm run typecheck
npm run build
npm run check:bundle
```

Per i test browser, in PowerShell:

```powershell
$env:PLAYWRIGHT_BROWSERS_PATH = Join-Path (Get-Location) '.playwright-browsers'
npx.cmd playwright install chromium
npm.cmd run test:e2e
```

Su macOS/Linux:

```sh
export PLAYWRIGHT_BROWSERS_PATH="$PWD/.playwright-browsers"
npx playwright install chromium
npm run test:e2e
```

La demo originale richiede un browser moderno: iOS 12 non e supportato. La presenza del repository pubblico non implica un sito pubblicato o un servizio di hosting attivo.

## Struttura

- `src/app`: navigazione, stato e persistenza.
- `src/domain`: regole e calcoli.
- `src/design-system`: stile e controlli condivisi.
- `src/features`: schermate e flussi applicativi.
- `src/data/hfs_demo_data.json`: dataset sintetico approvato.
- `tests`: test di dominio e interfaccia.
- `references/data/DATA_CONTRACT.md`: contratto del dataset.

Il repository ha una cronologia autonoma e contiene soltanto i file necessari alla demo e ai relativi test.
