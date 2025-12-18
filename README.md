# Einlauf-Modul-fuer-Brushed-Motoren-und-Servotester-
Dieses Projekt ist ein kombiniertes Servo-Testgeraet und Einlaufgeraet fuer Brushed-Motoren  z. B. aus dem RC-Bereich.  Der Motor wird dabei **ueber einen Fahrtenregler (ESC)** angesteuert.   Der Mikrocontroller erzeugt praezise Servosignale, die definierte Last-, Rampen- und Fahrprofile abfahren, um Kohlen und Kollektor sauber einzulaufen.


## Zweck des Projekts

### 🟢 Einlaufen von Brushed-Motoren
- Schonendes Einlaufen neuer Motoren
- Reduzierung von Funkenbildung
- Gleichmaessigeres Tragbild der Kohlen
- Besserer Wirkungsgrad und laengere Lebensdauer

### 🟢 Servo-Tester
- Klassischer Servo-Test mit Bewegung und Zeitsteuerung
- Ideal zum Pruefen von Servos oder ESC-Reaktionen
- Neutral-, Teil- und Vollgas-Signale

---

## Funktionen

- OLED-Menue (SSD1306, 128×64)
- Bedienung ueber Drehencoder
- Mehrere **Einlauf-Programme**:
  - Standard
  - Sicher (schonend)
  - Power
  - RealDrive
  - Dynamischer Crawler-Einlauf (Vor / Zurueck)
- Servo-Test mit Countdown & Fortschrittsbalken
- Shift-Mode (Getriebe-Simulation)
- Race-Mode (aggressives Gasprofil)
- Not-Exit per Long-Press (Servo geht sofort auf Neutral)

---

## Wichtiger Hinweis

⚠️ **Kein direkter Motoranschluss!**  
Dieses Geraet steuert **ausschliesslich das Servosignal**.

Der Motor muss immer ueber:
- einen **Brushed-ESC**
- oder einen geeigneten Motorregler

betrieben werden.

---
## Hardware

- LGT8 (z. B. LGT8F328P)
- OLED SSD1306 I²C (meist Adresse `0x3C`)
- Servo / ESC an Pin **D10**
- Drehencoder:
  - CLK → D2
  - DT  → D3
  - SW  → D4

---

## Software

- Arduino IDE
- Libraries:
  - Adafruit GFX Library
  - Adafruit SSD1306
  - Servo

Alle Parameter (Pulse, Zeiten, Einlaufprofile) sind in  
`settings.h` zentral einstellbar.

---

## Zielgruppe

- RC-Modellbauer
- Entwickler von Brushed-Motor-Setups
- Werkstatt- und Testaufbauten
- Einlaufgeraete fuer neue oder ueberholte Motoren

---

## Pin-Belegung

### Fahrtenregler / Servo-Ausgang

| Funktion                     | Arduino / LGT8 Pin | Beschreibung                                      |
|------------------------------|--------------------|--------------------------------------------------|
| Fahrtenregler / Servo Signal | **D10**            | PWM-Servosignal (Neutral ca. 1500 µs)            |
| +5–6 V Versorgung            | extern             | Nicht aus dem LGT8 versorgen                     |
| GND                          | GND                | Masse mit LGT8 zwingend verbinden                |

> Hinweis: Der Motor wird **nicht direkt** angeschlossen.  
> Der Anschluss an D10 ist **ausschliesslich das Steuersignal** fuer den Brushed-Fahrtenregler.

---

### Drehencoder

| Funktion        | Arduino / LGT8 Pin | Hinweis                          |
|-----------------|--------------------|----------------------------------|
| Encoder CLK     | D2                 | Interrupt-faehig                 |
| Encoder DT      | D3                 | Richtungs-Erkennung              |
| Encoder Taster  | D4                 | LOW bei gedrueckt (Pullup aktiv) |

---

### OLED Display (SSD1306, I2C)

| Funktion | Arduino / LGT8 Pin | Hinweis                    |
|----------|--------------------|----------------------------|
| SDA      | A4                 | I2C Datenleitung           |
| SCL      | A5                 | I2C Taktleitung            |
| Adresse  | –                  | Standard: `0x3C`           |
| VCC      | 5V                 | Je nach Display auch 3.3 V |
| GND      | GND                | Gemeinsame Masse           |

## Lizenz

MIT License – Nutzung auf eigene Gefahr.
