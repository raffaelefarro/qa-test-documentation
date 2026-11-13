# Casi di test: SauceDemo

Priorità: **A** alta, **M** media, **B** bassa. La colonna "Automatico" dice se esiste un test in [selenium-testng-saucedemo](https://github.com/raffaelefarro/selenium-testng-saucedemo).

## Login

| ID | Titolo | Passi | Risultato atteso | Pr. | Automatico |
|---|---|---|---|---|---|
| TC-01 | Login con credenziali valide | 1. Apri il sito 2. Inserisci `standard_user` e `secret_sauce` 3. Premi Login | Si apre il catalogo con il titolo "Products" | A | sì, `loginConCredenzialiValide` |
| TC-02 | Utente bloccato | Come TC-01 con `locked_out_user` | Resto sulla pagina di login e compare il messaggio "this user has been locked out" | A | sì, `utenteBloccato` |
| TC-03 | Password sbagliata | `standard_user` con una password errata | Messaggio "do not match any user" | A | sì, `credenzialiNonValide` |
| TC-04 | Utente inesistente | Un nome utente qualsiasi con `secret_sauce` | Messaggio "do not match any user" | M | sì, `credenzialiNonValide` |
| TC-05 | Nome utente vuoto | Lascio vuoto il nome e inserisco la password | Messaggio "Username is required" | M | sì, `credenzialiNonValide` |
| TC-06 | Password vuota | Inserisco il nome e lascio vuota la password | Messaggio "Password is required" | M | sì, `credenzialiNonValide` |

## Catalogo

| ID | Titolo | Passi | Risultato atteso | Pr. | Automatico |
|---|---|---|---|---|---|
| TC-07 | Numero di prodotti | Accedi come `standard_user` | Sono visibili 6 prodotti | M | sì, `sonoSeiProdotti` |
| TC-08 | Ordine per prezzo crescente | Scegli "Price (low to high)" | I prezzi vanno dal più basso al più alto | M | sì |
| TC-09 | Ordine per prezzo decrescente | Scegli "Price (high to low)" | I prezzi vanno dal più alto al più basso | M | sì |
| TC-10 | Immagini dei prodotti | Accedi come `standard_user` e guarda l'elenco | Ogni prodotto ha la sua immagine, diversa dalle altre | M | no, controllo visivo |

## Carrello

| ID | Titolo | Passi | Risultato atteso | Pr. | Automatico |
|---|---|---|---|---|---|
| TC-11 | Contatore del carrello | Aggiungi due prodotti | Il numero sul carrello va da 1 a 2 | A | sì, `contatoreCarrello` |
| TC-12 | Aggiungere ogni prodotto | Premi "Add to cart" su tutti e sei | Il contatore arriva a 6 e ogni pulsante diventa "Remove" | M | no |
| TC-13 | Togliere un prodotto | Aggiungi un prodotto e premi "Remove" | Il contatore scende e il prodotto sparisce dal carrello | M | no |

## Checkout

| ID | Titolo | Passi | Risultato atteso | Pr. | Automatico |
|---|---|---|---|---|---|
| TC-14 | Acquisto completo | Aggiungi un prodotto, apri il carrello, Checkout, compila nome, cognome e CAP, Continue, Finish | Compare "Thank you for your order!" | A | sì, `acquistoCompleto` |
| TC-15 | Nome mancante | Come TC-14 ma lascio vuoto il nome | Messaggio "First Name is required" | A | sì, `checkoutSenzaNome` |
| TC-16 | Cognome mancante | Come TC-14 ma lascio vuoto il cognome | Messaggio "Last Name is required" | M | no |
| TC-17 | CAP mancante | Come TC-14 ma lascio vuoto il CAP | Messaggio "Postal Code is required" | M | no |

## Utenti "difettosi"

| ID | Titolo | Passi | Risultato atteso | Pr. | Esito 13/11/2026 |
|---|---|---|---|---|---|
| TC-18 | Immagini con `problem_user` | Accedi come `problem_user` e guarda il catalogo | Ogni prodotto ha la sua immagine | M | **Fallito**, vedi [BUG-001](bug-reports/BUG-001-problem-user-immagini-uguali.md) |
| TC-19 | Aggiungere tre prodotti con `problem_user` | Aggiungi zaino, maglietta Bolt e luce da bici | Il contatore arriva a 3 | A | **Fallito**, vedi [BUG-002](bug-reports/BUG-002-problem-user-carrello.md) |
