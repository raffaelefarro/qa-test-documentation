# BUG-001: con `problem_user` tutti i prodotti mostrano la stessa immagine

| | |
|---|---|
| **Gravità** | Media |
| **Priorità** | Media |
| **Stato** | Aperto (comportamento voluto dal sito di prova) |
| **Trovato il** | 13/11/2026 |
| **Ambiente** | saucedemo.com, Chrome, Windows 11 |
| **Caso di test** | TC-18 |

## Passi per riprodurlo

1. Apri https://www.saucedemo.com/
2. Accedi con `problem_user` e `secret_sauce`
3. Guarda l'elenco dei prodotti

## Risultato ottenuto

Tutti e sei i prodotti mostrano la stessa immagine, un segnaposto di errore (`sl-404`).

## Risultato atteso

Ogni prodotto mostra la propria foto, come con `standard_user`.

## Note

Con `standard_user` le immagini sono corrette, quindi il problema dipende dall'utente. In un caso reale chiederei se i dati dell'utente puntano a un percorso sbagliato per le immagini.
