# Chapter 10

* X = matrix v/d input.
* W = weight matrix.
* b = bias vector.
* $\Phi$ = activation function (phi).
* n = # features.

hieruit kan je dus afleiden:

stel je hebt n = 2, dan geldt als volgt: $\Phi$(b + w1x1 +w2x2)

* Waarom zijn activatiefunctie nodig/nuttig?
  - activatiefuncties zijn nodig om niet lineaire functies te leren

### Coderen C10
* epoch = alle voorbeelden 1x bekijken
* shape=(4,) geeft een tuple terug, shape=(4) geeft een int terug
* Dense layer is een volledig geconnecteerde laag en doet eigenlijk de XW + b
* Softmax wordt berekent als volgt:
  - logits (getal)
  - exp(getal)
  - exp(getal) / som vd exp(getallen)
  - controleren kan je door de som van de softmax te nemen en die moet 1 zijn 
