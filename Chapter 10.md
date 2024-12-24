# Les 1 d1

* Supervised learning -> labels worden meegegeven (juiste antwoord)
	- classificatie (hond of kat)
	- regressie (bv. getal voorspellen)
* Unsupervised learning -> zonder labels (ontdekken van structuur in de data)
	- clustering

Lineaire regressie:
	- features: x1, x2, ..., xn (met n features) 
	 met x1 bv. opp vh huis
	 met x2 bv. bouwjaar vh huis
	 ... (! in excel zou dit 1 rij zijn)

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
