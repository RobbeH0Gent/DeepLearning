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
* 
