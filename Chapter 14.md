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
* trainbare parameters => kernel v/d filter (3x3=9) dus 9 !of je input nu 5x5 of 200x200 is, blijft gelijk
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




