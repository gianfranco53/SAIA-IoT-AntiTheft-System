# SAIA-IoT (Sistema Antifurto Intelligente per Autoveicoli)
## Proof of Concept: Architettura IoT Event-Driven e Sicura

[![Status](https://img.shields.io/badge/Status-Functional_PoC-green.svg)]()
[![Hardware](https://img.shields.io/badge/Hardware-ESP32_%7C_Android-blue.svg)]()
[![License](https://img.shields.io/badge/License-Proprietary/Research-red.svg)]()

SAIA-IoT è un sistema antifurto intelligente di nuova generazione per veicoli, progettato per superare i limiti dei tradizionali localizzatori GPS. Il progetto implementa un'architettura **event-driven** a basso consumo energetico, garantendo il controllo remoto totale senza dipendenze da infrastrutture cloud centralizzate.

---

### 📊 Analisi Comparativa
Perché SAIA-IoT si distingue dalle soluzioni commerciali standard:

| Caratteristica | Tracker GPS Standard | Antifurti Satellitari | **SAIA-IoT** |
| :--- | :--- | :--- | :--- |
| **Consumo Batteria** | Elevato (polling) | Medio/Alto | **Ottimizzato (Event-driven)** |
| **Costi Ricorrenti** | SIM dati (Cloud) | Canone/Abbonamento | **Zero (Telegram/SMS)** |
| **Sicurezza Attiva** | Taglio motore rischioso | Gestita da centrale | **Smart Safe-Stop (Fermo)** |
| **Privacy Dati** | Server terzi/Cloud | Server proprietari | **Decentralizzato (Direct)** |
| **Resilienza** | Bassa (Soggetta a jammer) | Media | **Alta (Persistenza EEPROM)** |

---

### 🚀 Caratteristiche Principali e Funzionamento
- **Immobilizzazione Intelligente:** Blocco motore remoto eseguito esclusivamente a veicolo fermo (Logica Safe-Stop).
- **Feedback Visivo:** Il sistema integra un LED di stato sul modulo relè per la verifica immediata dell'attivazione del blocco.
- **Unità di Controllo ESP32:** Gestione real-time con persistenza dello stato in EEPROM; in caso di distacco alimentazione, il sistema ricorda lo stato di blocco/sblocco impostato.
- **Alimentazione Diretta:** Il sistema è progettato per operare con alimentazione costante, garantendo la reperibilità del veicolo anche a quadro spento (senza dipendenza dal Terminale 15).
- **Gateway Android:** Smartphone dedicato in modalità kiosk per localizzazione e crittografia comunicazioni.
- **Notifiche Real-time:** Integrazione completa con Telegram Bot API per avvisi e comandi.

---

### 🛠 Architettura del Sistema
Il sistema è composto da tre livelli interagenti:
1.  **Control Layer (ESP32):** Microcontrollore che funge da server Bluetooth e gestisce l'interfaccia fisica (Relè/MOSFET) con il cablaggio del veicolo.
2.  **Communication Layer (Android):** Smartphone protetto da architettura anti-manomissione che funge da bridge tra la rete cellulare e l'unità di controllo locale.
3.  **User Layer (Telegram/SMS):** Interfaccia di comando remota accessibile da qualsiasi dispositivo autorizzato.

---

### 🛡 Sicurezza e Affidabilità
- **Logica di Sicurezza Operativa:** Il blocco motore non può essere attivato se il sistema rileva il veicolo in movimento tramite i sensori del gateway, prevenendo arresti pericolosi.
- **Resilienza Hardware:** L'uso della EEPROM dell'ESP32 garantisce che un eventuale tentativo di reset elettrico non sblocchi il veicolo se l'antifurto era attivo.

---

### 📈 Stato del Progetto
- [x] Prototipo hardware completamente funzionante.
- [x] Test in condizioni reali su veicolo privato superati con successo.
- [x] Implementazione persistenza stato su memoria non volatile.
- [x] Sistema di allerta Telegram attivo e stabile.

---

### 💼 Interessi Commerciali e Industriali
L'autore è aperto a collaborazioni per l'industrializzazione del prodotto, licenze tecnologiche o partnership tecniche. Il progetto si rivolge a:
- Aziende di sicurezza automotive.
- Gestori di flotte aziendali (Fleet Management).
- Provider di soluzioni assicurative (Insurtech).

---

### 👤 Autore
Sviluppato da un **Tecnico Multidisciplinare Senior** con solida esperienza in:
- Meccanica ed Elettronica Automotive.
- Sistemi Embedded e Sviluppo Firmware.
- Integrazione Sistemi Elettroinformatici.

**Contatti:** gianfr.colasanti@gmail.com
---

### ⚠️ Disclaimer
Questo repository è pubblicato esclusivamente a scopo di ricerca e valutazione tecnica (Proof of Concept). L'autore non si assume responsabilità per usi impropri. Nessuna licenza è attualmente concessa per usi commerciali senza accordi preventivi.
