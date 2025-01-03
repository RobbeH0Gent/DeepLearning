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

 
## Chapter 10
- Artificial Neural Network (ANN) is een machine learning model dat gebaseerd is op de biologische neurons in het menselijk brein.

### 10.1.3 The perceptron
- The perceptron == een laag van TLUs (Threshold Logic Unit) (*afkortingen worden niet op het examen gevraagd*)
![image](https://github.com/user-attachments/assets/acaab279-822a-4fee-9352-6926403c76cc)
met:
* x1 - x3 als input
* w1 - w3 als gewicht bij de input
* b als de bias van de berekeningsunit (bolletje op de afbeelding)
* De TLU berekent 2 dingen:
	- som (z) (eerste logo in de berekeningsunit)
 - stap functie ( step(z) ) (tweede logo in de berekeningsunit)
 - ![image](https://github.com/user-attachments/assets/bbf6bfc4-3765-4cdf-8dd2-f9fd53fd65a4)
 - Als de invoer negatief is -> antwoord = 0 (uit), anders 1 (!! ook voor antwoord = 0)) (a)
* a als antwoord

Oefening:
![image](https://github.com/user-attachments/assets/909dbf21-7007-46ad-a1b7-f5a931800f95)

**dit kunnen we ook makkelijker schrijven als:**
![image](https://github.com/user-attachments/assets/b66375e4-d902-44fe-a4a5-50d9827eb40c)

hierna passen we step functie toe voor de finale antwoorden:
![image](https://github.com/user-attachments/assets/646ec1ca-36f3-4ba4-b690-9c61c3b94677)

**of anders geschreven: (met symbool als activatiefunctie)**
![image](https://github.com/user-attachments/assets/58e4da2f-4a5e-4a09-9644-7a91a5cecf40)

#### Voor de mensen wie hun wiskunde lacking is:
![image](https://github.com/user-attachments/assets/d2b9aad3-ba92-437e-a65d-0c0f845ab873)

**maar informatica is ook niet altijd wiskunde want:**
![image](https://github.com/user-attachments/assets/6e69664f-9b31-45cd-bab9-93bc52a42d63)

dit kan niet in de wiskundige wereld...
maar in informatica gebruikt men broadcasting!
![image](https://github.com/user-attachments/assets/e568ee12-f436-4a47-baa4-f3f5693ded57)

**Te kennen voor het examen**
![image](https://github.com/user-attachments/assets/b08fb904-b6e6-4ce7-a34e-e210d9f60fe3)

Dit lees je als volgt: "de activatiefunctie van perceptron x is gelijk aan de step-functie op (X * W + b)" 


## Multilayer perceptron

- de output van de eerste perceptrons is de invoer van de volgende.
![image](https://github.com/user-attachments/assets/f21f8ac0-8654-4aaa-a24a-2230f1ea498a)

- $W^1$ = [[1,1], [1,1]] (2 input = 2 rijen, 2 outputs = 2 kolommen => 2x2 matrix)
- $b^1$ = [[-1.5, -.5]]
- $W^2$ = [[-1, 1]]
- $b^2$ = [[-0.5]] (!broadcasting is toegestaan!)

- rest van deze oefening is het XOR-probleem (ik heb deze op papier, discord: paus_de_14e)

- MLPs are feedforward NN -> signaal gaat maar in 1 directie
- ![image](https://github.com/user-attachments/assets/fe31b229-7161-49aa-b902-b15ae6b585a3)

### Backpropagation
- ![image](https://github.com/user-attachments/assets/c9c062d7-f615-4903-ae34-764d52ad5dc8)
1. Forward pass (batches gaan van input layer -> hidden layer -> next layer -> ... -> last layer)
2. Backward pass (vanachter weten ze het antwoord, foutmetric wordt berekend) (maakt gebruik van het algoritme: reverse-mode autodiff)

In de volksmond:
- predictie voor een batch, de error wordt berekend op het einde, achterwaarts door elke laag om de foutcontributie te meten voor de parameters en dan de W en b aanpassen


**Alle tussenstappen worden onthouden (zodat je de achterwaartse stap kan doen) -> meer geheugen en verschil met voorspellingen maken**
 

### Gradient descent
aka afgeleide in meerdere dimensies
- dit willen we gebruiken ipv stap functie omdat de stap functie lokaal altijd hetzelfde blijft
  
- activatiefuncties:
* bv sigmoide (zelfde gedrag als de stapfunctie maar minder bruusk) (!! tussen 0 en 1 !!)
* ![image](https://github.com/user-attachments/assets/ad514020-5db8-4ec9-967b-0f5c9f5736c1)
* ![image](https://github.com/user-attachments/assets/7119562a-4826-424a-860e-4d3c974bbe75)

* bv tanh (tangent symbolicus) (!! tussen -1 en 1 !!)
* ![image](https://github.com/user-attachments/assets/9971e8c5-b637-4399-b4c4-35ba2112d57a)
* ![image](https://github.com/user-attachments/assets/ed89bd52-de46-4396-a9d9-48dc8ee349f5)

* bv ReLU (rectified linear unit) (!! 0 ander lineair omhoog !!)
* ![image](https://github.com/user-attachments/assets/da8bae13-dff2-41ee-9e06-57311fe484a0)
* ![image](https://github.com/user-attachments/assets/65f9396d-6871-4ac4-bba3-47984484a48c)


### Regression MLP
- je wilt geen activatie functie gebruiken voor de output neurons. (want je wilt uitkomsten van - $\infty$ t.e.m. $\infty$

- MSE ( - )² (-> nadeel: ² van grote getallen maakt het nog veel groter... outliers hebben meer invloed) (dalparabool)
- ![image](https://github.com/user-attachments/assets/5f4bf360-38e8-4400-9c83-04aa93e33c65)

- MAE | - | (-> nadeel: heeft een knik onderaan	(V))
- ![image](https://github.com/user-attachments/assets/47c78f70-bdf4-41dc-848b-eb69790a26fa)

- Huber loss (combinatie van MAE en MSE)
- ![image](https://github.com/user-attachments/assets/1c4bb0e0-b043-4bee-986d-8f309c7b7c68)


### Classification MLP



 
