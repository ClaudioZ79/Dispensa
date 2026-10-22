# Scadenze Dispensa

Dashboard per tenere sotto controllo le scadenze della dispensa, con lista della spesa automatica.
Il database è Firebase Firestore, così la stessa dispensa si può condividere con altre persone.

## File

- `index.html`: la pagina (struttura, stile e logica).
- `firebase-config.js`: la configurazione del tuo progetto Firebase.
- `firestore.rules`: le regole di sicurezza del database.

## Configurare Firebase (una volta sola)

1. Vai su https://console.firebase.google.com e crea un progetto (per esempio "scadenze-dispensa").
2. Nel menu, apri **Build → Firestore Database** e premi **Crea database** (modalità produzione, scegli una regione europea).
3. Nella home del progetto premi l'icona **</>** (Web) e registra un'app. Copia l'oggetto `firebaseConfig`.
4. Incolla quell'oggetto in `firebase-config.js`, al posto di `null`:
   `window.FIREBASE_CONFIG = { apiKey: "...", ... };`
5. In **Firestore Database → Regole** incolla il contenuto di `firestore.rules` e premi **Pubblica**.

## Pubblicare la pagina

Con GitHub Pages: nel repository, **Settings → Pages → Deploy from a branch → main / (root)**.
L'app sarà online all'indirizzo `https://<tuo-utente>.github.io/<nome-repo>/`.

Per condividerla con qualcuno, manda il link: tutti vedono e modificano la stessa dispensa.

## Lista della spesa

La scheda **Lista della spesa** ha lo stesso aspetto e gli stessi pulsanti dell'app Casa:

- cerchio per segnare un articolo come comprato (va in **Nel carrello**), **− e +** per la quantità
  (passo 1 per i pezzi, 50 per g e ml, 0,5 per kg e l), **×** per toglierlo dalla lista;
- toccando il **nome** si corregge (Salva, Annulla, Esc);
- **Condividi o copia la lista**, **Svuota i comprati**, **Rimetti le voci tolte** e il modulo **Aggiungi alla lista**.

Su ogni prodotto della dispensa ci sono due pulsanti:

- **Aggiungi alla spesa**: lo mette in lista adesso e il prodotto resta in dispensa. Se è già in lista mostra
  "In lista della spesa".
- **Non aggiungere**: il prodotto non entra più da solo in lista e anche premendo **Finito** esce senza finire
  nella spesa. Premuto di nuovo torna automatico. La scelta vale per quel prodotto (campo `nonInLista`).

I campi dei dati restano quelli di Dispensa (`n`, `unita`, `preso`, `nascosto`).

## Limiti da sapere

- Chi ha il link può leggere e modificare i dati. Va bene per una cerchia fidata; per proteggere l'accesso servirebbe Firebase Authentication (da aggiungere in seguito).
- La lettura delle foto (pulsante "Scatta foto") funziona solo dentro Claude. Fuori da Claude si compila a mano.
- Senza configurazione Firebase i dati restano solo nel browser di chi usa la pagina.
