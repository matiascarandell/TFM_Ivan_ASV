# TFM Ivan — ASV (Autonomous Surface Vehicle)

Context compartit per a tots els assistents d'IA del projecte (Claude Code, Codex, Copilot).
**Si preneu una decisió de disseny, apunteu-la aquí.**

## Projecte

Vaixell de superfície autònom (ASV) imprès en 3D, controlat per un ESP32.
TFM de l'Ivan Peña, estudiant del màster MUENO a la Facultat de Nàutica de Barcelona (UPC), codirigit amb en Matias Carandell.

El punt de partida és el casc imprimible del n3m0 de Mike Holden. L'esquema preliminar planteja una primera versió amb pilotatge manual per Wi-Fi des del mòbil i control del motor i del timó amb un ESP32. L'objectiu del TFM és evolucionar el prototip cap a la navegació autònoma.

Vegeu [el context inicial del TFM](docs/context-projecte.md) per a les fonts, l'inventari de peces, les hipòtesis del muntatge i les comprovacions pendents. L'Ivan treballa amb Codex i en Matias amb Claude Code, que carrega aquest fitxer des de `CLAUDE.md`.

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
- 2026-11-25 — Partir del n3m0 i millorar-lo per iteracions — disposar d'un disseny de referència documentat per comparar-hi els canvis del TFM.

## Hardware

- Microcontrolador: ESP32 (la llista de compres apunta a una placa ESP-WROOM-32 de 38 pins amb CP2102 i USB-C, pendent de confirmar).
- Assignació de pins: vegeu `hardware/pinout.md` (per crear)

## Convencions

- Idioma: comentaris i documentació en català; noms de variables i funcions en anglès.
- Cada tasca en una branca pròpia (`firmware/...`, `cad/...`, `docs/...`), i s'integra amb un Pull Request.
- No pugeu credencials (Wi-Fi, claus). Feu servir `secrets.h`, que està al `.gitignore`.

## Com compilar

Per definir quan es creï el projecte de PlatformIO a `firmware/`.
