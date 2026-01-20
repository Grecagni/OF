# Open Factor Designer

Applicazione single-page per progettare pattern di microforatura e stimare il **fattore di apertura (OF)** di un pannello perforato. L’anteprima simula un foglio in scala con effetto “wave”, utile sia a designer sia a tecnici di prodotto.

## Perché usarlo
- Sostituisce i fogli Excel per OF con un’interfaccia pensata per prove “what-if”.
- Tiene sincronizzati campi numerici e slider con convalide e warning automatici.
- Mostra un’anteprima 1:1 con dimensioni coperte e numero di fori generati.
- Condivide un asset completo (SVG/PNG) o un link parametrico pronto da spedire.

## Funzionalità principali
- Tre modalità di calcolo (`Calcola OF`, `Calcola passo x=y`, `Calcola d`) con help contestuale.
- Supporto sia ai pattern **a griglia** sia **sfalsati (staggered)**, con toggle “Mostra griglia”.
- Anteprima vettoriale con effetto “Wave attivo” (disattivabile) e possibilità di visualizzare la griglia.
- Indicatori in tempo reale: area foro/cella, rapporti `d/x` e `d/y`, numero di fori, warning se `d ≥ min(x, y)`.
- Auto-scaling del pattern: righe/colonne ricalcolate per sfruttare al meglio la preview.
- Pulsanti dedicati per reset, esportazione SVG/PNG e copia dei parametri nell’hash.

## Modalità di calcolo
- **Calcola OF(d, x, y)**: parte da diametro e passi e restituisce l’OF corrente.
- **Calcola passo x = y (d, OF)**: calcola automaticamente un passo quadrato coerente; modifiche manuali disattivano l’auto-sync finché non si cambia `d` o OF.
- **Calcola d (OF, x, y)**: trova il diametro più adatto all’OF desiderato mantenendo fissi i passi `x` e `y`.

## Anteprima e indicatori
- Preview vettoriale 50×50 mm con clipping dinamico e bordo wave (disattivabile).
- Griglia opzionale per verificare allineamenti; layout responsive che occupa tutto lo schermo disponibile.
- Box informativo con aree, rapporti, numero di fori e messaggio di warning.

## Esportazione e condivisione
- **SVG**: l’anteprima viene serializzata senza elementi “preview-only” così il file rimane pulito e pronto per CAD.
- **PNG**: rendering su canvas con sfondo bianco e risoluzione basata sul pixel ratio del dispositivo.
- Naming file basato sui parametri (`pattern-d0.50-x5.00-y5.00.svg/png`).
- Il pulsante “Copia parametri” serializza i valori nell’hash (`d, x, y, n, m, grid, pattern, mode, t`) e li copia negli appunti.

## Avvio in locale
Per installazione e avvio in locale, vedi `GUIDA-LOCALE.md`.

## Roadmap (idee future)
1. Gestione di pattern triangolari/esagonali.
2. Esportazione DXF o CSV con le coordinate dei fori.
3. Possibilità di impostare larghezza/altezza reali del pannello invece della preview fissa.

Contribuzioni e segnalazioni sono benvenute: apri una issue o invia una pull request!
