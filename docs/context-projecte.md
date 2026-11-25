# Context inicial del TFM

Revisió del 25 de novembre de 2026.

## Objectiu

L'Ivan Peña, estudiant del màster MUENO de la FNB (UPC), i en Matias Carandell treballen en un vehicle de superfície autònom (USV o ASV) imprès en 3D. El projecte parteix del n3m0 de Mike Holden per reproduir-ne la plataforma física i introduir-hi millores graduals. L'esquema preliminar descriu el pilotatge manual per Wi-Fi amb un mòbil com a primera configuració. La navegació autònoma és l'objectiu del TFM i els criteris de validació encara estan per definir.

## Disseny de referència i fitxers d'impressió

El n3m0 és un vaixell desenvolupat per facilitar mesures oceanogràfiques. Té un casc imprès per seccions, motor brushless amb eix i hèlix, i timó accionat per servo. L'original usa Pixhawk amb ArduPilot Rover per seguir punts de pas i un ESP8266 separat per mesurar la temperatura de l'aigua i publicar-ne les dades. L'autor documenta proves de navegació autònoma el 2017. [Projecte a Hackaday](https://hackaday.io/project/25508-n3m0-the-autonomous-boat) · [Instruccions de muntatge](https://hackaday.io/project/25508/instructions)

El ZIP de `Preliminar docs/NEMO/` i el directori local `files/` contenen 21 STL, els mateixos models que enumera el full `PIEZAS 3D`. Hi ha sis seccions del casc i la variant `hull_1-2_from_front_orange`, que agrupa les dues primeres, cinc peces de tapa, el timó i el braç, la mampara de motor, els suports interns, l'antena i el bressol. La còpia revisada conté fitxers STL. Si hi ha STEP al Drive, encara cal identificar-ne la ubicació i la versió. El README i la llicència del paquet atribueixen els models a breezetrees (Mike Holden) i indiquen Creative Commons Attribution. [Models a Thingiverse](https://www.thingiverse.com/thing:3491904)

Les notes locals prioritzen PETG, ABS i PLA, en aquest ordre. Holden documenta un primer casc imprès en PLA. Abans de llançar la tirada completa, convé confirmar el volum de la impressora, la variant de proa i l'ajust dels suports amb les peces reals.

## Primera impressió de la proa amb PETG

El 25 de novembre de 2026 es va llançar la primera impressió de la proa sencera, `hull_1-2_from_front_orange.stl` (seccions 1 i 2 juntes, 184 × 119 × 206 mm). L'STL ja ve orientat: la cara d'unió amb la secció 3 queda contra la placa i la punta apunta amunt. Si cal una prova més curta, `hull_1_from_front_orange.stl` només té la punta (132 × 86 × 81 mm).

**Projecte de Bambu Studio:** `cad/impressio/proa_hull_1-2_PETG_P2S.3mf`, a la carpeta compartida de Drive. No és a Git, perquè el `.gitignore` exclou els `.3mf`. Malgrat el nom, el fitxer està configurat per a la P1S.

| Ajust | Valor aplicat | Motiu |
| --- | --- | --- |
| Impressora i perfil | Bambu Lab P1S, broquet de 0,4 mm, sobre `0.20mm Standard @BBL X1C` | La P1S fa servir els perfils de procés de la X1C |
| Filament i placa | Generic PETG negre (AMS) a 255 °C, Textured PEI a 70 °C | |
| Bucles de paret | **6, generador Arachne** | La paret de l'STL fa ~2,4 mm. Amb 4 bucles (~1,8 mm) quedaria una franja de farciment al mig per on podria filtrar l'aigua. Amb 6 bucles i Arachne, la paret és massissa |
| Capes superiors i inferiors | 5 i 5 | |
| Farciment | 15 % gyroid | Només afecta les zones més gruixudes |
| Costura | Alineada | |
| Velocitat de paret exterior i interior | 60 i 120 mm/s (el perfil base en porta 200 i 300) | Una velocitat més baixa millora l'adhesió entre capes |
| Ventilador | 20–50 % (el perfil base en porta 40–90 %) | Amb PETG, menys ventilació vol dir més adhesió entre capes |
| Brim | Només exterior, 8 mm | La peça és alta i recolza sobre un anell estret |
| Suports | Cap | El 95 % de les cares que miren avall tenen menys de 45°, i amb una paret de 2,4 mm els voladissos es recolzen sols. Els suports quedarien dins la proa, on costa treure'ls, o deixarien rugosa la superfície exterior |

**Previsió:** ~9 h 07 min i ~225 g de PETG.

**Lliçons de Bambu Studio:**
- En canviar de perfil al desplegable es perden els ajustos modificats. En canviar d'impressora, cal triar **Transferir** quan surt l'avís de canvis no desats.
- Per detectar un perfil perdut, mireu el temps estimat. Amb el perfil base, aquesta peça surt per unes 5 h 30 min i 179 g, amb només 2 parets.
- La P2S té una detecció d'acumulacions per sondeig (*Otros → Avanzado*) que val la pena activar. La P1S no la té.

**Pendent:** resultat de la impressió i de la prova d'estanquitat. Feu servir filament sec. Si és Bambu PETG HF, la fitxa indica 65 °C durant 8 h en un assecador amb aire forçat. [Fitxa Bambu PETG HF](https://store.bblcdn.com/s6/default/20423d7f839c4a66b9712508549c68b4/Bambu_PETG_HF_TDS.pdf)

