# 🚗 SAIA-IoT: Sistema Antifurto Intelligente per Autoveicoli

> **IoT & Security-by-Design PoC** | Sviluppato da **Gianfranco Colasanti**

[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![ESP32](https://img.shields.io/badge/ESP32-Platform-blue)](https://www.espressif.com/)
[![Kotlin](https://img.shields.io/badge/Kotlin-Android-purple)](https://kotlinlang.org/)

## 📱 Interfaccia Applicazione

### App Principale (Telefono Personale - Comandi)
![App Principale - Controllo Comandi](appprior.jpg)

### App Localizzatore (Modalità Kiosk)
![Localizzatore - UI Completa](app.jpg)

## 🔌 Architettura Hardware
### ESP32 con Relè Automotive
![ESP32 con Relè](hardware_setup.jpg)

## 🚨 Logica Operativa: Scenario di Furto
Il sistema non si limita a tracciare, ma reagisce secondo una sequenza deterministica basata su eventi reali:

### 1. Rilevamento Spostamento
L'allarme scatta automaticamente quando il veicolo si muove per più di **30 metri**.

### 2. Filtro Anti-Drift (GPS)
Per eliminare i falsi positivi (GPS drift), l'allarme viene validato solo se:
- Velocità ≥ **0.8 m/s** (≈ 3 km/h)
- Per almeno **2 rilevazioni consecutive**

### 3. Monitoraggio Stasi
Se il veicolo rimane fermo per almeno **2 minuti**, viene inviata una notifica Telegram:

## ⚠️ Disclaimer e Responsabilità

Questo progetto è pubblicato esclusivamente a scopo **didattico, sperimentale e di studio**.

Il sistema SAIA **non è certificato**, né progettato per l’uso commerciale o per l’installazione su veicoli destinati alla circolazione su strada pubblica.

L’autore **non incoraggia né autorizza** utilizzi che possano arrecare danni a persone, veicoli o cose, e **si astiene espressamente da qualsiasi uso improprio** del progetto che possa essere interpretato come pericoloso o contrario alle normative vigenti.

Chiunque replichi, modifichi o utilizzi il progetto lo fa **sotto la propria esclusiva responsabilità**.

L’autore **si dissocia esplicitamente** da ogni utilizzo illecito, pericoloso o non conforme alle norme di sicurezza e al Codice della Strada.
