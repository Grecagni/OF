# Open Factor Designer

Applicazione single-page per progettare pattern di microforatura e stimare il **fattore di apertura (OF)** di un pannello perforato. Tutto gira in locale: nessun build tool, zero dipendenze, basta aprire `index.html`. L’anteprima simula un foglio in scala con effetto “wave”, utile sia a designer sia a tecnici di prodotto.

## Perché usarlo
- Sostituisce i fogli Excel per OF con un’interfaccia pensata per prove “what-if”.
- Tiene sincronizzati campi numerici e slider con convalide e warning automatici.
- Mostra sempre un’anteprima 1:1 con dimensioni coperte e numero di fori generati.
- Condivide un asset completo (SVG/PNG) o un link parametrico pronto da spedire.

## Funzionalità principali
- Tre modalità di calcolo (`Calcola OF`, `Calcola passo x=y`, `Calcola d`) con help contestuale che spiega cosa sta succedendo.
- Supporto sia ai pattern **a griglia** sia **sfalsati (staggered)**, più toggle “Mostra griglia” e blocco automatico delle colonne quando si importano parametri manuali.
- Anteprima vettoriale con effetto “Wave attivo” (disattivabile) per simulare la lamiera, clip dinamico e possibilità di visualizzare la guida della griglia.
- Indicatori in tempo reale: area del foro/cella, rapporti `d/x` e `d/y`, numero di fori generati, copertura stimata e messaggio di warning se `d ≥ min(x, y)`.
- Pulsanti dedicati per **reset**, **esportazione SVG/PNG** (con sfondo bianco e naming basato sui parametri) e **copia del link** con hash sincronizzato.
- Auto-scaling del pattern: il numero di righe/colonne viene ricalcolato in base al diametro/step per usare al meglio la preview da 50×50 mm.

## Flusso rapido
1. Clona o scarica il repo e apri `index.html` in un browser moderno (Chrome, Edge, Firefox, Safari).
2. Scegli la modalità di calcolo dal select principale e imposta diametro/passi/OF con slider o input numerici.
3. Usa i toggle per mostrare la griglia o per attivare/disattivare l’effetto wave; controlla gli indicatori e il messaggio di stato.
4. Quando i parametri sono corretti, esporta l’anteprima in SVG/PNG oppure copia il link parametrico (`#d=…&x=…&…`) per condividerlo.

## Modalità di calcolo
- **Calcola OF(d, x, y)**: parte da diametro e passi e restituisce l’OF corrente, mantenendo aggiornato il valore nel pannello laterale.
- **Calcola passo x = y (d, OF)**: calcola automaticamente un passo quadrato coerente; se modifichi manualmente `x` o `y`, il sistema blocca l’auto-sync finché non cambi di nuovo `d` o OF.
- **Calcola d (OF, x, y)**: trova il diametro più adatto all’OF desiderato mantenendo fissi i passi `x` e `y`.

## Anteprima e indicatori
- Preview vettoriale 50×50 mm con clipping dinamico e bordo wave (disattivabile dal pulsante “Wave attivo”).
- Griglia opzionale per verificare gli allineamenti; il layout è responsive e occupa tutto lo schermo disponibile.
- Box informativo con aree, rapporti e numero di fori, più etichetta “Copertura stimata: … mm”.
- Warning accessibile (ARIA alert) quando i fori collidono o toccano il bordo, con evidenziazione del controllo diametro.

## Esportazione e condivisione
- **SVG**: l’anteprima viene serializzata senza elementi “preview-only” così il file rimane pulito e pronto per CAD.
- **PNG**: rendering su canvas con sfondo bianco e risoluzione basata sul pixel ratio del dispositivo.
- I file vengono nominati come `pattern-d0.50-x5.00-y5.00.svg/png` per favorire la tracciabilità.
- Il pulsante “Copia parametri” serializza i valori nell’hash (`d, x, y, n, m, grid, pattern, mode, t`) e li copia negli appunti; aprendo il link l’app ripristina automaticamente i parametri ed eventuali griglie manuali.

## Personalizzazioni utili
- **Valori di default**: modifica l’oggetto `defaults` in `script.js` per cambiare diametri, passi, pattern iniziale o modalità attiva.
- **Dimensioni preview**: aggiorna `PREVIEW_SIZE_MM`, `PREVIEW_MARGIN_MM` o `PX_PER_MM` per simulare pannelli più grandi o densità diverse.
- **Stile fori/export**: cambia `SVG_EMBEDDED_STYLES` e le costanti `PREVIEW_WAVE_*` per personalizzare colori, stroke o l’effetto wave.
- **Preset UI**: intervieni su `styles.css` per regolare layout, breakpoint mobile o look dei pulsanti.

## Struttura del progetto
- `index.html` – markup e layout generale dell’applicazione.
- `styles.css` – tema responsive, effetto wave del preview wrapper e pannello controlli.
- `script.js` – logica dell’interfaccia, calcolo parametri, rendering SVG, export e gestione hash.
- `CALCOLO-%.xlsx` – foglio di calcolo di riferimento (non necessario per l’app, utile come source storico).

## Requisiti tecnici
- Browser con supporto a ES2015+, `URLSearchParams`, `requestAnimationFrame`, API Clipboard.
- Nessuna dipendenza esterna, nessun server: funziona interamente in locale.

## Roadmap (idee future)
1. Gestione di pattern triangolari/esagonali.
2. Esportazione DXF o CSV con le coordinate dei fori.
3. Possibilità di impostare larghezza/altezza reali del pannello invece della preview fissa.

Contribuzioni e segnalazioni sono benvenute: apri una issue o invia una pull request!
