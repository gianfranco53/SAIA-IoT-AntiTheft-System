# SAIA-IoT: Sistema Antifurto Intelligente per Autoveicoli
## Design IoT & Security-by-Design PoC | Progettato da Gianfranco Colasanti

SAIA rappresenta l'integrazione di tecnologie Internet of Things (IoT) e comunicazioni wireless per offrire una soluzione di sicurezza automobilistica di nuova generazione. Il sistema supera i limiti degli antifurti tradizionali fornendo un controllo remoto strategico e una logica di blocco motore vincolata a rigorose condizioni di sicurezza.

### 🛡️ Sicurezza Attiva e Funzionalità Core

#### 1. Gestione Energetica e Autonomia
Il sistema è progettato con una logica di gestione dell'alimentazione a due livelli per massimizzare l'autonomia della batteria tampone:
* **Modalità Background:** Con l'app in esecuzione passiva, il consumo è drasticamente ridotto, consentendo un'operatività fino a circa **2 giorni** senza ricarica.
* **Modalità UI (Active Tracking):** L'interfaccia utente completa è attivabile per l'interazione in tempo reale e per abilitare il "Pulsante Gabbietta". Sebbene comporti un incremento dei consumi, garantisce la massima reattività durante un evento critico.
* **Alimentazione Sotto Quadro:** L'unità ESP32 è asservita al Terminale 15 (quadro strumenti), attivandosi automaticamente all'accensione del veicolo.

#### 2. Il "Pulsante Gabbietta" (Trappola Anti-Manomissione)
In modalità UI, il localizzatore mostra un finto tasto "PREMI PER FERMARE LA LOCALIZZAZIONE":
* **Azione:** La pressione attiva silenziosamente la fotocamera frontale.
* **Notifica:** Scatta una foto dell'intruso e la invia istantaneamente tramite Telegram al proprietario.
* **Protezione:** L'app funziona in **Android Lock Task Mode** (Modalità Kiosk), disabilitando i tasti di sistema. L'uscita è possibile solo tramite una sequenza segreta di tasti volume.
* ![Interfaccia App SAIA-IoT e Tasto Gabbietta](nome_app.jpg)

#### 3. Protocollo "Trigger a byte singolo"
Per eliminare il polling continuo e ridurre l'uso energetico del GPS, l'ESP32 funziona come Server:
* Al giro della chiave, l'ESP32 si avvia e invia un singolo byte (ping) al localizzatore Android (Client).
* Il localizzatore si risveglia istantaneamente e trasmette il comando memorizzato (BLOCCA/SBLOCCA) all'unità di controllo.
* ![Centralina ESP32 e Modulo Relè](esp32.jpg)

### 🛠️ Architettura Hardware e Scalabilità
Il sistema è costruito su una base hardware solida ed espandibile:
* **Unità di controllo:** ESP32 con gestione dello stato di blocco in memoria **EEPROM** per conservare lo stato anche in assenza di alimentazione.
* **Attuatore:** Relè Automotive (12V 30/40A) interposto sulla pompa carburante o Terminale 15. Il prototipo prevede l'evoluzione verso MOSFET **IRLB3034**.
* **Espandibilità (GPIO Liberi):** L'ESP32 dispone di pin aggiuntivi pronti per implementare:
    * Allarme acustico attivabile in remoto tramite comando.
    * LED di segnalazione "Auto Rubata" sul lunotto posteriore, programmabile per attivarsi in modo temporizzato dopo il rilevamento del furto.

### 📊 Analisi dell'Autonomia (Test Batteria Interna)

| Modalità Operativa | Stato GPS | Consumo Stimato (12h) | Autonomia Max |
| :--- | :--- | :--- | :--- |
| **Background (Passivo)** | SPENTO | **~ 3%** | **~ 2 Giorni** |
| **Monitoring Attivo (Furto)** | ACCESO | **~ 12%** | **~ 40 Ore** |
| **Interfaccia Utente (UI)** | ACCESO | **~ 100%** | Solo uso critico |

### 👤 Contatti e Collaborazioni
Sviluppato da **Gianfranco Colasanti**, tecnico multidisciplinare senior con esperienza in meccanica, elettronica e sistemi embedded.

L'autore è aperto a discussioni riguardanti partnership industriali, accordi di licenza e industrializzazione del prodotto nei settori:
* Gestione della flotta e logistica.
* Sistemi di sicurezza per autoveicoli.
* Insurtech e monitoraggio remoto.

📩 **E-mail:** gianfr.colasanti@gmail.com
🔗 **LinkedIn:** [gianfranco-colasanti-234b11300](https://www.linkedin.com/in/gianfranco-colasanti-234b11300)

---
### Disclaimer
Il sistema SAIA è un Proof of Concept pubblicato a scopo di ricerca e valutazione tecnica. L'autore non si assume responsabilità per usi impropri o installazioni non conformi alle normative vigenti.
