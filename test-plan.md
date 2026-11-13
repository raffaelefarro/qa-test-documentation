# Piano di test: SauceDemo

**Applicazione:** [saucedemo.com](https://www.saucedemo.com/), un negozio online di prova pubblico
**Versione del piano:** 1.0, 13/11/2026
**Autore:** Raffaele Farro

## Obiettivo

Verificare che chi compra possa fare l'intero percorso (accesso, scelta dei prodotti, carrello, checkout) e che gli errori vengano mostrati in modo chiaro. Serve anche da esempio di come imposto un piano di test.

## Cosa si testa

- Login (utenti validi, bloccati, campi sbagliati o vuoti)
- Catalogo prodotti: elenco, ordinamento, immagini
- Carrello: aggiungere e togliere prodotti, contatore
- Checkout: dati personali, riepilogo, conferma

## Cosa non si testa

- Prestazioni e carico (il sito è di terzi, non va stressato)
- Sicurezza (stesso motivo)
- Accessibilità e browser diversi da Chrome: da fare in un secondo momento

## Approccio

| Tipo | Come | Dove |
|---|---|---|
| Automatici | Selenium, TestNG, Page Object | [selenium-testng-saucedemo](https://github.com/raffaelefarro/selenium-testng-saucedemo) |
| Manuali | Casi di test scritti a mano, per le parti visive e per gli utenti "difettosi" del sito | [test-cases.md](test-cases.md) |

Automatizzo i percorsi che si ripetono a ogni rilascio e che non cambiano spesso. Provo a mano quello che si capisce meglio guardando (per esempio se un'immagine è quella giusta).

## Dati di test

Il sito mette a disposizione degli utenti di prova, tutti con password `secret_sauce`:

| Utente | A cosa serve |
|---|---|
| `standard_user` | percorso normale |
| `locked_out_user` | non può accedere |
| `problem_user` | comportamenti sbagliati di proposito (immagini, carrello) |
| `performance_glitch_user` | risposte lente |

## Ambiente

Chrome aggiornato, Windows 11. Il sito è sempre online, non c'è un ambiente di test separato.

## Criteri di uscita

- Tutti i casi di priorità alta eseguiti
- Nessun bug aperto di gravità alta o critica
- I test automatici passano nell'ultima esecuzione su GitHub Actions

## Rischi

- Il sito è di terzi: può cambiare o non essere raggiungibile, e un test può fallire senza colpa del codice
- Gli utenti "difettosi" sono costruiti per rompersi: i bug che si trovano sono voluti, ma servono per esercitarsi a segnalarli
