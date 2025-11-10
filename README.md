# Open Factor Designer

Applicazione single-page per progettare pattern di microforatura e stimare il **fattore di apertura (OF)** di un pannello perforato. È pensata per tecnici di prodotto e designer: tutto gira in locale, senza dipendenze o build tool.

## Funzionalità principali
- Calcolo interattivo del fattore di apertura, del passo `x = y` o del diametro `d` partendo dalle altre grandezze.
- Supporto ai pattern a **griglia** e **sfalsati (staggered)** con anteprima SVG dinamica e opzione per visualizzare la griglia di riferimento.
- Indicatori in tempo reale: area del foro/cella, rapporti `d/x` e `d/y`, numero di fori generati, copertura stimata della preview e warning quando i fori collidono.
- Esportazione diretta dell’anteprima in **SVG** o **PNG** (con sfondo bianco) e naming dei file basato sui parametri correnti.
- Condivisione veloce dei parametri tramite hash nell’URL e pulsante “Copia parametri”.
- Reset immediato allo stato iniziale e ripristino automatico dei parametri dal link condiviso.

## Come iniziare
1. Clona o scarica questo repository.
2. Apri il file `index.html` con qualsiasi browser moderno (Chrome, Edge, Firefox, Safari). Non serve alcun server locale.
3. Gioca con gli slider o i campi numerici per impostare diametro `d`, passi `x` e `y`, pattern e modalità di calcolo.

### Modalità di calcolo
- **Calcola OF(d, x, y)**: restituisce il fattore di apertura in base ai parametri impostati.
- **Calcola passo x = y (d, OF)**: imposta automaticamente un passo quadrato coerente con `d` e OF; puoi poi intervenire manualmente su `x` o `y`.
- **Calcola d (OF, x, y)**: trova il diametro più adatto a mantenere l’OF desiderato con i passi scelti.

Il fattore di apertura percentuale viene calcolato come:

```
OF = (Area del foro / Area della cella) × 100
    = (π × (d / 2)^2) / (x × y × Fpattern) × 100
```

dove `Fpattern` vale `1` per pattern a griglia e `0.5` per pattern sfalsati (righe alternate).

## Struttura del progetto
- `index.html` – markup e layout generale dell’applicazione.
- `styles.css` – tema responsive con pannello controlli e anteprima.
- `script.js` – logica dell’interfaccia, calcolo parametri, rendering SVG ed export.

## Personalizzazioni utili
- Valori di default: vedi l’oggetto `defaults` in `script.js` per cambiare diametri, passi o modalità iniziale.
- Dimensione della preview: aggiorna la costante `PREVIEW_SIZE_MM` per simulare pannelli più grandi/piccoli.
- Stili esportati: modifica `SVG_EMBEDDED_STYLES` per regolare colori e tratti dei fori nelle esportazioni.

## Condivisione dei parametri
Ogni combinazione di parametri viene serializzata nell’hash dell’URL (`#d=0.50&x=5.00&…`). Usa il pulsante **“Copia parametri”** per condividere un link già compilato: aprendo il link l’app ripristina automaticamente i valori, inclusa l’eventuale scelta della griglia manuale.

## Requisiti tecnici
- Browser con supporto a ES2015+, `URLSearchParams`, `requestAnimationFrame`, API Clipboard (per la copia automatica).
- Nessuna dipendenza esterna o configurazione di build.

## Roadmap (idee future)
1. Gestione di pattern triangolari/esagonali.
2. Esportazione DXF o CSV con le coordinate dei fori.
3. Possibilità di impostare larghezza/altezza reali del pannello invece della preview fissa.

Contribuzioni e segnalazioni sono benvenute: apri una issue o invia una pull request!
