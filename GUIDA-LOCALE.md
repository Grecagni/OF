# Guida locale

Questa guida raccoglie i passaggi per avviare l’app in locale e per personalizzarla.

## Avvio rapido
1. Clona o scarica il repo e apri `index.html` in un browser moderno (Chrome, Edge, Firefox, Safari).
2. Scegli la modalità di calcolo dal select principale e imposta diametro/passi/OF con slider o input numerici.
3. Usa i toggle per mostrare la griglia o per attivare/disattivare l’effetto wave; controlla gli indicatori e il messaggio di stato.
4. Quando i parametri sono corretti, esporta l’anteprima in SVG/PNG oppure copia il link parametrico (`#d=…&x=…&…`) per condividerlo.

## Requisiti tecnici
- Browser con supporto a ES2015+, `URLSearchParams`, `requestAnimationFrame`, API Clipboard.
- Nessuna dipendenza esterna, nessun server: funziona interamente in locale.

## Struttura del progetto
- `index.html` – markup e layout generale dell’applicazione.
- `styles.css` – tema responsive, effetto wave del preview wrapper e pannello controlli.
- `script.js` – logica dell’interfaccia, calcolo parametri, rendering SVG, export e gestione hash.
- `CALCOLO-%.xlsx` – foglio di calcolo di riferimento (non necessario per l’app, utile come source storico).

## Personalizzazioni utili
- **Valori di default**: modifica l’oggetto `defaults` in `script.js` per cambiare diametri, passi, pattern iniziale o modalità attiva.
- **Dimensioni preview**: aggiorna `PREVIEW_SIZE_MM`, `PREVIEW_MARGIN_MM` o `PX_PER_MM` per simulare pannelli più grandi o densità diverse.
- **Stile fori/export**: cambia `SVG_EMBEDDED_STYLES` e le costanti `PREVIEW_WAVE_*` per personalizzare colori, stroke o l’effetto wave.
- **Preset UI**: intervieni su `styles.css` per regolare layout, breakpoint mobile o look dei pulsanti.
