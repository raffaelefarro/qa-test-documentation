# BUG-002: con `problem_user` alcuni prodotti non si aggiungono al carrello

| | |
|---|---|
| **Gravità** | Alta |
| **Priorità** | Alta |
| **Stato** | Aperto (comportamento voluto dal sito di prova) |
| **Trovato il** | 13/11/2026 |
| **Ambiente** | saucedemo.com, Chrome, Windows 11 |
| **Caso di test** | TC-19 |

## Passi per riprodurlo

1. Accedi con `problem_user` e `secret_sauce`
2. Premi "Add to cart" sullo zaino (Sauce Labs Backpack)
3. Premi "Add to cart" sulla maglietta Bolt (Sauce Labs Bolt T-Shirt)
4. Premi "Add to cart" sulla luce da bici (Sauce Labs Bike Light)
5. Guarda il numero sul carrello e i pulsanti

## Risultato ottenuto

Il carrello segna **2**. Zaino e luce da bici passano a "Remove", mentre la maglietta Bolt resta con "Add to cart": il click non ha avuto effetto.

## Risultato atteso

Il carrello segna 3 e tutti e tre i pulsanti diventano "Remove".

## Impatto

Un cliente non riesce a comprare un prodotto che ha scelto e non riceve nessun messaggio di errore. Gravità alta perché blocca l'acquisto senza avvisare.

## Note

Con `standard_user` lo stesso percorso funziona. Gli altri prodotti non li ho provati uno per uno.
