# 🏎️ Thrustmaster Ferrari SF1000 Wheel Emulator for ESP32

[🇮🇹 Italiano](#-italiano) | [🇬🇧 English](#-english)

---

## 🇮🇹 Italiano

Emulatore hardware basato su **ESP32** sviluppato da **TF1_team (Bruschetta85)** che permette alle basi **Thrustmaster** (testato su **T818** e **T300RS**) di riconoscere una corona personalizzata come **Formula Wheel Add-On Ferrari SF1000 Edition**, sbloccando tutti i **23 pulsanti della corona** e il **D-Pad a 8 vie** senza bisogno di cavi USB esterni.

### ✨ Caratteristiche Principali
* **Plug & Play senza USB:** L'ESP32 si alimenta direttamente dalla base Thrustmaster (`3.3V`).
* **Supporto Completo SF1000:** 23 pulsanti mappabili (inclusi encoder rotativi e push) + D-Pad completo a 8 direzioni (cardinali e diagonali).
* **Firmware Precompilato:** Non serve configurare librerie o scrivere codice; basta estrarre il file `.bin` dall'archivio `.zip` e caricarlo sull'ESP32.

### ⬇️ Download Firmware (Gratuito / Offerta Libera)

Il firmware è disponibile **gratuitamente**: clicca sul pulsante qui sotto, inserisci **`0`** per il download gratuito oppure lascia un contributo facoltativo per supportare lo sviluppo della versione definitiva con pulsanti ed encoder fisici!

[![Download on Ko-fi](https://shields.io)](https://ko-fi.com/s/cdf13f5114)

### 🛠️ Occorrente
1. Una scheda **ESP32 Dev Module** (30 o 38 pin standard).
2. Un cavo/connettore **Mini-DIN 6 pin** (o adattatore Quick Release Thrustmaster) per collegarsi alla base.
3. Cavetti jumper / saldatore.

### 🔌 Schema dei Collegamenti (Pinout)

Collega i pin della base Thrustmaster all'ESP32 seguendo questa tabella:

| Segnale Base Thrustmaster | Pin ESP32 | Note |
| :--- | :--- | :--- |
| **+3.3V (VCC)** | **`3V3`** | ⚠️ Collegare al pin `3V3`, **NON** a `VIN` / `5V` |
| **GND** | **`GND`** | Massa comune |
| **MOSI** | **`GPIO 23`** | Linea dati dalla base |
| **MISO** | **`GPIO 19`** | Linea dati verso la base |
| **SCK** | **`GPIO 18`** | Clock SPI |
| **CS** | **`GPIO 5`** | Chip Select |
| **Avvio Sequenza Test** | **`GPIO 4`** | Collegare a **`3V3`** per avviare la sequenza automatica di test |

> **Nota sul pin `GPIO 4` (Solo per il firmware di test):** A volante collegato, il sistema resta in attesa a riposo. Collegando il pin `GPIO 4` a `3V3`, partirà la pressione automatica in sequenza di tutti i 23 pulsanti e delle 8 direzioni del D-Pad per verificare il corretto funzionamento nel Pannello di Controllo Thrustmaster.

### 📲 Come Caricare il Firmware sull'ESP32

1. Scarica ed estrai l'archivio **`.zip`** ottenuto da Ko-fi per ottenere il file **`.bin`**.
2. Collega l'ESP32 al PC tramite cavo USB e scegli uno dei due metodi seguenti:

#### Metodo 1: Da Browser (Consigliato)
1. Apri [ESP Web Tool](https://huhn.me) (usa Google Chrome o Microsoft Edge).
2. Clicca su **Connect** e seleziona la porta COM del tuo ESP32.
3. Carica il file **`.bin`** estratto all'indirizzo **`0x0`** e premi **Program**.

#### Metodo 2: Tramite Espressif Flash Download Tool (Windows)
1. Scarica ed esegui **Flash Download Tool** dal sito ufficiale Espressif.
2. Seleziona `ESP32` e `Develop` / `UART`.
3. Seleziona il file **`.bin`** e imposta l'offset **`0x0`**.
4. Imposta:
   * **SPI SPEED:** `40MHz`
   * **SPI MODE:** `DIO`
5. Seleziona la porta **COM** corretta, imposta **BAUD** a `921600` e clicca su **START**.

### 🎮 Primo Avvio e Verifica
1. Scollega il cavo USB dall'ESP32.
2. Collega l'ESP32 alla base **Thrustmaster T818** (o riavvia l'alimentazione della base se già accesa).
3. Apri il **Pannello di Controllo Thrustmaster** su Windows: vedrai comparire l'icona **Formula Wheel Add-On Ferrari SF1000 Edition**.
4. Collega il pin `GPIO 4` a `3V3` per osservare l'attivazione automatica di tutti i pulsanti e del D-Pad.

---

## 🇬🇧 English

Hardware emulator based on **ESP32** developed by **TF1_team (Bruschetta85)** that allows **Thrustmaster** wheelbases (tested on **T818** and **T300RS**) to recognize a custom steering wheel as a **Formula Wheel Add-On Ferrari SF1000 Edition**, unlocking all **23 wheel buttons** and the **8-way D-Pad** without external USB cables.

### ✨ Key Features
* **USB-Free Plug & Play:** The ESP32 is powered directly by the Thrustmaster wheelbase (`3.3V`).
* **Full SF1000 Support:** 23 mappable buttons (including rotary encoders and push buttons) + full 8-way D-Pad (cardinal and diagonal directions).
* **Pre-compiled Firmware:** No need to configure libraries or compile code; simply extract the `.bin` file from the `.zip` archive and flash it onto the ESP32.

### ⬇️ Download Firmware (Free / Pay What You Want)

The firmware is **free**: click the button below, enter **`0`** for a free download, or leave an optional tip to support the development of the full physical buttons & encoders version!

[![Download on Ko-fi](https://shields.io)](https://ko-fi.com/s/cdf13f5114)

### 🛠️ Requirements
1. An **ESP32 Dev Module** board (standard 30 or 38 pins).
2. A **6-pin Mini-DIN** cable/connector (or Thrustmaster Quick Release adapter) to connect to the wheelbase.
3. Jumper wires / soldering iron.

### 🔌 Wiring Diagram (Pinout)

Connect the Thrustmaster wheelbase pins to the ESP32 as follows:

| Thrustmaster Base Signal | ESP32 Pin | Notes |
| :--- | :--- | :--- |
| **+3.3V (VCC)** | **`3V3`** | ⚠️ Connect to `3V3` pin, **NOT** to `VIN` / `5V` |
| **GND** | **`GND`** | Common ground |
| **MOSI** | **`GPIO 23`** | Data line from wheelbase |
| **MISO** | **`GPIO 19`** | Data line to wheelbase |
| **SCK** | **`GPIO 18`** | SPI Clock |
| **CS** | **`GPIO 5`** | Chip Select |
| **Start Test Sequence** | **`GPIO 4`** | Connect to **`3V3`** to start the automatic button test sequence |

> **Note on `GPIO 4` (Test firmware only):** Once connected to the wheelbase, the emulator stays in a clean idle state. Connecting `GPIO 4` to `3V3` triggers the automatic sequential press of all 23 buttons and 8 D-Pad directions so you can verify everything in the Thrustmaster Control Panel.

### 📲 How to Flash the Firmware onto the ESP32

1. Download and extract the **`.zip`** archive from Ko-fi to get the **`.bin`** file.
2. Connect the ESP32 to your PC via USB cable and follow one of the methods below:

#### Method 1: Via Web Browser (Recommended)
1. Open [ESP Web Tool](https://huhn.me) (use Google Chrome or Microsoft Edge).
2. Click **Connect** and select your ESP32 COM port.
3. Load the extracted **`.bin`** file at address **`0x0`** and click **Program**.

#### Method 2: Via Espressif Flash Download Tool (Windows)
1. Download and run **Flash Download Tool** from the official Espressif website.
2. Select `ESP32` and `Develop` / `UART`.
3. Load the extracted **`.bin`** file and set the offset to **`0x0`**.
4. Set the following options:
   * **SPI SPEED:** `40MHz`
   * **SPI MODE:** `DIO`
5. Select your **COM** port, set **BAUD** to `921600`, and click **START**.

### 🎮 First Boot & Verification
1. Unplug the USB cable from the ESP32.
2. Connect the ESP32 to your **Thrustmaster T818** wheelbase (or power-cycle the wheelbase if already on).
3. Open the **Thrustmaster Control Panel** on Windows: the **Formula Wheel Add-On Ferrari SF1000 Edition** icon will appear.
4. Connect `GPIO 4` to `3V3` to watch all buttons and D-Pad directions trigger automatically.

---

## 👤 Author / Autore
Created and tested by **TF1_team (Bruschetta85)**.