Després d'imprimir, retalleu i polid el brim de la cara d'unió, perquè la junta amb la secció 3 tanqui bé. Si la prova d'estanquitat falla, canvieu els ajustos per aquest ordre: flux al 102–105 %, temperatura +5 °C, ventilador al 30 %.

1. **Prova de la peça en cru.** Submergiu la part baixa durant uns 30 minuts, amb l'obertura d'unió per sobre de l'aigua i paper absorbent sec a dins. Si apareix humitat, marqueu-ne el punt i comproveu si coincideix amb la costura o una zona prima. Anoteu el resultat amb els ajustos que hàgiu fet servir.
2. **Prova del casc muntat.** Reserveu les cares d'unió per a l'encolat. Amb la tapa posada i els passos d'eix i timó tapats provisionalment, repetiu la prova abans de muntar l'electrònica. Holden va detectar porositat a les capes del seu casc i hi va aplicar un recobriment epoxi. [Instruccions del n3m0](https://hackaday.io/project/25508/instructions)
3. **Imprimació i pintura.** Resoleu les fuites abans de fer l'acabat. Proveu l'adherència sobre un retall del mateix PETG, netejat i matisat segons les fitxes dels productes. Si cal un epoxi de segellat, trieu-ne un apte per al contacte amb aigua i comproveu la compatibilitat de la imprimació i la pintura amb l'epoxi curat. Per sota de la línia de flotació, feu servir un acabat que admeti immersió.

## Components i esquema preliminar

L'Excel [Materiales TFM Iván Peña.xlsx](<../Preliminar docs/Materiales TFM Iván Peña.xlsx>) recull alternatives d'AliExpress i Amazon a `COMPRAS`, l'inventari a `PIEZAS 3D` i dues imatges del diagrama a `ESQUEMA`. Els subtotals que mostra són 123,31 € i 174,25 € per als blocs principals, i 44,50 € en cadascun dels blocs de components addicionals. Les llistes inclouen alternatives d'hèlix, quantitats diferents segons el proveïdor i partides sense preu. Cal contrastar les comandes i les peces rebudes abans de donar per tancada la compra.

| Subsistema | Material identificat | Pendent de validar |
| --- | --- | --- |
| Propulsió | D2830 de 1.000 kV, ESC M60A de 60 A per a 2–3S, acoblament de 3,17 a 3,17 mm i eix de 3,17 × 300 mm | L'hèlix A figura amb Ø35 mm i eix de 3,17 mm. La B té un forat de 4 mm i el diàmetre exterior difereix entre l'Excel (44 mm) i el TXT (48 mm). Confirmar la variant, la fixació i el sentit de gir. |
| Segellat i muntatge | Retén NBR, tira adhesiva de 2 × 10 mm, tancaments i vareta del servo | Confirmar el tub de botzina i els seus suports, l'ajust del retén i la compressió de la junta de la tapa. |
| Alimentació i govern | LiPo 3S de 5.000 mAh amb XT60, UBEC anunciat de 5 V / 3 A, servo anunciat de 20 kg·cm / 180° | Verificar la sortida BEC del model d'ESC i el consum del servo. Dimensionar els reguladors a partir de la càrrega real. |
| Control i sensors | Placa ESP-WROOM-32 de 38 pins amb CP2102 i USB-C. Candidats Flywoo GOKU GM10 Pro V3 amb brúixola, OLED I²C de 0,96 polzades, DS18B20 i BNO085 | Confirmar variants, tensions, nivells lògics i interfícies. Assignar els GPIO quan es conegui la placa exacta. |

El [PDF de connexions](<../Preliminar docs/TFM_esquema_conexiones.pdf>) és un esquema funcional de dues pàgines. La LiPo alimenta l'ESC i un UBEC independent per a l'ESP32. L'ESP32 rep les ordres del mòbil i envia senyals a l'ESC i al servo, amb massa comuna. L'alimentació del servo des del BEC de l'ESC queda condicionada a verificar-ne tensió i corrent. El PDF identifica la necessitat d'aturar el motor si es perd l'enllaç. Els sensors figuren a la llista de compres i encara cal incorporar-los al cablejat i definir l'assignació de pins.

## Memòria i validació

- La [plantilla TFE v5 de la FNB](<../Preliminar docs/2025 FNB - Plantilla TFE v5.docx>) dona el format de portades, resums, capítols, bibliografia i annexos. Indica que la portada és obligatòria i proposa un resum de fins a 250 paraules amb abstract en anglès.
- El PDF d'ajuts de 2026 és documentació de context. Preveu un informe breu, un pressupost amb IVA i el vistiplau del tutor. El termini de justificació que hi figura, 30 de setembre de 2026, ja ha passat a la data de la revisió. [Convocatòria FNB 2026](https://www.fnb.upc.edu/sites/default/files/Punt%204%20-%20Convocat%C3%B2ria%20d%27ajuts%20per%20a%20la%20realitzaci%C3%B3%20de%20TFE%20innovadors%202026%20v2.pdf)
- Com a seqüència de treball, provar primer l'ajust de les peces i l'estanquitat del casc. Validar a banc l'alimentació, el servo, l'ESC i la parada per pèrdua de Wi-Fi abans de la primera navegació manual. A partir del prototip funcional, mesurar el comportament original i comparar-hi les millores, per exemple amb una prova repetible de seguiment de punts de pas.
