# ⚽ Fanta Step - Sistema di Fantacalcio "Daily Fantasy" 7v7
Questo repository contiene un sistema completo per la gestione di un Fantacalcio 7v7 in stile "Daily Fantasy", dove i partecipanti creano una nuova squadra per ogni giornata di campionato.

Il progetto è costruito su un'architettura ibrida che utilizza Google Sheets come database, Google Forms per la raccolta dati, e un notebook Python (Google Colab) per l'elaborazione dei punteggi, la validazione delle squadre e la generazione della classifica.

## 🚀 Caratteristiche Principali
- Gestione Daily Fantasy: Progettato per la modalità "una squadra per giornata". Se un utente non invia la formazione, prende 0 (zero) punti.

- Input Flessibile: Il Google Form è impostato per accettare input complessi, come "3 difensori in una sola cella", che vengono poi elaborati da Python.

- Elaborazione Dati in Python: Un notebook Google Colab (.ipynb) funge da "cervello" centrale. Si collega a Google Drive per:

   - Leggere i listoni (DB_Giocatori).

   - Leggere i voti di giornata (Input_Voti).

   - Leggere le formazioni inviate (Form_Responses).

- Validazione Automatica: Lo script valida ogni formazione inviata controllando:

  - Il budget (basato sui costi dei giocatori).

  - La validità dei giocatori inseriti.

  - La correttezza dell'invio.

- Classifica Storica: Lo script aggiorna la classifica generale sul file Google Sheet, sommando i punteggi di giornata e mantenendo uno storico dettagliato (es. G1_Punteggio, G1_Costo, G2_Punteggio...).

- Output per il Web: Lo script genera automaticamente un file index.html pulito e formattato, pronto per essere caricato su GitHub Pages e reso pubblico.
---
# 🔧 Come Funziona (Workflow dell'Admin)
Il sistema è progettato per essere gestito da un admin (o un gruppo di admin) con un workflow settimanale.

### 1. Setup Iniziale:

  - Creare una copia del file FantaStep.xlsx sul proprio Google Drive.

  - Creare un Google Form collegato al foglio DB_POR, DB_DIF, ecc. (come descritto nel PDF) che salvi le risposte nel foglio Form_Responses.

### 2. Ogni Giornata (Prima delle partite):

  - L'admin aggiorna il listone DB_Giocatori (se necessario).

  - L'admin azzera il foglio Form_Responses eliminando manualmente tutte le righe dalla 2 in giù (mantenendo l'intestazione della riga 1).

  - Gli utenti inviano le loro formazioni tramite il Google Form.

### 3. Ogni Giornata (Dopo le partite):

  - L'admin compila il foglio Input_Voti con tutti i bonus e malus (+3 per gol, -0.5 per falli, ecc.).

### 4. Calcolo Punteggi:

  - L'admin apre il notebook FantaStep.ipynb in Google Colab.

  - Esegue tutte le celle in ordine.

  - Lo script legge i dati, calcola i punteggi di giornata (Cella 4), aggiorna la classifica storica (Cella 5) e genera il file index.html (Cella 6).

### 5. Pubblicazione:

  - Lo script fa scaricare automaticamente il file index.html aggiornato.

  - L'admin carica (fa il "commit" e "push") questo nuovo index.html su GitHub per aggiornare la classifica pubblica sul sito GitHub Pages.
---
# 📂 Struttura del Repository
- FantaStep.xlsx: Il file template di Google Sheets. Contiene:

  - DB_Giocatori: Il listone master.

  - DB_POR, DB_DIF, DB_CC, DB_ATT: Fogli ausiliari per popolare il Google Form.

  - Input_Voti: Dove l'admin inserisce i voti di giornata.

  - Form_Responses: Dove il Google Form salva le formazioni inviate.

  - Classifica: Il database storico che viene scritto e aggiornato dallo script Colab.

- FantaStep.ipynb: Il notebook Jupyter/Colab con tutto il codice Python per l'elaborazione.

- FantaStep.pdf: La documentazione di progetto che spiega in dettaglio l'architettura e il flusso di lavoro.

- index.html: Il file della classifica pubblica generato dallo script.

---
# ⚖️ Licenza
Questo progetto è rilasciato sotto la Licenza MIT. Questo significa che sei libero di usare, modificare, distribuire e persino vendere questo codice, a condizione che includi l'avviso di copyright originale (presente nel file LICENSE).

Vedi il file LICENSE per i dettagli completi.

---
https://losteph.github.io/FantaStep/
