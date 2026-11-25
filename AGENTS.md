# TFM Ivan — ASV (Autonomous Surface Vehicle)

Context compartit per a tots els assistents d'IA del projecte (Claude Code, Codex, Copilot).
**Si preneu una decisió de disseny, apunteu-la aquí.**

## Projecte

Vaixell de superfície autònom (ASV) imprès en 3D, controlat per un ESP32.
TFM de l'Ivan Peña, codirigit amb en Matias Carandell (UPC).

## Estructura del repositori

| Carpeta     | Contingut |
|-------------|-----------|
| `firmware/` | Codi de l'ESP32 (PlatformIO) |
| `hardware/` | Esquemes elèctrics, PCB, llista de components (BOM), assignació de pins |
| `cad/`      | Fitxers font del disseny 3D. Els STL i STEP grans van a Drive, no aquí |
| `docs/`     | Memòria del TFM, notes, resultats de proves |

## Decisions preses

<!-- Format: data — decisió — motiu -->
- 2026-11-25 — Codi a Git/GitHub, fitxers grans a Drive — el repositori es manté lleuger.

## Hardware

- Microcontrolador: ESP32 (model per concretar)
- Assignació de pins: vegeu `hardware/pinout.md` (per crear)

## Convencions

- Idioma: comentaris i documentació en català; noms de variables i funcions en anglès.
- Cada tasca en una branca pròpia (`firmware/...`, `cad/...`, `docs/...`), i s'integra amb un Pull Request.
- No pugeu credencials (Wi-Fi, claus). Feu servir `secrets.h`, que està al `.gitignore`.

## Com compilar

Per definir quan es creï el projecte de PlatformIO a `firmware/`.
