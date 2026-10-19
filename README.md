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

## Limiti da sapere

- Chi ha il link può leggere e modificare i dati. Va bene per una cerchia fidata; per proteggere l'accesso servirebbe Firebase Authentication (da aggiungere in seguito).
- La lettura delle foto (pulsante "Scatta foto") funziona solo dentro Claude. Fuori da Claude si compila a mano.
- Senza configurazione Firebase i dati restano solo nel browser di chi usa la pagina.
