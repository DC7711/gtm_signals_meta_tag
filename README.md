📄 README.md — Documentazione per “Signals Template”
markdown
Copia
Modifica
# Signals Template – Tag GTM Personalizzato

Il **Signals Template** è un tag personalizzato per Google Tag Manager progettato per **inviare eventi in modo asincrono** tramite richieste `fetch()` a un endpoint esterno, passando dinamicamente i parametri tramite variabili GTM.

---

## 🔍 Descrizione del Template

### 📌 Cosa fa questo tag?

Questo tag consente di inviare richieste `fetch()` POST con payload JSON a un server remoto, trasmettendo dati dinamici raccolti nel contenitore GTM (ad esempio ID utente, tipo evento, timestamp, ecc.).

### 🧠 Quando e perché usarlo?

Usalo quando:
- Vuoi tracciare eventi personalizzati verso un endpoint proprietario.
- Hai bisogno di inviare dati raccolti via GTM in tempo reale a un sistema esterno (es. CRM, database, endpoint di analytics).
- Preferisci un sistema più leggero e asincrono rispetto all’uso di pixel o librerie JS pesanti.

---

## ⚙️ Istruzioni per l’uso

### 1. **Importazione del template**
- Vai su **Templates** in GTM
- Clicca su **Nuovo > Importa**
- Carica il file `template.tpl`

### 2. **Crea un nuovo tag**
- Clicca su **Tag > Nuovo**
- Scegli **"Signals Template"** come tipo di tag

### 3. **Compila i campi richiesti**
| Campo | Descrizione |
|-------|-------------|
| `endpoint` | URL completo dell'API a cui inviare i dati (es. `https://api.tuosito.com/event`) |
| `payload` | Oggetto JSON costruito con variabili GTM (`{{}}`) che definisce il corpo della richiesta |

### Esempio `payload`:
```json
{
  "userId": "{{user_id}}",
  "eventType": "{{event_type}}",
  "timestamp": "{{timestamp}}"
}
🧪 Esempio di configurazione
✅ Esempio di tag configurato:
Trigger: All Pages o evento personalizzato (es. formSubmit)

Endpoint: https://api.neting.it/signals

Payload:

json
Copia
Modifica
{
  "lead": "{{Form Email}}",
  "type": "formSubmit",
  "formName": "{{Form Name}}"
}
⚠️ Possibili errori comuni:
Endpoint errato o con CORS bloccato → assicurarsi che il server accetti richieste POST CORS da domini pubblici

Payload non valido → controlla che le variabili GTM siano definite e restituiscano un valore stringa/JSON valido

Mancanza di un trigger → il tag non viene mai attivato

🧱 Requisiti tecnici
Requisito	Stato
✅ Browser supportati	Tutti i browser moderni che supportano fetch()
✅ GTM Web container	Sì
✅ Richiesta asincrona via JS	Sì
🔒 GDPR/Privacy	Il tag non usa cookie. I dati inviati devono essere conformi alle normative (gestisci via Consent Mode se necessario)
🚫 Script esterni	Nessuno richiesto

📚 Risorse utili
Guida a variabili GTM

fetch() API

🛟 Supporto
Per segnalare problemi o proporre miglioramenti, apri una Issue su GitHub.

📝 Licenza
Distribuito con licenza Apache 2.0.

yaml
Copia
Modifica

---

## 🔁 Prossimi passaggi per te

1. Copia questo testo in un file `README.md` nel tuo repo GitHub
2. Usa il link diretto al README nel campo `documentation:` del tuo `metadata.yaml`, ad esempio:
   ```yaml
   documentation: "https://github.com/neting/gtm-signals-template#readme"
