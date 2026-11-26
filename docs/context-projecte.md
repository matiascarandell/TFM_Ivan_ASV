# Context inicial del TFM

Revisió del 25 de novembre de 2026.

## Objectiu

L'Ivan Peña, estudiant del màster MUENO de la FNB (UPC), i en Matias Carandell treballen en un vehicle de superfície autònom (USV o ASV) imprès en 3D. El projecte parteix del n3m0 de Mike Holden per reproduir-ne la plataforma física i introduir-hi millores graduals. L'esquema preliminar descriu el pilotatge manual per Wi-Fi amb un mòbil com a primera configuració. La navegació autònoma és l'objectiu del TFM i els criteris de validació encara estan per definir.

## Disseny de referència i fitxers d'impressió

El n3m0 és un vaixell desenvolupat per facilitar mesures oceanogràfiques. Té un casc imprès per seccions, motor brushless amb eix i hèlix, i timó accionat per servo. L'original usa Pixhawk amb ArduPilot Rover per seguir punts de pas i un ESP8266 separat per mesurar la temperatura de l'aigua i publicar-ne les dades. L'autor documenta proves de navegació autònoma el 2017. [Projecte a Hackaday](https://hackaday.io/project/25508-n3m0-the-autonomous-boat) · [Instruccions de muntatge](https://hackaday.io/project/25508/instructions)

