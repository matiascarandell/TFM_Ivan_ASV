# Context inicial del TFM

Revisió del 25 de novembre de 2026.

## Objectiu

L'Ivan Peña, estudiant del màster MUENO de la FNB (UPC), i en Matias Carandell treballen en un vehicle de superfície autònom (USV o ASV) imprès en 3D. El projecte parteix del n3m0 de Mike Holden per reproduir-ne la plataforma física i introduir-hi millores graduals. L'esquema preliminar descriu el pilotatge manual per Wi-Fi amb un mòbil com a primera configuració. La navegació autònoma és l'objectiu del TFM i els criteris de validació encara estan per definir.

## Disseny de referència i fitxers d'impressió

El n3m0 és un vaixell desenvolupat per facilitar mesures oceanogràfiques. Té un casc imprès per seccions, motor brushless amb eix i hèlix, i timó accionat per servo. L'original usa Pixhawk amb ArduPilot Rover per seguir punts de pas i un ESP8266 separat per mesurar la temperatura de l'aigua i publicar-ne les dades. L'autor documenta proves de navegació autònoma el 2017. [Projecte a Hackaday](https://hackaday.io/project/25508-n3m0-the-autonomous-boat) · [Instruccions de muntatge](https://hackaday.io/project/25508/instructions)

El ZIP de `Preliminar docs/NEMO/` i el directori local `files/` contenen 21 STL, els mateixos models que enumera el full `PIEZAS 3D`. Hi ha sis seccions del casc i la variant `hull_1-2_from_front_orange`, que agrupa les dues primeres, cinc peces de tapa, el timó i el braç, la mampara de motor, els suports interns, l'antena i el bressol. La còpia revisada conté fitxers STL. Si hi ha STEP al Drive, encara cal identificar-ne la ubicació i la versió. El README i la llicència del paquet atribueixen els models a breezetrees (Mike Holden) i indiquen Creative Commons Attribution. [Models a Thingiverse](https://www.thingiverse.com/thing:3491904)

Les notes locals prioritzen PETG, ABS i PLA, en aquest ordre. Holden documenta un primer casc imprès en PLA. Abans de llançar la tirada completa, convé confirmar el volum de la impressora, la variant de proa i l'ajust dels suports amb les peces reals.

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
