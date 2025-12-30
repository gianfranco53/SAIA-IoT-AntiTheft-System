# SAIA-IoT: Sistema Antifurto Intelligente per Autoveicoli
## Design IoT & Security-by-Design PoC | Progettato da Gianfranco Colasanti

[![Hardware](https://img.shields.io/badge/Hardware-ESP32_%7C_Android-blue.svg)]()
[![Security](https://img.shields.io/badge/Security-Safe--Stop_%7C_Trap_Button-red.svg)]()

SAIA rappresenta l'integrazione di tecnologie Internet of Things (IoT) e comunicazioni wireless per offrire una soluzione di sicurezza automobilistica di nuova generazione. Il sistema supera i limiti degli antifurti tradizionali fornendo un controllo remoto strategico e una logica di blocco motore vincolata a rigorose condizioni di sicurezza.

---

### 🛡️ Sicurezza Attiva e Funzionalità Core

#### 1. Gestione Energetica e Autonomia
Il sistema è progettato con una logica di Power Management a due livelli per massimizzare l'autonomia della batteria tampone:
* [cite_start]**Modalità Background:** Con l'app in esecuzione passiva, il consumo è drasticamente ridotto, permettendo un'operatività fino a circa **2 giorni** senza ricarica. [cite: 66, 75]
* **Modalità UI (Active Tracking):** L'interfaccia utente completa è attivabile per l'interazione in tempo reale e per abilitare il "Pulsante Gabbietta". [cite_start]Sebbene comporti un incremento dei consumi, garantisce la massima reattività durante un evento critico. [cite: 70, 72, 74]
* [cite_start]**Alimentazione Sotto Quadro:** L'unità ESP32 è asservita al Terminale 15 (quadro strumenti), attivandosi automaticamente all'accensione del veicolo. [cite: 14, 63]

#### 2. Il "Pulsante Gabbietta" (Trappola Anti-Manomissione)
In modalità UI, il localizzatore mostra un finto tasto "PREMI PER FERMARE LA LOCALIZZAZIONE":
* [cite_start]**Azione**: La pressione attiva silenziosamente la fotocamera frontale. [cite: 38, 39]
* [cite_start]**Notifica**: Scatta una foto dell'intruso e la invia istantaneamente via Telegram al proprietario. [cite: 39, 53]
* **Protezione**: L'app opera in *Android Lock Task Mode* (Modalità Kiosk), disabilitando i tasti di sistema. [cite_start]L'uscita è possibile solo tramite una sequenza segreta di tasti volume. [cite: 33, 35, 36]

#### 3. Protocollo "Single-Byte Trigger"
Per eliminare il polling continuo e ridurre l'uso energetico del GPS, l'ESP32 opera come Server:
* [cite_start]Al giro della chiave, l'ESP32 si avvia e invia un singolo byte (ping) al localizzatore Android (Client). [cite: 21]
* [cite_start]Il localizzatore si risveglia istantaneamente e trasmette il comando memorizzato (BLOCCA/SBLOCCA) all'unità di controllo. [cite: 22]

---

### 🛠️ Architettura Hardware e Scalabilità
Il sistema è costruito su una base hardware solida ed espandibile:
* [cite_start]**Unità di Controllo**: ESP32 con gestione dello stato di blocco in memoria **EEPROM** per conservare lo stato anche in assenza di alimentazione. [cite: 13, 42]
* [cite_start]**Attuatore**: Relè Automotive (12V 30/40A) interposto sulla pompa carburante o Terminale 15. Il prototipo prevede l'evoluzione verso MOSFET **IRLB3034**. [cite: 61, 63, 64]
* **Espandibilità (GPIO Liberi)**: L'ESP32 dispone di pin aggiuntivi pronti per implementare:
    * Allarme acustico attivabile remotamente tramite comando.
    * LED di segnalazione "Auto Rubata" sul lunotto posteriore, programmabile per attivarsi temporizzato dopo il rilevamento del furto.

---

### 📊 Analisi dell'Autonomia (Test Batteria Interna)
| Modalità Operativa | Stato GPS | Consumo Stimato (12h) | Autonomia Max |
| :--- | :--- | :--- | :--- |
| **Background (Passivo)** | OFF | **~ 3%** | **~ 2 Giorni** |
| **Active Tracking (Furto)** | ON | **~ 12%** | ~ 40 Ore |
| **Interfaccia Utente (UI)** | ON | **~ 100%** | Solo uso critico |

---

### 👤 Contatti e Collaborazioni
[cite_start]Sviluppato da **Gianfranco Colasanti**, tecnico multidisciplinare senior con esperienza in meccanica, elettronica e sistemi embedded. [cite: 2]

[cite_start]L'autore è aperto a discussioni riguardanti partnership industriali, accordi di licenza e industrializzazione del prodotto nei settori: [cite: 28, 46]
* **Fleet Management** & Logistica.
* **Automotive Security Systems**.
* **Insurtech** e monitoraggio remoto.

📩 **Email:** gianfr.colasanti@gmail.com

---
### Disclaimer
Il sistema SAIA è un Proof of Concept pubblicato a scopo di ricerca e valutazione tecnica. [cite_start]L'autore non si assume responsabilità per usi impropri o installazioni non conformi alle normative vigenti. [cite: 40, 41]
