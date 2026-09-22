# DataViz GeoTime

**Lingua:** [English](README.md) · **Italiano**

Pannello interattivo per **esplorare indicatori nello spazio e nel tempo**: mappe, grafici, filtri geografici e confronti tra periodi, a partire da cataloghi aperti, file propri o uno snapshot di esempio.

Questo repository è una **vetrina pubblica** (descrizione e screenshot). Non contiene il software dell’applicazione.

**App:** [geo-analysis.datav1z.com](https://geo-analysis.datav1z.com/)  
**Sito:** [datav1z.com](https://datav1z.com/)

![Panoramica della dashboard DataViz GeoTime](docs/images/hero-dashboard.png)

---

## A chi serve

DataViz GeoTime è pensato per chi deve **leggere un territorio e una serie storica insieme**, senza passare da un flusso di lavoro spezzato tra foglio di calcolo, GIS e grafici sparsi.

È utile in particolare a:

- analisti e ricercatori che confrontano indicatori tra aree e anni;
- chi lavora su **dati aperti italiani ed europei** e vuole una lettura immediata su mappa;
- redazioni, uffici studi e team di policy che devono **mostrare** un risultato (variazione, concentrazione, outlier) e poi scaricare dati o un report;
- chi ha un proprio dataset territoriale e vuole caricarlo nello stesso ambiente visivo dei cataloghi integrati.

Non è un GIS da editing, né un notebook di data science. È una **dashboard di lettura**: scegli la fonte, la geografia e la misura, poi navighi mappa, barre, linea e indicatori di sintesi.

---

## Cosa vedi in un colpo solo

L’interfaccia è divisa in due aree.

A **sinistra** (o in alto/in basso su alcuni layout) c’è la colonna dei **controlli**: ricerca nel catalogo, scelta della fonte, geografia dei dati, dataset, dimensioni, anni, misura. Da qui si carica il dataset e si tiene traccia di cosa è già in dashboard.

A **destra** c’è la **dashboard**: titolo del contesto, azioni (opzioni di layout, schermo intero, pulizia), striscia della legenda, tre visual principali (mappa, barre, linea) e pannelli di sintesi, qualità e anteprima tabellare.

Le tre visual condividono selezione, evidenza e scala colore. Cliccare un territorio sulla mappa, passare sulla barra o filtrare dalla sidebar aggiorna il resto in modo coerente.

---

## Caricare i dati

### Cataloghi integrati

Dalla sezione **Dataset source** si può:

- **cercare un dataset** per titolo, codice o tema (suggerimenti dopo Invio, raggruppati per fonte);
- scegliere l’ambito **Italia** o **internazionale**;
- selezionare la fonte e i filtri propri di quella fonte (territorio, dimensioni, anni, misura);
- caricare il dataset in dashboard.

La ricerca **non scarica** i dati: precompila i filtri. Il download avviene con l’azione di load, con un feedback esplicito (in caricamento / pronto / già caricato).

Le famiglie di catalogo coperte oggi, a titolo di **orientamento** (elenchi pubblici, non un inventario tecnico):

**Italia** — statistica ufficiale e amministrativa, previdenza, finanza pubblica, ambiente, istruzione, sanità, coesione, elezioni e altre banche dati aperte nazionali.

**Internazionale** — indicatori di sviluppo, finanza, statistica europea a più livelli territoriali, confronti tra paesi, dati demografici e socio-economici degli Stati Uniti.

Su alcune fonti, quando esiste una formula validata, si può passare da una misura **già pubblicata** a una misura **calcolata** nello stesso contesto (stesso territorio, stesso periodo), senza uscire dalla dashboard.

### File propri e progetti salvati

Oltre ai cataloghi si può:

- **caricare un file** territoriale/temporale con una procedura guidata (riconoscimento di colonne tempo, geografia e misure);
- **riaprire un progetto** o una configurazione salvata, per ritrovare filtri, layout e dataset di partenza.

I dettagli di formato, schema e integrazione non sono documentati qui: l’obiettivo di questa pagina è descrivere l’esperienza, non ricostruire l’ambiente di esecuzione.

---

## Geografia: da mondo a punto

La dashboard adatta la mappa al **livello territoriale** del dataset: paesi, regioni europee, province, comuni, sezioni di censimento, strutture puntuali, e analoghi livelli extra-UE quando la fonte li fornisce.

Si può:

- filtrare o **evidenziare** gruppi territoriali (macroaree, regioni, raggruppamenti della fonte);
- selezionare singoli territori da mappa, barre o elenco;
- aggregare le barre a un livello superiore (es. da comune a regione) scegliendo anche come aggregare la misura;
- in alcuni contesti, **scendere nel dettaglio** di un sito o di una struttura (tabella di drill-down, cerchi sulla mappa).

Filtro e highlight sono due logiche diverse: il filtro restringe il perimetro analitico; l’highlight tiene tutto visibile e sottolinea la selezione.

![Italia — posti letto ospedalieri come cerchi proporzionali](docs/images/italy-hospital-beds.png)

![Italia — sezioni di censimento e misura calcolata](docs/images/italy-census-sections.png)

![Tabella di dettaglio su strutture sanitarie](docs/images/italy-facility-table.png)

---

## Le tre visual

### Mappa

La mappa è il pezzo centrale. Può rappresentare i valori come:

- **coropleta** (riempimento delle aree);
- **cerchi proporzionali** (utile per punti, strutture, o quando il riempimento delle aree è poco leggibile);
- combinazioni con **basemap** classica o satellitare, proiezione e inquadratura.

Si può adattare l’inquadratura alla selezione, reimpostare la vista, e aprire le opzioni di mappa (tipo, sfondo, modo valore). Sui dataset italiani a scala fine la mappa può espandersi per dare più spazio al territorio.

Su smartphone e tablet lo **zoom e il riquadro di selezione sul grafico** sono disattivati, per non perdere la vista mentre si scorre la pagina; restano click e hover. Su desktop restano zoom e interazioni da analisi.

![Opzioni mappa — cerchi proporzionali su basemap satellitare](docs/images/map-options-circles.png)

### Barre

Il grafico a barre mette a confronto i territori (o i gruppi aggregati) per la misura corrente. Si può:

- ordinare e limitare ai primi N;
- ruotare l’orientamento;
- fissare l’asse durante l’animazione temporale;
- mostrare etichette e valori;
- allineare i colori alla stessa scala della mappa.

### Linea (o barre nel tempo)

La visual temporale mostra l’andamento della misura. Si possono confrontare territori, totali, aggregati, e — quando il dataset ha una vera serie — animare o scorrere il tempo. In **confronto temporale** la linea si nasconde: il racconto passa alla variazione tra due periodi, non al livello anno per anno.

---

## Tempo: un anno, due periodi, tutta la serie

Il tempo è un asse di prima classe, non un filtro secondario.

- **Periodo corrente** — slider o scelta dell’anno (o del periodo) visibile su mappa e barre; le KPI e la linea restano ancorate alla serie.
- **Passo di animazione** — si può avanzare per anno o per aggregati più larghi, con play e velocità.
- **Confronto temporale** — si scelgono due estremi (spesso primo e ultimo anno disponibili, ma qualsiasi coppia della serie). Mappa e barre mostrano la **variazione** (assoluta o percentuale), con scala divergente centrata sullo zero.

Nella modalità confronto la **legenda** ha due ambiti:

- **Relative** — colori tarati sul confronto che stai guardando;
- **Absolute** — estremi **fissi su tutta la serie storica** di confronti possibili, così cambiando gli anni i colori restano confrontabili e non si ricalibrano a ogni spostamento dello slider.

![Confronto temporale (variazione assoluta) su mappa europea](docs/images/time-comparison.png)

---

## Colore e legenda

La striscia sotto le azioni della dashboard è la **legenda condivisa** da mappa e barre.

Si può scegliere:

- scala **continua** o **discreta**;
- metodo di classificazione (intervalli uguali, quantili, interruzioni naturali, log, code estreme, divergente intorno allo zero, …);
- palette automatica o manuale, con inversione;
- ambito **absolute / relative** (livelli nel tempo, o variazioni in confronto).

Passare sulla legenda può evidenziare i territori che cadono in quella classe. Il marcatore sulla barra colore segue il valore sotto il puntatore.

---

## KPI, qualità e tabelle

Intorno alle visual ci sono pannelli di contesto:

- **KPI** — sintesi del perimetro visibile (totale, estremi, distribuzione). Con un solo territorio selezionato, in confronto temporale la sintesi può seguire il percorso anno per anno di quell’area.
- **Qualità dei dati** — copertura, buchi, territori confrontabili o meno tra due periodi.
- **Anteprima** — tabella del frame corrente, con export.
- **Tooltip** — al passaggio sulla mappa: nome, codice, valore, e su desktop un mini-andamento storico (nascosto su telefono e tablet per non coprire la mappa).

![Eurostat a livello NUTS, con pannello qualità](docs/images/international-eurostat.png)

---

## Layout, lingua, temi

- **Stile e colore** della pagina (temi chiari e scuro).
- **Lingua** dell’interfaccia (almeno italiano e inglese), con commutazione dalla sidebar.
- **Schermo intero** della dashboard (su dispositivi touch una modalità che non rompe i menu).
- **Sidebar comprimibile**: su schermi stretti i comandi lingua / riapertura restano nella riga delle azioni, senza lasciare una striscia vuota.
- **Smartphone in verticale** — layout compatto; **in orizzontale** — stessa logica della vista tablet (sidebar e dashboard affiancate).
- Dropdown della fonte dataset **contenuti nella colonna**, senza uscire dal pannello.

![Tema scuro, tooltip mappa e andamento nel tempo](docs/images/dark-theme.png)

---

## Esportare e condividere

Dalla dashboard si può portare via il lavoro, senza ricostruire i filtri a mano:

- dati del perimetro filtrato;
- dati sottostanti a mappa, barre o linea;
- **screenshot** della vista;
- **progetto / configurazione** per riaprire lo stesso allestimento;
- **report** di sintesi per una lettura esterna.

L’app è pensata anche per essere **incorporata nel sito** DataViz e ospitata come servizio, non solo come sessione locale.

---

## Cosa questa pagina non è

Non è un manuale di installazione, non elenca dipendenze, porte, variabili d’ambiente, schema dei file o procedure di replica.  
Il software resta fuori da questo repository. Per **usare** l’applicazione: [geo-analysis.datav1z.com](https://geo-analysis.datav1z.com/).

---

## Screenshot

| Vista | File |
|--------|------|
| Dashboard di esempio (popolazione mondiale) | `docs/images/hero-dashboard.png` |
| Italia — posti letto, cerchi proporzionali | `docs/images/italy-hospital-beds.png` |
| Italia — sezioni di censimento | `docs/images/italy-census-sections.png` |
| Tabella di drill-down strutture | `docs/images/italy-facility-table.png` |
| Internazionale — Eurostat NUTS | `docs/images/international-eurostat.png` |
| Confronto temporale | `docs/images/time-comparison.png` |
| Tema scuro e tooltip | `docs/images/dark-theme.png` |
| Opzioni mappa, cerchi e satellite | `docs/images/map-options-circles.png` |

---

## Crediti

**DataViz GeoTime** — [datav1z.com](https://datav1z.com/)  
I dataset restano di proprietà e sotto le licenze delle rispettive fonti pubbliche; l’applicazione li presenta in un unico ambiente visivo.