Els fitxers grans de referència (ZIP i STL del n3m0, imatges, plantilla TFE, Excel de materials i PDF de la convocatòria) són a la [carpeta docs/preliminar del Drive compartit](https://drive.google.com/drive/folders/1IYJpQ53MpCIR9uY6o-lHEXJpz1orXL6a).

El ZIP del n3m0 i el directori files/ contenen 21 STL, els mateixos models que enumera el full `PIEZAS 3D`. Hi ha sis seccions del casc i la variant `hull_1-2_from_front_orange`, que agrupa les dues primeres, cinc peces de tapa, el timó i el braç, la mampara de motor, els suports interns, l'antena i el bressol. La còpia revisada conté fitxers STL. Si hi ha STEP al Drive, encara cal identificar-ne la ubicació i la versió. El README i la llicència del paquet atribueixen els models a breezetrees (Mike Holden) i indiquen Creative Commons Attribution. [Models a Thingiverse](https://www.thingiverse.com/thing:3491904)

Les notes locals prioritzen PETG, ABS i PLA, en aquest ordre. Holden documenta un primer casc imprès en PLA. Abans de llançar la tirada completa, convé confirmar el volum de la impressora, la variant de proa i l'ajust dels suports amb les peces reals.

## Primera impressió de la proa amb PETG

Per imprimir una sola secció, feu servir `hull_1_from_front_orange.stl`. La variant `hull_1-2_from_front_orange.stl` combina les dues primeres seccions. Els valors següents són una proposta per a la primera prova amb broquet de 0,4 mm, pendent de confirmar a la impressora.

| Ajust a Bambu Studio | Valor inicial |
| --- | --- |
| Perfil de procés i orientació | `0.20 mm Standard`. Punta de proa cap amunt i cara plana d'unió contra la placa. |
| Alçada de capa | 0,20 mm |
| Bucles de paret | 4, aproximadament 1,7–1,8 mm on el gruix de l'STL ho permet |
| Capes sòlides superiors i inferiors | 5 a cada costat |
| Farciment | 10% gyroid |
| Costura | Alineada i accessible per inspeccionar-la i segellar-la |
| Velocitat de paret exterior | 45 mm/s |
| Vora d'adhesió (*brim*) | Exterior, 5 mm |
| Suports | Desactivats si la previsualització confirma que no hi ha illes a l'aire |

Seleccioneu el perfil del PETG i de la placa que feu servir i mantingueu-ne les temperatures i la ventilació per a la primera prova. Feu servir filament sec. Si és Bambu PETG HF, la fitxa indica 65 °C durant 8 h en un assecador amb aire forçat. A `Preview`, reviseu per tipus de línia que els perímetres del fons i dels costats siguin continus i que la punta es tanqui sense zones flotants. Deseu el `.3mf` amb els ajustos efectivament aplicats. [Fitxa Bambu PETG HF](https://store.bblcdn.com/s6/default/20423d7f839c4a66b9712508549c68b4/Bambu_PETG_HF_TDS.pdf)

1. **Prova de la peça en cru.** Submergiu la part baixa durant uns 30 minuts, amb l'obertura d'unió per sobre de l'aigua i paper absorbent sec a dins. Si apareix humitat, marqueu-ne el punt i comproveu si coincideix amb la costura o una zona prima. Anoteu el resultat amb els ajustos que hàgiu fet servir.
2. **Prova del casc muntat.** Reserveu les cares d'unió per a l'encolat. Amb la tapa posada i els passos d'eix i timó tapats provisionalment, repetiu la prova abans de muntar l'electrònica. Holden va detectar porositat a les capes del seu casc i hi va aplicar un recobriment epoxi. [Instruccions del n3m0](https://hackaday.io/project/25508/instructions)
3. **Imprimació i pintura.** Resoleu les fuites abans de fer l'acabat. Proveu l'adherència sobre un retall del mateix PETG, netejat i matisat segons les fitxes dels productes. Si cal un epoxi de segellat, trieu-ne un apte per al contacte amb aigua i comproveu la compatibilitat de la imprimació i la pintura amb l'epoxi curat. Per sota de la línia de flotació, feu servir un acabat que admeti immersió.

## Components i esquema preliminar

L'Excel Materiales TFM Iván Peña.xlsx recull alternatives d'AliExpress i Amazon a `COMPRAS`, l'inventari a `PIEZAS 3D` i dues imatges del diagrama a `ESQUEMA`. Els subtotals que mostra són 123,31 € i 174,25 € per als blocs principals, i 44,50 € en cadascun dels blocs de components addicionals. Les llistes inclouen alternatives d'hèlix, quantitats diferents segons el proveïdor i partides sense preu. Cal contrastar les comandes i les peces rebudes abans de donar per tancada la compra.

| Subsistema | Material identificat | Pendent de validar |
| --- | --- | --- |
| Propulsió | D2830 de 1.000 kV, ESC M60A de 60 A per a 2–3S, acoblament de 3,17 a 3,17 mm i eix de 3,17 × 300 mm | L'hèlix A figura amb Ø35 mm i eix de 3,17 mm. La B té un forat de 4 mm i el diàmetre exterior difereix entre l'Excel (44 mm) i el TXT (48 mm). Confirmar la variant, la fixació i el sentit de gir. |
| Segellat i muntatge | Retén NBR, tira adhesiva de 2 × 10 mm, tancaments i vareta del servo | Confirmar el tub de botzina i els seus suports, l'ajust del retén i la compressió de la junta de la tapa. |
| Alimentació i govern | LiPo 3S de 5.000 mAh amb XT60, UBEC anunciat de 5 V / 3 A, servo anunciat de 20 kg·cm / 180° | Verificar la sortida BEC del model d'ESC i el consum del servo. Dimensionar els reguladors a partir de la càrrega real. |
| Control i sensors | Placa ESP-WROOM-32 de 38 pins amb CP2102 i USB-C. Candidats Flywoo GOKU GM10 Pro V3 amb brúixola, OLED I²C de 0,96 polzades, DS18B20 i BNO085 | Confirmar variants, tensions, nivells lògics i interfícies. Assignar els GPIO quan es conegui la placa exacta. |

El [PDF de connexions](preliminar/TFM_esquema_conexiones.pdf) és un esquema funcional de dues pàgines. La LiPo alimenta l'ESC i un UBEC independent per a l'ESP32. L'ESP32 rep les ordres del mòbil i envia senyals a l'ESC i al servo, amb massa comuna. L'alimentació del servo des del BEC de l'ESC queda condicionada a verificar-ne tensió i corrent. El PDF identifica la necessitat d'aturar el motor si es perd l'enllaç. Els sensors figuren a la llista de compres i encara cal incorporar-los al cablejat i definir l'assignació de pins.

## Memòria i validació

- La plantilla TFE v5 de la FNB dona el format de portades, resums, capítols, bibliografia i annexos. Indica que la portada és obligatòria i proposa un resum de fins a 250 paraules amb abstract en anglès.
- El PDF d'ajuts de 2026 és documentació de context. Preveu un informe breu, un pressupost amb IVA i el vistiplau del tutor. El termini de justificació que hi figura, 30 de setembre de 2026, ja ha passat a la data de la revisió. [Convocatòria FNB 2026](https://www.fnb.upc.edu/sites/default/files/Punt%204%20-%20Convocat%C3%B2ria%20d%27ajuts%20per%20a%20la%20realitzaci%C3%B3%20de%20TFE%20innovadors%202026%20v2.pdf)
- Com a seqüència de treball, provar primer l'ajust de les peces i l'estanquitat del casc. Validar a banc l'alimentació, el servo, l'ESC i la parada per pèrdua de Wi-Fi abans de la primera navegació manual. A partir del prototip funcional, mesurar el comportament original i comparar-hi les millores, per exemple amb una prova repetible de seguiment de punts de pas.
