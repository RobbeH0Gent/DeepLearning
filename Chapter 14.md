# Deep computer vision using CNN

- Waarom gebruiken we dit/problemen?
  * te veel parameters
  * geen "gedeelde" parameters (telkens opnieuw alles beginnen leren) -> (een hond kan is boven in de afbeelding staan ipv gecentreerd)
-> Oplossing: convolutionele laag

* De invoer is vast
* De filter is trainbaar
* Convolutie maakt gebruik van het inwendig product
* Stride is stapgrootte (zowel horizontaal als verticaal)
* Kernel is hoe groot uw filter is (bv. 3x3) (altijd oneven = duidelijk midden)
* Padding kan
  - valid zijn dan ga je niet uit uw input
  - same zijn dat voeg je extra pixels toe (symmetrisch) (grootte vd output == grootte vd input (als stride = 1))
* aantal vermenigvuldigen met padding = valid => dimensie - n * dimensie - n * kernel v/d filter
* trainbare parameters => kernel v/d filter (3x3=9) dus 9 !of je input mu 5x5 of 200x200 is, blijft gelijk
* kleurenafbeeldingen hebben 3 kanalen -> rood, groen en blauw (examen 2024) => filter wordt een balkje (3 kanalen)
  - aantal vermenigvuldigen zal dan grootte van de kernel x diepte zijn (vb. 3x3x3 = 27 * aantal keer je het doet)
  - extra: bias en activatie functie -> de bias is ook een trainbare parameter dus 27 + 1 = 28
  - hieruit kan je afleiden dat het aantal vermenigvuldigen != aantal trainbare paramters
  - ![image](https://github.com/user-attachments/assets/f608f1fc-4c86-48d8-8ffd-3fbda6e7ecb8)
* feature map is een andere benaming voor een kanaal in de uitvoer (altijd gelijk aan het aantal filters)

### Hoe berekent men zoiets?
![image](https://github.com/user-attachments/assets/1f2f1987-f783-4bd9-bd76-e639b9c5643f)

* ram nogdig voor de parameters -> aantal parameters, het aantal bytes ((bits / 8) * aantal parameters) = 3.613.600 +- 3,6 MB
* ram nodig voor een hele afbeelding -> grootte van de afbeelding heeft van belang.
* 1 Voorspelling
  - Invoer: 200 * 300 * 3 * 4 bytes : 720.000 bytes -> 720 KB (0.72 MB)
  - Eerste laag: 100 * 150 * 100 * 4 bytes : 6.000.000 -> 6 MB
  - Tweede laag: 50 * 75 * 200 * 4 bytes : 3.000.000 -> 3 MB
  - Uitvoer/laatste laag: 25 * 38 * 400 * 4 bytes : 1.520.000 -> 1.52 MB
  - !! niet optellen !!
  - ! het max dat je tegelijkertijd zal nodig hebben is 12.6 MB;
  - ![image](https://github.com/user-attachments/assets/173cf22e-a21e-4416-a9b6-ee90112e06bb)
* Trainen is een ander verhaal, nm. backprop (-> alle tussenstappen zijn nodig)
  - +- 11 MB / afbeelding (wel optellen)
  - ![image](https://github.com/user-attachments/assets/8ec40918-a974-40f7-b796-3fd805c6b64a)
  - +- 550 MB + 3,6 MB (parameters) + 3.6 MB (gradient per parameter) +-= 560 MB

 ## Pooling layers
 - werkt ONafhankelijk op elk kanaal
 - heeft geen leerbare parameters
 - max pooling, pool_size=2, stride=2 (voordeel: juiste translatie in kleine variantie/schuiving)
 - ![image](https://github.com/user-attachments/assets/3fc1463f-53f7-434f-a929-c9585484bb83)
   * ![image](https://github.com/user-attachments/assets/92d3f6c7-9b63-4494-a4d7-38772520b66a)
 - average pooling ipv max, het gemiddelde
 - global average pooling
   * zet het aantal kanalen om naar getallen
   * berekent dan het gemiddelde van de 25 getallen in het eerste kanaal
   * kanalen = feature detector (1024) -> detecteert in welke maten die feature aanwezig is
   * 1 o f2 Fully Connected lagen met op de laatste laag de softmax voor de classificatie
   * ![image](https://github.com/user-attachments/assets/fcc2f096-c968-46fc-bde5-10dda4216762)


## Typische CNN architectuur

* Invoer
* meerdermaal
  - conv layer
  - conv layer
  - pooling
* eventueel een GAP layer
* 1 o f 2 Fully Connected layers
* ![image](https://github.com/user-attachments/assets/1204f089-a571-40b7-8303-1b5cd80ddf16)

* De spatiale dimensie daalt (maw de afbeelding wordt kleiner)
* Het aantal filters/kanalen stijgt (meerdere features)

### Regularisatie
* tegen overfitting
* in het 2e heb je L2- regularisatie gezien
* ![image](https://github.com/user-attachments/assets/fe482799-5ec4-4dca-ac57-9b48f47d54e5)

* Regularisatie in AlexNet
  1. Dropout (tijdens trainen: random activaties op 0 zetten) (heeft geen leerbare parameters)
     - ![image](https://github.com/user-attachments/assets/7f2902bc-437e-475a-8f46-73931f454550)
     - tijdens testen doet het niets

  2. Data augmentatie (foto lichtjes aanpassen (pixels niet exact hetzelfde))
     - ![image](https://github.com/user-attachments/assets/402c304d-7b78-4c8a-9d09-804d1351c4c8)
     - bij het vb van de paddos, is het bv niet muttig dat je die foto op zijn kop zet, want dit komt in de realiteit niet voor.
    
  3. Local Response Normalisation (deze wordt vandaag de dag niet meer gebruikt)
     - ![image](https://github.com/user-attachments/assets/624e555a-8b23-41c8-bec7-19bbeda48721)


* ResNet
  - Residual Connection (skip connection) (makkelijk om van achter naar voor door het netwerk te propageren)
  - ![image](https://github.com/user-attachments/assets/f1fc4ee8-4fa0-4c38-be09-a5b6070974e2)
  1. Eerste lagen zorgen ervoor dat de afbeelding veel kleiner wordt (afb / 4)
  2. Diepe 'stack' residual blocks 
    - (![image](https://github.com/user-attachments/assets/1a9c8b35-9297-49c5-b03d-c4beb0607b79))
    - Kan niet met de sequential API
    - Lukt niet altijd zo gemakkelijk
    - ![image](https://github.com/user-attachments/assets/6526a159-0014-4ea3-85ae-170ac97cefb5)
    - Batch Normalisation
  3. GAP laag
  4. FC + softmax

### Flashback Normalization vorig jaar + Batch normalization bij training
- ![image](https://github.com/user-attachments/assets/c1c7edff-1286-4811-9751-812b0f8273e0)
- ![image](https://github.com/user-attachments/assets/f7324424-9765-406f-9db1-af8764ccdaff)
- Dit lees je als: voor elke rij wordt het gemiddelde afgetrokken gedeelt door de standaardafwijking
- ![image](https://github.com/user-attachments/assets/487bdd58-4822-42ae-b3f8-5e67287b25be)
- met elke standaardafwijking ongeveer 1 en het gemiddelde ongeveer 0
- ![image](https://github.com/user-attachments/assets/b56739cd-c740-4d2d-ab8d-e62a3a0d825b)
- het gemiddelde wordt hier dus gamma en de standaardafwijking beta


### Batch Norm tijdens 'inference' (testen)
- Schatting maken wat de mu en sigma kan zijn over alle trainingsvoorbeelden heen
- ![image](https://github.com/user-attachments/assets/af8e5a7d-fc23-48f8-b463-1e20f8445f14)
- deze parameters zijn niet-leerbaar **maar wij zullen deze zelf aanpassen**
- ![image](https://github.com/user-attachments/assets/4902d547-9b1c-4764-8ad9-77bbfd365f84)
- sigma doen we op dezelfde manier als hierboven
- ![image](https://github.com/user-attachments/assets/9de39a59-7d36-476b-96e1-4cf4c37c13b4)
- 


## Transfer learning

![image](https://github.com/user-attachments/assets/6fc25876-4da8-4881-b246-3d9fb5717c27)
*optionele fine-tuning stap*
![image](https://github.com/user-attachments/assets/e08cd81a-1032-496d-aa05-d3ae734303fe)
![image](https://github.com/user-attachments/assets/b79473f3-8bac-48bc-bd6a-db8abd4bcadc)
**als je dit vergeet is alles kapot!**
![image](https://github.com/user-attachments/assets/ad940f61-87e8-44e8-9451-ffccb01d3e97)
![image](https://github.com/user-attachments/assets/947c2fba-50b2-4220-827b-f2d9eb52d7cc)


Data augmentation -> als je niet zo een grote datasets hebt, is dit handig. (foto een beetje veranderen bv)


## Classificatie en Localisatie

![image](https://github.com/user-attachments/assets/75788a7e-6ee7-4b89-8fd6-02b4fed107e8)
we doen dit niet in pixels maar als volgt: 
![image](https://github.com/user-attachments/assets/593923a6-9212-4298-8dd4-c395aaa73686)
met bv y = 0.6 en x = 0.5 (de oorsprong begint bij pcs altijd linksbovenaan) 
zo worden de hoogte en de breedte ook gerelativeerd
* de classificatie wordt getraind met de X-entropy
* de Bounding box met de MSE (mean square error -> | - |²)
* Opmerkingen bij Bounding Box
![image](https://github.com/user-attachments/assets/d40e2728-9613-458f-bf27-27681bd424ef)
![image](https://github.com/user-attachments/assets/1b01f7b4-a975-440a-9483-c61d30f0c14f)

-> Intercsection over union:
![image](https://github.com/user-attachments/assets/1e94b989-cdbf-4a34-9537-97be53ed31a1)
![image](https://github.com/user-attachments/assets/ccc1eade-37f2-4037-acf9-769197e870c0)
keras.metrics.MeanIoU


## Object detection
* meerdere objecten in een foto die je wilt classificieren en localiseren
* dit netwerk heeft 3 outputs
* ![image](https://github.com/user-attachments/assets/0cbdba4b-db76-483a-9960-5a13eaec0eef)
* obj score -> lage waarden, negeert de andere outputs, andersom dan kijk je wat er staat en waar.
* sliding window approach is traag en hetzelfde object wordt meerdere keren gedetecteerd -> oplossing: non-max suppression
* Non-max suppression
  - invoer: lijst van BBs (met mogelijks dubbels)
  - uitvoer: lijst van BBs (hopelijk zonder dubbels)
  - Stappen:
    1. Verwijder alle BBs met een 'lage' objectness score. (laag kan je zelf kiezen)
    2. Selecteer (en verwijder uit de lijst) de BB met de hoogste objectness score. -> verwijder alle BBs met een 'hoge' IoU, met gekozen BB
    3. Herhaal stap 2 tot de lijst leeg is."

* Fully Convolutional Networks
  - ![image](https://github.com/user-attachments/assets/57bc1bdc-09ca-43ee-b287-0329e86cce11)
  - ![image](https://github.com/user-attachments/assets/6628c3e0-8391-4131-8ac6-b78b056d5bc7)
  - het probleem, dit staat vast: ![image](https://github.com/user-attachments/assets/cbeca284-c071-4fc9-9858-8e12aec8f8fc)
  - voor conv geldt alleen dat het **minstens** 7x7 moet zijn
  - ![image](https://github.com/user-attachments/assets/b66efc5d-2eba-4df2-9b9f-b7e6207b3b0e)
 
 * YOLO
 * Object tracking
 * Semantic segmentation
   - ![image](https://github.com/user-attachments/assets/ebe8d8fd-5a82-454b-b32a-b36a5aa06573)
   - elke pixel in de afbeelding is geclassificeerd tot een klasse (behoort tot een klasse)
  
 * Instance segmentation
   - objecten van dezelfde klassen worden niet gemerged













