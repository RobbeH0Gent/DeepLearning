# Les 1 d1

* Supervised learning -> labels worden meegegeven (juiste antwoord)
	- classificatie (hond of kat)
	- regressie (bv. getal voorspellen)
* Unsupervised learning -> zonder labels (ontdekken van structuur in de data)
	- clustering

## Lineaire regressie:
features: x1, x2, ..., xn (met n features)
- met x1 bv. opp vh huis
- met x2 bv. bouwjaar vh huis
- ... (! in excel zou dit 1 rij zijn)

![image](https://github.com/user-attachments/assets/be167b23-a2b6-4e9a-9b5b-754dd639d464)

Doel: vind de b en de w's zodat het model goed werkt. -> Mean Square Error (wiskundig)
!! zorg dat deze MSE minimaal is !!
![image](https://github.com/user-attachments/assets/ebc92e4a-7615-4ead-a582-0598a6f439f7)
met: 
  - m: aantal trainingspunten
  - som van alle trainingsdata (1 -> m)
  - ^y: voorspelling
  - y: juiste waarde
  - itje boven de y's wijst op het i-de voorbeeld/rij
  - je kwadrateert (²) zodat de outliers niet zo neig opvallen

![image](https://github.com/user-attachments/assets/349ccd62-823d-4d42-93d5-964760bf1c18)

### Normal equation
Optimale waarden voor b en w:
![image](https://github.com/user-attachments/assets/4baddb81-c1c4-4987-8b09-d45c8ac32ad3)
!! werkt alleen voor lineaire regressie !!


## Logistische regressie (binaire classificatie)

![image](https://github.com/user-attachments/assets/06d0ad28-594c-4fad-8463-9b98675fcad9)
Valt te lezen als:
- Wat is de kans dat y = 1 wetende dat x.
	- vb. Wat is de kans dat het een spam e-mail is (y = 1) wetende dat er deze woorden in staan (x)
 - 
!! Je wilt dat je kans tussen 0 en 1 ligt ( 0 <= prob <= 1) !!
![image](https://github.com/user-attachments/assets/7ea5b9e8-c253-4d12-99d7-599b432d2da3)
![image](https://github.com/user-attachments/assets/0e6c66e9-a715-4fa7-84c3-b77d54b7dca8)

Wiskundig klopt dit niet -> BCE
We gebruiken de kostfunctie Binary Crossentropy
![image](https://github.com/user-attachments/assets/0ef8c649-e1fd-4078-b67b-031c2c3ad1f8)

- als y = 1 dan valt het 2e deel weg (want 1-1 = 0 en alles *0 is 0) **Blauw**
- als y = 0 dan val het 1ste deel weg (want *0 is 0) **Paars**

![image](https://github.com/user-attachments/assets/280fc2d4-9fda-4228-b185-be855994c191)

Met gevolg wordt de definitie dus:
![image](https://github.com/user-attachments/assets/f2e97635-aeba-45a6-a639-980d864e3812)


## Verschil tussen machine - en deep learning
- Machine learning gaan we vaak gebruiken voor tabulaire data (bv. data in excel/tabellen)
- Machine learning heeft niet zoveel hyperparameters
- Machine learning kan zelf zinvolle antwoorden geven zonder al te veel data te hebben.

- Deep learning gaan we vooral gebruiken op text, videos, fotos, ...
- Deep learning is zoals LEGO, je kan de lagen op oneindig veel manieren op elkaar zetten
- Deep learning heeft typisch veel meer data nodig dan machine learning om goed te werken.

 
